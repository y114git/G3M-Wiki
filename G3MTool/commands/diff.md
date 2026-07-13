# diff

Compare data files or `.g3mpatch` files and write a Markdown report.

```bash
G3MTool diff <file1> <file2> [output-dir] [--full] [--cache <dir>]
```

- **Argument:** `file1`
  - **Required:** Yes
  - **Description:** First data file or `.g3mpatch`

- **Argument:** `file2`
  - **Required:** Yes
  - **Description:** Second data file or `.g3mpatch`

- **Argument:** `output-dir`
  - **Required:** No
  - **Description:** Directory for the report. Default: `diff/` next to the
    executable

- **Option:** `--full`
  - **Description:** Generate full text/code/JSON diffs plus deeper TPI,
    reference, and asset-order details

- **Option:** `--cache <dir>`
  - **Description:** Reuse `.g3mcache` analysis for repeated data-file
    comparisons

The report file is named `diff_{timestamp}.md`.

## Modes

- **Mode:** Standard
  - **Behavior:** Reports resource-level differences, changed text-file counts,
    resource counts, asset-order/index differences, sprite frame differences,
    and selected reference checks

- **Mode:** `--full`
  - **Behavior:** Includes detailed text/code/JSON diffs and deeper
    exported-resource detail

With global `--json`, `diff` writes a single JSON object to stdout and still
writes the Markdown report to disk.
