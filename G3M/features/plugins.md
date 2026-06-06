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
