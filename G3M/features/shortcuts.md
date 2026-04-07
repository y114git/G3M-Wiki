# Desktop Shortcuts

G3M can create desktop shortcuts that patch mods and launch a game **without opening the full G3M window**. This is useful for one-click modded game launching from your desktop or start menu.

---

## Creating a Shortcut

1. Select the game and mods you want in the Library.
2. Click the **Shortcut** button in the title bar (scissors/link icon).
3. The Shortcut Creation dialog opens.

The dialog shows:

- **Game** — The current game.
- **Mode** — Chapter Mode or Normal Mode.
- **Selected mods** — Which mods will be patched for each chapter.
- **Launch options** — Launch via Steam, Direct Launch chapter, PortProton.

4. Click **Create**. A file save dialog opens asking where to save the shortcut.
5. G3M creates a platform-appropriate shortcut file.

---

## Shortcut File Types

| Platform | File Type | Description |
| --- | --- | --- |
| Windows | `.vbs` | A VBScript file that launches G3M in headless mode with the embedded configuration. |
| macOS | `.command` | A shell script that launches G3M's shortcut runner. |
| Linux | `.sh` | A shell script that launches G3M's shortcut runner. |

---

## How It Works

The shortcut file contains an embedded JSON configuration (base64-encoded) with:

- **game_id** — Which game to patch and launch.
- **chapter_mode** — Whether Chapter Mode is active.
- **chapter_mods** — A dictionary mapping each chapter ID to the mod ID that should be applied.
- **launch_via_steam** — Whether to launch through Steam.
- **use_portproton** — Whether to use PortProton (Linux).
- **direct_launch_chapter** — Which chapter to launch directly into (if any).
- **profile** — Which profile to use for resolving mod paths.

When the shortcut is executed:

1. G3M's headless runner starts without the graphical interface.
2. It reads the embedded configuration.
3. It locates each mod by ID in the specified profile's mods folder.
4. It backs up the game's original data files.
5. It patches each chapter's data with the assigned mod using G3MTool.
6. It launches the game (directly or via Steam).
7. It monitors the game process.
8. When the game exits, it restores all original files from backups.

---

## Limitations

- Each chapter can have **at most one mod** assigned in a shortcut. If a chapter has multiple mods selected in the Library, shortcut creation is blocked and a warning message appears.
- The shortcut references mods by ID. If you delete or rename a mod, the shortcut will fail to find it.
- The shortcut uses the G3M installation path at the time of creation. If you move G3M, the shortcut will break.

---

## Shortcut Runner Logging

The headless shortcut runner writes its own log file to `{user_data_root}/logs/shortcut.log`. If something goes wrong with a shortcut launch, check this file for details.
