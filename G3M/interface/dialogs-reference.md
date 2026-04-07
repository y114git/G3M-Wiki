# Dialogs Reference

G3M uses many dialogs throughout the application. This page catalogs all dialogs, their triggers, and their contents.

---

## Confirmation Dialogs

### Generic Confirmation

A simple yes/no dialog used across the application.

| Field | Content |
| --- | --- |
| Title | Context-dependent (e.g., "Confirm", "Delete Mod") |
| Body | Context-dependent question (e.g., "Are you sure you want to delete this mod?") |
| Buttons | OK / Cancel (or Yes / No) |

Triggers: Delete mod, delete profile, delete game version, delete plugin, restore game version, close game while running, and more.

---

## Game Dialogs

### Game Running Warning

Shown when G3M detects a supported game is already running during startup.

| Field | Content |
| --- | --- |
| Title | "Game is running" |
| Body | Message explaining that a game process was detected and G3M cannot proceed. |
| Buttons | OK (closes G3M) |

### Game Path Validation

Shown when the user selects a game folder that doesn't contain the expected executable.

| Field | Content |
| --- | --- |
| Title | "Invalid game path" |
| Body | "The selected folder does not contain [game executable]. Please select the correct folder." |
| Buttons | OK |

### Game Path Set Confirmation

Shown briefly in the status bar (not a dialog) when a game path is successfully configured.

---

## Mod Dialogs

### Add Mod Dialog

Shown when clicking the "+" button in the Library.

| Field | Content |
| --- | --- |
| Title | "Add Mod" |
| Options | "Import Mod" — Open file picker. "Create Mod" — Open Mod Editor for a new mod. |
| Buttons | Cancel |

### Mod Import — Merge or Overwrite

Shown when importing a mod that has the same ID as an existing mod.

| Field | Content |
| --- | --- |
| Title | "Mod already exists" |
| Body | "A mod with ID [id] already exists. What would you like to do?" |
| Buttons | Merge / Replace / Cancel |

### Mod Delete Confirmation

| Field | Content |
| --- | --- |
| Title | "Delete Mod" |
| Body | "Are you sure you want to delete [mod name]? This will remove all mod files from disk." |
| Buttons | Delete / Cancel |

### Mod Editor Dialog

A complex dialog for creating and editing mods. See [Mod Editor](../mods/mod-editor.md) for full documentation.

### Mod Versions Dialog

Dialog for managing per-mod version snapshots. See [Mod Versions](../mods/mod-versions.md) for full documentation.

### File Picker Dialog (Mod Download)

Shown when a GameBanana mod has multiple downloadable files. See [Mod Details Panel](mod-details.md#file-picker-dialog).

---

## Profile Dialogs

### New Profile

| Field | Content |
| --- | --- |
| Title | "New Profile" |
| Body | "Enter a name for the new profile:" |
| Input | Text field for profile name. |
| Buttons | Create / Cancel |

### Delete Profile Confirmation

| Field | Content |
| --- | --- |
| Title | "Delete Profile" |
| Body | "Are you sure you want to delete profile [name]? All mods in this profile will be deleted." |
| Buttons | Delete / Cancel |

### Rename Profile

| Field | Content |
| --- | --- |
| Title | "Rename Profile" |
| Body | "Enter a new name:" |
| Input | Text field pre-filled with current name. |
| Buttons | Rename / Cancel |

---

## Download Dialogs

### One-Click Install Confirmation

Shown when a `g3m://` URL is received.

| Field | Content |
| --- | --- |
| Title | "One-Click Install" |
| Body | "Do you want to download from:\n[URL]\n\nPlease verify this source before proceeding." |
| Buttons | Download / Cancel |

### Download Overwrite Prompt

Shown when a downloaded mod conflicts with an existing library mod.

| Field | Content |
| --- | --- |
| Title | "Mod already exists" |
| Body | "A mod with this ID already exists in your library. What would you like to do?" |
| Buttons | Merge / Replace / Skip |

---

## Game Version Dialogs

### Create Version

| Field | Content |
| --- | --- |
| Title | "Save Game Version" |
| Body | "Enter a label for this version:" |
| Input | Text field. |
| Buttons | Save / Cancel |

### Restore Version Confirmation

| Field | Content |
| --- | --- |
| Title | "Restore Game Version" |
| Body | "This will replace your current game files with the saved version. Current modifications will be lost. Continue?" |
| Buttons | Restore / Cancel |

### Delete Version Confirmation

| Field | Content |
| --- | --- |
| Title | "Delete Version" |
| Body | "Are you sure you want to delete version [label]?" |
| Buttons | Delete / Cancel |

### Rename Version

| Field | Content |
| --- | --- |
| Title | "Rename Version" |
| Body | "Enter a new label:" |
| Input | Text field. |
| Buttons | Rename / Cancel |

---

## Plugin Dialogs

### Delete Plugin Confirmation

| Field | Content |
| --- | --- |
| Title | "Delete Plugin" |
| Body | "Are you sure you want to delete plugin [name]?" |
| Buttons | Delete / Cancel |

### Plugin Compatibility Warning

| Field | Content |
| --- | --- |
| Title | "Incompatible Plugin" |
| Body | "Plugin [name] requires API version [X] but the current version is [Y]. It may not work correctly." |
| Buttons | Enable Anyway / Cancel |

### Plugin Relation Warning

| Field | Content |
| --- | --- |
| Title | "Plugin Conflict" |
| Body | "Plugin [A] conflicts with plugin [B]. You cannot enable both at the same time." |
| Buttons | OK |

---

## Customization Dialogs

### Color Picker

The system's native color selection dialog. Varies by platform:

- **Windows**: Windows Color Picker with color wheel, sliders, and hex input.
- **macOS**: macOS Color Panel with color wheel, sliders, and custom palettes.
- **Linux**: Qt's built-in color dialog.

### File Selection Dialogs

Used for selecting background images, logos, fonts, audio files, and game paths. Uses the system's native file dialog with appropriate file type filters.

---

## System Dialogs

### File Save Dialog

Used for exporting mods, themes, and game versions. System native dialog with file name and location input.

### Folder Picker Dialog

Used for selecting game paths and Full Install destinations. System native folder picker.

---

## Announcement Dialog

Shows in-app announcements and polls. See [Announcements & Polls](../features/announcements.md) for full documentation.

---

## Chat Dialog

The in-app chat window. See [Chat](../features/chat.md) for full documentation.

---

## Modding Tools Dialog

A multi-tab dialog for patch creation, application, merging, inspection, and diffing. See [Modding Tools](../features/modding-tools.md) for full documentation.

---

## Shortcut Creation Dialog

Shows the current mod configuration and creates desktop shortcuts. See [Desktop Shortcuts](../features/shortcuts.md) for full documentation.

---

## Game Manager Dialog

Manages game visibility, order, and custom games. See [Game Manager](../games/game-manager.md) for full documentation.

---

## About Dialog

Shows application info, version, links, and license. See [About & Changelog](about-and-changelog.md) for details.

---

## Changelog Dialog

Scrollable list of version history entries. See [About & Changelog](about-and-changelog.md) for details.

---

## Update Dialog

Shows when an app update is available. See [Update System](../features/update-system.md) for details.

---

## Data Migration Dialog

Shown on first launch when a legacy DELTAHUB data folder is detected.

| Field | Content |
| --- | --- |
| Title | "Data Migration" |
| Body | "A DELTAHUB data folder was detected. Would you like to import your existing data or start fresh?" |
| Buttons | Import Data / Start Fresh |

---

## Error Notification

Shown when a critical error occurs:

| Field | Content |
| --- | --- |
| Title | "Error" |
| Body | Error description with details. |
| Buttons | OK |

Error notifications may also appear as transient status bar messages (red text) for non-critical errors.

---

## Dialog Theming

All G3M dialogs use the current theme colors:

- **Background**: Elements color.
- **Border**: Border color.
- **Text**: Main Text color.
- **Buttons**: Styled with Elements/Hover/Select colors.
- **Title bar**: Custom title bar matching the main window.

System dialogs (file pickers, color picker) use the system theme and are not affected by G3M's custom theme.
