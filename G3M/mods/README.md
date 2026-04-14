# Mods

G3M supports multiple mod formats and provides a complete workflow for browsing, importing, creating, editing, exporting, and versioning mods.

---

## Mod Structure

Every mod in G3M is stored as a folder inside the current profile's `mods/` directory. Inside each mod folder:

| File / Folder | Required | Description |
| --- | --- | --- |
| `mod_config.json` | Yes | The mod's configuration file containing metadata and file references. |
| Chapter data files | No | The actual mod data files (e.g., patched `data.win`, `.g3mpatch`, `.xdelta`, `.csx` scripts). Organized by chapter/section. |
| `icon.png` (or similar) | No | A local icon image for the mod. Referenced in `mod_config.json`. |
| `mod_versions/` | No | Subfolder containing saved version snapshots as `.zip` archives. |
| Extra files | No | Any additional files the mod needs (DLLs, audio banks, textures, etc.). |

---

## mod_config.json Format

The mod configuration file is a JSON file with the following top-level structure:

| Field | Type | Description |
| --- | --- | --- |
| `config_version` | string | Schema version (e.g., `"1.0.0"`). |
| `metadata` | object | Nested object containing all mod metadata fields (see below). |
| `files` | object | Chapter-to-file-data mapping. Each key is a chapter/section ID, and the value is a file data object. |

### `metadata` Object Fields

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | Unique mod identifier. Local mods use `local_<uuid>`. GameBanana mods use `gb_mod_<id>` or `gb_wip_<id>`. |
| `name` | string | Display name of the mod. |
| `version` | string | Version string (e.g., "1.0.0"). |
| `author` | string | The mod author's name. |
| `description` | string | A brief description of what the mod does. |
| `homepage` | string | URL to the mod's homepage (GameBanana page, website, etc.). |
| `icon` | string | Path to the icon file (relative to the mod folder) or a URL. |
| `game` | string | The game ID this mod is for (e.g., `"deltarune"`, `"undertale"`, `"pizzatower"`). |
| `game_version` | string | Which game version this mod is designed for. |
| `tags` | array | List of string tags: `"textedit"`, `"customization"`, `"gameplay"`, `"other"`. |

Per-mod playtime, added date, and last-updated timestamps are stored separately in the profile's `mods_data.json`, not in `mod_config.json`.

### File Data Object

Each entry in the `files` object:

| Field | Type | Description |
| --- | --- | --- |
| `description` | string | Description specific to this chapter/section. |
| `data_file_path` | string | Path to the main data file (local path or URL). For patches: path to the `.g3mpatch`, `.xdelta`, `.vcdiff`, or `.csx` file. |
| `extra_files` | array | List of paths to additional files that should be copied into the game directory during patching. |

---

## Supported Mod Formats

G3M recognizes and can import mods from multiple formats:

| Format | Extension(s) | Description |
| --- | --- | --- |
| **G3M native** | folder with `mod_config.json` | The native format. Already structured for G3M. |
| **g3mpatch** | `.g3mpatch`, `.zip` containing `g3mpatch.json` | A binary patch format created by G3MTool. Contains a manifest describing which chunks of the data file to modify. |
| **xdelta** | `.xdelta`, `.vcdiff` | Standard binary diff/patch format. Requires the original data file as a base. |
| **CSX script** | `.csx` | C# script executed by G3MTool to programmatically modify game data. |
| **Raw data file** | `.win`, `.ios`, `.unx`, `.droid` | A complete replacement for the game's data file. |
| **DELTAMOD** | `.zip` containing `_deltamodInfo.json` (or `meta.json`) and `modding.xml` | A mod format used by Deltamod Manager. G3M automatically converts it to native G3M format on import. |
| **PizzaOven (NORMAL)** | `.zip` with `mod.json` and patch/audio/language files | Pizza Tower mods from the PizzaOven manager. G3M simulates the PizzaOven build against a temp game copy and converts the result. Requires Pizza Tower game path. |
| **AFOM/CYOP** | `.zip` with tower folder(s), each containing an `.ini` with `[properties]` | Pizza Tower custom level (tower) mods. G3M deploys the tower folders to `%APPDATA%\PizzaTower_GM2\towers\` on launch and removes them after. |
| **Archives** | `.zip`, `.7z`, `.rar` | Compressed archives that may contain any of the above formats. G3M extracts and inspects them automatically. |

These conversion paths are not limited to the Library import button. The same archive detection is also used by the Downloads auto-use flow, one-click installs, and mod version archive import where applicable.

### Supported Archive Formats

G3M can extract archives in these formats:
- **ZIP** (`.zip`) — Built-in support.
- **7-Zip** (`.7z`) — Supported via the py7zr library.
- **RAR** (`.rar`) — Supported via the rarfile library.

---

## Mod ID Conventions

- **Local mods**: `local_<uuid>` — Automatically generated when creating or importing a mod locally.
- **GameBanana mods**: `gb_mod_<gamebanana_mod_id>` — Generated from the GameBanana mod ID when downloading from the browser.
- **GameBanana WIP mods**: `gb_wip_<gamebanana_wip_id>` — For work-in-progress mods on GameBanana.

---

## Mod Lifecycle

1. **Obtain** — Browse GameBanana, import from file, or create from scratch.
2. **Import / Install** — The mod is placed in the profile's `mods/` folder with a valid `mod_config.json`.
3. **Select** — Mark the mod as "Used" for one or more chapters in the Library.
4. **Patch** — On launch, G3M applies the mod's patches to the game's data files.
5. **Play** — The game runs with the modded files.
6. **Restore** — When the game exits, G3M restores the original game files from backups.
7. **Update** — If a newer version is available on GameBanana, update the mod files.
8. **Version** — Save snapshots of the mod as versions for rollback.
9. **Export** — Package the mod as a `.zip` for sharing.
