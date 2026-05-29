# diff

Compare data files and/or `.g3mpatch` files and write a Markdown report.

```bash
G3MTool diff <file1> <file2> [output-dir] [--full] [--cache <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `file1` | Yes | First data file or `.g3mpatch` |
| `file2` | Yes | Second data file or `.g3mpatch` |
| `output-dir` | No | Directory for the report. Default: `diff/` next to the executable |

| Option | Description |
| --- | --- |
| `--full` | Include full text/code/JSON diffs, including binary-heavy exported resource folders |
| `--cache <dir>` | Reuse `.g3mcache` analysis for repeated data-file comparisons |

The report file is named `diff_{timestamp}.md`.

## Modes

| Mode | Behavior |
| --- | --- |
| Standard | Reports resource-level changed/new/deleted entries and avoids expensive full text diffs for binary-heavy folders |
| `--full` | Exports more resource data and includes detailed text/code/JSON diffs |

Standard mode is the default because it is faster and produces smaller reports. Use `--full` when you need detailed property or code differences.

## Supported Inputs

| Input Pair | Behavior |
| --- | --- |
| data vs data | Compare resource hashes and report changed/new/deleted resources |
| data vs `.g3mpatch` | Compare patch contents against the data file |
| `.g3mpatch` vs `.g3mpatch` | Compare patch manifests and resource lists |

## Example

```bash
G3MTool diff data_v1.win data_v2.win reports --cache .g3mcache
G3MTool diff data_v1.win data_v2.win reports --full
```

`diff` is read-only. It does not modify data files or patches.
