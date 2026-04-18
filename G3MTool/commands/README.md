# Commands Overview

G3MTool provides six top-level commands. All commands support the [global options](../getting-started.md#global-options) `--verbose`, `--log`, `--json`, and `--version`.

| Command | Description |
| --- | --- |
| [`patch`](patch.md) | Create, apply, validate, or merge G3M resource patches (`.g3mpatch`) |
| [`xpatch`](xpatch.md) | Create or apply raw xdelta binary patches |
| [`execute`](execute.md) | Run `.csx` C# scripts, passthrough to xdelta, or launch external programs |
| [`info`](info.md) | Display resource counts and metadata for a data file or `.g3mpatch` |
| [`diff`](diff.md) | Compare two data files or patches and generate a Markdown diff report |
| [`version`](version.md) | Print the installed G3MTool version |

All commands that accept a data file accept any GameMaker data file extension: `.win`, `.ios`, `.unx`, `.droid`.

When an output path argument is optional and omitted, output is saved next to the G3MTool executable.
