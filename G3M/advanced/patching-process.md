# Patching Process

G3M applies mod files for the launch session, then restores backups after the
game exits.

## Normal flow

The current launch pipeline is:

1. Check the game path and selected mods.
2. Back up files G3M may replace.
3. Apply DATA inputs in priority order and copy Extra files.
4. Start the game and monitor its process.
5. Restore files after exit.

## Patch types G3M can apply

G3M accepts these DATA inputs:

- `.g3mpatch`
- `.xdelta`
- `.vcdiff`
- `.csx`
- raw GameMaker data files such as `.win`, `.ios`, `.unx`, `.droid`

Extra files from mods are copied separately from the main data patching step.

## Multiple mods

For one target with several DATA mods, G3M calls `G3MTool patch merge`. Each
input starts from the same original file. Order runs from low to high priority.

The **Merge Properties** and **Merge Code** settings also affect how some
overlapping changes are combined.

## Safety and recovery

- Backups are stored before patching starts.
- If patching fails, G3M attempts to restore the original files immediately.
- After deployment, G3M stores SHA-256 fingerprints in
  `%LOCALAPPDATA%\G3M\settings\session.lock`.
- After a crash, G3M restores the previous session only if every tracked path
  still matches its deployed fingerprint.
- If another process changed a tracked path, G3M archives recovery data and
  leaves that path unchanged.
- Backup work also uses `%LOCALAPPDATA%\G3M\patching_backups\`.

See [Backup and Restore](backup-and-restore.md) for the recovery rules.

## G3MTool

G3MTool interprets inputs and creates, applies, or merges DATA patches. G3M
handles targets, backups, Extra files, progress, and final placement.

The bundled G3MTool also supports batch CLI workflows for advanced users.
`patch batch apply` and `patch batch create` run repeated jobs against one
original file, while `patch batch merge` accepts multiple quoted merge sets such
as `"mod_a.g3mpatch,mod_b.xdelta"`. Batch jobs hash their inputs first and skip
repeated identical work by copying the first generated result to later duplicate
output names.
