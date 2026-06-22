# Logging

G3M writes logs to the user data directory so problems can be inspected after the fact.

## Main files

- `%LOCALAPPDATA%\G3M\logs\g3m.log`
- `%LOCALAPPDATA%\G3M\logs\shortcut.log`

## Archived logs

Older session logs are kept under:

`%LOCALAPPDATA%\G3M\logs\g3m\`

## When to check logs

Logs are the first place to look for:

- import failures
- patching failures
- download issues
- plugin errors
- launch and restore problems

## Which log to open

Open `%LOCALAPPDATA%\G3M\logs\g3m.log` for normal app usage: imports, UI actions, plugin loading, settings, downloads, and regular launches.

Open `%LOCALAPPDATA%\G3M\logs\shortcut.log` when you launched from a desktop shortcut. Shortcut launches run through a smaller headless runner, so shortcut-specific failures are usually easiest to diagnose there.

Archived logs under `%LOCALAPPDATA%\G3M\logs\g3m\` are older main-session logs. Use them when the current log has already been overwritten by a restart.
