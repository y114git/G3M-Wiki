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

Archive-style G3M patches may also be plain `.zip` files that contain `g3mpatch.json`.

## Core metadata files

- `mod_config.json` for G3M mods
- `plugin_config.json` for plugins
- `theme_config.json` for theme packages
- legacy `theme.json` is still recognized during theme import

## Settings and state files

- `%LOCALAPPDATA%\G3M\settings\settings.json`
- `%LOCALAPPDATA%\G3M\settings\blocklist.json`
- `%LOCALAPPDATA%\G3M\settings\custom_games.json`
- `%LOCALAPPDATA%\G3M\downloads\downloads_history.json`
- `%LOCALAPPDATA%\G3M\game_versions\game_versions_data.json`
- `%LOCALAPPDATA%\G3M\plugins\plugins_data.json`

## Plugin API note

The current plugin API version is `1.1.0`.
