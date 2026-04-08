# Importing Mods

G3M offers several ways to add mods to your library.

---

## From the Mods Browser (GameBanana)

1. Open the **Mods Browser** tab.
2. Find a mod and click its card to open the details overlay.
3. Click **Download**. If multiple files are available, choose one from the file picker.
4. The mod is downloaded in the background (visible in the Downloads panel).
5. After download, G3M automatically extracts the archive and imports the mod into your library (unless "No auto-use" is enabled in Downloads settings).
6. If the mod already exists in your library (same ID), a merge/overwrite dialog appears.

---

## From Local Files

### File Picker

1. In the Library tab, click the **Add Mod** button (plus icon).
2. Choose **Import Mod**.
3. A file picker opens. Select one or more files. Supported file types:
   - `.zip`, `.7z`, `.rar` — Archives containing mod files.
   - `.g3mpatch` — A G3M patch file.
   - `.xdelta`, `.vcdiff` — Binary diff patches.
   - `.csx` — C# script patches.
   - `.win`, `.ios`, `.unx`, `.droid` — Raw data files.
4. G3M processes each file:
   - Archives are extracted to a temporary folder.
   - The contents are inspected for a `mod_config.json` (G3M native), `_deltamodInfo.json` / `meta.json` / `modding.xml` (DELTAMOD format), `mod.json` (PizzaOven format), or raw data files.
   - If a `mod_config.json` is found, the mod is imported directly.
   - If DELTAMOD files are found, the mod is converted to G3M format automatically.
   - If PizzaOven format is detected (for Pizza Tower mods), G3M attempts auto-conversion.
   - If only raw data/patch files are found, G3M generates a minimal `mod_config.json` with the file(s) assigned to the appropriate chapter.
5. The mod appears in the Library immediately after import.

### Drag and Drop

You can drag files or folders directly onto the G3M window:

- **Archives** (`.zip`, `.7z`, `.rar`) — Extracted and imported as mods.
- **Patch files** (`.g3mpatch`, `.xdelta`, `.vcdiff`, `.csx`) — Imported as single-file mods.
- **Data files** (`.win`, `.ios`, `.unx`, `.droid`) — Imported as raw-data mods.
- **Folders** — If the folder contains a `mod_config.json`, imported directly. Otherwise, scanned for supported files.
- **URLs** — If a URL is dropped, G3M downloads the file and imports it.

### Import Queue

If multiple files are dropped at once, they are queued and processed one at a time. A status message shows which file is being processed.

---

## One-Click Install

G3M registers custom URL protocol handlers (`g3m://` and `deltahub://`). When you click a one-click install link on a website (such as GameBanana), G3M:

1. Receives the URL.
2. Parses the download URL from the protocol link.
3. Shows a confirmation dialog with the download URL and source.
4. If confirmed, queues the download through the Downloads system.
5. After download, the mod is automatically imported.

See [One-Click Install](../advanced/one-click-install.md) for full details.

---

## DELTAMOD Conversion

If the imported archive contains a `_deltamodInfo.json` (or `meta.json`) and `modding.xml` file (DELTAMOD format from Deltamod Manager), G3M converts it automatically:

- Reads the DELTAMOD metadata (name, author, description, game, version).
- Maps the DELTAMOD game identifier (e.g., `toby.deltarune`) to the G3M game ID.
- Extracts patch files and data files.
- Creates a `mod_config.json` with the correct structure.
- Assigns files to the appropriate chapters based on file naming patterns.

Supported DELTAMOD game mappings:

| DELTAMOD ID | G3M Game |
| --- | --- |
| `toby.deltarune` | deltarune |
| `toby.deltarune.demo` | deltarunedemo |
| `toby.undertale` | undertale |
| `fans.utyellow` | undertaleyellow |
| `other.pizzatower` | pizzatower |

---

## PizzaOven & AFOM/CYOP Conversion

For Pizza Tower, G3M auto-detects and converts two PizzaOven-originated mod types:

- **NORMAL mods** — A folder (or `.zip`) with `mod.json` and mod content files (xdelta patches, audio banks, language files, fonts, etc.). G3M copies the game to a temp directory, simulates applying the mod as PizzaOven would, diffs the result against the original, and produces a native G3M mod from the changes. Requires the Pizza Tower game path to be configured.
- **AFOM/CYOP mods** — Custom level archives where each root entry is a tower folder with a valid `.ini` containing `[properties]`, `name`, and `mainlevel`. G3M stores the tower folders in the mod directory and deploys them to `%APPDATA%\PizzaTower_GM2\towers\` on launch.

**GMLoader** mods (with GML folders like `audio/`, `code/`, `lib/`) are not supported and cannot be converted.

See [PizzaOven & AFOM/CYOP Conversion](po-conversion.md) for full details.

---

## Merge / Overwrite

When importing a mod whose ID matches an existing mod in the library:

- A dialog appears asking whether to **merge** (update the existing mod's files) or **replace** (delete the old mod and import fresh).
- Merging preserves existing version snapshots and other data in the mod folder.
- Replacing removes the old folder entirely and creates a new one.

