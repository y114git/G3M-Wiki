# Mod Editor

The Mod Editor is the built-in dialog for creating a new local mod or editing an existing one.

## What you can edit

The current editor covers the core mod fields:

- name
- author
- version
- description
- game
- game version
- homepage
- tags
- icon
- info files

It also lets you attach per-slot data files and extra files.

## Supported main file types

For chapter or slot data, the editor can work with:

- raw GameMaker data files
- `.g3mpatch`
- `.xdelta`
- `.vcdiff`
- `.csx`

## What happens on save

For local mods, G3M writes or updates `mod_config.json`, copies chosen assets into the mod folder, and refreshes the Library view.

The mod ID stays stable after creation.
