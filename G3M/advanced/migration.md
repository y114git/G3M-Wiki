# Migration

G3M handles data migration from the legacy DELTAHUB application and between internal format versions.

---

## DELTAHUB → G3M Migration

When G3M is launched for the first time and detects a `DELTAHUB` data folder but no `G3M` data folder, it offers a migration choice:

- **Import Data** — Copies the entire DELTAHUB data directory to the new G3M location. This includes settings, mods, profiles, plugins, downloads, and all configuration files.
- **Start Fresh** — Creates a new empty G3M data folder.

If the import fails (e.g., file permission errors), a notification is shown and a fresh folder is created instead.

---

## Settings Migration

When loading settings from an older version, G3M automatically migrates legacy keys:

### Theme Color Keys

Older versions used different key names for theme colors. These are renamed automatically:

| Old Key | New Key |
| --- | --- |
| `custom_color_background` | `custom_background_color` |
| `custom_color_elements` | `custom_elements_color` |
| `custom_color_border` | `custom_border_color` |
| `custom_color_hover` | `custom_hover_color` |
| `custom_color_select` | `custom_select_color` |
| `custom_color_main_text` | `custom_main_text_color` |
| `custom_color_secondary_text` | `custom_secondary_text_color` |
| `custom_color_button` | `custom_elements_color` |
| `custom_color_button_hover` | `custom_hover_color` |
| `custom_color_button_select` | `custom_select_color` |
| `custom_color_text` | `custom_main_text_color` |
| `custom_color_version_text` | `custom_secondary_text_color` |

### Chapter ID Migration

Older versions used numeric chapter IDs. These are mapped to the new string-based IDs:

| Old ID | New ID |
| --- | --- |
| `-1` | `deltarune` |
| `0` | `deltarune_0` |
| `1` | `deltarune_1` |
| `2` | `deltarune_2` |
| `3` | `deltarune_3` |
| `4` | `deltarune_4` |
| `-10` | `deltarunedemo` |
| `-20` | `undertale` |
| `-30` | `undertaleyellow` |
| `-40` | `pizzatower` |
| `-50` | `sugaryspire` |

### Default Settings

If any expected settings key is missing (e.g., after an update adds new settings), G3M fills it with the default value from the settings schema. This ensures the application always has a complete configuration.

### Cache Format Version

The `cache_format_version` key in settings is updated to match the current app version on every launch. This allows G3M to detect when settings were last touched by a different version.

---

## Profile Migration

If settings contain profile-related keys at the top level (from an older version that didn't use separate profile folders), they are extracted and written into the Default profile's `profile.json`. The keys are then removed from the main settings.

Legacy per-game mod folders that were stored flat in the mods directory are restructured into the profile-based folder hierarchy.

---

## Mod Config Migration

Older mod configurations may use legacy field names:

| Legacy Field | Current Field |
| --- | --- |
| `tagline` | `description` |
| `icon_url` | `icon` |
| `key` / `mod_key` | `id` |
| `external_url` / `external_link` / `site` / `url` | `homepage` |

These are resolved when loading mod configs — the application checks both legacy and current field names.

---

## Automatic and Silent

All migrations are automatic and silent. They happen during application startup or when loading the relevant data. No user interaction is required. If a migration changes the settings file, it is written back to disk immediately.
