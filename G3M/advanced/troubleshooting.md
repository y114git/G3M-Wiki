# Troubleshooting

Check whether the failure occurs during startup, import, launch, or a network
request. Then retry with no mods or one known-good mod.

Check game path, selected profile, write access to game folder, and running G3M
or game processes.

Logs:

- `%LOCALAPPDATA%\G3M\logs\g3m.log`
- `%LOCALAPPDATA%\G3M\logs\shortcut.log`
- `%LOCALAPPDATA%\G3M\logs\g3m\`

For a report, include relevant log lines or create a [Support Package](../features/support-packages.md).

## Reset local data

Close G3M, then remove its data directory only if you accept losing local
settings, profiles, plugins, and installed mods. Reopen G3M to create a new
data directory.
