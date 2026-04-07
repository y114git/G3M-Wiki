# Full Install

Some games supported by G3M can be downloaded and installed entirely through the application, without requiring a prior game purchase or external installer. This feature is called **Full Install**.

---

## Supported Games

| Game | Full Install | Notes |
| --- | --- | --- |
| DELTARUNE | No | Requires Steam or manual installation. |
| DELTARUNE DEMO | Yes | Free demo, can be downloaded directly. |
| UNDERTALE | No | Requires Steam or manual installation. |
| UNDERTALE Yellow | Yes | Free fan game, downloadable. |
| Pizza Tower | No | Requires Steam purchase. |
| Sugary Spire | Yes | Free fan game, downloadable. |
| Custom games | No | Custom games never support Full Install. |

---

## How Full Install Works

### Enabling

1. Go to Settings → Game.
2. Find the game you want to install.
3. Check the **Full Install** checkbox. (Only visible for games that support it.)
4. The main action button in the status bar changes from "Launch" to **Install**.

### Installation Process

1. Click **Install**.
2. A folder picker dialog appears. Select where you want the game to be installed.
3. G3M creates the game folder if it doesn't exist.
4. G3M downloads the game files from the configured download source.
5. A progress bar shows the download and extraction progress.
6. After extraction:
   - The game path is automatically set to the new folder.
   - The Full Install checkbox is disabled (installation complete).
   - The status bar shows "Installation complete" (or similar).
   - The action button reverts to "Launch".

### Download Sources

Game files are downloaded from the G3M cloud infrastructure or directly from the game's official distribution point. The URLs are configured in the application's global settings, which are fetched from the server on startup.

### Platform Restrictions

- **macOS**: Full Install may not be available for all games on macOS, because the distributed binaries are Windows-only. The checkbox is hidden for unsupported platform combinations.
- **Linux**: Full Install downloads Windows binaries. You may need to configure Wine/PortProton to run them.

---

## After Installation

Once a game is installed via Full Install:

- It behaves exactly like a manually installed game.
- You can browse and install mods for it.
- You can launch it with mods applied.
- The game path appears in Settings → Game just like any other configured game.
- You can change the game path later if you move the files.

---

## Reinstalling

If you need to reinstall the game (e.g., corrupted files):

1. Delete the existing game folder manually.
2. Go to Settings → Game and clear the game path.
3. Re-enable the Full Install checkbox.
4. Click Install and choose a new destination.

---

## Cancellation

During the download and extraction process, you can click **Cancel** in the status bar. This:

1. Aborts the download.
2. Removes any partially downloaded or extracted files.
3. Restores the previous state (no game path set, Full Install re-enabled).

---

## Disk Space

Full Install downloads the complete game files, which can range from a few hundred MB to several GB depending on the game. Ensure you have sufficient disk space at the chosen install location before starting.
