# Data Directory

G3M stores its user data outside the game folders. This is where your settings,
profiles, downloads, plugins, logs, and custom files live.

## Location

| Platform | Path                                                    |
| -------- | ------------------------------------------------------- |
| Windows  | `%LOCALAPPDATA%\\G3M` with `%APPDATA%\\G3M` as fallback |
| macOS    | `~/Library/Application Support/G3M`                     |
| Linux    | `~/.local/share/G3M`                                    |

The default remains unchanged. In **Settings > App > Advanced**, you can select
any folder as the data root. G3M uses that folder directly and does not add a
`G3M` subfolder.

When changing the location, choose whether to copy the current data or use the
selected folder without copying. The old folder is never deleted. Restart G3M
after a successful change. Resetting the setting returns to the platform
default through the same flow.

If a configured removable drive or network location is unavailable, GUI startup
offers retry, another folder, or the default location. Shortcut launches stop
with an error instead of silently using the wrong profiles.

## Main folders

The examples below use `<data-root>` for either the default path above or the
folder selected in settings.

- `<data-root>/settings/`
  - **Purpose:** App settings, blocklist, custom games, crash/session state

- `<data-root>/profiles/`
  - **Purpose:** Per-profile mod libraries and profile-specific state

- `<data-root>/downloads/`
  - **Purpose:** Download history and downloaded archives

- `<data-root>/game_versions/`
  - **Purpose:** Saved game version archives and their index

- `<data-root>/plugins/`
  - **Purpose:** Installed plugins and `plugins_data.json`

- `<data-root>/lang/`
  - **Purpose:** External language files copied from bundled resources

- `<data-root>/logs/`
  - **Purpose:** Current and archived logs

## Important files

- `<data-root>/settings/settings.json`
  - **Purpose:** Main app settings

- `<data-root>/settings/blocklist.json`
  - **Purpose:** Hidden-mod rules

- `<data-root>/settings/custom_games.json`
  - **Purpose:** Custom games plus order and visibility

- `<data-root>/settings/session.lock`
  - **Purpose:** Active launch backup map and deployed-file fingerprints

- `<data-root>/downloads/downloads_history.json`
  - **Purpose:** Download history

- `<data-root>/game_versions/game_versions_data.json`
  - **Purpose:** Saved game version records

- `<data-root>/plugins/plugins_data.json`
  - **Purpose:** Plugin enabled state and plugin settings

## Profiles

Each profile is a folder inside `<data-root>/profiles/`. Mod
folders live directly inside the profile folder, alongside the profile JSON file
and `mods_data.json`.

That means the current layout is:

- `<data-root>/profiles/<ProfileName>/<ProfileName>.json`
- `<data-root>/profiles/<ProfileName>/mods_data.json`
- `<data-root>/profiles/<ProfileName>/<ModFolder>/...`

There is no separate active `mods/` subfolder inside a profile.

## Custom files

Custom assets are stored at the data root with fixed base names:

- `<data-root>/custom_background.*`
- `<data-root>/custom_logo.*`
- `<data-root>/custom_font.*`
- `<data-root>/custom_startup_sound.*`
- `<data-root>/custom_background_music.*`

The exact extension depends on the file you selected.

## Temporary and recovery files

- Launch-time patch backups use `<data-root>/patching_backups/`.
- Crash recovery uses `<data-root>/settings/session.lock`.
- Sessions with external file changes move under
  `<data-root>/patching_backups/recovery_conflicts/` for manual inspection.
- Download and import operations may also create temporary files while they run.
