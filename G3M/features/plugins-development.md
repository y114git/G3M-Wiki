# Plugin Development Guide

This guide explains how to create plugins for G3M.

---

## Getting Started

### Plugin Structure

Create a new folder with a unique name (e.g., `my_plugin/`):

```
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
  "api_version": "1"
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

| Field | Type | Description |
| --- | --- | --- |
| `config_version` | int | Must be `1`. |
| `id` | string | Unique plugin ID. Use lowercase, alphanumeric, and underscores. |
| `name` | string | Human-readable name. |
| `description` | string | Brief description. |
| `author` | string | Your name. |
| `version` | string | Version string (e.g., "1.0.0"). |
| `entry` | string | Python file name for the entry point. |

### Optional Fields

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `api_version` | string | `"1"` | Target Plugin API version. |
| `icon` | string | `null` | Relative path to icon image. |
| `homepage` | string | `null` | URL to plugin homepage/repository. |
| `tags` | array | `[]` | Category tags: `interface`, `game_experience`, `tool`, `other`. |
| `relations` | object | `{}` | Dependencies and conflicts. |
| `hooks` | array | `[]` | Hook names this plugin implements. |
| `settings_schema` | object | `{}` | Plugin settings definition. |

---

## Hooks

Hooks let your plugin execute code at specific lifecycle points.

### Available Hooks

| Hook | When | Parameters |
| --- | --- | --- |
| `pre_launch` | Before game patching and launch. | `PluginTaskRuntime` context. |
| `post_launch` | After game exits and files are restored. | `PluginTaskRuntime` context. |
| `on_mod_install` | When a mod is imported/installed. | Mod info, target path. |
| `on_mod_uninstall` | When a mod is deleted. | Mod info. |
| `on_settings_tab` | When Settings tab is displayed. | `PluginUiContext` with parent widget. |

### Declaring Hooks

In `plugin_config.json`:

```json
{
  "hooks": ["pre_launch", "post_launch"]
}
```

### Implementing Hooks

In your entry file, define functions matching the hook names:

```python
def pre_launch(runtime):
    """Called before game is patched and launched."""
    runtime.report_status("My plugin is preparing...")
    runtime.report_progress(50)
    # Do your work here
    runtime.report_status("My plugin is ready.")
    runtime.report_progress(100)

def post_launch(runtime):
    """Called after game exits."""
    runtime.report_status("Cleaning up...")
```

### PluginTaskRuntime

The `runtime` parameter provides:

| Method | Description |
| --- | --- |
| `report_progress(percent)` | Report progress (0–100). |
| `report_status(message)` | Display a status message. |
| `is_cancelled()` | Check if the user cancelled the operation. |
| `get_backup_manager()` | Access the host's backup manager for file backup/restore. |

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

| Service | Access | Description |
| --- | --- | --- |
| `app_state` | `context.app_state` | Application state (game mode, paths, flags). |
| `feedback_service` | `context.feedback_service` | Show status messages and notifications. |
| `settings_service` | `context.settings_service` | Read/write application settings. |
| `profile_service` | `context.profile_service` | Access profile data. |
| `game_registry_service` | `context.game_registry_service` | Query game definitions. |
| `customization_service` | `context.customization_service` | Theme and customization data. |
| `downloads_manager` | `context.downloads_manager` | Enqueue downloads. |
| `localization_service` | `context.localization_service` | Access translations. |
| `plugin_settings` | `context.plugin_settings` | Plugin-specific settings storage. |

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

Settings are persisted in `plugins_state.json` under your plugin's ID.

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

G3M checks relations when enabling. If the required plugin is missing, a warning is shown.

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

The `on_settings_tab` hook lets you add UI widgets to the Settings tab:

```python
from PyQt6.QtWidgets import QLabel, QCheckBox, QVBoxLayout, QWidget

def on_settings_tab(ui_context):
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

1. Copy your plugin folder into `{user_data_root}/plugins/`.
2. Restart G3M.
3. Go to Settings → Plugins.
4. Your plugin appears in the "Installed" section.
5. Click **Enable** to activate it.

### Distribution via Plugin Catalog

To list your plugin in G3M's online plugin catalog, contact the G3M developer. The catalog is curated to ensure quality and safety.

### Distribution as ZIP

Package your plugin folder as a `.zip`. Users can download and extract it into their `plugins/` directory. In the future, G3M may support direct plugin ZIP installation from the UI.

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

Always wrap potentially failing operations in try/except blocks and log errors with `logger.error(..., exc_info=True)`.

---

## API Version Compatibility

The current Plugin API version is **1**. Your plugin's `api_version` must match the host's version:

- `api_version: "1"` — Compatible with G3M Plugin API v1.
- If the API version changes in a future G3M release, plugins targeting the old version may not load.

Always test your plugin with the latest G3M version before distributing.
