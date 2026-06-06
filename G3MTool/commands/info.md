# info

Show metadata for a data file or `.g3mpatch`.

```bash
G3MTool info <target> [-v] [--json] [--cache <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `target` | Yes | Data file (`.win`, `.ios`, `.unx`, `.droid`) or `.g3mpatch` |

| Option | Alias | Description |
| --- | --- | --- |
| `--verbose` | `-v` | Print full per-resource listings |
| `--cache <dir>` | | Store and reuse the standard non-verbose data-file info snapshot |

`--json` is a global option and is also supported by `info`.

## Data file output

Without `--verbose`, `info` prints:

- file name, size, game name, bytecode version, and interpreted GameMaker version
- resource counts
- selected GeneralInfo fields
- variable counts by instance type
- first and last function names
- code parent/child counts
- audio group names
- extension names
- room-order preview

With `--verbose`, G3MTool reads the live data file and prints extended per-resource listings for the resource families implemented in `InfoCommand`.

## Patch output

For `.g3mpatch`, `info` validates the manifest and prints:

- creation time
- tool name and version
- original file metadata
- patch statistics
- per-resource-type counts in verbose mode

With `--json`, G3MTool prints the manifest as JSON.
