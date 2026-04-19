# info

Display information about a GameMaker data file or a `.g3mpatch` file.

```
G3MTool info <target> [--verbose]
```

| Argument | Required | Description |
| --- | --- | --- |
| `target` | Yes | Path to a data file (`.win`, `.ios`, `.unx`, `.droid`) or a `.g3mpatch` file |

| Option | Alias | Description |
| --- | --- | --- |
| `--verbose` | `-v` | Show full per-resource detailed listing (every item with all properties) |
| `--json` | | Output all information as structured JSON |

---

## Data File Info

### Without `--verbose`

Prints a summary:

```
Data File: data.win
Size: 123,456,789 bytes
Game: DELTARUNE
Bytecode: 17
Version: 2.3.7.606

Resources:
  Sprites:         482
  Sounds:          318
  Code:           4721
  GameObjects:     276
  Rooms:            89
  Backgrounds:      61
  Fonts:            14
  Scripts:         194
  Shaders:          12
  Paths:             8
  Timelines:         3
  Extensions:        5
  Variables:      2104
  Functions:       892
  Strings:        8832
  AudioGroups:       6
  EmbTextures:      28
  TexPageItems:   3047
  TexGroupInfo:      4
  Tilesets:         61

GeneralInfo:
  DisplayName: DELTARUNE
  Name: DELTARUNE
  FileName: DELTARUNE.exe
  Config: Default
  GameID: 12345678
  Version: 1.0.0 (build 0)
  Window: 640x480
  SteamAppID: 1671210
  BytecodeVersion: 17
  GMS2FPS: 30.0
  Rooms: 89

Variables by InstanceType:
  Self           1832
  Global          272

Functions (first/last):
  [0]    @@is_string@@
  [891]  scr_custom_end

Code entries: 312 top-level, 4409 child

AudioGroups:
  [0] audiogroup_default
  [1] audiogroup_music
  ...

Extensions:
  GMExtensionXbox
  ...

Room order (89 rooms):
  [0] rm_init
  [1] rm_title
  ...
```

### With `--verbose`

Prints the summary above, then a full per-resource listing for every resource type. For each resource, all relevant properties are shown on one line. Examples:

**Sprites:**
```
=== Sprites (482) ===
  [0] spr_player  64x64  origin:(32,32)  frames:8  mask:RotatedRect  bbox:(4,4,60,60)  speed:15
  [1] spr_enemy_A  32x32  origin:(16,32)  frames:4  ...
```

**Sounds:**
```
=== Sounds (318) ===
  [0] snd_step  type:normal  flags:Regular  vol:1.00  group:audiogroup_sfx  file:snd_step.ogg
```

**Code Entries:**
```
=== Code Entries (4721) ===
  [0] gml_Object_obj_player_Create_0  len:2048  locals:12  args:0  parent:-  children:3
  [1] gml_Object_obj_player_Step_0    len:8192  locals:7   args:0  parent:-  children:1
```

**GameObjects:**
```
=== GameObjects (276) ===
  [0] obj_player  sprite:spr_player  parent:<none>  depth:0  [visible,persistent]
        events: Create_0, Step_0, Step_2, Draw_0, Other_10
```

**Rooms:**
```
=== Rooms (89) ===
  [0] rm_town_01  640x480  layers:5  instances:42  speed:30  persistent:false  creationCode:gml_Room_rm_town_01_Create
        layer: Background  type:Background  depth:100  instances:0
        layer: Instances   type:Instances   depth:0    instances:42
```

**Fonts:**
```
=== Fonts (14) ===
  [0] fnt_main  display:Arial  size:12  bold:false  italic:false  glyphs:95  range:32-126
```

**EmbeddedTextures:**
```
=== EmbeddedTextures (28) ===
  [0] texture_0  2048x2048
  [1] texture_1  2048x1024
```

---

## Patch File Info

When `target` is a `.g3mpatch` file:

### Without `--verbose`

```
G3M Patch: my_mod.g3mpatch
Created: 2025-11-01T14:22:00Z
Tool: G3MTool v1.0.0

Original:
  File: data.win
  Size: 123,456,789 bytes
  GMS: 2.3.7.606

Statistics:
  Changed: 12
  New: 2
  Deleted: 1
```

### With `--verbose`

Adds a per-type resource breakdown:

```
Resources by type:
  Sprites: 3 changed, 1 new, 0 deleted
  CodeEntries: 8 changed, 1 new, 1 deleted
  Rooms: 1 changed, 0 new, 0 deleted
```

### With `--json`

Outputs the complete `G3MPatchManifest` as indented JSON. See [G3M Patch Format](../patch-format.md) for the schema.
