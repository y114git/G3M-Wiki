# Mod Editor

The Mod Editor is the built-in dialog for creating a new local mod or editing an
existing one.

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

It also lets you attach per-slot data files and extra files. Each extra entry
can use **Install** or **Dependency only** status.

For FRICKBEARS3 mods, the current editor also understands addon-style extra-file
layouts and keeps them in the normal mod file structure instead of treating them
as unrelated loose files.

## Supported main file types

For chapter or slot data, the editor can work with:

- raw GameMaker data files
- `.g3mpatch`
- `.xdelta`
- `.vcdiff`
- `.csx`

## What happens on save

For local mods, G3M writes or updates `mod_config.json`, copies chosen assets
into the mod folder, and refreshes the Library view.

The mod ID stays stable after creation.

## Dependency-only files

A dependency-only entry stays inside the mod folder but G3M does not copy it to
the game, `addons`, `towers`, or another deployment target. CSX mods can keep
nested scripts, sprites, sounds, and other resources beside their entry script
with this status.

G3M adds an unconfigured folder as one dependency-only folder entry when the
editor imports or opens mod content that is missing from `mod_config.json`.
It does not create one config entry per descendant file.

A dependency-only folder does not change the status of a child entry. You can
mark `resources/` as dependency-only and add `resources/runtime/` as a separate
Install entry. G3M then deploys the child entry.
