# Patching Process

When you launch a game with mods, G3M temporarily changes the target files, starts the game, and restores the originals when the session ends.

## Normal flow

The current launch pipeline is:

1. Validate the selected game path and the chosen mods.
2. Back up files that may be changed.
3. Apply the selected mod data in order.
4. Copy any extra files the mods ship.
5. Launch the game.
6. Watch the running process.
7. Restore the original files after the game closes.

## Patch types G3M can apply

G3M currently recognizes these main data formats:

- `.g3mpatch`
- `.xdelta`
- `.vcdiff`
- `.csx`
- raw GameMaker data files such as `.win`, `.ios`, `.unx`, `.droid`

Extra files from mods are copied separately from the main data patching step.

## Multiple mods

If more than one mod is selected for the same slot, G3M applies them in order. Later mods can override earlier ones.

The **Merge Properties** and **Merge Code** settings also affect how some overlapping changes are combined.

## Safety and recovery

- Backups are stored before patching starts.
- If patching fails, G3M attempts to restore the original files immediately.
- If the app crashes during a session, recovery data in `settings/session.lock` is used on the next start.
- Backup work also uses `patching_backups/` under the G3M data directory.

## G3MTool

Patch creation, patch apply, diff-style operations, and script execution are delegated to the bundled `G3MTool` binaries through the G3M adapter layer.
