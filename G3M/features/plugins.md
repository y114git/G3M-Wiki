# Plugins

G3M has a plugin system that lets third-party developers extend the application with new functionality. Plugins can hook into the mod lifecycle, add UI elements, and integrate with G3M's services.

---

## Plugin API Version

The current Plugin API version is **1.0.0**. Plugins declare which API version they target. G3M checks compatibility: a plugin is compatible if its declared API version matches the host's API version.

---

## Plugin Structure

Each plugin is a folder inside the `plugins/` directory of the user data folder. The folder contains:

| File | Required | Description |
| --- | --- | --- |
| `plugin_config.json` | Yes | The plugin manifest containing metadata and configuration. |
| Python entry file | Yes | The main Python file specified in the manifest's `entry` field. |
| `lang/` | No | Subfolder with localization files (`lang_en.json`, etc.) for plugin-specific strings. |
| Icon file | No | An icon image referenced in the manifest. |
| Additional files | No | Any other files the plugin needs. |

---

## Plugin Manifest (`plugin_config.json`)

| Field | Type | Description |
| --- | --- | --- |
| `config_version` | int | Manifest schema version (currently 1). |
| `id` | string | Unique plugin identifier (e.g., "my_awesome_plugin"). |
| `name` | string | Display name shown in the Plugins tab. |
| `description` | string | Brief description of what the plugin does. |
| `author` | string | Plugin author name. |
| `version` | string | Plugin version string. |
| `entry` | string | Filename of the main Python script (e.g., "main.py"). |
| `api_version` | string | The Plugin API version this plugin targets (e.g., "1"). |
| `icon` | string | Relative path to the plugin's icon image. |
| `homepage` | string | URL to the plugin's homepage or repository. |
| `tags` | array | List of category tags. Valid tags: `interface`, `game_experience`, `tool`, `other`. |
| `relations` | object | Dependency and conflict declarations. Keys are plugin IDs, values are `"require"` or `"conflict"`. |
| `hooks` | array | List of hook names this plugin implements. See Plugin Hooks section for valid values. |
| `settings_schema` | object | Schema for plugin-specific settings. |

---

## Plugin Tags

Plugins are categorized by tags, which appear as filter checkboxes in the Plugins settings tab:

| Tag | Description |
| --- | --- |
| `interface` | Plugins that modify or extend the G3M user interface. |
| `game_experience` | Plugins that enhance or alter the game experience. |
| `tool` | Utility plugins (converters, analyzers, etc.). |
| `other` | Plugins that don't fit the above categories. |

---

## Plugin Hooks

Hooks allow plugins to execute code at specific points in the G3M lifecycle:

| Hook | When It Fires |
| --- | --- |
| `app_ready` | After application initialization completes. |
| `app_shutdown` | When the application is shutting down. |
| `before_mod_apply` | Before mods are patched, before game launch. Can add to the backup manager. |
| `after_mod_apply_before_launch` | After all mods are applied, before the game process is started. |
| `mod_apply_cancelled` | When the patching/launch is cancelled by the user. |
| `after_game_started` | After the game process is launched. |
| `before_restore_after_exit` | After the game exits, before game files are restored. |
| `after_restore_after_exit` | After game files are restored. |
| `language_changed` | When the UI language changes. |
| `theme_changed` | When the theme changes. |
| `profile_changed` | When the active profile changes. |
| `settings_view` | When the Settings tab is shown. Plugin can add its own UI widgets. |
| `main_view` | When the main view is shown. Plugin can inject UI elements. |
| `navigation_actions` | When the navigation bar is built. Plugin can add action buttons. |
| `game_registry` | When the game registry is initialized. Plugin can register custom games. |
| `background_task` | For background tasks unrelated to a specific lifecycle point. |

Hooks are executed in a background thread to avoid blocking the UI. Plugins receive a `PluginTaskRuntime` context that provides:

- Progress reporting callbacks.
- Status message callbacks.
- Cancellation checks.
- Access to the host's backup manager (for file backup/restore).

---

## Plugin Context

When a plugin is loaded, it receives a `PluginContext` object with access to:

- **app_state** — The application's current state (game mode, paths, settings).
- **feedback_service** — For showing status messages and notifications.
- **settings_service** — For reading/writing application settings.
- **profile_service** — For accessing profile data.
- **game_registry_service** — For querying game definitions.
- **customization_service** — For theme and UI customization.
- **downloads_manager** — For enqueuing downloads.
- **localization_service** — For accessing localized strings (including plugin-specific strings).
- **plugin_settings** — A `PluginSettingsAccessor` for reading/writing this plugin's own settings.

For UI hooks, a `PluginUiContext` is also provided with a subset of these services.

---

## Plugin Settings

Plugins can define their own settings via the `settings_schema` field in the manifest. These settings are stored in `plugins/plugins_data.json` under the `settings` key for each plugin. The `PluginSettingsAccessor` provides `get(key, default)`, `set(key, value)`, and `all()` methods.

---

## Plugin Catalog

G3M maintains an online plugin catalog. The Plugins settings tab shows:

- **Available plugins** — Plugins from the catalog that are not yet installed.
- **Installed plugins** — Plugins found in the local `plugins/` folder.

For each plugin, the tab shows: name, author, version, description, icon, tags, compatibility status, and action buttons (Install / Update / Enable / Disable / Delete / Open Homepage).

### Installing from Catalog

Click **Install** on an available plugin. G3M downloads the plugin archive and extracts it into the `plugins/` folder. The plugin becomes available immediately (but must be enabled before its hooks run).

### Updating

If a plugin has a newer version in the catalog than the locally installed version, an **Update** button appears.

---

## Enabling / Disabling Plugins

Installed plugins are disabled by default. Click **Enable** to activate a plugin. When enabled:

- Its hooks are registered and will fire at the appropriate lifecycle points.
- Its localization strings are loaded.
- It appears as "enabled" in the plugins list.

Click **Disable** to deactivate a plugin without uninstalling it. Its hooks stop firing, but its files remain on disk.

---

## Plugin Relations

Plugins can declare dependencies and conflicts:

- **require** — This plugin requires another plugin to be installed and enabled.
- **conflict** — This plugin cannot coexist with another plugin.

G3M checks relations when enabling plugins. If a required plugin is missing or a conflicting plugin is enabled, a warning is shown.

---

## Compatibility

A plugin is marked as **incompatible** if:

- Its `api_version` does not match the host's Plugin API version.
- Its manifest is malformed or missing required fields.
- Its entry Python file cannot be loaded.

Incompatible plugins are displayed with a warning and cannot be enabled.

---

## Plugin Localization

Plugins can include their own localization files in a `lang/` subfolder. Each file follows the same format as G3M's language files (JSON with nested keys). Plugin strings are merged into the main localization system and can be accessed via the `localization_service`.

---

## Deleting a Plugin

Click **Delete** on an installed plugin. The plugin's folder is removed from disk. If the plugin was enabled, its hooks are unregistered first.
