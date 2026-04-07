# Frequently Asked Questions

---

## General

### What is G3M?

G3M (GameMaker Mod Manager) is a desktop application for managing mods for GameMaker-based games. It supports browsing, downloading, installing, creating, and launching mods for games like DELTARUNE, UNDERTALE, Pizza Tower, and more.

### Is G3M free?

Yes. G3M is free and open-source software, licensed under GPL-3.0.

### What platforms does G3M support?

Windows 10 (version 1809+), macOS, and Linux. The primary development platform is Windows.

### What games does G3M support?

Built-in support for DELTARUNE, DELTARUNE DEMO, UNDERTALE, UNDERTALE Yellow, Pizza Tower, and Sugary Spire. You can also add any GameMaker-based game as a custom game.

### Do I need to install Python to use G3M?

No. G3M is distributed as a standalone executable. Python is bundled inside the application.

---

## Mods

### Where can I find mods?

G3M has a built-in Mods Browser that connects directly to GameBanana. You can browse, search, and download mods without leaving the application. You can also import mods from local files obtained from other sources.

### Can I use multiple mods at once?

Yes. G3M supports selecting multiple mods per game chapter. They are applied in order — see [Modpacks](../mods/modpacks.md).

### Will mods break my game?

No. G3M automatically backs up all original game files before applying mods and restores them after you exit the game. Your game files are never permanently modified. See [Backup & Restore](backup-and-restore.md).

### What mod formats does G3M support?

- **g3mpatch** — G3M's native patch format (compact, fast).
- **xdelta / vcdiff** — Standard binary diff patches.
- **CSX scripts** — C# scripts for programmatic modifications.
- **Raw data files** — Complete data file replacements.
- **DELTAMOD** — Auto-converted on import.
- **PizzaOven** — Auto-converted for Pizza Tower mods.

See [Patching Formats](../mods/patching-formats.md) for details.

### Can I create my own mods?

Yes. G3M includes a Mod Editor for creating mods from scratch and a full set of Modding Tools for creating patches, converting formats, merging data, and more. See [Creating Mods](../mods/creating-mods.md).

### How do I update a mod?

If the mod was downloaded from GameBanana, G3M detects when a newer version is available and shows an "Update" indicator. Click the action button to update.

### Can I share mods with friends?

Yes. Use the **Export** button on a mod card to create a `.zip` file. Send the file to your friend, who can import it into their G3M using Library → Add Mod → Import Mod.

---

## Installation & Setup

### How do I set up my game?

Go to Settings → Game → click the change path button for your game → select the game's installation folder. G3M validates the path by looking for the game's executable. See [Getting Started](../getting-started.md).

### Can G3M detect my game automatically?

Yes. On first launch, G3M scans common Steam installation paths and known directories to auto-detect installed games. See [Game Detection](../games/game-detection.md).

### What if my game is not detected?

Set the path manually in Settings → Game. Navigate to the folder containing the game's executable.

### Can I use G3M with a non-Steam version of the game?

Yes. G3M works with any installation of the game, whether from Steam, itch.io, or a direct download. Just point the game path to the correct folder.

---

## Features

### What are Profiles?

Profiles let you maintain separate mod collections. Each profile has its own set of installed mods and mod selections. Useful for keeping different mod setups (e.g., "Vanilla", "Modded Playthrough", "Testing"). See [Profiles](../features/profiles.md).

### What is Direct Launch?

For DELTARUNE, Direct Launch lets you skip the title screen and load directly into a specific chapter. Double-click a chapter tab in the Library to enable it. See [Launch Modes](../games/launch-modes.md).

### What is Full Install?

Some free games (DELTARUNE DEMO, UNDERTALE Yellow, Sugary Spire) can be downloaded and installed entirely through G3M. Enable Full Install in Settings → Game, then click Install. See [Full Install](../games/full-install.md).

### How does the Chat work?

G3M has a built-in anonymous chat with language-specific channels. No account needed. See [Chat](../features/chat.md).

### Can I create desktop shortcuts?

Yes. G3M can create desktop shortcuts that patch mods and launch a game without opening the full UI. See [Desktop Shortcuts](../features/shortcuts.md).

### What are Plugins?

Plugins are third-party extensions that add functionality to G3M. They can hook into the mod lifecycle, add settings UI, and more. See [Plugins](../features/plugins.md).

---

## Customization

### Can I change G3M's appearance?

Yes, extensively. G3M supports:

- Seven customizable theme colors.
- Custom background images or videos.
- Custom fonts.
- Custom logo.
- Custom startup sound and background music.
- Adjustable border radius.
- Theme import/export.

See [Customization](../customization/README.md).

### How do I share my theme?

Export your theme as a `.g3mtheme.zip` file (Settings → Appearance → Export Theme). Send the file to someone else, who can import it in their G3M. See [Theme Packages](../customization/theme-packages.md).

---

## Privacy & Security

### Does G3M collect personal data?

No. G3M has an optional anonymous analytics system that collects usage statistics (mod installs, game launches, etc.) with no personal information. It is disabled by default. See [Analytics](analytics.md).

### Are one-click install links safe?

G3M always shows a confirmation dialog before downloading from a one-click install link. You must explicitly approve the download. See [One-Click Install](one-click-install.md).

### Can mods contain viruses?

G3M itself does not scan mods for malware. GameBanana has its own file scanning system. Always download mods from trusted sources. CSX script mods execute code, so only use scripts from sources you trust.

---

## Technical

### Where does G3M store its data?

- Windows: `%APPDATA%\G3M`
- macOS: `~/Library/Application Support/G3M`
- Linux: `~/.local/share/G3M`

### How do I report a bug?

1. Check the log file at `{data_folder}/logs/g3m.log`.
2. Report the issue on [GitHub Issues](https://github.com/y114git/G3M/issues) with a description and the relevant log sections.
3. Or reach out on the [Discord server](https://discord.gg/2MFdvFfD9a).

### How do I reset G3M to defaults?

Delete the entire user data folder (see locations above) and restart G3M. Warning: this removes all mods, profiles, and settings.

### Can I run multiple versions of G3M?

G3M enforces a single running instance. You cannot run two copies simultaneously. However, you can install different versions in different folders and use them at different times.

### What is the "Librarby" easter egg?

Very rarely, the Library tab label shows "Librarby" instead of "Library". It's a harmless easter egg.
