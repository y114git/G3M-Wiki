# Troubleshooting

Common issues and their solutions.

---

## G3M Won't Start

### "Another instance is already running"

G3M enforces a single running instance. If you see this, another G3M process is still active. Check your system tray or task manager and close the existing instance.

### "Game is currently running"

G3M checks for running game processes on startup. Close any running DELTARUNE, UNDERTALE, Pizza Tower, or other supported game before launching G3M.

### Crash on Startup

Check the log file at `{user_data_root}/logs/g3m.log` for error details. Common causes:

- Corrupted settings file — Delete `settings/settings.json` and restart. G3M will create fresh defaults.
- Missing dependencies — Ensure you have the latest version installed.
- Incompatible OS version — G3M requires Windows 10 1809+ (build 17763).

### (Linux) "Could not load the Qt platform plugin xcb"

Full error:

```
Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized.
```

Since Qt 6.5, the `xcb` platform plugin requires the `libxcb-cursor0` library. Install it with:

```bash
# Debian / Ubuntu
sudo apt install libxcb-cursor0

# Fedora / RHEL
sudo dnf install xcb-util-cursor
```

Then restart G3M.

---

## Game Path Not Found

If G3M cannot find your game:

1. Go to Settings → Game.
2. Click the change path button for the game.
3. Navigate to the folder containing the game executable (e.g., `DELTARUNE.exe`).
4. If the executable is not in the selected folder, G3M shows a warning.

Common reasons:

- Game installed in a non-standard location.
- Game installed via a launcher other than Steam.
- Game folder moved after installation.

---

## Mods Not Appearing in Library

- Make sure you're looking at the correct **game** in the game selector dropdown.
- Check the correct **profile** is active.
- For DELTARUNE, check the correct **chapter tab** — a mod only appears in tabs for which it has data.
- If using filters, try clearing them (reset search text, deselect all tags).

---

## Mod Installation Fails

- **"Game is running"** — Close the game before installing mods.
- **Permission errors** — Ensure G3M has write access to the game directory. Games installed in `Program Files` may require running G3M as administrator.
- **Corrupted mod files** — Try re-downloading or re-importing the mod.
- **Unsupported format** — The mod may not be in a format G3M can process. Check [Supported Mod Formats](../mods/README.md#supported-mod-formats).

---

## One-Click Install Not Working

- Ensure the `g3m://` protocol is registered. On Windows, check `HKEY_CURRENT_USER\Software\Classes\g3m`. On Linux, check `~/.local/share/applications/g3m.desktop`.
- Try reinstalling G3M to re-register the protocol.
- Make sure your browser allows custom protocol handlers.

---

## Background Music / Sounds Not Playing

- Verify the audio file is in a supported format (`.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, `.aac`).
- Check that the file exists in the data folder.
- Ensure "Disable startup sound" is unchecked for startup sounds.
- Check system audio settings and volume.

---

## Theme Not Applying

- After importing a theme, some changes (like fonts) require a restart.
- Verify the `.zip` theme package contains a valid `theme_config.json` manifest.
- Check the log file for theme loading errors.

---

## Update Fails

- Ensure you have an active internet connection.
- Check if your firewall or antivirus is blocking G3M's update requests.
- Try manually downloading the latest version from [GitHub Releases](https://github.com/y114git/G3M/releases).
- If "Enable beta updates" is checked, try unchecking it for stable releases only.

---

## GameBanana Rate Limit

GameBanana allows 250 API requests per hour. If you browse mods intensively, you may hit this limit. Wait a few minutes and try again. The status bar shows: "GameBanana API rate limit reached."

---

## Log Files

G3M writes detailed logs to:

| Log | Location |
| --- | --- |
| Main log | `{user_data_root}/logs/g3m.log` |
| Shortcut runner log | `{user_data_root}/logs/shortcut.log` |
| Archived logs | `{user_data_root}/logs/g3m/` (timestamped copies from previous sessions) |

When reporting bugs, include the relevant log file.

---

## Corrupted Settings

If `settings.json` becomes corrupted (invalid JSON), G3M:

1. Detects the corruption on load.
2. Creates a backup of the corrupted file as `settings.json.invalid.bak`.
3. Shows a warning: "Corrupted files found."
4. Creates fresh default settings.

Your old settings are preserved in the `.bak` file for manual recovery.

---

## Resetting G3M

To completely reset G3M to factory defaults:

1. Close G3M.
2. Delete the user data folder:
   - Windows: `%LOCALAPPDATA%\G3M`
   - macOS: `~/Library/Application Support/G3M`
   - Linux: `~/.local/share/G3M`
3. Restart G3M. Everything will be recreated from scratch.

**Warning**: This deletes all mods, profiles, settings, and plugins.
