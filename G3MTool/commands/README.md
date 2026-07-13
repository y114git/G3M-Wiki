# Commands Overview

- **Command:** [`patch`](patch.md)
  - **Description:** Create, apply, batch-process, validate, or merge
    `.g3mpatch` files

- **Command:** [`xpatch`](xpatch.md)
  - **Description:** Create or apply xdelta patches

- **Command:** [`execute`](execute.md)
  - **Description:** Run a `.csx` script, invoke `xdelta`, or launch an external
    program

- **Command:** [`info`](info.md)
  - **Description:** Show metadata for a data file or `.g3mpatch`

- **Command:** [`diff`](diff.md)
  - **Description:** Compare data files or `.g3mpatch` files and write a
    Markdown report

- **Command:** [`--version`](version.md)
  - **Description:** Print the installed G3MTool version

All data-file arguments accept `.win`, `.ios`, `.unx`, and `.droid`.

Global options are documented in
[Getting Started](../getting-started.md#global-options). Commands that support
`--cache <dir>` reuse `.g3mcache` analysis; commands that support `--json` emit
machine-readable JSON; commands that use xdelta can also take the global
`--xdelta-path <path>` override.

`patch batch apply`, `patch batch create`, and `patch batch merge` are for
non-interactive bulk work and deduplicate identical jobs during the run. Batch
apply/create require `--out-dir`; batch merge writes data outputs by default and
uses `--out` only when you also want merged `.g3mpatch` files.
