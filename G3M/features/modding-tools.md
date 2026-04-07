# Modding Tools

The Modding Tools dialog is a powerful utility for mod developers. It provides tabs for converting, patching, merging, comparing, and inspecting game data files.

---

## Opening Modding Tools

Accessible from the Library or the title bar (wrench icon). The dialog is non-modal — you can keep it open while using the rest of G3M.

---

## Tabs

The Modding Tools dialog has five tabs:

### 1. Convert DATA

Convert between different data/patch formats.

**Inputs:**
- **Source file** — Select a source data file (`.win`, `.ios`, `.unx`, `.droid`) or patch file (`.g3mpatch`, `.xdelta`, `.vcdiff`, `.csx`).
- **Original data file** — The unmodified game data file (required for patch-to-data conversions).
- **Target format** — Choose the output format from: `g3mpatch`, `xdelta`, `data.win`, `game.ios`.

**How it works:**
- **Data → g3mpatch**: Creates a g3mpatch by comparing the modified data file against the original.
- **Data → xdelta**: Creates an xdelta binary diff between the original and modified data files.
- **g3mpatch → data**: Applies the g3mpatch to the original data file, producing a full modified data file.
- **xdelta → data**: Applies the xdelta patch to the original, producing a full data file.
- **csx → data**: Executes the CSX script against the original data, producing a modified data file.

The output file is saved to a location you choose.

**Verification**: After conversion, G3M can optionally verify the result by applying the generated patch to the original and comparing it against the expected output. This ensures the patch was created correctly.

### 2. Patch

Apply a patch to a game data file.

**Inputs:**
- **Original data file** — The unmodified game data file.
- **Patch file** — A `.g3mpatch`, `.xdelta`, `.vcdiff`, or `.csx` file.
- **Output file** — Where to save the patched result.

G3M detects the patch format automatically and applies it using the appropriate method:
- `.g3mpatch` / `.zip` with `g3mpatch.json` → G3MTool patch application.
- `.xdelta` / `.vcdiff` → xdelta binary patching.
- `.csx` → CSX script execution.

### 3. Merge

Merge two data files together.

**Inputs:**
- **Base data file** — The original unmodified data.
- **File A** — First modified data file (or patch).
- **File B** — Second modified data file (or patch).
- **Output file** — Where to save the merged result.
- **Merge Properties** checkbox — Whether to merge game object properties.
- **Merge Code** checkbox — Whether to merge code blocks.

The merge operation first applies File A to the base, then applies File B on top. Properties and code merging rules control how conflicts are resolved.

This is useful for combining two mods that modify different parts of the game data. If both mods modify the same resource, the second mod's changes take precedence.

### 4. Info

Inspect a data file to see its contents.

**Inputs:**
- **Data file** — A `.win`, `.ios`, `.unx`, `.droid` game data file.

**Output:**
- Displays a structured view of the data file's contents (chunks, resources, sprites, sounds, scripts, etc.) as reported by G3MTool.

### 5. Diff

Compare two data files and show the differences.

**Inputs:**
- **File A** — First data file.
- **File B** — Second data file.
- **Detailed diff** checkbox — Shows detailed per-resource differences instead of just a summary.

**Output:**
- A text report listing which resources were added, removed, or modified between the two files. Useful for understanding what a mod changes.

---

## G3MTool

All Modding Tools operations use **G3MTool** — a bundled command-line tool that handles GameMaker data file manipulation. G3MTool is included with G3M for all platforms:

- **Windows**: `G3MTool.exe`
- **macOS**: `G3MTool` (Unix executable)
- **Linux**: `G3MTool` (Unix executable)

G3MTool supports:
- Creating and applying g3mpatch patches.
- Creating and applying xdelta patches.
- Executing CSX scripts against data files.
- Merging data files with configurable property/code merge modes.
- Inspecting data file structure.
- Comparing (diffing) data files.

The tool reports progress during long operations (percentage-based), which is displayed in the Modding Tools dialog.

---

## Supported File Types

| Extension | Type | Description |
| --- | --- | --- |
| `.win` | Data | Windows GameMaker data file. |
| `.ios` | Data | iOS GameMaker data file. |
| `.unx` | Data | Linux/Unix GameMaker data file. |
| `.droid` | Data | Android GameMaker data file. |
| `.g3mpatch` | Patch | G3M's native binary patch format. |
| `.xdelta` | Patch | xdelta binary diff format. |
| `.vcdiff` | Patch | VCDIFF binary diff format (treated same as xdelta). |
| `.csx` | Script | C# script for programmatic data modification. |

---

## Output Log

Each tab has a text output area that shows the result of the operation, including:
- Success/failure messages.
- File sizes before and after.
- Verification results.
- Error details if something went wrong.
- G3MTool's stdout/stderr output.
