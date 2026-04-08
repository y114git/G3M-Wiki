# Data Directory Reference

This page provides a complete map of every file and folder in G3M's user data directory.

---

## Location

| Platform | Path |
| --- | --- |
| Windows | `%LOCALAPPDATA%\G3M` (falls back to `%APPDATA%\G3M` if LOCALAPPDATA is unset) |
| macOS | `~/Library/Application Support/G3M` |
| Linux | `~/.local/share/G3M` |

---

## Top-Level Structure

```
G3M/
├── settings/
│   ├── settings.json
│   ├── blocklist.json
│   ├── custom_games.json
│   └── session.lock          (only present while game is running / after crash)
├── profiles/
│   ├── Default/
│   │   ├── Default.json      (profile state file)
│   │   ├── mods_data.json    (mod metadata cache)
│   │   ├── mod_folder_1/     (mod folders are directly in the profile dir)
│   │   │   ├── mod_config.json
│   │   │   ├── data/
│   │   │   ├── icon.png
│   │   │   └── mod_versions/
│   │   └── mod_folder_2/
│   └── MyProfile/
│       ├── MyProfile.json
│       ├── mods_data.json
│       └── (mod folders...)
├── downloads/
│   ├── downloads_history.json
│   └── (downloaded archive files)
├── game_versions/
│   ├── game_versions_data.json
│   └── (version archive files)
├── plugins/
│   ├── plugins_data.json     (plugin enabled/settings state)
│   ├── plugin_folder_1/
│   │   ├── plugin_config.json
│   │   ├── main.py
│   │   ├── icon.png
│   │   └── lang/
│   └── plugin_folder_2/
├── themes/
│   └── (user-saved .zip theme archives)
├── lang/
│   ├── lang_en.json
│   ├── lang_es.json
│   ├── lang_ru.json
│   └── (other language files)
├── logs/
│   ├── g3m.log
│   ├── shortcut.log
│   └── g3m/
│       └── (archived log files with timestamps)
├── custom_background.<ext>
├── custom_logo.<ext>
├── custom_font.<ext>
├── custom_startup_sound.<ext>
└── custom_background_music.<ext>
```

---

## settings/ Directory

### settings.json

The main application configuration file. Contains all user preferences as a flat JSON object. See [File Formats Reference → settings.json](file-formats.md#settingsjson) for the complete key list.

### blocklist.json

Mod blocklist rules. Structure:

```json
{
  "global": [
    { "prefix_type": "name", "value": "some mod name" }
  ],
  "deltarune": [
    { "prefix_type": "id", "value": "12345" }
  ]
}
```

### custom_games.json

Custom game definitions and game display order/visibility:

```json
{
  "schema_version": 1,
  "order": ["deltarune", "undertale", "pizzatower", "my_custom_game"],
  "visibility": { "deltarune": true, "undertale": true },
  "custom_games": [
    {
      "id": "my_custom_game",
      "name": "My Game",
      "data_file": "data.win",
      "executable": "MyGame.exe",
      "process_name": "MyGame",
      "game_path": "C:/Games/MyGame"
    }
  ]
}
```

---

## profiles/ Directory

Each profile is a subfolder. Every G3M installation always has a `Default/` profile.

### `<ProfileName>.json`

Per-profile state file. The filename matches the profile folder name (e.g., `Default.json`). Contains profile-specific settings keys such as `selected_game_type`, `used_mods_<chapter_id>` entries, `chapter_mode_enabled`, and `full_install_enabled`. These keys are stored separately from `settings.json` and loaded/saved when switching profiles.

### `mods_data.json`

Cached mod metadata for the profile, written on scan.

### Mod folders

Mod folders are stored **directly** in the profile directory (not in a `mods/` subdirectory). Each mod folder contains:

| File | Purpose |
| --- | --- |
| `mod_config.json` | Mod metadata and file references. |
| `*.g3mpatch` / `*.xdelta` / `*.csx` / `*.win` | The mod's data/patch files. |
| `icon.png` (or other image format) | Mod icon. |
| `extra_files/` | Additional files the mod copies into the game folder. |
| `mod_versions/` | Subfolder containing version snapshot `.zip` archives. |
| Documentation files | Optional `.txt`, `.md`, `.pdf`, `.html` readme files. |

---

## downloads/ Directory

### downloads_history.json

Array of download records:

```json
[
  {
    "id": "dl_abc123",
    "name": "Cool Mod v2.0",
    "source_kind": "gamebanana",
    "target_kind": "mod",
    "status": "downloaded",
    "use_status": "ready",
    "url": "https://files.gamebanana.com/...",
    "file_path": "cool_mod_v2.0.zip",
    "file_size": 5242880,
    "progress": 100,
    "created_at": "2024-03-20T10:30:00Z",
    "updated_at": "2024-03-20T10:31:00Z"
  }
]
```

Downloaded archive files are stored directly in the `downloads/` folder.

---

## game_versions/ Directory

### game_versions_data.json

Array of game version records:

```json
[
  {
    "id": "gv_xyz789",
    "label": "Clean Install 1.10",
    "game_id": "deltarune",
    "file_path": "deltarune_clean_1.10.zip",
    "file_size": 104857600,
    "status": "ready",
    "created_at": "2024-03-15T08:00:00Z"
  }
]
```

Version archive `.zip` files are stored directly in `game_versions/`.

---

## plugins/ Directory

Each plugin is a folder containing at minimum `plugin_config.json` and a Python entry file. See [Plugins](../features/plugins.md) for details.

### plugins_data.json

Stored inside `plugins/` (at `plugins/plugins_data.json`). Structure:

```json
{
  "enabled": {
    "my_plugin": true,
    "another_plugin": false
  },
  "settings": {
    "my_plugin": { "custom_key": "custom_value" },
    "another_plugin": {}
  }
}
```

---

## themes/ Directory

Contains user-saved theme package archives (`.zip` files). When you import a theme via Settings, it is saved here. The directory is scanned to populate the theme selector list.

---

## lang/ Directory

Contains language JSON files synced from the bundled resources. On each launch:

1. G3M copies bundled language files to `lang/`.
2. If the external file exists, G3M merges new keys from the bundled version into the external file.
3. User customizations to existing keys are preserved.

---

## logs/ Directory

### g3m.log

Current session log. Overwritten on each launch (previous copy is archived first).

### shortcut.log

Log from the most recent headless shortcut launch.

### g3m/ Subdirectory

Archived logs from previous sessions. File names include timestamps. These are not automatically cleaned up.

---

## Custom Media Files

Custom media files are stored at the data directory root:

| File | Accepted Extensions |
| --- | --- |
| `custom_background.<ext>` | Image: `.png .jpg .jpeg .gif .bmp .ico .webp`; Video: `.mp4 .webm .avi .mkv .mov .m4v .3gp .mpg .mpeg .flv .wmv` |
| `custom_logo.<ext>` | Same as background. |
| `custom_font.<ext>` | `.ttf .otf` |
| `custom_startup_sound.<ext>` | `.mp3 .wav .ogg .flac .m4a .aac` |
| `custom_background_music.<ext>` | `.mp3 .wav .ogg .flac .m4a .aac` |

The file extension depends on the original file you selected. Only one custom file of each type exists at a time — selecting a new one replaces the old one.

---

## Temporary Files

During operations, G3M may create temporary files:

- **Backup directory** — Created during game patching, deleted after restoration. Location: `{user_data_root}/patching_backups/` for normal patches; inside a system temp directory for modpack patches.
- **Download temp files** — Partial downloads before completion. Location: `downloads/` folder.
- **Archive extraction temp** — Temporary extraction directory during mod import. Location: system temp directory.

All temporary files are cleaned up after their operation completes (or on the next launch if G3M crashed).
