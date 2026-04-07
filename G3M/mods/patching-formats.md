# Patching Formats

G3M supports multiple ways to modify game data files. Each format has different trade-offs in terms of size, compatibility, and flexibility.

---

## g3mpatch

G3M's native patch format, created and applied by the bundled G3MTool.

### Structure

A g3mpatch can be distributed as:

- A single `.g3mpatch` file.
- A `.zip` archive containing `g3mpatch.json` and one or more binary chunk files.

The `g3mpatch.json` manifest describes:

- The target data file type (`.win`, `.ios`, `.unx`, `.droid`).
- A list of modified chunks with their offset, size, and replacement data.
- Optional metadata (creator tool version, creation date).

### How It Works

1. G3MTool reads the original game data file.
2. It reads the g3mpatch manifest.
3. For each listed chunk, it replaces the bytes at the specified offset with the new data.
4. The result is written to the output path.

### Advantages

- **Small file size** — Only modified chunks are stored, not the entire data file.
- **Fast application** — Chunk replacement is a fast operation.
- **Verification** — G3MTool can verify a patch was applied correctly by comparing the result against an expected hash.
- **Native creation** — The Modding Tools dialog can create g3mpatches by comparing an original and modified data file.

### Limitations

- Requires the exact original data file to apply. If the game updates and the data file changes, the patch may produce incorrect results.
- Cannot express structural changes (adding/removing resources) — only byte-level modifications.

---

## xdelta / vcdiff

Standard binary diff formats widely used in the modding community.

### Extensions

- `.xdelta` — xdelta format.
- `.vcdiff` — VCDIFF (RFC 3284) format.

Both are treated identically by G3M. G3MTool handles both formats.

### How It Works

1. G3MTool reads the original data file and the xdelta/vcdiff patch.
2. The patch describes a series of copy and insert instructions that transform the original into the modified version.
3. The transformed file is written to the output path.

### Creating xdelta Patches

In Modding Tools → Convert DATA:

1. Select the original data file.
2. Select the modified data file.
3. Choose "xdelta" as the target format.
4. G3MTool generates the xdelta patch.

### Advantages

- **Standard format** — xdelta patches can be created and applied by many tools, not just G3M.
- **Compact** — Efficient encoding for binary differences.
- **Widely understood** — Many mod creators are familiar with xdelta.

### Limitations

- Slightly slower to apply than g3mpatch for large files.
- Requires the exact original data file.
- Cannot be partially applied — it's all or nothing.

---

## CSX Scripts

C# scripts executed by G3MTool against game data files.

### Extension

`.csx` — C# script file.

### How It Works

1. G3MTool loads the `.csx` script.
2. The script receives a reference to the game data file structure.
3. The script programmatically modifies resources (sprites, sounds, scripts, objects, rooms, etc.).
4. The modified data is written to the output path.

### Advantages

- **Maximum flexibility** — Can make any modification that's expressible in code.
- **Version-resilient** — Well-written scripts can work across different game versions because they reference resources by name rather than byte offset.
- **Composable** — Multiple CSX scripts can be applied in sequence, each modifying the data independently.
- **Readable** — Script source code documents exactly what the mod changes.

### Limitations

- Requires G3MTool to execute (not a standalone format).
- Slower than binary patches for complex modifications.
- Requires programming knowledge to create.
- Security consideration — scripts execute code, so only use trusted sources.

---

## Raw Data Replacement

The simplest patching method — replacing the entire game data file.

### Extensions

`.win`, `.ios`, `.unx`, `.droid`

### How It Works

1. The mod contains a complete modified data file.
2. G3M copies this file directly over the game's data file, replacing it entirely.
3. On restoration, the backed-up original is copied back.

### Advantages

- **Simplest** — No diffing, no complex application logic.
- **Guaranteed correctness** — The exact intended file is used.

### Limitations

- **Large file size** — The entire data file is stored (often 100+ MB), even if only a small change was made.
- **No merging** — Cannot be combined with other mods that modify the same data file. The last mod applied wins completely.
- **Version-locked** — Only works with the exact game version the modder used.

---

## Format Comparison

| Feature | g3mpatch | xdelta | CSX | Raw Data |
| --- | --- | --- | --- | --- |
| File size | Small | Small | Tiny (script only) | Large |
| Application speed | Fast | Fast | Variable | Fast (copy) |
| Requires original file | Yes | Yes | Yes | No |
| Version resilient | No | No | Possible | No |
| Composable | Limited | No | Yes | No |
| Creation difficulty | Easy (tool) | Easy (tool) | Requires coding | Easy (copy) |
| Community familiarity | G3M-specific | High | Low | High |

---

## Format Detection

G3M automatically detects the patch format by examining the file:

1. If the file extension is `.g3mpatch`, or the file is a `.zip` containing `g3mpatch.json` → **g3mpatch**.
2. If the file extension is `.xdelta` or `.vcdiff` → **xdelta/vcdiff**.
3. If the file extension is `.csx` → **CSX script**.
4. If the file extension is `.win`, `.ios`, `.unx`, or `.droid` → **raw data replacement**.

This detection happens transparently during import and patching — you don't need to specify the format manually.

---

## Converting Between Formats

The Modding Tools → Convert DATA tab lets you convert between formats:

| Source | Target | Requires Original |
| --- | --- | --- |
| Modified data → g3mpatch | Yes (original needed for diff) | Yes |
| Modified data → xdelta | Yes (original needed for diff) | Yes |
| g3mpatch → data | Yes (original to apply patch to) | Yes |
| xdelta → data | Yes (original to apply patch to) | Yes |
| CSX → data | Yes (original to execute against) | Yes |
| g3mpatch → xdelta | Indirect (apply to data, then create xdelta) | Yes |
| xdelta → g3mpatch | Indirect (apply to data, then create g3mpatch) | Yes |
