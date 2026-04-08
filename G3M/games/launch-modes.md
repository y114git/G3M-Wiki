# Launch Modes

G3M supports several ways to launch a game, each suited to different scenarios.

---

## Normal Launch (No Mods)

If no mods are selected ("used") for any chapter, clicking **Launch** starts the game without modifications.

1. G3M resolves the game executable path.
2. The game is started directly or through Steam.
3. The game monitor thread begins watching for the game process.
4. When the game exits, the monitor signals completion.
5. No patching or restoration is needed.

---

## Modded Launch

If one or more mods are selected, clicking **Launch** triggers the full patching pipeline:

1. **Backup** original game files.
2. **Patch** each chapter's data with its selected mod(s).
3. **Copy** extra files from mods into the game directory.
4. **Launch** the game.
5. **Monitor** the game process.
6. **Restore** original files after the game exits.

See [Patching Process](../advanced/patching-process.md) for the detailed step-by-step breakdown.

---

## Chapter Mode Launch (DELTARUNE)

For DELTARUNE, **Chapter Mode** allows each chapter to have its own independent mod selection. When launching in Chapter Mode:

1. G3M iterates through each chapter tab (Main Menu, Chapter 1, Chapter 2, etc.).
2. For each chapter that has a mod selected, it patches that chapter's specific data directory.
3. Chapters without mods are left unmodified.
4. The game is launched.
5. The player can access any chapter — modded chapters use the patched data, unmodded chapters use vanilla data.
6. On exit, all patched chapters are restored.

### Normal Mode (Single Selection)

In Normal Mode (the default), one mod selection applies to the game's primary data file. All chapters share the same modded data. This is simpler but doesn't allow mixing different mods across chapters.

### Switching Between Modes

Toggle Chapter Mode in Settings → Library → "Chapter Mode" checkbox. The change takes effect immediately:

- **Normal → Chapter Mode**: The current single mod selection is assigned to all chapters. You can then customize each chapter independently.
- **Chapter Mode → Normal**: The first chapter's mod selection becomes the single selection. Other chapters' selections are preserved in memory but not applied.

---

## Direct Launch

Direct Launch skips the game's title screen and loads directly into a specific chapter. Available only for DELTARUNE.

### Enabling Direct Launch

1. In the Library, switch to the DELTARUNE game.
2. Double-click a chapter tab (e.g., "Chapter 1").
3. The chapter tab is highlighted to indicate Direct Launch is active for that chapter.
4. When you click **Launch**, the game opens directly into that chapter.

### How It Works

G3M modifies the game's launch configuration or startup parameters to bypass the main menu. The exact method depends on the game version:

- For DELTARUNE, G3M may modify certain startup variables or pass command-line arguments that cause the game to jump directly into the specified chapter.

### Disabling Direct Launch

Double-click the same chapter tab again to deactivate Direct Launch. The game will launch normally into the title screen.

### Per-Chapter Direct Launch

Only one chapter can have Direct Launch active at a time. Activating it for one chapter deactivates it for others.

---

## Launch via Steam

When "Launch via Steam" is enabled in Settings → Game and the game has a Steam App ID:

1. G3M patches the game files normally.
2. Instead of running the executable directly, G3M opens the URL `steam://rungameid/<app_id>`.
3. Steam handles the actual process launch.
4. Steam overlay, cloud saves, and achievements function normally.
5. G3M still monitors the game process by name.

### Steam App IDs

| Game | Steam App ID |
| --- | --- |
| DELTARUNE | 1671210 |
| DELTARUNE DEMO | 1690940 |
| UNDERTALE | 391540 |
| Pizza Tower | 2231450 |

Games without a Steam App ID (UNDERTALE Yellow, Sugary Spire, custom games without an ID) cannot use Steam launch.

### Steam Blocking (DELTARUNE)

DELTARUNE has a special behavior: when launching directly (not through Steam), Steam may attempt to start alongside the game. G3M can block this by preventing the Steam process from auto-launching, ensuring a clean non-Steam execution.

---

## PortProton Launch (Linux)

On Linux, PortProton provides a Wine-based compatibility layer for running Windows games.

### Configuration

1. In Settings → Game, enable "Use PortProton".
2. Set the PortProton path to your PortProton installation directory.
3. When launching a game, G3M uses PortProton to run the `.exe` instead of native execution.

### How It Works

1. G3M patches the game files.
2. Instead of running the executable directly, it passes the executable path to PortProton's launcher script.
3. PortProton handles Wine prefix management and execution.
4. G3M monitors the game process.

---

## Shortcut Launch (Headless)

Desktop shortcuts run G3M's headless runner, which patches and launches without the GUI. See [Desktop Shortcuts](../features/shortcuts.md) for details.

### Key Differences from GUI Launch

- No window is shown.
- Progress is logged to `shortcut.log` instead of displayed in a status bar.
- No cancel button — close the shortcut script process to abort.
- Used mods are specified in the shortcut config, not from the current Library selection.
- The active profile is specified in the shortcut config.

---

## Launch Button States

The main action button in the status bar reflects the current launch context:

| State | Button Text | Color | Behavior |
| --- | --- | --- | --- |
| Ready, no mods | Launch | Default | Launches vanilla game. |
| Ready, mods selected | Launch | Highlighted | Patches mods, then launches. |
| Full Install mode | Install | Default | Downloads game files. |
| Updates available | Update | Yellow | Updates selected mods before launch. |
| Game is running | Close | Red | Terminates the running game. |
| Operation in progress | Cancel | Red | Cancels current operation. |
| Initializing | Please wait... | Gray (disabled) | Nothing — waiting for init. |
| No game path | Set game path | Warning | Redirects to Settings → Game. |

---

## Multiple Mods Per Chapter

When multiple mods are selected for a single chapter, they are applied **sequentially** in the order they appear in the used mods list:

1. Mod 1 is patched onto the original data file.
2. Mod 2 is patched onto the result from step 1.
3. Mod 3 is patched onto the result from step 2.
4. And so on.

Later mods' changes take priority over earlier mods' changes when they modify the same resources. This is important for compatibility:

- Two mods that modify different resources will coexist fine.
- Two mods that modify the same resource will conflict — the last one wins.
- Using the "Merge Properties" and "Merge Code" settings can help reduce conflicts.

### Reordering Mods

In the Library, you can reorder the used mods for a chapter to control which mod is applied first. The order matters when mods overlap.
