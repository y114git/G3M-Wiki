# Mod Versions

G3M lets you save and restore snapshots of any installed mod. Each snapshot is stored as a `.zip` archive inside the mod's `mod_versions/` subfolder.

---

## Opening the Versions Dialog

In the Library, click the **Versions** button on a mod card. The Mod Versions dialog opens showing all saved versions for that mod.

---

## Version List

Each version row shows:

- **File name** — The `.zip` archive name (which is also the version label).
- **File size** — Human-readable size of the archive.
- **Date** — The modification timestamp of the archive file.

---

## Actions

### Save Current Version

Click **Save Version**. A dialog prompts for a version label (name). G3M then:

1. Creates a `.zip` archive of the entire mod folder (excluding the `mod_versions/` subfolder itself).
2. Saves the archive into `<mod_folder>/mod_versions/<label>.zip`.
3. The new version appears in the list immediately.

### Restore a Version

Select a version in the list and click **Restore**. G3M:

1. Deletes all current mod files (except the `mod_versions/` subfolder).
2. Extracts the selected `.zip` archive into the mod folder.
3. The mod in the Library now reflects the restored version's files and metadata.

A confirmation dialog appears before restoring.

### Delete a Version

Select a version and click **Delete**. The `.zip` archive is permanently deleted from disk. A confirmation is required.

### Import a Version

You can also drag and drop `.zip` files directly onto the Mod Versions dialog. They are copied into the `mod_versions/` folder as new version snapshots.

---

## Automatic Versioning

G3M does not create versions automatically. You must manually save versions when you want to preserve a particular state of a mod.

---

## Use Case

Mod versions are useful when:

- You update a mod from GameBanana but want to keep the old version as a fallback.
- You experiment with manual edits to a mod and want to save checkpoints.
- You receive multiple variants of a mod and want to switch between them easily.
