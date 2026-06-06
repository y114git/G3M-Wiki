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
| `--output <path>` | `-o` | Output file path; required in practice for write-producing script workflows |
| `--input <dir>` | `-i` | Input directory passed to the script as the first script argument |

## `.csx` scripts

```bash
G3MTool execute script.csx --data data.win --output patched.win
G3MTool execute import_sprites.csx --data data.win --input sprites --output patched.win
G3MTool execute report.csx
```

Current behavior:

- If `--data` is set, G3MTool loads the file into the script globals.
- If `--input` is set, the directory path is prepended to script arguments.
- If `--data` is set and `--output` is omitted, the command falls back to a file path next to the executable using the same file name as the input data file.
- If `--data` is omitted, the script can still run, but data-dependent helpers must handle the missing loaded file.

## xdelta passthrough

```bash
G3MTool execute xdelta -d -s original.win patch.xdelta output.win
```

Use this for raw xdelta arguments. For the common create/apply workflow, [`xpatch`](xpatch.md) is simpler.

## External programs

```bash
G3MTool execute some_tool.exe --arg value
```

G3MTool starts the program, forwards stdout and stderr, and returns the child process exit code.

## Built-in scripts

G3MTool embeds import and export scripts under `G3MToolCLI/Assets/scripts/`. They cover the resource families currently represented by those embedded script files, including sprites, sounds, code entries, game objects, rooms, backgrounds, fonts, shaders, paths, timelines, extensions, GeneralInfo, audio groups, embedded textures, texture page items, texture group info, asset order, and tilesets.

See [CSX Scripting](../csx-scripting.md) for script globals and compatibility details.
