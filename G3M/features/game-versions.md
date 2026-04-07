# Game Versions

The Game Versions feature lets you save complete snapshots of a game's files and restore them later. This is useful for keeping clean backups of unmodified game data or preserving specific game states.

---

## Overview

A "game version" is a compressed archive of the game's data directory. G3M stores these archives in the `game_versions/` folder of your user data directory, indexed by a `game_versions.json` file.

---

## Creating a Version

1. Open the Game Versions dialog (accessible from the Library or Settings → Game area).
2. Select the game you want to snapshot.
3. Click **Create Version**.
4. Enter a version label (e.g., "Clean Install 1.10" or "Before modding").
5. G3M copies the game's data files into a `.zip` archive. During archiving, a progress indicator shows the operation status.
6. The new version appears in the list.

### What Is Saved

The archive includes the game's base data folder contents — typically the folder containing `data.win` (or equivalent) and associated runtime files. Game executables may be excluded if they are in a protected path.

Protected executables (the game's own `.exe` and any custom executable configured in settings) are not overwritten during restore operations to prevent accidental damage.

---

## Version List

Each version row shows:

- **Label** — The user-chosen name for this version.
- **Game** — Which game this version belongs to.
- **Size** — Archive file size.
- **Date** — When the version was created.
- **Status** — Ready, Archiving, Applying, or Error.

---

## Restoring a Version

Select a version in the list and click **Apply** (or **Restore**). G3M:

1. Shows a confirmation dialog.
2. Extracts the archive into the game's data directory, replacing current files.
3. Protected executables are skipped.
4. The game is now in the exact state it was when the version was created.

This is destructive — any current modifications to the game files will be overwritten.

---

## Deleting a Version

Select a version and click **Delete**. The archive file is permanently removed from disk. A confirmation is required.

---

## Renaming a Version

Select a version and click **Rename**. Enter a new label. The archive file on disk is renamed accordingly.

---

## Importing a Version

You can import a game version archive from an external `.zip` file. Click **Import**, select the file, and G3M copies it into the `game_versions/` folder. A unique path is generated if a file with the same name already exists.

---

## Cancellation

Long-running archive or restore operations can be cancelled. Cancelling an archive operation removes the partially created file. Cancelling a restore operation leaves the game files in an intermediate state (partial extraction), so it is recommended to restore again from a known-good version.

---

## Recovery

On startup, G3M checks for game version records that are in an intermediate state (e.g., "Archiving" or "Applying" from a crash). These are cleaned up automatically — failed archives are removed, and stale status is reset.
