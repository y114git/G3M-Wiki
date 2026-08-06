# File Formats

This page is a quick map of the file types G3M actually cares about.

## Main game data files

- `.win`
- `.ios`
- `.unx`
- `.droid`

## Main patch formats

- `.g3mpatch`
- `.xdelta`
- `.vcdiff`
- `.csx`

Archive-style G3M patches may also be plain `.zip` files that contain
`g3mpatch.json`.

## Core metadata files

- `mod_config.json` for G3M mods
- `plugin_config.json` for plugins
- `theme_config.json` for theme packages
- legacy `theme.json` is still recognized during theme import

### Extra-file status

An installed extra file keeps the compact string form:

```json
"extra_files": ["runtime/config.json"]
```

A dependency-only entry uses an object so scripts can read it inside the mod
folder without deploying it:

```json
"extra_files": [
  {"file_path": "scripts/", "status": "dependency"}
]
```

Readers preserve unknown status strings for format compatibility. Runtime
deployment selects entries whose status is `install`.

## Settings and state files

- `%LOCALAPPDATA%\G3M\settings\settings.json`
- `%LOCALAPPDATA%\G3M\settings\blocklist.json`
- `%LOCALAPPDATA%\G3M\settings\custom_games.json`
- `%LOCALAPPDATA%\G3M\downloads\downloads_history.json`
- `%LOCALAPPDATA%\G3M\game_versions\game_versions_data.json`
- `%LOCALAPPDATA%\G3M\plugins\plugins_data.json`

## Plugin API note

The current plugin API version is `1.1.0`.
