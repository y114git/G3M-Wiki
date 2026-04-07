# Mod Editor

The Mod Editor is a dialog for creating new mods or editing existing ones. It lets you set all mod metadata and assign data files to chapters.

---

## Opening the Mod Editor

- **Create mode**: Library → Add Mod button → **Create Mod**.
- **Edit mode**: Library → click **Edit** on any installed mod card.

---

## Fields

| Field | Description |
| --- | --- |
| **Name** | The mod's display name. Required. |
| **Author** | The mod author. |
| **Version** | Version string (e.g., "1.0.0"). |
| **Description** | A text description of the mod. |
| **Game** | Dropdown to select which game the mod is for. Lists all visible games (built-in + custom). |
| **Game Version** | Which version of the game this mod targets. |
| **Icon** | Button to select an icon image (`.png`, `.jpg`, etc.). The icon is copied into the mod folder. |
| **Tags** | Comma-separated or individually added tags. Common tags: "customization", "gameplay", "text edit", "other". |
| **Homepage** | URL to the mod's website or GameBanana page. |

---

## Chapter / File Assignments

Below the metadata fields, the editor shows a section for assigning data files to chapters.

For multi-chapter games (like DELTARUNE), each chapter appears as a separate row. For single-tab games, there is one row.

For each chapter row:

- **Data file** — Button to select the main data file for this chapter. Can be a `.win`, `.ios`, `.unx`, `.droid` raw file, a `.g3mpatch` patch, a `.xdelta`/`.vcdiff` patch, or a `.csx` script.
- **Description** — Optional description specific to this chapter's data.
- **Extra files** — Button to add additional files that should be copied into the game folder during patching (e.g., DLLs, audio files, texture packs). Multiple extra files can be added per chapter.
- **Remove** — Button to clear the assignment for this chapter.

---

## Creating a Mod

When you fill in the fields and click **Create** (or **Save** in create mode):

1. G3M generates a unique `local_<uuid>` ID.
2. Creates a new folder in the profile's mods directory.
3. Copies the icon (if any) into the mod folder.
4. Copies selected data files into the mod folder, organized by chapter.
5. Generates a `mod_config.json` with all metadata and file references.
6. The mod appears in the Library immediately.

---

## Editing a Mod

In edit mode, the editor pre-fills all fields with the mod's current data. You can change any field. When you click **Save**:

1. The `mod_config.json` is updated with the new metadata.
2. If data files were changed, old files may be replaced.
3. The icon is updated if a new one was selected.
4. The Library refreshes to show the updated mod.

---

## Notes

- The mod ID cannot be changed after creation.
- Deleting a chapter's file assignment removes that chapter's data from the mod. If a mod has no data for a chapter, it will not appear in that chapter's tab in the Library.
- Extra files are stored as relative paths within the mod folder.
