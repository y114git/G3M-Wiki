# G3MTool

G3MTool is the command-line tool and reference implementation for the `.g3mpatch` format. It works with GameMaker data files (`.win`, `.ios`, `.unx`, `.droid`), creates and applies patches, merges mods, compares files, prints metadata, runs `.csx` scripts, and can use xdelta when needed.

Current documented version: `1.1.0`.

## Commands

| Command | Purpose |
| --- | --- |
| [`patch`](commands/patch.md) | Create, apply, validate, or merge `.g3mpatch` files |
| [`xpatch`](commands/xpatch.md) | Create or apply binary xdelta patches |
| [`execute`](commands/execute.md) | Run `.csx` scripts, invoke bundled xdelta, or launch an external program |
| [`info`](commands/info.md) | Inspect a data file or `.g3mpatch` |
| [`diff`](commands/diff.md) | Compare data files and/or `.g3mpatch` files |
| [`--version`](commands/version.md) | Print the installed G3MTool version |

## Core Terms

| Term | Meaning |
| --- | --- |
| `.g3mpatch` | G3MTool's patch format. It stores resource-level changes, metadata, helper data, and optionally an xdelta fallback. |
| xdelta | Binary patch format. It can be smaller for exact file replacement, but it depends on the expected original file. |
| data file | GameMaker data file accepted by G3MTool: `.win`, `.ios`, `.unx`, or `.droid`. |
| `.g3mcache` | Optional analysis cache used by commands that support `--cache <dir>`. It stores reusable metadata and hashes, not replacement resource payloads. |

## Global Options

| Option | Alias | Description |
| --- | --- | --- |
| `--verbose` | `-v` | Print detailed logs and timing breakdowns |
| `--log [path]` | `-l` | Write a log file. If no path is supplied, G3MTool writes to `logs/{command}_{timestamp}.log` next to the executable |
| `--json` | | JSON output for commands that support it |
| `--version` | `-V` | Print the version and exit |

## Platform Support

G3MTool targets .NET 10 and can be published as a self-contained binary.

| Runtime | Platform |
| --- | --- |
| `win-x64` | Windows 64-bit |
| `linux-x64` | Linux 64-bit |
| `linux-arm64` | Linux ARM64 |
| `osx-x64` | macOS Intel |
| `osx-arm64` | macOS Apple Silicon |

## Output Defaults

When an output path is optional and omitted, G3MTool writes command output next to the executable unless the command page states another default. `diff` writes reports to a `diff/` directory next to the executable.
