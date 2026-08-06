# Patching Process

When you launch a game with mods, G3M temporarily changes the target files,
starts the game, and restores the originals when the session ends.

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

If more than one mod is selected for the same slot, G3M passes the original
data file and the ordered raw inputs to `G3MTool patch merge`. G3MTool derives
each input from the same original and merges them from low to high priority.

The **Merge Properties** and **Merge Code** settings also affect how some
overlapping changes are combined.

## Safety and recovery

- Backups are stored before patching starts.
- If patching fails, G3M attempts to restore the original files immediately.
- After deployment, G3M stores SHA-256 fingerprints in
  `%LOCALAPPDATA%\G3M\settings\session.lock`.
- After a crash, G3M restores the previous session only if every tracked path
  still matches its deployed fingerprint.
- If another process changed a tracked path, G3M archives the recovery data and
  leaves the changed game files in place.
- Backup work also uses `%LOCALAPPDATA%\G3M\patching_backups\`.

See [Backup and Restore](backup-and-restore.md) for the recovery rules.

## G3MTool

G3M delegates patch input interpretation, apply, create, batch, and merge to
the bundled G3MTool. G3M keeps backups, target discovery, extra-file copying,
progress display, and final file placement.

The bundled G3MTool also supports batch CLI workflows for advanced users.
`patch batch apply` and `patch batch create` run repeated jobs against one
original file, while `patch batch merge` accepts multiple quoted merge sets such
as `"mod_a.g3mpatch,mod_b.xdelta"`. Batch jobs hash their inputs first and skip
repeated identical work by copying the first generated result to later duplicate
output names.
