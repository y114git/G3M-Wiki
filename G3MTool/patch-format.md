# G3M Patch Format

`.g3mpatch` is G3MTool's patch format. It stores a manifest, changed resource files, changed code entries, helper metadata, and optional xdelta fallback data.

G3MTool is the reference implementation for this format.

## Typical Layout

```text
patch_{timestamp}.g3mpatch
├── g3mpatch.json
├── Sprites/
│   └── spr_player/
│       ├── spr_player.json
│       └── spr_player_0.png
├── Sounds/
│   └── snd_music/
│       └── snd_music.json
├── CodeEntries/
│   └── gml_Object_obj_player_Step_0/
│       ├── gml_Object_obj_player_Step_0.gml
│       └── gml_Object_obj_player_Step_0.asm
├── Rooms/
│   └── rm_intro/
│       └── rm_intro.json
├── Helpers/
│   ├── asset_order.txt
│   ├── object_events.json
│   ├── variables_functions.json
│   ├── texture_page_items.json
│   └── sprite_frame_map.json
└── Xdelta/
    └── <hash>.xdelta
```

`Xdelta/` exists only when the patch was created with `--xdelta-fallback`. Older patches may contain legacy exact-fallback data; current G3MTool still accepts it when applying.

Deleted resources are listed in `g3mpatch.json`; they do not need resource payload files.

## Manifest

`g3mpatch.json` contains:

| Field | Description |
| --- | --- |
| `createdAt` | Patch creation timestamp |
| `tool` | Tool name and version |
| `original` | Source data-file metadata |
| `modified` | Modified data-file metadata |
| `resources` | Changed, new, and deleted resources by type |
| `statistics` | Resource and file counts |
| `applyPlan` | Hints used by G3MTool to skip unnecessary apply work |

Example:

```json
{
  "createdAt": "2026-05-29T10:00:00.000Z",
  "tool": {
    "name": "G3MTool",
    "version": "1.1.0"
  },
  "original": {
    "filename": "data.win",
    "size": 123456789,
    "md5": "a1b2c3d4...",
    "bytecodeVersion": 17,
    "gmsVersion": "GM 2022.0",
    "generalInfo": {
      "displayName": "DELTARUNE",
      "name": "DELTARUNE",
      "fileName": "DELTARUNE.exe",
      "config": "Default",
      "gameID": 0,
      "major": 2023,
      "minor": 6,
      "release": 0,
      "build": 0
    }
  },
  "modified": {},
  "resources": {
    "Sprites": {
      "changed": [
        {
          "name": "spr_player",
          "files": {
            "spr_player.json": "Sprites/spr_player/spr_player.json"
          }
        }
      ],
      "new": [],
      "deleted": []
    }
  },
  "statistics": {
    "totalChanged": 1,
    "totalNew": 0,
    "totalDeleted": 0,
    "totalChangedFiles": 2,
    "totalNewFiles": 0
  }
}
```

## Data File Metadata

| Field | Description |
| --- | --- |
| `filename` | Base file name |
| `size` | File size in bytes |
| `md5` | MD5 identity used for exact source checks and optional xdelta fallback checks |
| `bytecodeVersion` | GameMaker bytecode version |
| `gmsVersion` | Interpreted GameMaker version string |
| `generalInfo` | Selected GeneralInfo fields from the data file |

## Resource Changes

Each resource type may contain:

| Field | Description |
| --- | --- |
| `changed` | Resources present in both original and modified files with different content |
| `new` | Resources present only in the modified file |
| `deleted` | Resource names present only in the original file |

Resource payloads are exported only for changed and new resources. Some resource types may be promoted to a full-type export when order, duplicate names, version-sensitive layout, or merge safety requires it.

## Resource Types

Common keys include:

| Key | Contents |
| --- | --- |
| `GeneralInfo` | Game metadata |
| `Options` | Game options |
| `Language` | Language data |
| `Sprites` | Sprite metadata and frame PNGs |
| `Sounds` | Sound metadata and embedded audio references |
| `CodeEntries` | GML source and bytecode assembly |
| `GameObjects` | Object definitions and events |
| `Rooms` | Room definitions, layers, instances, tiles |
| `Backgrounds` | Background and tileset resources |
| `Fonts` | Font metadata and glyph data |
| `Scripts` | Script wrapper resources |
| `Shaders` | Shader source |
| `Paths` | Path resources |
| `Timelines` | Timeline resources |
| `Extensions` | Extension metadata |
| `Variables` | Variable table |
| `Functions` | Function table |
| `Strings` | String table |
| `AudioGroups` | Audio group definitions |
| `EmbeddedAudio` | Embedded audio payloads |
| `EmbeddedTextures` | Texture page payloads |
| `TexturePageItems` | Texture page item mappings |
| `TextureGroupInfo` | Texture group metadata |
| `AnimationCurves` | Animation curve resources |
| `Sequences` | Sequence resources |
| `ParticleSystems` | Particle system resources |
| `ParticleSystemEmitters` | Particle emitter resources |
| `EffectInfo` | Effect data |

## Helpers

G3MTool writes helper files only when they are needed for reliable apply or merge behavior. Helper files can preserve resource ordering, object-event links, code metadata, texture mappings, and sprite frame mappings.

These helpers exist to prevent index drift, broken event links, texture-page mismatches, and code reference errors when a patch targets a data file that is not byte-identical to the original.

## Xdelta Fallback

`patch create --xdelta-fallback` stores an xdelta fallback built from the original and modified data files.

`patch apply` behavior:

| Mode | Behavior |
| --- | --- |
| Default | Try normal `.g3mpatch` apply first. If it fails and the patch contains fallback data, try xdelta. |
| `--xdelta-fallback` | Try xdelta first. If it fails, continue with normal `.g3mpatch` apply. |

The fallback is exact but depends on xdelta's source-file requirements. It can increase patch size.

## `.g3mcache`

`.g3mcache` is separate from `.g3mpatch`. Commands use it only when the user passes `--cache <dir>`.

The cache can store data-file metadata, resource hashes, name counts, order-sensitive names, and standard `info` snapshots. G3MTool validates cache entries by file size and stored MD5 when available before use. Cache data helps analysis-heavy commands skip repeated work; it does not replace resource payloads during apply.

## Creation Flow

1. Load or reuse analysis for the original data file.
2. Load the modified data file. If the input is `.xdelta`, apply it to the original first.
3. Hash resources by type and name.
4. Compare original and modified hashes.
5. Export changed/new resources from the modified data file.
6. Store changed code as GML and/or ASM where needed.
7. Add helper data required by the changed resource types.
8. Write `g3mpatch.json` and the patch contents.
9. Remove temporary files.

## Apply Flow

1. Read the patch manifest and needed payloads.
2. Load the target data file.
3. Choose the required import steps from `applyPlan` and changed resource types.
4. Apply resources and helper-guided repairs.
5. Validate critical references.
6. Write the output data file.

G3MTool skips heavy operations only when the patch content and apply plan show that the operation is not needed.
