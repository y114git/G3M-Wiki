# Steam Integration

G3M integrates with Steam in several ways: launching games through Steam, detecting Steam library paths, and handling Steam-related edge cases.

---

## Launch via Steam

When "Launch via Steam" is enabled in Settings → Game:

1. G3M patches the game files as usual (backup, apply mods, copy extra files).
2. Instead of directly executing the game's `.exe`, G3M opens the Steam URL:
   ```
   steam://rungameid/<steam_app_id>
   ```
3. Steam receives the request and starts the game.
4. Steam overlay, cloud saves, achievements, and playtime tracking all work normally.
5. G3M monitors the game process by name (not by PID, since Steam spawns it separately).

### When to Use Steam Launch

- **Use Steam Launch** if you want Steam overlay, cloud saves, and achievement tracking.
- **Don't use Steam Launch** if the mod conflicts with Steam overlay, or if you want faster launch without Steam startup.

### Requirements

- Steam must be installed and running (or will auto-launch).
- The game must have a Steam App ID configured.
- The game must be in your Steam library.

---

## Steam App IDs

| Game | Steam App ID |
| --- | --- |
| DELTARUNE | 1671210 |
| DELTARUNE DEMO | 1671200 |
| UNDERTALE | 391540 |
| Pizza Tower | 2231450 |
| UNDERTALE Yellow | — (not on Steam) |
| Sugary Spire | — (not on Steam) |

Custom games can have a Steam App ID set during creation. If set, the "Launch via Steam" option becomes available for that game.

---

## Steam Library Path Detection

When auto-detecting game paths, G3M reads Steam's library configuration:

### Windows

1. Reads the registry key `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Valve\Steam` (or `HKEY_LOCAL_MACHINE\SOFTWARE\Valve\Steam`) to find the Steam installation path.
2. Reads `<steam_path>/steamapps/libraryfolders.vdf` to discover all Steam library folders.
3. For each library folder, scans `<library>/steamapps/common/` for known game directories.

### macOS

1. Checks `~/Library/Application Support/Steam/steamapps/libraryfolders.vdf`.
2. Scans each library folder's `steamapps/common/` directory.

### Linux

1. Checks `~/.steam/steam/steamapps/libraryfolders.vdf` and `~/.local/share/Steam/steamapps/libraryfolders.vdf`.
2. Scans each library folder's `steamapps/common/` directory.

---

## Steam Path Awareness

G3M detects if a game is installed in a Steam library path by checking if the game path is under any `steamapps/common/` directory. This is used for:

- **Launch mode decisions** — If the game is in a Steam path and Steam launch is enabled, use Steam URL launch.
- **Permission handling** — Steam library paths in `Program Files` may require elevated permissions for file operations.

---

## Steam Blocking (DELTARUNE)

DELTARUNE has a unique behavior: when launched directly (not through Steam), the game or its DRM may attempt to start Steam in the background. This can cause:

- Steam overlay appearing unexpectedly.
- Steam claiming the game is running.
- Conflicts with file modifications.

G3M can block this by intercepting the Steam launch attempt. This is specific to DELTARUNE and is handled automatically when Direct Launch is used without Steam launch enabled.

---

## Process Monitoring with Steam

When using Steam launch, there is a timing challenge:

1. G3M opens the `steam://rungameid/` URL.
2. Steam processes the URL and starts the game.
3. There may be a delay between the URL request and the actual game process appearing.
4. G3M's game monitor polls for the game process by name.
5. The monitor accounts for this delay — it waits for the process to appear before starting the playtime timer.

If the game fails to start (e.g., Steam shows an error, game is not installed), the monitor eventually times out and G3M restores the backed-up files.

---

## Non-Steam Games

Games without a Steam App ID (UNDERTALE Yellow, Sugary Spire, custom games without IDs) are always launched directly, regardless of the "Launch via Steam" setting. The setting is simply not applicable to them.

For these games, the Steam launch option does not appear in the Settings UI, or appears disabled with a tooltip explaining why.

---

## Steam Deck Compatibility

G3M can run on Steam Deck in Desktop Mode. Considerations:

- Install G3M from the Linux release.
- Game paths are typically under `/home/deck/.local/share/Steam/steamapps/common/`.
- Steam launch works via the `steam://` URL scheme, which Desktop Mode handles.
- Direct launch and PortProton may also work depending on your Proton configuration.
