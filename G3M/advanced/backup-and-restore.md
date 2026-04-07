# Backup & Restore

G3M automatically backs up game files before applying mods and restores them after the game exits. This ensures your game files are never permanently modified.

---

## How Backups Work

### Before Launch

When you click **Launch** with mods selected:

1. G3M creates a temporary backup directory.
2. For each chapter that has a mod selected, G3M backs up the game's original data file (e.g., `data.win`) by copying it to the backup directory.
3. If the mod includes extra files, G3M records which files will be added so they can be removed later.
4. Only then does G3M apply the mod patches to the game files.

### After Game Exit

When the game process exits (detected by the game monitor):

1. G3M restores each backed-up file to its original location, overwriting the modded version.
2. Any files that were added by the mod (extra files) and did not exist before are removed.
3. The backup directory is cleaned up.
4. A status message confirms restoration.

---

## Backup Manager

The backup system is managed by the `BackupManager`, which tracks:

- **Original files** — A mapping of chapter IDs to file paths and their backup locations. Files that did not exist before modding are tracked with a `null` backup path (meaning they should be deleted on restore).
- **Added files** — Files that were created during patching (not present in the original game). These are removed during restoration.
- **Modification order** — The order in which files were modified, ensuring restoration happens in the correct sequence.

---

## Session Manifest

A session manifest is written to the backup directory during patching. This JSON file records the complete state of the backup session, allowing recovery even if G3M crashes during gameplay.

---

## Failure Handling

- If a backup fails (e.g., disk full, permission denied), the launch is aborted and an error message is shown. The game is not started.
- If restoration fails for a specific file, an error is logged but restoration continues for other files.
- If G3M crashes while the game is running, the backup files remain in the backup directory. On the next launch, G3M can detect the unrestored state and offer to clean up.

---

## What Is Protected

- The game's main data file (e.g., `data.win`, `game.ios`, `data.unx`).
- Any files overwritten by mod extra files.
- G3M does **not** back up the game executable — executables are protected from overwrite by the patching system (they are excluded from patch operations).

---

## Game Version Backups

The [Game Versions](../features/game-versions.md) feature provides a separate, user-controlled backup system for saving complete snapshots of game files. Unlike the automatic launch backups, game version backups are permanent until explicitly deleted.
