# Plugins

Plugins let G3M grow beyond the built-in launcher features.

## Where to find it

1. Open G3M.
2. Open **Settings**.
3. Scroll to the plugins area or open the plugin list/details dialog from the
   plugin controls.
4. Enable, disable, update, or inspect installed plugins there.

Some plugins also add their own Settings UI. If a plugin provides settings,
those controls appear in the Settings view after the plugin is installed and
enabled.

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

- installed plugin folders live under `%LOCALAPPDATA%\G3M\plugins\`
- enabled state and plugin settings live in
  `%LOCALAPPDATA%\G3M\plugins\plugins_data.json`
- plugin-specific files created by a plugin usually live inside that plugin's
  own folder unless the plugin documents another location

## Important safety note

Plugins are powerful and not sandboxed. Only enable plugins you trust.

## Install a plugin

1. Download the plugin from G3M's plugin catalog or from a trusted source.
2. Use the plugin install flow in G3M for a plugin archive or folder, or place
   the plugin folder under `%LOCALAPPDATA%\G3M\plugins\`.
3. Restart G3M if the plugin does not appear immediately.
4. Enable the plugin from the plugin controls.

A valid plugin folder must contain `plugin_config.json`. If the manifest is
missing or invalid, G3M will not load the plugin.

## Enable or disable a plugin

Enable means G3M may run the plugin's hooks and show its UI. Disable means the
plugin remains installed on disk but its hooks should not run.

Disabling a plugin does not delete its files or settings. The enabled state is
saved in:

`%LOCALAPPDATA%\G3M\plugins\plugins_data.json`

## Update a plugin

When updating a plugin, G3M keeps the plugin's saved enabled state and settings
record in `plugins_data.json`. The current install service replaces packaged
files while trying to avoid deleting unrelated files the plugin created inside
its folder.

If something looks wrong after an update:

1. Check whether the plugin is still enabled.
2. Open the plugin details/error area.
3. Check `%LOCALAPPDATA%\G3M\logs\g3m.log` for the raw error.

## Delete a plugin

Deleting a plugin removes its installed plugin folder from
`%LOCALAPPDATA%\G3M\plugins\`. That can also remove files the plugin stored
inside its folder.

If you only want to stop using a plugin temporarily, disable it instead of
deleting it.

## Error Handling

Recent G3M builds classify several plugin failures more precisely instead of
showing only raw exceptions.

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

Raw exception details are still kept in logs, but the installed plugin record
now tries to present a clearer user-facing reason when the cause is known.
