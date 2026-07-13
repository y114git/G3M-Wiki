# Plugin Development Guide

This guide explains how to create plugins for G3M.

---

## Getting Started

### Plugin Structure

Create a new folder with a unique name (e.g., `my_plugin/`):

```text
my_plugin/
├── plugin_config.json     # Required: Plugin manifest
├── main.py                # Required: Entry point
├── lang/                  # Optional: Localization
│   ├── lang_en.json
│   └── lang_ru.json
└── icon.png               # Optional: Plugin icon
```

### Minimal plugin_config.json

```json
{
  "config_version": 1,
  "id": "my_plugin",
  "name": "My Plugin",
  "description": "A simple G3M plugin.",
  "author": "YourName",
  "version": "1.0.0",
  "entry": "main.py",
  "api_version": "1.1.0"
}
```

### Minimal main.py

```python
def on_load(context):
    """Called when the plugin is loaded."""
    pass
```

---

## Plugin Manifest Fields

### Required Fields

- **Field:** `config_version`
  - **Type:** int
  - **Description:** Must be `1`.

- **Field:** `id`
  - **Type:** string
  - **Description:** Unique plugin ID. Use lowercase, alphanumeric, and
    underscores.

- **Field:** `name`
  - **Type:** string
  - **Description:** Human-readable name.

- **Field:** `description`
  - **Type:** string
  - **Description:** Brief description.

- **Field:** `author`
  - **Type:** string
  - **Description:** Your name.

- **Field:** `version`
  - **Type:** string
  - **Description:** Version string (e.g., "1.0.0").

- **Field:** `entry`
  - **Type:** string
  - **Description:** Python file name for the entry point.

### Optional Fields

- **Field:** `api_version`
  - **Type:** string
  - **Default:** `"1.1.0"`
  - **Description:** Target Plugin API version.

- **Field:** `icon`
  - **Type:** string
  - **Default:** `null`
  - **Description:** Relative path to icon image.

- **Field:** `homepage`
  - **Type:** string
  - **Default:** `null`
  - **Description:** URL to plugin homepage/repository.

- **Field:** `tags`
  - **Type:** array
  - **Default:** `[]`
  - **Description:** Category tags: `interface`, `game_experience`, `tool`,
    `other`.

- **Field:** `relations`
  - **Type:** object
  - **Default:** `{}`
  - **Description:** Dependencies and conflicts.

- **Field:** `hooks`
  - **Type:** array
  - **Default:** `[]`
  - **Description:** Hook names this plugin implements.

- **Field:** `settings_schema`
  - **Type:** object
  - **Default:** `{}`
  - **Description:** Plugin settings definition.

---

## Hooks

Hooks let your plugin execute code at specific lifecycle points.

### Available Hooks

- **Hook:** `app_ready`
  - **When:** After app initialization completes.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `app_shutdown`
  - **When:** When the app is shutting down.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `before_mod_apply`
  - **When:** Before mods are patched/launched.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `after_mod_apply_before_launch`
  - **When:** After patching, before game start.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `mod_apply_cancelled`
  - **When:** When patching/launch is cancelled.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `after_game_started`
  - **When:** After game process is launched.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `before_restore_after_exit`
  - **When:** After game exits, before restore.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `after_restore_after_exit`
  - **When:** After file restoration completes.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `shortcut_dialog`
  - **When:** When the shortcut dialog flow runs.
  - **Parameters:** `PluginUiContext`

- **Hook:** `before_mod_apply_shortcut`
  - **When:** Before shortcut patching starts.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `after_mod_apply_before_launch_shortcut`
  - **When:** After shortcut patching, before launch.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `before_restore_after_exit_shortcut`
  - **When:** Before shortcut restore starts.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `after_restore_after_exit_shortcut`
  - **When:** After shortcut restore completes.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `language_changed`
  - **When:** When the UI language changes.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `theme_changed`
  - **When:** When the theme changes.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `profile_changed`
  - **When:** When the active profile changes.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `settings_view`
  - **When:** When Settings tab is shown.
  - **Parameters:** `PluginUiContext`

- **Hook:** `main_view`
  - **When:** When the main view is shown.
  - **Parameters:** `PluginUiContext`

- **Hook:** `navigation_actions`
  - **When:** When the nav bar is built.
  - **Parameters:** `PluginUiContext`

- **Hook:** `game_registry`
  - **When:** When game registry is initialized.
  - **Parameters:** `PluginTaskRuntime`

- **Hook:** `background_task`
  - **When:** For background tasks.
  - **Parameters:** `PluginTaskRuntime`

### Declaring Hooks

In `plugin_config.json`:

```json
{
  "hooks": ["before_mod_apply", "after_restore_after_exit"]
}
```

### Implementing Hooks

In your entry file, define functions matching the hook names:

```python
def before_mod_apply(runtime):
    """Called before game is patched and launched."""
    runtime.report_status("My plugin is preparing...")
    runtime.report_progress(50)
    # Do your work here
    runtime.report_status("My plugin is ready.")
    runtime.report_progress(100)

def after_restore_after_exit(runtime):
    """Called after game exits and files are restored."""
    runtime.report_status("Cleaning up...")
```

### PluginTaskRuntime

The `runtime` parameter provides:

- **Method:** `report_progress(percent)`
  - **Description:** Report progress (0–100).

- **Method:** `report_status(message)`
  - **Description:** Display a status message.

- **Method:** `is_cancelled()`
  - **Description:** Check if the user cancelled the operation.

- **Method:** `get_backup_manager()`
  - **Description:** Access the host's backup manager for file backup/restore.

---

## Plugin Context

When your plugin is loaded, `on_load()` receives a `PluginContext`:

```python
def on_load(context):
    # Access application state
    game_mode = context.app_state.game_mode

    # Read a setting
    game_path = context.settings_service.get("game_path")

    # Access plugin-specific settings
    my_setting = context.plugin_settings.get("my_key", "default_value")

    # Show a status message
    context.feedback_service.show_status("My Plugin loaded!", "info")
```

### Available Services

- **Service:** `app_state`
  - **Access:** `context.app_state`
  - **Description:** Application state (game mode, paths, flags).

- **Service:** `feedback_service`
  - **Access:** `context.feedback_service`
  - **Description:** Show status messages and notifications.

- **Service:** `settings_service`
  - **Access:** `context.settings_service`
  - **Description:** Read/write application settings.

- **Service:** `profile_service`
  - **Access:** `context.profile_service`
  - **Description:** Access profile data.

- **Service:** `game_registry_service`
  - **Access:** `context.game_registry_service`
  - **Description:** Query game definitions.

- **Service:** `customization_service`
  - **Access:** `context.customization_service`
  - **Description:** Theme and customization data.

- **Service:** `downloads_manager`
  - **Access:** `context.downloads_manager`
  - **Description:** Enqueue downloads.

- **Service:** `localization_service`
  - **Access:** `context.localization_service`
  - **Description:** Access translations.

- **Service:** `plugin_settings`
  - **Access:** `context.plugin_settings`
  - **Description:** Plugin-specific settings storage.

---

## Plugin Settings

Define a settings schema to let users configure your plugin:

### In plugin_config.json

```json
{
  "settings_schema": {
    "auto_backup": {
      "type": "boolean",
      "default": true,
      "label": "Enable auto-backup"
    },
    "backup_count": {
      "type": "integer",
      "default": 5,
      "label": "Maximum backup count"
    }
  }
}
```

### Reading Settings

```python
def on_load(context):
    auto_backup = context.plugin_settings.get("auto_backup", True)
    backup_count = context.plugin_settings.get("backup_count", 5)
```

### Writing Settings

```python
context.plugin_settings.set("last_run", "2024-03-20")
```

### Listing All Settings

```python
all_settings = context.plugin_settings.all()
```

Settings are persisted on Windows in
`%LOCALAPPDATA%\G3M\plugins\plugins_data.json` under the `settings` key for your
plugin's ID.

---

## Plugin Localization

### Adding Translations

Create `lang/lang_en.json`:

```json
{
  "my_plugin": {
    "status_ready": "My Plugin is ready!",
    "status_error": "My Plugin encountered an error.",
    "setting_label": "Enable My Feature"
  }
}
```

Create `lang/lang_ru.json` for Russian, etc.

### Using Translations

```python
from services.localization_service import tr

def on_load(context):
    message = tr("my_plugin.status_ready")
    context.feedback_service.show_status(message, "info")
```

---

## Plugin Relations

### Dependencies

Declare that your plugin requires another plugin:

```json
{
  "relations": {
    "other_plugin_id": "require"
  }
}
```

G3M checks relations when enabling. If the required plugin is missing, a warning
is shown.

### Conflicts

Declare that your plugin is incompatible with another:

```json
{
  "relations": {
    "conflicting_plugin_id": "conflict"
  }
}
```

G3M warns if both plugins are enabled simultaneously.

---

## Settings Tab Hook

The `settings_view` hook lets you add UI widgets to the Settings tab:

```python
from PyQt6.QtWidgets import QLabel, QCheckBox, QVBoxLayout, QWidget

def settings_view(ui_context):
    """Add a custom settings panel."""
    widget = QWidget()
    layout = QVBoxLayout(widget)

    label = QLabel("My Plugin Settings")
    layout.addWidget(label)

    checkbox = QCheckBox("Enable feature")
    checkbox.setChecked(ui_context.plugin_settings.get("feature_enabled", False))
    checkbox.stateChanged.connect(
        lambda state: ui_context.plugin_settings.set("feature_enabled", bool(state))
    )
    layout.addWidget(checkbox)

    return widget
```

---

## Installation

### Manual Installation

1. Copy your plugin folder into `%LOCALAPPDATA%\G3M\plugins\` on Windows,
   `~/.local/share/G3M/plugins/` on Linux, or
   `~/Library/Application Support/G3M/plugins/` on macOS.
2. Restart G3M.
3. Go to Settings → Plugins.
4. Your plugin appears in the "Installed" section.
5. Click **Enable** to activate it.

### Distribution via Plugin Catalog

To list your plugin in G3M's online plugin catalog, contact the G3M developer.
The catalog is curated to ensure quality and safety.

### Distribution as ZIP

Package your plugin folder as a `.zip`. Current G3M builds can install plugin
archives through the plugin install flow, and users can still extract them
manually into `%LOCALAPPDATA%\G3M\plugins\` on Windows,
`~/.local/share/G3M/plugins/` on Linux, or
`~/Library/Application Support/G3M/plugins/` on macOS.

---

## Debugging

### Logging

Use standard Python logging in your plugin:

```python
import logging

logger = logging.getLogger("my_plugin")

def on_load(context):
    logger.info("My Plugin loaded successfully")
```

Log output appears in G3M's main log file (`g3m.log`).

### Error Handling

If your plugin raises an unhandled exception:

- The error is logged.
- The plugin is marked as "error" state.
- Other plugins continue to function.
- G3M does not crash.

Always wrap potentially failing operations in try/except blocks and log errors
with `logger.error(..., exc_info=True)`.

---

## API Version Compatibility

The current Plugin API version is **1.1.0**. Your plugin's `api_version` must
match the host's version:

- `api_version: "1.1.0"` — Compatible with the current G3M Plugin API.
- If the API version changes, plugins targeting a different version may not
  load.

Always test your plugin with the latest G3M version before distributing.
