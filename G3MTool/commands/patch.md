# patch

Create, apply, validate, or merge G3M-native resource patches (`.g3mpatch`). This is the primary command for mod authors and the main engine behind G3M's patch system.

See [G3M Patch Format](../patch-format.md) for a detailed explanation of the `.g3mpatch` file structure and how patches are created.

---

## patch create

Compare an original and a modified `data.win` and produce a `.g3mpatch` file capturing all resource-level differences.

```
G3MTool patch create <original> <modified> [output] [--xdelta-fallback]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Path to the original (unmodified) data file |
| `modified` | Yes | Path to the modified data file **or** an `.xdelta` patch file (auto-applied to original first) |
| `output` | No | Output `.g3mpatch` path. Default: `patch_{timestamp}.g3mpatch` next to executable |

| Option | Description |
| --- | --- |
| `--xdelta-fallback` | Also embed an exact xdelta fallback in `Xdelta/`. Disabled by default. Use only when byte-perfect fallback is required if semantic apply fails. |

**Example — compare two data files:**

```bash
G3MTool patch create data.win data_modded.win my_mod.g3mpatch
```

**Example — create from an existing xdelta:**

```bash
G3MTool patch create data.win existing_mod.xdelta my_mod.g3mpatch
```

When `modified` is an `.xdelta` file, G3MTool applies it to `original` in a temp file and proceeds with the result. The xdelta source is embedded in `Xdelta/` only when `--xdelta-fallback` is passed.

**What the command outputs:**

On success, prints the output path and a statistics summary:

```
Patch created successfully: my_mod.g3mpatch
  Changed: 12 (18 files)
  New:     2 (3 files)
  Deleted: 1
```

**How it works internally:**

1. Load `original` → hash all resources in memory.
2. Load `modified` → hash all resources in memory.
3. Compare hashes per resource type to find changed, new, and deleted resources.
4. Export only the changed/new resources from `modified` to a temp directory.
5. Decompile changed CodeEntries (GML source + bytecode assembly) in memory.
6. Build the `G3MPatchManifest` (see [patch format](../patch-format.md)).
7. Create the ZIP: write `g3mpatch.json`, add resource files, write code entry files from memory, add asset order helpers, and optionally embed an xdelta fallback if `--xdelta-fallback` is set.
8. Clean up all temp files.

---

## patch apply

Apply a `.g3mpatch`, `.xdelta`, or raw data file to a `data.win`.

```
G3MTool patch apply <data> <patch> [output]
```

| Argument | Required | Description |
| --- | --- | --- |
| `data` | Yes | Path to the original data file |
| `patch` | Yes | Path to the patch — `.g3mpatch`, `.xdelta`, or another data file (auto-converted) |
| `output` | No | Output data file path. Default: same filename as `data`, next to executable |

**Example:**

```bash
G3MTool patch apply data.win my_mod.g3mpatch patched.win
```

Non-`.g3mpatch` inputs are auto-converted: an `.xdelta` is applied directly; a raw data file is converted to a patch using `data` as the original reference, then applied.

If semantic `.g3mpatch` apply fails, or if the semantic output hash does not match the patch's expected modified-file hash, and the archive contains an xdelta fallback under `Xdelta/` (or legacy `Exact/`), G3MTool attempts that fallback against the original file.

---

## patch validate

Validate a `.g3mpatch` file and optionally check whether it is compatible with a specific data file.

```
G3MTool patch validate <patch> [--data <data.win>]
```

| Argument / Option | Required | Description |
| --- | --- | --- |
| `patch` | Yes | Path to the `.g3mpatch` file |
| `--data` / `-d` | No | Path to a data file to check compatibility against |

**Example — validate only:**

```bash
G3MTool patch validate my_mod.g3mpatch
```

**Example — validate and check compatibility:**

```bash
G3MTool patch validate my_mod.g3mpatch --data data.win
```

On success, prints:

```
Patch is valid.
  Tool: G3MTool v1.0.2
  Created: 2025-11-01T14:22:00Z
  Resources: 12 changed, 2 new, 1 deleted
```

With `--json`, outputs the full manifest as JSON. Exit code is `1` if validation fails (corrupt archive, missing `g3mpatch.json`, invalid schema).

---

## patch merge

Merge two or more patches into a single coherent `.g3mpatch`. Requires the original `data.win` as context to resolve conflicts.

```
G3MTool patch merge <original> <patch1> <patch2> [patch3 ...] [options]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Path to the original data file (used as merge base) |
| `patch1`, `patch2`, ... | Yes (min 2) | Patch files in priority order: **lowest priority first, highest last**. Accepts `.g3mpatch`, `.xdelta`, or raw data files. |

| Option | Alias | Description |
| --- | --- | --- |
| `--out <path>` | `-o` | Output path for the merged `.g3mpatch`. This is the default mode if no flags are specified. |
| `--apply <path>` | `-a` | Instead of saving a merged patch, apply the merged result directly and save the resulting data file to this path. |
| `--code` | | Enable Git-style 3-way merge for GML code entries. Without this flag, the highest-priority patch wins for conflicting code entries. |
| `--properties` | | Enable deep key-level merge for JSON property files. Without this flag, the highest-priority patch wins for conflicting property files. |
| `--report <path>` | `-r` | Write a Markdown report of merge conflicts and resolutions to this path. |

**Example — merge two mods:**

```bash
G3MTool patch merge data.win mod_a.g3mpatch mod_b.g3mpatch --out merged.g3mpatch
```

Here `mod_b` has higher priority: if both mods change the same resource, `mod_b`'s version wins (unless `--code` or `--properties` enables deeper merging).

**Example — merge and apply immediately:**

```bash
G3MTool patch merge data.win mod_a.g3mpatch mod_b.g3mpatch --apply patched.win --code --report merge_report.md
```

**Priority and conflict resolution:**

- Resources changed by only one patch: always included as-is.
- Resources changed by multiple patches: the **rightmost** (highest-priority) patch's version is used at the resource level.
- With `--code`: GML code entries from conflicting patches are 3-way merged against the original GML. Conflicts that cannot be auto-resolved are marked in the report.
- With `--properties`: JSON property files are merged key-by-key. Conflicting keys use the highest-priority value.
- Deleted resources: if a resource is deleted in any patch, deletion wins unless a higher-priority patch modifies it.
