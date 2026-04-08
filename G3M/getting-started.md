# Getting Started

## System Requirements

| Requirement | Details |
| --- | --- |
| OS | Windows 10 version 1809 or later (64-bit only); macOS 11 (Big Sur) or later; Linux with glibc 2.28 or later |
| Python | 3.14 or later (bundled in the installer; not needed separately) |
| Disk space | ~150 MB for the application itself; additional space for mods and game files |
| Internet | Required for browsing GameBanana, chat, updates, and announcements. Offline use is possible for local mods. |

---

## Installation

### Windows

1. Download the latest `G3M_setup_v<version>.exe` installer from the [GitHub Releases](https://github.com/y114git/G3M/releases) page.
2. Run the installer. It uses Inno Setup and supports English, Spanish, and Russian during installation.
3. Choose an installation folder. The default is `C:\Program Files\G3M`.
4. Optionally create a desktop shortcut when prompted.
5. After installation, G3M launches automatically.

The installer requires Windows 10 build 17763 (version 1809) or higher. Older versions of Windows are blocked during setup.

### macOS

**Minimum: macOS 11 (Big Sur).** Older macOS versions are not supported.

1. Download the `.zip` release from GitHub.
2. Move `G3M.app` to your Applications folder (or any user folder). Do **not** run it from the download location — macOS App Translocation will put it in a read-only path and updates will fail.
3. Launch `G3M.app`.

### Linux

**Minimum: glibc 2.28.** Supported distributions include:

- Debian 10 (Buster) or later
- RHEL 8 / AlmaLinux 8 / Rocky Linux 8 or later
- Ubuntu 18.10 or later (**not** Ubuntu 18.04 LTS — it ships glibc 2.27). Ubuntu 20.04 LTS (glibc 2.31) is recommended for stable operation.
- Fedora 29 or later

1. Download the Linux release from GitHub.
2. Extract the archive.
3. Run the `G3M` executable from the extracted folder.
4. G3M registers a `.desktop` entry for the `g3m://` protocol handler automatically.

---

## First Launch

### Single Instance

G3M enforces a single running instance. If you try to open G3M while it is already running, the existing window is brought to front. If a `g3m://` URL was passed to the second instance, it is forwarded to the first one.

### Game Process Check

On startup, G3M checks if any supported game is already running (by scanning process names like `DELTARUNE.exe`, `UNDERTALE.exe`, `PizzaTower.exe`, etc.). If a game process is detected, G3M shows a warning dialog and exits. You must close the game before launching G3M.

### Splash Screen

A splash screen is shown while the application loads. It has a watchdog timeout of 15 seconds — if initialization stalls, the splash is dismissed automatically and the main window appears.

### Data Migration from DELTAHUB

If G3M detects a legacy `DELTAHUB` data folder (from the previous version of the application) and no `G3M` data folder exists yet, it offers a choice:

- **Import Data** — Copies all settings, mods, profiles, and configuration from the old DELTAHUB folder into the new G3M folder.
- **Start Fresh** — Creates a clean G3M folder from scratch.

If the import fails, a notification is shown and a fresh folder is created instead.

### Game Path Auto-Detection

After the main window appears, G3M tries to automatically detect installed games by scanning known locations (Steam library paths, common install directories). If a game is found, its path is saved and a status message confirms it. If auto-detection fails, you are prompted to set paths manually in **Settings → Game**.

---

## Data Storage

All user data is stored in a platform-specific folder:

| Platform | Location |
| --- | --- |
| Windows | `%LOCALAPPDATA%\G3M` |
| macOS | `~/Library/Application Support/G3M` |
| Linux | `~/.local/share/G3M` |

Inside this folder:

| Subfolder / File | Purpose |
| --- | --- |
| `settings/settings.json` | Main application configuration (paths, colors, toggles, etc.) |
| `settings/blocklist.json` | Blocklist entries |
| `settings/custom_games.json` | Custom game registry |
| `profiles/` | One subfolder per profile, each containing a `profile.json` with mod selections |
| `profiles/<name>/mods/` | Local mod folders for that profile |
| `downloads/` | Downloaded mod archives and `downloads_history.json` history |
| `game_versions/` | Saved game version archives and `game_versions_data.json` index |
| `plugins/` | Installed plugin folders |
| `plugins/plugins_data.json` | Plugin enabled/disabled state and per-plugin settings |
| `lang/` | Language files (synced from bundled + user-editable) |
| `logs/` | Application log files, archived into `logs/g3m/` on each launch |

---

## Setting Up a Game

1. Open **Settings** (gear icon or the Settings tab).
2. Go to the **Game** section.
3. For each game you want to use, click the corresponding **Change folder path** button and select the game's installation folder.
   - For DELTARUNE on Steam, this is typically `C:\Program Files (x86)\Steam\steamapps\common\DELTARUNEdemo` (demo) or the full game equivalent.
   - For Pizza Tower: the folder containing `PizzaTower.exe`.
   - For UNDERTALE: the folder containing `UNDERTALE.exe`.
4. After selecting a folder, G3M validates it by looking for the expected game executable.
5. The path is saved and the game becomes usable across the app.

### Custom Executable

For each game, you can optionally set a **Custom Executable** — a specific `.exe` (or `.app` on macOS) to launch instead of the auto-detected one. This is useful if you have a modded or renamed game executable. The custom executable setting is per-game and persists across sessions.

### Full Install (Supported Games Only)

Some games support **Full Install** — downloading the game files from scratch:

- **DELTARUNE DEMO** — Downloads the demo files automatically and creates a game folder.
- **UNDERTALE Yellow** — Downloads and extracts game files.
- **Sugary Spire** — Downloads and extracts game files.

Enable the **Full Install** checkbox, then click the main action button (which changes to **Install**). You will be prompted to select a destination folder. After download and extraction, the game path is automatically set to the new folder.

Full Install is not available on macOS for certain games. The checkbox is disabled after a successful installation.
