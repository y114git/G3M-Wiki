# diff

Compare two GameMaker data files or `.g3mpatch` files and generate a Markdown diff report with resource-level changes.

```
G3MTool diff <file1> <file2> [output-dir]
```

| Argument | Required | Description |
| --- | --- | --- |
| `file1` | Yes | First file — data file (`.win`, `.ios`, `.unx`, `.droid`) or `.g3mpatch` |
| `file2` | Yes | Second file — same types accepted |
| `output-dir` | No | Directory to write the diff report into. Default: `diff/` next to the G3MTool executable |

The output report is named `diff_{timestamp}.md` inside the output directory.

---

## Example

```bash
G3MTool diff data_v1.win data_v2.win ./reports/
```

Prints:

```
Comparing files...
  File 1: C:\games\DELTARUNE\data_v1.win
  File 2: C:\games\DELTARUNE\data_v2.win
  Output: C:\tools\G3MTool\reports\diff_20251101_142200.md
Diff report created: C:\tools\G3MTool\reports\diff_20251101_142200.md
  Differences: 47
```

---

## Report Format

The Markdown report lists differences per resource type. For each type, changed, new, and deleted resources are listed by name. The report is designed to be read in a Markdown viewer or committed to a repository for review.

Example excerpt:

```markdown
# Diff Report
**File 1:** data_v1.win
**File 2:** data_v2.win
**Generated:** 2025-11-01 14:22:00

## Sprites
- **Changed:** spr_player, spr_enemy_A
- **New:** spr_new_boss
- **Deleted:** *(none)*

## CodeEntries
- **Changed:** gml_Object_obj_player_Step_0, gml_Script_scr_init
- **New:** gml_Script_scr_new_feature
- **Deleted:** gml_Script_scr_old_debug

## Rooms
- **Changed:** rm_boss_01
```

---

## Notes

- `diff` does not modify any files — it is a read-only inspection tool.
- When comparing two `.g3mpatch` files, the diff is performed on their manifests' resource lists, not on the raw bytes of the ZIP.
- For deeper per-property inspection of a single file, use [`info --verbose`](info.md).
