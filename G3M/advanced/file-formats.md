# File Formats Reference

This page catalogs every file format that G3M reads, writes, or processes.

---

## Game Data Files

These are the main data files for GameMaker-based games. G3M patches these files when applying mods.

| Extension | Platform | Description |
| --- | --- | --- |
| `.win` | Windows | The primary GameMaker data file on Windows (commonly `data.win`). |
| `.ios` | iOS | GameMaker data file for iOS builds (commonly `game.ios`). |
| `.unx` | Linux | GameMaker data file for Linux/Unix builds. |
| `.droid` | Android | GameMaker data file for Android builds. |

---

## Patch Formats

Patches modify game data files without replacing them entirely. G3M supports multiple patch formats.

### g3mpatch

- **Extension**: `.g3mpatch` or `.zip` containing `g3mpatch.json`
- **Created by**: G3MTool (bundled with G3M)
- **Description**: G3M's native patch format. Contains a JSON manifest (`g3mpatch.json`) describing which chunks of the data file to modify, along with the modified chunk data. Can be stored as a single `.g3mpatch` file or as a `.zip` archive containing the manifest and data files.
- **Advantages**: Compact (only changed data is stored), supports verification, created automatically by Modding Tools.

### xdelta / vcdiff

- **Extensions**: `.xdelta`, `.vcdiff`
- **Description**: Standard binary diff/patch formats. Stores the minimal set of instructions to transform the original file into the modified version. Requires the original unmodified data file to apply.
- **Usage**: Common in the modding community. G3M can both create and apply xdelta patches via G3MTool.

### CSX Scripts

- **Extension**: `.csx`
- **Description**: C# script files executed by G3MTool against a game data file. Allows programmatic modifications (adding sprites, changing code, modifying resources). More flexible than binary patches but requires G3MTool to execute.
- **Usage**: Advanced mod creation. Scripts can perform complex transformations that binary patches cannot express.

---

## Mod Configuration

### mod_config.json

The core metadata file for every G3M mod. JSON format.

**Top-level fields:**

| Field | Type | Description |
| --- | --- | --- |
| `config_version` | string | Schema version (e.g., `"1.0.0"`). |
| `metadata` | object | Nested object containing all mod metadata (see below). |
| `files` | object | Chapter-to-file mapping (see below). |

**`metadata` object fields:**

| Field | Type | Example |
| --- | --- | --- |
| `id` | string | `"local_abc123"` or `"gb_mod_45678"` |
| `name` | string | `"My Awesome Mod"` |
| `version` | string | `"1.2.0"` |
| `author` | string | `"ModAuthor"` |
| `description` | string | `"A cool mod that changes the intro."` |
| `homepage` | string | `"https://gamebanana.com/mods/12345"` |
| `icon` | string | `"icon.png"` |
| `game` | string | `"deltarune"` |
| `game_version` | string | `"1.10"` |
| `tags` | array | `["customization", "gameplay"]` |

Per-mod playtime, added date, and last-updated timestamps are stored in the profile's `mods_data.json`, not in `mod_config.json`.

**files object:**

Each key is a chapter/section identifier (e.g., `"deltarune_1"`, `"undertale"`, `"pizzatower"`). The value is:

| Field | Type | Description |
| --- | --- | --- |
| `description` | string | Chapter-specific description. |
| `data_file_path` | string | Path to the main data/patch file (relative to mod folder). |
| `extra_files` | array | List of additional file paths to copy into the game folder. |

---

## Plugin Configuration

### plugin_config.json

The manifest file for G3M plugins. JSON format.

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `config_version` | int | Yes | Schema version (currently 1). |
| `id` | string | Yes | Unique plugin identifier. |
| `name` | string | Yes | Display name. |
| `description` | string | Yes | Brief description. |
| `author` | string | Yes | Author name. |
| `version` | string | Yes | Plugin version. |
| `entry` | string | Yes | Main Python file name (e.g., "main.py"). |
| `api_version` | string | Yes | Target Plugin API version (e.g., `"1.0.0"`). Must match the app's `PLUGIN_API_VERSION`. |
| `icon` | string | No | Icon file path. |
| `homepage` | string | No | URL to project page. |
| `tags` | array | No | Category tags. |
| `relations` | object | No | Dependencies/conflicts (`{plugin_id: "require"/"conflict"}`). |
| `hooks` | array | No | List of hook names. |
| `settings_schema` | object | No | Plugin settings definition. |

---

## Settings Files

### settings.json

Main application settings. Stored in `{user_data_root}/settings/settings.json`.

Key sections:

| Key | Type | Description |
| --- | --- | --- |
| `game_path` | string | DELTARUNE installation folder path. |
| `demo_game_path` | string | DELTARUNE DEMO folder path. |
| `undertale_game_path` | string | UNDERTALE folder path. |
| `undertaleyellow_game_path` | string | UNDERTALE Yellow folder path. |
| `pizzatower_game_path` | string | Pizza Tower folder path. |
| `sugaryspire_game_path` | string | Sugary Spire folder path. |
| `custom_game_path_<id>` | string | Custom game folder paths. |
| `launch_via_steam` | boolean | Launch games through Steam. |
| `use_portproton` | boolean | Use PortProton on Linux. |
| `portproton_path` | string | Path to PortProton installation. |
| `use_custom_executable` | boolean | Use custom game executable. |
| `custom_executable_path` | string | DELTARUNE custom executable path. |
| `custom_background_path` | string | Path to custom background file. |
| `background_disabled` | boolean | Disable background image. |
| `disable_startup_sound` | boolean | Mute startup sound. |
| `disable_animations` | boolean | Turn off UI animations. |
| `pause_background_music_unfocused` | boolean | Pause music when unfocused. |
| `custom_background_color` | string | Hex color for background. |
| `custom_elements_color` | string | Hex color for elements. |
| `custom_border_color` | string | Hex color for borders. |
| `custom_hover_color` | string | Hex color for hover state. |
| `custom_select_color` | string | Hex color for selection. |
| `custom_main_text_color` | string | Hex color for main text. |
| `custom_secondary_text_color` | string | Hex color for secondary text. |
| `custom_border_radius` | integer | Window corner radius (0–20). |
| `beta_updates_enabled` | boolean | Include beta versions in update checks. |
| `skip_patching_warnings` | boolean | Skip confirmation before patching. |
| `merge_properties` | boolean | Merge game object properties during patching. |
| `merge_code` | boolean | Merge code blocks during patching. |
| `hide_mods_browser_tab` | boolean | Hide the Mods Browser tab. |
| `hide_library_tab` | boolean | Hide the Library tab. |
| `hide_library_filters` | boolean | Hide filters in the Library. |
| `show_reset_buttons` | boolean | Show reset buttons in Appearance. |
| `analytics_opt_in_enabled` | boolean | Enable anonymous analytics. |
| `downloads_no_auto_use` | boolean | Don't auto-install downloads. |
| `downloads_delete_after_use` | boolean | Delete archives after install. |
| `downloads_save_local_imports` | boolean | Record local imports as downloads. |
| `demo_mode_enabled` | boolean | Legacy demo mode flag. |
| `active_profile` | string | Name of the active profile. |
| `last_selected` | object | Last selected game/chapter per context. |
| `cache_format_version` | string | App version that last wrote settings. |
| `announce_identity` | string | Anonymous UUID for poll voting. |
| `announce_poll_votes` | object | Record of submitted poll votes. |

### blocklist.json

Mod blocklist rules. Stored in `{user_data_root}/settings/blocklist.json`.

Structure: Object with game IDs (or "global") as keys, each mapping to an array of rule objects with `prefix_type` and `value`.

### custom_games.json

Custom game registry. Stored in `{user_data_root}/settings/custom_games.json`.

| Field | Description |
| --- | --- |
| `schema_version` | Schema version (currently 1). |
| `order` | Array of game IDs in display order. |
| `visibility` | Object mapping game IDs to boolean visibility. |
| `custom_games` | Array of custom game records. |

### `<ProfileName>.json`

Per-profile state. Stored in `{user_data_root}/profiles/<name>/<name>.json` (e.g., `profiles/Default/Default.json`).

Contains profile-specific flat keys: `selected_game_type`, `used_mods_<chapter_id>` (arrays of mod IDs), `chapter_mode_enabled`, `full_install_enabled`, and similar.

### plugins_data.json

Plugin enabled/disabled state and per-plugin settings. Stored in `{user_data_root}/plugins/plugins_data.json`.

Structure: `{"enabled": {"plugin_id": bool, ...}, "settings": {"plugin_id": {...}, ...}}`.

### downloads_history.json

Download history. Stored in `{user_data_root}/downloads/downloads_history.json`.

Array of download record objects with fields described in [Downloads](../features/downloads.md).

### game_versions_data.json

Game version records. Stored in `{user_data_root}/game_versions/game_versions_data.json`.

---

## Archive Formats

G3M can extract files from these archive formats:

| Format | Extension | Library Used |
| --- | --- | --- |
| ZIP | `.zip` | Built-in `zipfile` module |
| 7-Zip | `.7z` | `py7zr` library |
| RAR | `.rar` | `rarfile` library |
| TAR (all variants) | `.tar.gz`, `.tar.bz2`, `.tar.xz`, `.tar`, `.tgz` | Built-in `tarfile` module |
| LZMA | `.lzma` | Built-in `lzma` module |

---

## Theme Package

### Theme package (.zip)

A standard `.zip` archive containing a `theme_config.json` manifest and optional media asset files. See [Theme Packages](../customization/theme-packages.md) for details.

Recognized manifest file names: `theme_config.json` (current), `theme.json` (legacy).

---

## DELTAMOD Format

Legacy mod format from Deltamod Manager.

| File | Description |
| --- | --- |
| `_deltamodInfo.json` or `meta.json` | JSON metadata (name, author, game, etc.) |
| `modding.xml` | XML descriptor with mod metadata and file references. |

G3M auto-converts DELTAMOD mods on import. See [Importing Mods](../mods/importing.md#deltamod-conversion).

---

## PizzaOven Format

Mod format for Pizza Tower via PizzaOven.

| File | Description |
| --- | --- |
| `mod.json` | Metadata file with mod name, author, and structure. |
| `audio/`, `code/`, `texture/`, etc. | Folders containing mod resources. |

G3M attempts auto-conversion of eligible PizzaOven mods. See [Importing Mods](../mods/importing.md#pizzaoven-conversion).

---

## Supported Audio Formats

For custom startup sounds and background music:

`.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, `.aac`

---

## Supported Image Formats

For custom backgrounds, logos, and mod icons:

`.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.ico`, `.webp`

---

## Supported Video Formats

For custom backgrounds:

`.mp4`, `.webm`, `.avi`, `.mkv`, `.mov`, `.m4v`, `.3gp`, `.mpg`, `.mpeg`, `.flv`, `.wmv`

---

## Supported Font Formats

For custom application fonts:

`.ttf` (TrueType), `.otf` (OpenType)
