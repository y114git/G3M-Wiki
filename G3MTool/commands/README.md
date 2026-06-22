# Commands Overview

| Command | Description |
| --- | --- |
| [`patch`](patch.md) | Create, apply, batch-process, validate, or merge `.g3mpatch` files |
| [`xpatch`](xpatch.md) | Create or apply xdelta patches |
| [`execute`](execute.md) | Run a `.csx` script, invoke `xdelta`, or launch an external program |
| [`info`](info.md) | Show metadata for a data file or `.g3mpatch` |
| [`diff`](diff.md) | Compare data files or `.g3mpatch` files and write a Markdown report |
| [`--version`](version.md) | Print the installed G3MTool version |

All data-file arguments accept `.win`, `.ios`, `.unx`, and `.droid`.

Global options are documented in [Getting Started](../getting-started.md#global-options). Commands that support `--cache <dir>` reuse `.g3mcache` analysis; commands that support `--json` emit machine-readable JSON; commands that use xdelta can also take the global `--xdelta-path <path>` override.

`patch batch apply`, `patch batch create`, and `patch batch merge` are for non-interactive bulk work and deduplicate identical jobs during the run. Batch apply/create require `--out-dir`; batch merge writes data outputs by default and uses `--out` only when you also want merged `.g3mpatch` files.
