# Security

G3M downloads community content and can run plugin or script-style extensions,
so trust still matters.

## Practical trust model

- install mods from sources you trust
- treat plugins as full-power local code
- treat `.csx` content as something to trust before running

## Helpful built-in protections

- one-click install asks for confirmation
- launch flow creates backups before patching
- restore logic tries to return files after the session
- settings corruption handling exists for broken config files

## Important limitation

Plugins are not sandboxed. A plugin runs with the same general local permissions
as the app process.
