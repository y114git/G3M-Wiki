# G3M Patch Format

A `.g3mpatch` file is a standard ZIP archive. It contains a JSON manifest (`g3mpatch.json`), exported resource data for every changed or added resource, GML and assembly source for changed code entries, helper data (asset order), and optionally an exact xdelta fallback patch.

---

## Archive Structure

```
patch_{timestamp}.g3mpatch   ← ZIP archive
├── g3mpatch.json            ← Manifest (see below)
├── Sprites/
│   └── spr_player/
│       ├── spr_player.json          ← Sprite metadata
│       └── spr_player_frame0.png    ← Texture frames
├── Sounds/
│   └── snd_music/
│       └── snd_music.json
├── CodeEntries/
│   └── gml_Object_obj_player_Step_0/
│       ├── gml_Object_obj_player_Step_0.gml   ← Decompiled GML source
│       ├── gml_Object_obj_player_Step_0.asm   ← Bytecode assembly
│       └── child_entry.asm                    ← Child entry assembly (if any)
├── Rooms/
│   └── rm_intro/
│       └── rm_intro.json
├── Helpers/
│   └── assetorder.json       ← Asset list ordering metadata
└── Xdelta/                   ← Optional, only with --xdelta-fallback
    └── <hash>.xdelta         ← Exact binary xdelta fallback
```

Every changed or newly added resource gets its own named subfolder under its resource type directory. Deleted resources are listed only in the manifest — no files are included for them.

---

## Manifest (`g3mpatch.json`)

```json
{
  "createdAt": "2025-11-01T14:22:00.000Z",
  "tool": {
    "name": "G3MTool",
    "version": "1.0.0"
  },
  "original": {
    "filename": "data.win",
    "size": 123456789,
    "md5": "a1b2c3d4...",
    "bytecodeVersion": 17,
    "gmsVersion": "2.3.7.606",
    "generalInfo": {
      "displayName": "DELTARUNE",
      "name": "DELTARUNE",
      "fileName": "DELTARUNE.exe",
      "config": "Default",
      "gameID": 12345678,
      "major": 1, "minor": 0, "release": 0, "build": 0,
      "defaultWindowWidth": 640, "defaultWindowHeight": 480,
      "steamAppID": 1671210
    }
  },
  "modified": { ... },
  "resources": {
    "Sprites": {
      "changed": [
        { "name": "spr_player", "files": { "spr_player.json": "Sprites/spr_player/spr_player.json" } }
      ],
      "new": [],
      "deleted": []
    },
    "CodeEntries": {
      "changed": [
        {
          "name": "gml_Object_obj_player_Step_0",
          "files": {
            "gml_Object_obj_player_Step_0.gml": "CodeEntries/gml_Object_obj_player_Step_0/gml_Object_obj_player_Step_0.gml",
            "gml_Object_obj_player_Step_0.asm": "CodeEntries/gml_Object_obj_player_Step_0/gml_Object_obj_player_Step_0.asm"
          }
        }
      ],
      "new": [],
      "deleted": ["gml_Script_old_function"]
    }
  },
  "statistics": {
    "totalChanged": 3,
    "totalNew": 1,
    "totalDeleted": 1,
    "totalChangedFiles": 5,
    "totalNewFiles": 2
  }
}
```

### `original` / `modified` Fields

| Field | Type | Description |
| --- | --- | --- |
| `filename` | string | Base filename of the data file |
| `size` | integer | File size in bytes |
| `md5` | string | MD5 hash of the data file |
| `bytecodeVersion` | integer | GameMaker bytecode version |
| `gmsVersion` | string | GameMaker Studio version string |
| `generalInfo` | object | Full GeneralInfo block from the data file |

### `resources` Dictionary

Keyed by resource type. Every type with at least one change is present. Types with no changes are omitted.

| Key | Description |
| --- | --- |
| `changed` | List of resources that existed in `original` and differ in `modified`. Each entry has `name` and `files`. |
| `new` | List of resources present in `modified` but not in `original`. |
| `deleted` | List of resource names present in `original` but not in `modified`. No files included — deletion is applied by name. |

### Resource Types

| Type key | Game assets |
| --- | --- |
| `Sprites` | Sprites and their texture frames |
| `Sounds` | Sound assets (metadata; audio banks are separate files) |
| `CodeEntries` | GML code entries — both GML source and bytecode `.asm` |
| `GameObjects` | Object definitions, events, physics |
| `Rooms` | Room layouts, layers, instances |
| `Backgrounds` | Background/tileset assets |
| `Fonts` | Fonts and glyph tables |
| `Scripts` | Script assets (wrappers referencing CodeEntries) |
| `Shaders` | GLSL ES vertex + fragment shaders |
| `Paths` | Path assets |
| `Timelines` | Timeline assets |
| `Extensions` | Extension definitions and file references |
| `Variables` | Variable table |
| `Functions` | Function table |
| `Strings` | String table |
| `AudioGroups` | Audio group definitions |
| `EmbeddedTextures` | Embedded texture atlases |
| `TexturePageItems` | Texture page item UV mappings |
| `TextureGroupInfo` | Texture group metadata |

### `statistics` Fields

| Field | Description |
| --- | --- |
| `totalChanged` | Total number of changed resources across all types |
| `totalNew` | Total number of new resources across all types |
| `totalDeleted` | Total number of deleted resources across all types |
| `totalChangedFiles` | Total number of files belonging to changed resources |
| `totalNewFiles` | Total number of files belonging to new resources |

---

## Optional Xdelta Fallback (`Xdelta/`)

By default, `patch create` does not embed a binary fallback. Passing `--xdelta-fallback` adds a full xdelta3 binary patch in `Xdelta/`. This is an exact diff of the original and modified data files and is used if the semantic resource-level apply fails or if the semantic output hash does not match the expected modified-file hash. Legacy patches with `Exact/` are still accepted by `patch apply`.

---

## How a Patch Is Created

1. Load original `data.win` into memory → hash all resources by type and name using SHA-based content hashing.
2. Load modified `data.win` into memory → hash all resources.
3. Compare hashes per type: identify which resource names are **changed**, **new**, or **deleted**.
4. For changed/new resources (except CodeEntries): export their data from the modified data file to a temporary directory.
5. For CodeEntries: decompile GML source and serialize bytecode assembly directly to memory (no disk I/O).
6. Build the `G3MPatchManifest` from the comparison results.
7. Create the ZIP archive: write `g3mpatch.json`, add exported resource files, write code entries from memory, add asset order helpers, and optionally embed the xdelta fallback.
8. Clean up all temporary files.

If the `modified` argument is an `.xdelta` file instead of a `.win`, G3MTool applies it to the original first to get the modified data file, then proceeds normally with the result.

---

## Version-Sensitive Export Promotion

When the GameMaker version changes between `original` and `modified` (e.g., a game update), the binary layout of some resource types changes. G3MTool automatically promotes `Rooms` and `TextureGroupInfo` to full-export (all resources, not just changed ones) in this case, to prevent applying old binary format data with a new format game.
