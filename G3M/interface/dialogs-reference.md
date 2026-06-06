# Dialogs Reference

G3M uses many focused dialogs instead of forcing everything into the main window.

## Main dialogs you will run into

- Chat
- Downloads
- Game Versions
- Modding Tools
- Profile Manager
- Game Manager
- Mod Editor
- Mod Versions
- Announcement dialog
- Blocklist dialog
- About and Changelog

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
