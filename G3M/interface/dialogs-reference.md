# Dialogs Reference

G3M uses many focused dialogs instead of forcing everything into the main window.

## Main dialogs you will run into

| Dialog | Where it is usually opened | What it is for |
| --- | --- | --- |
| Downloads | Downloads page/button | Inspect downloads, retries, auto-use, and manual attention states |
| Game Versions | Small Game Versions button near game controls | Save, restore, import, export, or delete game folder snapshots |
| Modding Tools | Title bar/tools/menu area | Batch-convert installed mod DATA files, patch, merge, inspect, and diff DATA/patch files |
| Mod Diagnostics | Library header button | Preview file conflicts, patch targets, and `.g3mpatch` resource changes before launch |
| Profile Manager | Profile selector controls | Create, duplicate, rename, delete, reorder, import, and export profiles |
| Game Manager | Settings -> game settings area | Hide/reorder built-in games and manage custom games |
| Mod Editor | Local mod creation/edit actions | Create or edit `mod_config.json` and mod files |
| Mod Versions | Mod details/version controls | Switch, import, export, or delete saved versions of one mod |
| Announcement dialog | Startup or announcement action | Show current announcement messages |
| Blocklist dialog | Settings or browser/search blocklist action | Hide mods by ID, name, or category |
| About and Changelog | Help/about title-bar menu | View app info, links, and release notes |

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

The current codebase keeps specialized workflows in dedicated dialogs instead of burying them in tabs or side panels, which is why many advanced actions open their own window.

If a page says "open the dialog" but you do not see the button, check the related area first: game-related dialogs are usually near game controls or Settings, mod-related dialogs are usually in Library or mod details, and utility dialogs are usually in the title bar/tools area.
