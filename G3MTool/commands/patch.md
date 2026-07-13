# patch

Create, apply, batch-process, validate, or merge `.g3mpatch` files.

## patch create

```bash
G3MTool patch create <original> <modified> [output] \
  [--xdelta-fallback] [--cache <dir>] [--xdelta-path <path>]
```

- **Argument:** `original`
  - **Required:** Yes
  - **Description:** Original data file (`.win`, `.ios`, `.unx`, `.droid`)

- **Argument:** `modified`
  - **Required:** Yes
  - **Description:** Modified data file or `.xdelta` patch

- **Argument:** `output`
  - **Required:** No
  - **Description:** Output `.g3mpatch`. Default: `patch_{timestamp}.g3mpatch`
    next to the executable

- **Option:** `--xdelta-fallback`
  - **Description:** Store an embedded xdelta fallback built from `original` and
    the modified result

- **Option:** `--cache <dir>`
  - **Description:** Read and write `.g3mcache` analysis files for reusable
    data-file analysis

If `modified` is `.xdelta`, G3MTool applies it to `original` first and creates
the `.g3mpatch` from that temporary result.

## patch apply

```bash
G3MTool patch apply <data> <patch> [output] \
  [--xdelta-fallback] [--cache <dir>] [--xdelta-path <path>]
```

- **Argument:** `data`
  - **Required:** Yes
  - **Description:** Base data file

- **Argument:** `patch`
  - **Required:** Yes
  - **Description:** `.g3mpatch`, `.xdelta`, or another data file

- **Argument:** `output`
  - **Required:** No
  - **Description:** Output data file. Default: same file name as `data`, next
    to the executable

- **Option:** `--xdelta-fallback`
  - **Description:** For `.g3mpatch` input, try the embedded xdelta copy first;
    if it fails, continue with normal apply

- **Option:** `--cache <dir>`
  - **Description:** Reuse `.g3mcache` analysis only when `patch` must first be
    converted from a data file or `.xdelta` into `.g3mpatch`

Input behavior:

| Input       | Behavior                                             |
| ----------- | ---------------------------------------------------- |
| `.g3mpatch` | Apply resource-level changes                         |
| `.xdelta`   | Apply xdelta directly                                |
| data file   | Convert it to `.g3mpatch` against `data`, then apply |

Default `.g3mpatch` apply tries the normal G3MTool flow first. If that fails and
the patch contains fallback data, G3MTool can fall back to xdelta.

## patch validate

```bash
G3MTool patch validate <patch> [--data <data-file>] [--cache <dir>]
```

- **Argument / Option:** `patch`
  - **Required:** Yes
  - **Description:** `.g3mpatch` file

- **Argument / Option:** `--data`, `-d`
  - **Required:** No
  - **Description:** Data file to compare against manifest compatibility
    metadata

- **Argument / Option:** `--cache <dir>`
  - **Required:** No
  - **Description:** Reuse cached data-file identity when checking `--data`

Validation checks that the patch can be read and that the manifest is
structurally valid. With `--data`, G3MTool also compares the supplied data file
to manifest identity fields.

## patch merge

```bash
G3MTool patch merge <original> <patch1> <patch2> [patch3 ...] \
  [options] [--cache <dir>] [--xdelta-path <path>]
```

- **Argument:** `original`
  - **Required:** Yes
  - **Description:** Data file used as merge context

- **Argument:** `patch1`, `patch2`, ...
  - **Required:** Yes, at least 2
  - **Description:** Inputs in priority order, lowest first and highest last

Accepted merge inputs:

- `.g3mpatch`
- `.xdelta`
- data files (`.win`, `.ios`, `.unx`, `.droid`)

- **Option:** `--apply <path>`
  - **Alias:** `-a`
  - **Description:** Write the merged data file

- **Option:** `--out <path>`
  - **Alias:** `-o`
  - **Description:** Also keep the merged `.g3mpatch`

- **Option:** `--code`
  - **Alias:** —
  - **Description:** Enable Git-style 3-way merge for GML code files

- **Option:** `--properties`
  - **Alias:** —
  - **Description:** Enable deep merge for JSON property files

- **Option:** `--report <path>`
  - **Alias:** `-r`
  - **Description:** Write a Markdown merge report

- **Option:** `--cache <dir>`
  - **Alias:** —
  - **Description:** Reuse `.g3mcache` analysis while converting `.xdelta` or
    data-file inputs

If `--apply` is omitted, G3MTool writes the merged data file to the current
directory as `<original>_merged<ext>`. Add `--out` when you also want to keep
the intermediate merged `.g3mpatch`.

## patch batch

Batch commands run multiple independent jobs against the same original data
file. They are still plain CLI commands; there is no interactive selection
layer.

Common batch options:

| Option                | Description                             |
| --------------------- | --------------------------------------- |
| `--out-dir <dir>`     | Required for batch apply/create         |
| `--cache <dir>`       | Reuse `.g3mcache` analysis across jobs  |
| `--continue-on-error` | Keep running later jobs after a failure |

Before processing, batch mode hashes the original and all inputs. If two jobs
have the same effective inputs and flags, G3MTool runs the expensive job once
and copies the first output to the later output name.

### patch batch apply

```bash
G3MTool patch batch apply <original> <patches...> --out-dir <dir> \
  [--cache <dir>] [--continue-on-error] [--xdelta-fallback]
```

Each patch is applied independently to the same original data file. This does
not merge patches.

Example:

```bash
G3MTool patch batch apply game.win mod1.g3mpatch mod2.xdelta mod3.win \
  --out-dir patched
```

Outputs are named from the original and patch file names, for example
`game_mod1.win`, `game_mod2.win`, and `game_mod3.win`. The data-file extension
matches the original extension.

### patch batch create

```bash
G3MTool patch batch create <original> <modified...> --out-dir <dir> \
  [--cache <dir>] [--continue-on-error] [--xdelta-fallback]
```

Creates one `.g3mpatch` for each modified input. Inputs can be modified data
files or `.xdelta` patches.

Example:

```bash
G3MTool patch batch create original.win modified_a.win modified_b.win \
  mod_c.xdelta --out-dir patches
```

### patch batch merge

```bash
G3MTool patch batch merge <original> <sets...> \
  [--apply <data-dir>] [--out <patch-dir>] [--cache <dir>] \
  [--continue-on-error] [--code] [--properties] [--report]
```

Each set is one quoted, comma-separated list of patches. Patch order inside a
set is low to high priority, matching `patch merge`.

Example:

```bash
G3MTool patch batch merge game.win "base.xdelta,ui.g3mpatch" \
  "combat.win,localization.xdelta,hotfix.g3mpatch" \
  --apply merged --out merged-patches
```

Rules:

- every set must contain at least two patches
- use commas as the only separator
- spaces around commas are ignored
- paths with spaces are supported because the whole set is quoted
- paths containing commas are not supported in this mode
- patched data outputs are written to the current directory by default, or to
  `--apply <data-dir>` when it is set
- `--out <patch-dir>` also saves each intermediate merged `.g3mpatch`
- `--code`, `--properties`, and `--report` apply to every set

Batch merge writes both a merged `.g3mpatch` and a patched data file for each
set. If a merge report is created, duplicate jobs also copy the report to the
duplicate output name.
