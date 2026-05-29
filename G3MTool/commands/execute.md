# execute

Run a `.csx` script, invoke bundled xdelta, or launch an external program.

```bash
G3MTool execute <target> [args...] [--data <data-file>] [--output <output>] [--input <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `target` | Yes | `.csx` script path, `xdelta`, or external program path |
| `args` | No | Arguments passed to the target |

| Option | Alias | Description |
| --- | --- | --- |
| `--data <path>` | `-d` | Data file to load before running a `.csx` script |
| `--output <path>` | `-o` | Output file or directory path. If `--data` is set and `--output` is omitted, G3MTool writes next to the executable |
| `--input <dir>` | `-i` | Input directory passed to the script as its first script argument |

## `.csx` Scripts

```bash
G3MTool execute script.csx --data data.win --output patched.win
G3MTool execute import_sprites.csx --data data.win --input sprites --output patched.win
G3MTool execute report.csx
```

When `--data` is set, G3MTool loads the data file into `ScriptGlobals.Data`. When `--input` is set, G3MTool prepends the directory path to the script arguments.

## xdelta Passthrough

```bash
G3MTool execute xdelta -d -s original.win patch.xdelta output.win
```

Use this for raw xdelta3 arguments. For common xdelta create/apply operations, [`xpatch`](xpatch.md) is simpler.

## External Programs

```bash
G3MTool execute some_tool.exe --arg value
```

G3MTool starts the program, forwards stdout/stderr, and exits with the program exit code.

## Built-In Scripts

G3MTool embeds import/export scripts used by its patch pipeline. They cover major GameMaker resource types, including sprites, sounds, code entries, game objects, rooms, backgrounds, fonts, shaders, paths, timelines, extensions, GeneralInfo, audio groups, embedded textures, texture page items, texture group info, tilesets, and asset order.

See [CSX Scripting](../csx-scripting.md) for script globals and compatibility notes.
