# Plugins

Plugins let G3M grow beyond the built-in launcher features.

## Current plugin API version

`1.1.0`

## Required manifest file

Every plugin is centered on:

`plugin_config.json`

The manifest points to the plugin entry file and describes things such as:

- plugin id
- name
- version
- `api_version`
- tags
- hooks
- optional settings schema

## Storage

- plugin files live under the G3M data directory `plugins/`
- enabled state and plugin settings live in `plugins/plugins_data.json`

## Important safety note

Plugins are powerful and not sandboxed. Only enable plugins you trust.

## Error Handling

Recent G3M builds classify several plugin failures more precisely instead of showing only raw exceptions.

Examples:

- plugin manifest missing or invalid
- entry file missing
- icon file missing
- unsafe path inside a plugin package
- missing `create_plugin()` factory
- plugin package too large or otherwise invalid
- incompatible Plugin API
- missing plugin dependencies
- conflicts with another enabled plugin

Raw exception details are still kept in logs, but the installed plugin record now tries to present a clearer user-facing reason when the cause is known.
