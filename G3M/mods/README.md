# Mods

G3M works with profile-local mod folders and a shared `mod_config.json` schema. The app can browse, import, create, patch, version, and export mods across several file formats.

---

## Storage

Installed mods live directly in the active profile directory:

- `profiles/<ProfileName>/<mod id>/mod_config.json`
- `profiles/<ProfileName>/<mod id>/...patch files, docs, icons, extras`
- `profiles/<ProfileName>/<mod id>/mod_versions/`
- `profiles/<ProfileName>/mods_data.json`

`mods_data.json` stores library metadata such as playtime and timestamps separately from `mod_config.json`.

---

## Core Mod Schema

Every native mod is a folder with `mod_config.json`. The top-level structure is:

- `config_version`
- `metadata`
- `info_files`
- `files`

`metadata` includes the mod identity, display text, icon, game id, version, tags, and related URLs. `files` maps each chapter or game section to patch data such as `data_file_path` and `extra_files`.

Current built-in tag names are:

- `textedit`
- `customization`
- `gameplay`
- `other`
- `CYOP/AFOM`

---

## Supported Data Formats

G3M recognizes these primary payload types:

| Type | Extensions |
| --- | --- |
| G3MTool patch | `.g3mpatch` |
| xdelta patch | `.xdelta`, `.vcdiff` |
| C# script patch | `.csx` |
| Full data replacement | `.win`, `.unx`, `.ios`, `.droid` |

Archives can also be imported when they contain supported mod content. The archive extensions accepted by the app are:

- `.zip`
- `.7z`
- `.rar`
- `.tar.gz`
- `.lzma`
- `.gz`

---

## Import and Conversion

G3M can convert or unpack several external formats during import, including:

- native G3M folders
- G3MTool patch archives
- DELTAMOD packages
- PizzaOven packages
- AFOM/CYOP tower packages

The same detection logic is reused by manual import, download auto-use, protocol installs, and some version restore flows.

---

## Mod IDs

Current ID conventions are:

- `local_<uuid>` for local mods
- `gb_mod_<id>` for GameBanana mods
- `gb_wip_<id>` for GameBanana WIP entries

---

## Runtime Flow

When a selected mod is launched, G3M resolves the target game files, applies the patch or replacement data, copies extra files, runs plugin hooks, starts the game, and restores the original files after exit.
