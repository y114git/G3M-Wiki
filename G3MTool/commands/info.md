# info

Print metadata for a data file or `.g3mpatch`.

```bash
G3MTool info <target> [-v] [--json] [--cache <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `target` | Yes | Data file (`.win`, `.ios`, `.unx`, `.droid`) or `.g3mpatch` |

| Option | Alias | Description |
| --- | --- | --- |
| `--verbose` | `-v` | Print full per-resource listings |
| `--json` | | Print JSON where supported |
| `--cache <dir>` | | Store/reuse the standard non-verbose data-file info snapshot |

## Data File Output

Without `--verbose`, `info` prints:

- file name, size, game name, bytecode version, interpreted GameMaker version
- resource counts
- selected GeneralInfo fields
- variable counts by instance type
- first and last function names
- code parent/child counts
- audio group names
- extension names
- first room-order entries

With `--verbose`, G3MTool reads the data file and prints full per-resource listings for sprites, sounds, backgrounds, fonts, paths, scripts, shaders, game objects, rooms, code entries, functions, variables, strings, embedded textures, texture page items, audio groups, extensions, and timelines.

`--cache <dir>` applies only to standard non-verbose data-file output. Verbose output still reads the data file because it prints full live resource lists.

## Patch Output

For `.g3mpatch`, `info` validates the manifest and prints:

- creation time
- tool name and version
- original file metadata
- patch statistics
- per-resource-type counts in verbose mode

With `--json`, G3MTool prints the manifest as JSON.

## Examples

```bash
G3MTool info data.win
G3MTool info data.win --cache .g3mcache
G3MTool info data.win --verbose
G3MTool info mod.g3mpatch --json
```
