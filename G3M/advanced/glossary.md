# Glossary

Definitions of terms used throughout this wiki and the G3M application.

---

## A

### Analytics
Optional anonymous usage statistics collected by G3M. Disabled by default. See [Analytics](analytics.md).

### API Version (Plugin)
The Plugin API version number (currently **1**). Plugins must target a compatible API version to be loaded.

### Auto-Detection
The process by which G3M automatically finds installed games by scanning Steam library paths and known directories.

### Auto-Use
When enabled (default), downloaded mods are automatically imported into the Library without manual intervention.

---

## B

### Backup
A copy of original game files created before patching. Restored after the game exits. See [Backup & Restore](backup-and-restore.md).

### Beta Updates
Pre-release versions of G3M. Opt-in via Settings → General → "Enable beta updates".

### Blocklist
A set of rules that hide specific mods from the Mods Browser and Library based on ID, name, or category. See [Blocklist Manager](../features/blocklist.md).

### Border Radius
The corner rounding of the main window and UI panels. Configurable from 0 (square) to 20 (round) pixels.

---

## C

### Chapter Mode
A DELTARUNE-specific mode where each game chapter has its own independent mod selection. When disabled (Normal Mode), one mod selection applies to the entire game.

### Chapter Tab
In the Library, tabs representing different game chapters (e.g., "Ch.0 Main Menu", "Ch.1", "Ch.2"). Visible when Chapter Mode is active for DELTARUNE.

### CSX Script
A C# script file (.csx) that programmatically modifies GameMaker data files. Executed by G3MTool.

### Custom Game
A user-added game that is not in G3M's built-in game list. Created via the Game Manager dialog.

---

## D

### Data File
The main game data file for a GameMaker game (e.g., `data.win`, `game.ios`, `data.unx`, `data.droid`). This file contains all game resources and is the target of mod patching.

### DELTAMOD
A legacy mod format from the Deltamod Manager. G3M auto-converts DELTAMOD mods on import.

### Direct Launch
A DELTARUNE feature that skips the title screen and loads directly into a specific chapter.

### Download Record
An entry in the Downloads panel tracking a download's status, source, target, progress, and associated file.

---

## E

### Extra Files
Additional files included with a mod (DLLs, audio banks, textures, etc.) that are copied into the game directory during patching and removed during restoration.

---

## F

### Full Install
A feature for downloading and installing free games (DELTARUNE DEMO, UNDERTALE Yellow, Sugary Spire) entirely through G3M.

---

## G

### G3M
GameMaker Mod Manager. The application this wiki documents.

### G3MTool
A command-line tool bundled with G3M for GameMaker data file manipulation. Supports creating/applying patches, converting formats, merging data, inspecting files, and diffing.

### g3mpatch
G3M's native patch format. Stores only the modified chunks of a game data file, making it compact and fast to apply.

### GameBanana
A game modding community website. G3M integrates directly with GameBanana's API for browsing and downloading mods.

### Game Monitor
A background thread that watches a running game process and signals G3M when the game exits.

### Game Version
A saved snapshot of a game's data files, stored as a ZIP archive. See [Game Versions](../features/game-versions.md).

---

## H

### Hook (Plugin)
A named lifecycle event that plugins can subscribe to. Hooks: `pre_launch`, `post_launch`, `on_mod_install`, `on_mod_uninstall`, `on_settings_tab`.

---

## L

### Launch via Steam
An option to start games through Steam's URL protocol (`steam://rungameid/`) instead of directly running the executable.

### Library
The main tab for managing installed mods, selecting mods for play, and launching games.

---

## M

### Mod
A modification to a game's data files. Can be a patch (g3mpatch, xdelta, csx), a full data replacement, or a collection of extra files.

### mod_config.json
The metadata file inside every G3M mod folder. Contains the mod's ID, name, author, version, file assignments, and other metadata.

### Mod Browser / Mods Browser
The tab for browsing and downloading mods from GameBanana.

### Mod Card
A visual card in the Library or Mods Browser representing a single mod, showing its icon, name, author, version, and action buttons.

### Modpack
An informal term for selecting multiple mods for a single game chapter. G3M applies them sequentially.

### Mod Versions
Per-mod version snapshots stored as ZIP archives. See [Mod Versions](../mods/mod-versions.md).

---

## N

### Normal Mode
The default mode where one mod selection applies to the game's primary data file (vs. Chapter Mode which allows per-chapter selections).

### NSFW
Not Safe For Work. Mods flagged as NSFW are hidden by default in the Mods Browser.

---

## O

### One-Click Install
A URL protocol (`g3m://`, `deltahub://`) that allows installing mods with a single click from a website.

### Online Presence
The player counter in the title bar showing how many users currently have G3M open.

---

## P

### Patching
The process of modifying a game's data file with a mod's changes. See [Patching Process](patching-process.md).

### PizzaOven
A mod format for Pizza Tower. G3M can auto-convert eligible PizzaOven mods.

### Plugin
A third-party extension that adds functionality to G3M. See [Plugins](../features/plugins.md).

### PO File
Portable Object file — a standard translation format. G3M can use PO files to create text translation mods.

### PortProton
A Wine-based compatibility layer for running Windows games on Linux. G3M integrates with it as a launch option.

### Profile
A separate collection of installed mods with independent selections and settings. See [Profiles](../features/profiles.md).

---

## R

### Restoration
The process of reverting game files to their original state after patching, using the backups created before launch.

---

## S

### Settings Schema
The default values and structure definition for G3M's settings file. Ensures all expected keys exist.

### Single Instance
G3M's enforcement of only one running copy at a time. Second launches forward their arguments to the first instance.

### Splash Screen
The loading screen shown during G3M initialization.

### Steam App ID
A numeric identifier for a game on the Steam platform (e.g., 391540 for UNDERTALE).

---

## T

### Tag
A category label applied to mods or plugins for filtering purposes. Mod tags: Text Edit, Customization, Gameplay, Other. Plugin tags: Interface, Game Experience, Tool, Other.

### Theme
The collection of colors, background, font, logo, and audio that define G3M's visual and auditory appearance.

### Theme Package
A `.g3mtheme.zip` archive containing a complete theme configuration for sharing.

### Title Bar
The custom-drawn bar at the top of the G3M window containing the logo, tabs, social buttons, and window controls.

---

## U

### Used Mods
The mods currently selected ("in use") for each chapter in the Library. When the game is launched, used mods are patched into the game data.

### User Data Directory
The platform-specific folder where G3M stores all its data. See [Data Directory Reference](data-directory.md).

---

## V

### vcdiff
A binary diff format (RFC 3284), treated identically to xdelta by G3M.

---

## X

### xdelta
A binary diff/patch format widely used for game mods. G3M can create and apply xdelta patches.
