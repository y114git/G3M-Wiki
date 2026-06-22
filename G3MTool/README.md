# G3MTool

G3MTool is the command-line tool and reference implementation for the `.g3mpatch` format. It works with GameMaker data files, creates and applies `.g3mpatch` patches, runs batch patch jobs, merges patches, compares files, prints metadata, runs `.csx` scripts, and exposes direct xdelta helpers.

Current code version: **1.2.0**

## Supported data-file extensions

- `.win`
- `.ios`
- `.droid`
- `.unx`

## Commands

| Command | Purpose |
| --- | --- |
| [`patch`](commands/patch.md) | Create, apply, batch-process, validate, or merge `.g3mpatch` files |
| [`xpatch`](commands/xpatch.md) | Create or apply binary xdelta patches |
| [`execute`](commands/execute.md) | Run a `.csx` script, `xdelta`, or an external program |
| [`info`](commands/info.md) | Show metadata for a data file or `.g3mpatch` |
| [`diff`](commands/diff.md) | Compare data files or `.g3mpatch` files and write a Markdown report |
| [`--version`](commands/version.md) | Print the tool version |

## Global options

| Option | Meaning |
| --- | --- |
| `-v`, `--verbose` | Enable verbose output |
| `-l`, `--log <path>` | Enable file logging; use `--log default` to write `logs/{command}_{timestamp}.log` next to the executable |
| `--json` | Output machine-readable JSON for supported commands |
| `--xdelta-path <path>` | Use a specific xdelta executable instead of the bundled binary |
| `--version`, `-V` | Print the version and exit |

## Runtime behavior

- Running `G3MTool` with no arguments starts the interactive prompt.
- The executable name is `G3MTool`.
- The project targets **.NET 10** and is configured for self-contained single-file publish output.
- Platform-specific bundled xdelta binaries are embedded for Windows, Linux, and macOS publish targets.

## Output defaults

When an output path is optional and omitted, commands generally write next to the executable unless a command page states a different default. `diff` writes into `<executable>/diff/` by default.

Batch apply and batch create require `--out-dir` and write generated files into that directory. Batch merge writes patched data files to the current directory by default, can redirect them with `--apply`, and can additionally keep merged `.g3mpatch` files with `--out`.
