# Game Detection

G3M uses several methods to detect installed games and monitor running game processes.

---

## Path Auto-Detection

On first launch (or when no game path is configured), G3M scans common installation locations to find supported games.

### Steam Library Detection

G3M reads Steam's library configuration to find game installation paths:

1. Locates the Steam installation directory from the system registry (Windows), default paths (macOS/Linux), or environment variables.
2. Reads `libraryfolders.vdf` to discover all Steam library folders.
3. For each library folder, checks `steamapps/common/` for known game directories.
4. For each found game directory, verifies the expected executable exists.

### Direct Path Scanning

G3M also checks common default installation paths:

| Platform | Checked Paths |
| --- | --- |
| Windows | `C:\Program Files (x86)\Steam\steamapps\common\*`, `C:\Program Files\Steam\steamapps\common\*`, `D:\SteamLibrary\steamapps\common\*` |
| macOS | `~/Library/Application Support/Steam/steamapps/common/*`, `/Applications/*` |
| Linux | `~/.steam/steam/steamapps/common/*`, `~/.local/share/Steam/steamapps/common/*` |

### Expected Folder Names

Each built-in game has known folder names G3M searches for:

| Game | Expected Folder Names |
| --- | --- |
| DELTARUNE | `DELTARUNEdemo`, `DELTARUNE`, `deltarune` |
| DELTARUNE DEMO | `DELTARUNEdemo`, `DELTARUNE demo` |
| UNDERTALE | `UNDERTALE`, `Undertale` |
| Pizza Tower | `PizzaTower`, `Pizza Tower` |

---

## Executable Detection

For each game, G3M looks for specific executable files to confirm the game is installed:

### Per-Game Executables

| Game | Windows | macOS | Linux |
| --- | --- | --- | --- |
| DELTARUNE | `DELTARUNE.exe`, `DELTARUNE` | `DELTARUNE.app`, `DELTARUNEdemo.app` | `DELTARUNE`, `DELTARUNE.exe` |
| DELTARUNE DEMO | `SURVEY_PROGRAM.exe`, `DELTARUNE.exe` | `DELTARUNEdemo.app` | `DELTARUNE`, `SURVEY_PROGRAM` |
| UNDERTALE | `UNDERTALE.exe` | `UNDERTALE.app` | `UNDERTALE` |
| UNDERTALE Yellow | `Undertale Yellow.exe`, `UNDERTALE.exe` | — | `Undertale Yellow` |
| Pizza Tower | `PizzaTower.exe` | `PizzaTower.app` | `PizzaTower` |
| Sugary Spire | `SugarySpire_ExhibitionNight.exe` | `SugarySpire_ExhibitionNight.app` | `SugarySpire_ExhibitionNight` |

If the expected executable is found in the specified folder, the path is considered valid.

---

## Process Monitoring

G3M monitors running processes for two purposes:

### Startup Check

Before G3M fully initializes, it checks if any supported game is already running. This prevents conflicts where G3M might try to modify files that are in use.

Process names checked: `DELTARUNE.exe`, `DELTARUNE`, `UNDERTALE.exe`, `UNDERTALE`, `PizzaTower.exe`, `PizzaTower`, `SugarySpire_ExhibitionNight.exe`, `SugarySpire_ExhibitionNight`, `runner` (generic GameMaker runner), and `Undertale Yellow.exe`.

If any of these processes are found running, a dialog appears warning the user to close the game first.

### Game Monitor

After launching a game, G3M starts a monitor thread that:

1. Polls the process list periodically (every 1–2 seconds).
2. Looks for the game's expected process name.
3. Tracks the process start time and running duration.
4. Detects when the process exits.
5. Signals the main application to begin file restoration.

The monitor uses the `psutil` library for cross-platform process enumeration.

---

## Data File Detection

For each game, G3M identifies the main data file that mods patch:

| Game | Typical Data File | Location |
| --- | --- | --- |
| DELTARUNE | `data.win` (Windows), `game.ios` (macOS) | `<game_path>/` |
| UNDERTALE | `data.win` | `<game_path>/` |
| Pizza Tower | `data.win` | `<game_path>/` |
| Custom games | User-specified data file name | `<game_path>/` |

The data file name is part of the game definition. For custom games, you specify it during game creation.

---

## Chapter Resource Directories

For multi-chapter games like DELTARUNE, G3M identifies per-chapter resource directories within the game folder. Each chapter may have its own subfolder containing chapter-specific data that gets patched independently.

The chapter-to-folder mapping is determined by the game definition's tab configuration. For DELTARUNE:

| Chapter | Folder Key |
| --- | --- |
| Main Menu (Ch.0) | `deltarune_0` |
| Chapter 1 | `deltarune_1` |
| Chapter 2 | `deltarune_2` |
| Chapter 3 | `deltarune_3` |
| Chapter 4 | `deltarune_4` |

---

## Custom Executable Resolution

When a custom executable is configured for a game:

1. G3M first checks if the custom executable path exists.
2. If it exists, that executable is used for launching.
3. If it does not exist, G3M falls back to auto-detecting the standard executable.
4. A warning may be shown if the custom executable is missing.

The custom executable setting is stored per-game in the settings file (e.g., `custom_executable_path` for DELTARUNE, `pizzatower_custom_executable_path` for Pizza Tower).
