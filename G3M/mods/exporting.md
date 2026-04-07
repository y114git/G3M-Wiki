# Exporting Mods

G3M can export any installed mod as a `.zip` archive for sharing with other users.

---

## How to Export

1. In the Library, find the mod you want to export.
2. Click the **Export** button on the mod card.
3. A file save dialog opens. Choose a destination folder and file name.
4. G3M packages the entire mod folder (including `mod_config.json`, data files, icon, extra files) into a `.zip` archive.
5. The exported `.zip` can be shared and imported into another G3M installation.

---

## What Is Included

The exported archive contains:

- `mod_config.json` — Full mod metadata and file references.
- All data files (patches, raw data, scripts) for every chapter the mod covers.
- Icon file (if present).
- Extra files (DLLs, audio banks, textures, etc.).
- Any documentation files in the mod root (e.g., `.txt`, `.md`, `.pdf`, `.html` readme files).

The `mod_versions/` subfolder is **not** included in the export — only the current state of the mod is exported.

---

## Importing an Exported Mod

Recipients import the `.zip` using the standard import process:

1. Library → Add Mod → Import Mod → select the `.zip` file.
2. Or drag and drop the `.zip` onto the G3M window.

G3M detects the `mod_config.json` inside and imports it as a native G3M mod.
