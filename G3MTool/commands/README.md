# Commands Overview

| Command | Description |
| --- | --- |
| [`patch`](patch.md) | Create, apply, validate, or merge `.g3mpatch` files |
| [`xpatch`](xpatch.md) | Create or apply xdelta patches |
| [`execute`](execute.md) | Run a `.csx` script, invoke `xdelta`, or launch an external program |
| [`info`](info.md) | Show metadata for a data file or `.g3mpatch` |
| [`diff`](diff.md) | Compare data files or `.g3mpatch` files and write a Markdown report |
| [`--version`](version.md) | Print the installed G3MTool version |

All data-file arguments accept `.win`, `.ios`, `.unx`, and `.droid`.

Global options are documented in [Getting Started](../getting-started.md#global-options). Commands that support `--cache <dir>` reuse `.g3mcache` analysis; commands that support `--json` emit machine-readable JSON; commands that use xdelta can also take the global `--xdelta-path <path>` override.
