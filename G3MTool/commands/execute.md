# execute

Execute a `.csx` C# script against a GameMaker data file, pass through arguments to the bundled xdelta binary, or launch an external program.

```
G3MTool execute <target> [args...] [--data <data.win>] [--output <output.win>] [--input <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `target` | Yes | One of: path to a `.csx` script, the literal string `xdelta`, or path to any external executable |
| `args` | No | Arguments forwarded verbatim to the target |

| Option | Alias | Description |
| --- | --- | --- |
| `--data <path>` | `-d` | Path to the data file to load before executing the script. Optional for `.csx` scripts. |
| `--output <path>` | `-o` | Output file path. Required when `--data` is specified. |
| `--input <dir>` | `-i` | Input directory for import scripts (e.g., a folder of exported sprites). Passed to the script as `InputDir`. |

---

## Executing a .csx Script

`.csx` scripts are C# scripts compiled and run at runtime using Roslyn. They receive a `ScriptGlobals` object that gives access to the loaded `UndertaleData` (the parsed GameMaker data file) and the G3MTool API surface.

```bash
# Run a script that modifies a data file
G3MTool execute my_script.csx --data data.win --output patched.win

# Run a script that imports sprites from a folder
G3MTool execute ImportSprites.csx --data data.win --input sprites/ --output patched.win

# Run a script that doesn't need a data file (e.g., generates a report)
G3MTool execute report_generator.csx
```

When `--input` is specified, the directory path is prepended to the script arguments and available as `InputDir` in `ScriptGlobals`.

If `--output` is omitted but `--data` is provided, the output defaults to the same filename as `data`, placed next to the G3MTool executable.

### Built-in Scripts

G3MTool ships a set of built-in Export/Import `.csx` scripts embedded in the binary. These cover all major GameMaker resource types. They are used internally by `patch create` and `patch apply` to serialize and deserialize game resources.

| Script | Purpose |
| --- | --- |
| `ExportSprites.csx` / `ImportSprites.csx` | Sprite frames and metadata |
| `ExportSounds.csx` / `ImportSounds.csx` | Sound asset metadata |
| `ExportCodeEntries.csx` / `ImportCodeEntries.csx` | GML source and bytecode |
| `ExportGameObjects.csx` / `ImportGameObjects.csx` | Object definitions and events |
| `ExportRooms.csx` / `ImportRooms.csx` | Room layouts, layers, instances |
| `ExportBackgrounds.csx` / `ImportBackgrounds.csx` | Background/tileset assets |
| `ExportFonts.csx` / `ImportFonts.csx` | Font definitions and glyph tables |
| `ExportShaders.csx` / `ImportShaders.csx` | GLSL ES vertex and fragment shaders |
| `ExportPaths.csx` / `ImportPaths.csx` | Path assets |
| `ExportTimelines.csx` / `ImportTimelines.csx` | Timeline assets |
| `ExportExtensions.csx` / `ImportExtensions.csx` | Extension definitions |
| `ExportGeneralInfo.csx` / `ImportGeneralInfo.csx` | GeneralInfo block |
| `ExportAudioGroups.csx` / `ImportAudioGroups.csx` | Audio group definitions |
| `ExportEmbeddedTextures.csx` / `ImportEmbeddedTextures.csx` | Embedded texture atlases |
| `ExportTexturePageItems.csx` / `ImportTexturePageItems.csx` | Texture page UV mappings |
| `ExportTextureGroupInfo.csx` / `ImportTextureGroupInfo.csx` | Texture group metadata |
| `ExportTilesets.csx` / `ImportTilesets.csx` | Tileset assets |
| `ExportAssetOrder.csx` / `ImportAssetOrder.csx` | Asset list ordering |

See [CSX Scripting](../csx-scripting.md) for the full `ScriptGlobals` API and how to write custom scripts.

---

## xdelta Passthrough

When `target` is the literal string `xdelta`, all subsequent arguments are forwarded directly to the bundled xdelta3 binary.

```bash
# Equivalent to: xdelta3 -d -s original.win patch.xdelta output.win
G3MTool execute xdelta -d -s original.win patch.xdelta output.win
```

This is provided for compatibility with workflows that use raw xdelta command syntax. For most use cases, [`xpatch`](xpatch.md) is more convenient.

---

## External Program

When `target` is any path other than a `.csx` file, G3MTool launches it as an external process with the given arguments, captures stdout and stderr, and forwards the exit code.

```bash
G3MTool execute some_tool.exe --arg1 value1
```

stdout is printed to stdout, stderr to stderr. The exit code of the external process becomes G3MTool's exit code.
