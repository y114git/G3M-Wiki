# Data Directory

G3M stores its user data outside the game folders. This is where your settings, profiles, downloads, plugins, logs, and custom files live.

## Location

| Platform | Path |
| --- | --- |
| Windows | `%LOCALAPPDATA%\\G3M` with `%APPDATA%\\G3M` as fallback |
| macOS | `~/Library/Application Support/G3M` |
| Linux | `~/.local/share/G3M` |

## Main folders

| Folder | Purpose |
| --- | --- |
| `settings/` | App settings, blocklist, custom games, crash/session state |
| `profiles/` | Per-profile mod libraries and profile-specific state |
| `downloads/` | Download history and downloaded archives |
| `game_versions/` | Saved game version archives and their index |
| `plugins/` | Installed plugins and `plugins_data.json` |
| `lang/` | External language files copied from bundled resources |
| `logs/` | Current and archived logs |

## Important files

| File | Purpose |
| --- | --- |
| `settings/settings.json` | Main app settings |
| `settings/blocklist.json` | Hidden-mod rules |
| `settings/custom_games.json` | Custom games plus order and visibility |
| `settings/session.lock` | Session recovery data after launch-time patching |
| `downloads/downloads_history.json` | Download history |
| `game_versions/game_versions_data.json` | Saved game version records |
| `plugins/plugins_data.json` | Plugin enabled state and plugin settings |

## Profiles

Each profile is a folder inside `profiles/`. Mod folders live directly inside the profile folder, alongside the profile JSON file and `mods_data.json`.

That means the current layout is:

- `profiles/<ProfileName>/<ProfileName>.json`
- `profiles/<ProfileName>/mods_data.json`
- `profiles/<ProfileName>/<ModFolder>/...`

There is no separate active `mods/` subfolder inside a profile.

## Custom files

Custom assets are stored at the data root with fixed base names:

- `custom_background.*`
- `custom_logo.*`
- `custom_font.*`
- `custom_startup_sound.*`
- `custom_background_music.*`

The exact extension depends on the file you selected.

## Temporary and recovery files

- Launch-time patch backups use `patching_backups/`.
- Crash recovery uses `settings/session.lock`.
- Download and import operations may also create temporary files while they run.
