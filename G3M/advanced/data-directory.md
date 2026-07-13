# Data Directory

G3M stores its user data outside the game folders. This is where your settings,
profiles, downloads, plugins, logs, and custom files live.

## Location

| Platform | Path                                                    |
| -------- | ------------------------------------------------------- |
| Windows  | `%LOCALAPPDATA%\\G3M` with `%APPDATA%\\G3M` as fallback |
| macOS    | `~/Library/Application Support/G3M`                     |
| Linux    | `~/.local/share/G3M`                                    |

## Main folders

- **Windows path:** `%LOCALAPPDATA%\G3M\settings\`
  - **Purpose:** App settings, blocklist, custom games, crash/session state

- **Windows path:** `%LOCALAPPDATA%\G3M\profiles\`
  - **Purpose:** Per-profile mod libraries and profile-specific state

- **Windows path:** `%LOCALAPPDATA%\G3M\downloads\`
  - **Purpose:** Download history and downloaded archives

- **Windows path:** `%LOCALAPPDATA%\G3M\game_versions\`
  - **Purpose:** Saved game version archives and their index

- **Windows path:** `%LOCALAPPDATA%\G3M\plugins\`
  - **Purpose:** Installed plugins and `plugins_data.json`

- **Windows path:** `%LOCALAPPDATA%\G3M\lang\`
  - **Purpose:** External language files copied from bundled resources

- **Windows path:** `%LOCALAPPDATA%\G3M\logs\`
  - **Purpose:** Current and archived logs

## Important files

- **Windows path:** `%LOCALAPPDATA%\G3M\settings\settings.json`
  - **Purpose:** Main app settings

- **Windows path:** `%LOCALAPPDATA%\G3M\settings\blocklist.json`
  - **Purpose:** Hidden-mod rules

- **Windows path:** `%LOCALAPPDATA%\G3M\settings\custom_games.json`
  - **Purpose:** Custom games plus order and visibility

- **Windows path:** `%LOCALAPPDATA%\G3M\settings\session.lock`
  - **Purpose:** Session recovery data after launch-time patching

- **Windows path:** `%LOCALAPPDATA%\G3M\downloads\downloads_history.json`
  - **Purpose:** Download history

- **Windows path:** `%LOCALAPPDATA%\G3M\game_versions\game_versions_data.json`
  - **Purpose:** Saved game version records

- **Windows path:** `%LOCALAPPDATA%\G3M\plugins\plugins_data.json`
  - **Purpose:** Plugin enabled state and plugin settings

## Profiles

Each profile is a folder inside `%LOCALAPPDATA%\G3M\profiles\` on Windows. Mod
folders live directly inside the profile folder, alongside the profile JSON file
and `mods_data.json`.

That means the current layout is:

- `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\<ProfileName>.json`
- `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\mods_data.json`
- `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\<ModFolder>\...`

There is no separate active `mods/` subfolder inside a profile.

## Custom files

Custom assets are stored at the data root with fixed base names:

- `%LOCALAPPDATA%\G3M\custom_background.*`
- `%LOCALAPPDATA%\G3M\custom_logo.*`
- `%LOCALAPPDATA%\G3M\custom_font.*`
- `%LOCALAPPDATA%\G3M\custom_startup_sound.*`
- `%LOCALAPPDATA%\G3M\custom_background_music.*`

The exact extension depends on the file you selected.

## Temporary and recovery files

- Launch-time patch backups use `%LOCALAPPDATA%\G3M\patching_backups\`.
- Crash recovery uses `%LOCALAPPDATA%\G3M\settings\session.lock`.
- Download and import operations may also create temporary files while they run.
