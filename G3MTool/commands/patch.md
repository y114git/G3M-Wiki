# patch

Create, apply, validate, or merge `.g3mpatch` files.

## patch create

```bash
G3MTool patch create <original> <modified> [output] [--xdelta-fallback] [--cache <dir>] [--xdelta-path <path>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Original data file (`.win`, `.ios`, `.unx`, `.droid`) |
| `modified` | Yes | Modified data file or `.xdelta` patch |
| `output` | No | Output `.g3mpatch`. Default: `patch_{timestamp}.g3mpatch` next to the executable |

| Option | Description |
| --- | --- |
| `--xdelta-fallback` | Store an embedded xdelta fallback built from `original` and the modified result |
| `--cache <dir>` | Read and write `.g3mcache` analysis files for reusable data-file analysis |

If `modified` is `.xdelta`, G3MTool applies it to `original` first and creates the `.g3mpatch` from that temporary result.

## patch apply

```bash
G3MTool patch apply <data> <patch> [output] [--xdelta-fallback] [--cache <dir>] [--xdelta-path <path>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `data` | Yes | Base data file |
| `patch` | Yes | `.g3mpatch`, `.xdelta`, or another data file |
| `output` | No | Output data file. Default: same file name as `data`, next to the executable |

| Option | Description |
| --- | --- |
| `--xdelta-fallback` | For `.g3mpatch` input, try the embedded xdelta copy first; if it fails, continue with normal apply |
| `--cache <dir>` | Reuse `.g3mcache` analysis only when `patch` must first be converted from a data file or `.xdelta` into `.g3mpatch` |

Input behavior:

| Input | Behavior |
| --- | --- |
| `.g3mpatch` | Apply resource-level changes |
| `.xdelta` | Apply xdelta directly |
| data file | Convert it to `.g3mpatch` against `data`, then apply |

Default `.g3mpatch` apply tries the normal G3MTool flow first. If that fails and the patch contains fallback data, G3MTool can fall back to xdelta.

## patch validate

```bash
G3MTool patch validate <patch> [--data <data-file>] [--cache <dir>]
```

| Argument / Option | Required | Description |
| --- | --- | --- |
| `patch` | Yes | `.g3mpatch` file |
| `--data`, `-d` | No | Data file to compare against manifest compatibility metadata |
| `--cache <dir>` | No | Reuse cached data-file identity when checking `--data` |

Validation checks that the patch can be read and that the manifest is structurally valid. With `--data`, G3MTool also compares the supplied data file to manifest identity fields.

## patch merge

```bash
G3MTool patch merge <original> <patch1> <patch2> [patch3 ...] [options] [--cache <dir>] [--xdelta-path <path>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Data file used as merge context |
| `patch1`, `patch2`, ... | Yes, at least 2 | Inputs in priority order, lowest first and highest last |

Accepted merge inputs:

- `.g3mpatch`
- `.xdelta`
- data files (`.win`, `.ios`, `.unx`, `.droid`)

| Option | Alias | Description |
| --- | --- | --- |
| `--out <path>` | `-o` | Write the merged `.g3mpatch` |
| `--apply <path>` | `-a` | Also write the merged data file |
| `--code` | | Enable Git-style 3-way merge for GML code files |
| `--properties` | | Enable deep merge for JSON property files |
| `--report <path>` | `-r` | Write a Markdown merge report |
| `--cache <dir>` | | Reuse `.g3mcache` analysis while converting `.xdelta` or data-file inputs |

If neither `--out` nor `--apply` is set, G3MTool still writes a merged `.g3mpatch` to its default output path.
