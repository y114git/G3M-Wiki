# patch

Create, apply, validate, or merge `.g3mpatch` files.

## patch create

```bash
G3MTool patch create <original> <modified> [output] [--xdelta-fallback] [--cache <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Original data file (`.win`, `.ios`, `.unx`, `.droid`) |
| `modified` | Yes | Modified data file or `.xdelta` patch |
| `output` | No | Output `.g3mpatch`. Default: `patch_{timestamp}.g3mpatch` next to the executable |

| Option | Description |
| --- | --- |
| `--xdelta-fallback` | Store an xdelta fallback built from `original` and the modified data file |
| `--cache <dir>` | Read/write `.g3mcache` analysis for real data-file inputs |

If `modified` is `.xdelta`, G3MTool applies it to `original` in a temporary file and then creates the `.g3mpatch` from that result. The xdelta fallback is stored only when `--xdelta-fallback` is passed.

Examples:

```bash
G3MTool patch create data.win data_modded.win mod.g3mpatch
G3MTool patch create data.win mod.xdelta mod.g3mpatch --cache .g3mcache
G3MTool patch create data.win data_modded.win mod.g3mpatch --xdelta-fallback
```

## patch apply

```bash
G3MTool patch apply <data> <patch> [output] [--xdelta-fallback]
```

| Argument | Required | Description |
| --- | --- | --- |
| `data` | Yes | Data file to patch |
| `patch` | Yes | `.g3mpatch`, `.xdelta`, or data file |
| `output` | No | Output data file. Default: same file name as `data`, next to the executable |

| Option | Description |
| --- | --- |
| `--xdelta-fallback` | For `.g3mpatch` input, try stored xdelta fallback first; if it fails, continue with normal apply |

Input behavior:

| Input | Behavior |
| --- | --- |
| `.g3mpatch` | Apply resource-level changes |
| `.xdelta` | Apply xdelta directly |
| data file | Convert it to `.g3mpatch` against `data`, then apply |

Default `.g3mpatch` apply tries the normal G3MTool flow first. If that fails and the patch contains fallback data, G3MTool tries xdelta as a last resort.

`--cache` is not used by `patch apply`. Apply needs the real target data file and real patch payloads to write the output.

## patch validate

```bash
G3MTool patch validate <patch> [--data <data-file>] [--cache <dir>]
```

| Argument / Option | Required | Description |
| --- | --- | --- |
| `patch` | Yes | `.g3mpatch` file |
| `--data`, `-d` | No | Data file to compare against manifest compatibility metadata |
| `--cache <dir>` | No | Reuse cached data-file identity when checking `--data` |

Validation checks that the patch has a readable manifest. With `--data`, G3MTool compares the data file identity against the manifest original metadata and warns when it differs.

```bash
G3MTool patch validate mod.g3mpatch
G3MTool patch validate mod.g3mpatch --data data.win --cache .g3mcache
```

## patch merge

```bash
G3MTool patch merge <original> <patch1> <patch2> [patch3 ...] [options] [--cache <dir>]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Data file used as merge context |
| `patch1`, `patch2`, ... | Yes, at least 2 | Inputs in priority order, lowest first and highest last. Accepts `.g3mpatch`, `.xdelta`, or data files |

| Option | Alias | Description |
| --- | --- | --- |
| `--out <path>` | `-o` | Write the merged `.g3mpatch` |
| `--apply <path>` | `-a` | Also write the merged data file |
| `--code` | | Enable 3-way merge for GML conflicts |
| `--properties` | | Enable key-level merge for JSON property files |
| `--report <path>` | `-r` | Write a Markdown merge report |
| `--cache <dir>` | | Reuse `.g3mcache` analysis while converting `.xdelta` or data-file inputs |

If neither `--out` nor `--apply` is set, G3MTool writes a merged `.g3mpatch` to the default output path.

Examples:

```bash
G3MTool patch merge data.win mod_a.g3mpatch mod_b.g3mpatch --out merged.g3mpatch
G3MTool patch merge data.win mod_a.xdelta mod_b.win --out merged.g3mpatch --apply merged.win --cache .g3mcache
```

Merge rules:

| Case | Behavior |
| --- | --- |
| One patch changes a resource | Include that change |
| Multiple patches change the same resource | Highest-priority input wins unless a deeper merge option applies |
| `--code` conflict | Try 3-way GML merge against the original |
| `--properties` conflict | Merge JSON object keys where possible |
| Delete vs lower-priority edit | Delete wins unless a higher-priority input replaces the resource |

For complex GameMaker data, merge may need helper-guided order, object-event, texture, or code repairs. G3MTool runs those steps only when the input patches require them.
