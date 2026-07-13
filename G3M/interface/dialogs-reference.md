# Dialogs Reference

G3M uses many focused dialogs instead of forcing everything into the main
window.

## Main dialogs you will run into

- **Dialog:** Downloads
  - **Where it is usually opened:** Downloads page/button
  - **What it is for:** Inspect downloads, retries, auto-use, and manual
    attention states

- **Dialog:** Game Versions
  - **Where it is usually opened:** Small Game Versions button near game
    controls
  - **What it is for:** Save, restore, import, export, or delete game folder
    snapshots

- **Dialog:** Modding Tools
  - **Where it is usually opened:** Title bar/tools/menu area
  - **What it is for:** Batch-convert installed mod DATA files, patch, merge,
    inspect, and diff DATA/patch files

- **Dialog:** Mod Diagnostics
  - **Where it is usually opened:** Library header button
  - **What it is for:** Preview file conflicts, patch targets, and `.g3mpatch`
    resource changes before launch

- **Dialog:** Profile Manager
  - **Where it is usually opened:** Profile selector controls
  - **What it is for:** Create, duplicate, rename, delete, reorder, import, and
    export profiles

- **Dialog:** Game Manager
  - **Where it is usually opened:** Settings -> game settings area
  - **What it is for:** Hide/reorder built-in games and manage custom games

- **Dialog:** Mod Editor
  - **Where it is usually opened:** Local mod creation/edit actions
  - **What it is for:** Create or edit `mod_config.json` and mod files

- **Dialog:** Mod Versions
  - **Where it is usually opened:** Mod details/version controls
  - **What it is for:** Switch, import, export, or delete saved versions of one
    mod

- **Dialog:** Announcement dialog
  - **Where it is usually opened:** Startup or announcement action
  - **What it is for:** Show current announcement messages

- **Dialog:** Blocklist dialog
  - **Where it is usually opened:** Settings or browser/search blocklist action
  - **What it is for:** Hide mods by ID, name, or category

- **Dialog:** About and Changelog
  - **Where it is usually opened:** Help/about title-bar menu
  - **What it is for:** View app info, links, and release notes

## Typical confirmation dialogs

The current app also shows confirmation prompts for actions such as:

- deleting mods
- deleting profiles
- deleting saved versions
- restoring saved versions
- deleting plugins

## File and picker dialogs

G3M uses standard file or folder pickers for:

- game paths
- importing mods
- exporting mods
- custom background, logo, font, and audio
- saved version import or export

## UI principle

The current codebase keeps specialized workflows in dedicated dialogs instead of
burying them in tabs or side panels, which is why many advanced actions open
their own window.

If a page says "open the dialog" but you do not see the button, check the
related area first: game-related dialogs are usually near game controls or
Settings, mod-related dialogs are usually in Library or mod details, and utility
dialogs are usually in the title bar/tools area.
