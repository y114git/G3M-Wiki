# Data Directory Reference

This page provides a complete map of every file and folder in G3M's user data directory.

---

## Location

| Platform | Path |
| --- | --- |
| Windows | `%APPDATA%\G3M` |
| macOS | `~/Library/Application Support/G3M` |
| Linux | `~/.local/share/G3M` |

---

## Top-Level Structure

```
G3M/
├── settings/
│   ├── settings.json
│   ├── blocklist.json
│   └── custom_games.json
├── profiles/
│   ├── Default/
│   │   ├── profile.json
│   │   └── mods/
│   │       ├── mod_folder_1/
│   │       │   ├── mod_config.json
│   │       │   ├── data/
│   │       │   ├── icon.png
│   │       │   └── mod_versions/
│   │       └── mod_folder_2/
│   └── MyProfile/
│       ├── profile.json
│       └── mods/
├── downloads/
│   ├── downloads.json
│   └── (downloaded archive files)
├── game_versions/
│   ├── game_versions.json
│   └── (version archive files)
├── plugins/
│   ├── plugin_folder_1/
│   │   ├── plugin_config.json
│   │   ├── main.py
│   │   ├── icon.png
│   │   └── lang/
│   └── plugin_folder_2/
├── plugins_state.json
├── lang/
│   ├── lang_en.json
│   ├── lang_es.json
│   ├── lang_ru.json
│   ├── lang_zh_cn.json
│   └── lang_zh_tw.json
├── logs/
│   ├── g3m.log
│   ├── shortcut.log
│   └── g3m/
│       ├── g3m_2024-03-20_14-30-00.log
│       └── g3m_2024-03-19_09-15-00.log
├── custom_background.png
├── custom_logo.png
├── custom_font.ttf
├── custom_startup_sound.mp3
└── custom_background_music.mp3
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

### profile.json

Per-profile state file:

```json
{
  "used_mods": {
    "deltarune_1": ["mod_id_1", "mod_id_2"],
    "deltarune_2": ["mod_id_3"],
    "undertale": []
  }
}
```

### mods/ Subdirectory

Contains one folder per installed mod. Each mod folder contains:

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

### downloads.json

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

### game_versions.json

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

### plugins_state.json

Stored at the data directory root (not inside `plugins/`):

```json
{
  "my_plugin": {
    "enabled": true,
    "settings": {
      "custom_key": "custom_value"
    }
  },
  "another_plugin": {
    "enabled": false,
    "settings": {}
  }
}
```

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

| File | Source |
| --- | --- |
| `custom_background.<ext>` | Set via Settings → Appearance → Custom Background. |
| `custom_logo.<ext>` | Set via Settings → Appearance → Custom Logo. |
| `custom_font.<ext>` | Set via Settings → Appearance → Custom Font. |
| `custom_startup_sound.<ext>` | Set via Settings → Appearance → Select startup sound. |
| `custom_background_music.<ext>` | Set via Settings → Appearance → Select background music. |

The file extension depends on the original file you selected. Only one custom file of each type exists at a time — selecting a new one replaces the old one.

---

## Temporary Files

During operations, G3M may create temporary files:

- **Backup directory** — Created during game patching, deleted after restoration. Location: typically a subdirectory of the game path or a system temp directory.
- **Download temp files** — Partial downloads before completion. Location: `downloads/` folder.
- **Archive extraction temp** — Temporary extraction directory during mod import. Location: system temp directory.

All temporary files are cleaned up after their operation completes (or on the next launch if G3M crashed).
