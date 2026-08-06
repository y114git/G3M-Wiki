# Backup and Restore

G3M backs up each file that a modded launch will replace and records files that
the launch adds. It stores the backup under `<data-root>/patching_backups/` and
writes the active session to `<data-root>/settings/session.lock`.

After patching finishes, G3M records the size and SHA-256 hash of every deployed
file. Directory entries use a hash built from each relative file path and its
contents. G3M starts the game only after it saves these fingerprints.

## Normal exit

After the game exits, G3M compares the deployed files with their saved
fingerprints. A match lets G3M restore replaced files and remove files that the
mod added. G3M writes restored files through a temporary file and `os.replace`
so another process cannot observe a partial copy.

G3M refuses restoration if any tracked path changed after launch. This protects
edits made by the game, the user, Steam, another mod tool, or an updater. The
status bar reports that external changes prevented restoration.

## Crash recovery

G3M checks `session.lock` during the next startup. It restores the previous
session only when all tracked paths still match the deployed fingerprints.

If a tracked path changed, G3M keeps the backup and session record under
`<data-root>/patching_backups/recovery_conflicts/` and removes the active lock.
It does not overwrite the changed game files. The archived session remains
available for manual inspection.

Old manifests without deployed fingerprints retain the legacy restore behavior.
An empty manifest has no work to perform, so G3M removes its backup directory and
lock.

## Game Versions

Backup and Restore protects one launch session. Game Versions stores snapshots
that you create and restore from the Game Versions dialog.
