# Games

G3M supports six built-in games and an unlimited number of user-added custom games.

---

## Built-in Games

| Game | ID | Steam App ID | GameBanana ID | Chapter Tabs | Full Install | Direct Launch |
| --- | --- | --- | --- | --- | --- | --- |
| DELTARUNE | `deltarune` | 1671210 | 6755 | Main Menu, Ch.1, Ch.2, Ch.3, Ch.4 | No | Yes |
| DELTARUNE DEMO | `deltarunedemo` | 1690940 | — | Demo (single tab) | Yes | No |
| UNDERTALE | `undertale` | 391540 | 5506 | Single tab | No | Yes |
| UNDERTALE Yellow | `undertaleyellow` | — | 19606 | Single tab | Yes | Yes |
| Pizza Tower | `pizzatower` | 2231450 | 7692 | Single tab | No | Yes |
| Sugary Spire | `sugaryspire` | — | 18218 | Single tab | Yes | Yes |

### DELTARUNE

The primary supported game. Has five content tabs (Main Menu + Chapters 1–4) and supports Chapter Mode, where each chapter has an independent mod selection. DELTARUNE has the unique ability to **block Steam** when using Direct Launch — meaning when you launch DELTARUNE directly (not through Steam), G3M can prevent Steam from opening alongside the game.

Executables searched for:
- **Windows**: `DELTARUNE.exe`, `DELTARUNE`
- **Linux**: `DELTARUNE`, `DELTARUNE.exe`
- **macOS**: `DELTARUNE.app`, `DELTARUNEdemo.app`

Process names monitored: `DELTARUNE.exe`, `DELTARUNE`, `runner`

### DELTARUNE DEMO

The free demo version of DELTARUNE. It does **not** have a GameBanana ID, meaning you cannot browse mods for it in the Mods Browser. Mods must be imported locally or obtained from other sources. It supports Full Install — G3M can download and set up the demo game files for you.

The demo has a single tab. Direct Launch is not supported for the demo.

### UNDERTALE

Toby Fox's first game. Single content tab. Supports GameBanana browsing (ID: 5506).

Executables: `UNDERTALE.exe` / `UNDERTALE` / `UNDERTALE.app`

### UNDERTALE Yellow

A fan-made game built on the Undertale engine. Supports Full Install and GameBanana browsing (ID: 19606). Does not have a Steam App ID.

Executables: `Undertale Yellow.exe`, `Undertale Yellow`, `UNDERTALE.exe`, `UNDERTALE`

### Pizza Tower

A fast-paced platformer built on GameMaker. Single content tab. Supports GameBanana browsing (ID: 7692).

Executables: `PizzaTower.exe` / `PizzaTower` / `PizzaTower.app`

### Sugary Spire

A fan-made Pizza Tower mod/game. Supports Full Install and GameBanana browsing (ID: 18218). Does not have a Steam App ID.

Executables: `SugarySpire_ExhibitionNight.exe` / `SugarySpire_ExhibitionNight` / `SugarySpire_ExhibitionNight.app`

---

## Game Path Configuration

Each game requires a configured folder path that points to its installation directory. G3M validates the path by checking for one of the expected executables.

### Auto-Detection

On first launch, G3M scans common installation paths (Steam library folders, default install directories) and automatically configures any games it finds.

### Manual Path Setting

In Settings → Game, click the change-path button for any game. A folder picker opens. Select the folder containing the game's executable. If the executable is not found in the selected folder, a warning appears.

### Custom Executable

Each game supports a Custom Executable override. When enabled, G3M uses the specified executable path instead of the auto-detected one. This is useful for:
- Modded or renamed game executables.
- Running a specific version of the game.
- Testing with a modified binary.

---

## Game Launching

When you click **Launch** in the status bar, G3M:

1. Checks if the game is already running. If yes, shows a warning.
2. Determines the selected mods for each relevant chapter/tab.
3. Backs up the game's original data files (e.g., `data.win`) to a temporary backup folder.
4. Patches each chapter's data file with the selected mod using the appropriate patching method (g3mpatch, xdelta, csx, or raw data copy).
5. Copies any extra files from the mod into the game directory.
6. If plugins are active, executes plugin hooks (`before_mod_apply`, `after_mod_apply_before_launch`, `after_game_started`, etc.).
7. Launches the game executable (directly or via Steam, depending on settings).
8. Starts a game monitor that watches for the game process.
9. While the game is running, the action button shows "Close" and the status shows the game name and playtime.
10. When the game exits, G3M restores all backed-up files to their original state, removing any mod-added files.

### Launch via Steam

When "Launch via Steam" is enabled and the game has a Steam App ID, G3M opens `steam://rungameid/<app_id>` instead of running the executable directly. This ensures Steam overlay, cloud saves, and achievements work correctly.

### Direct Launch

For DELTARUNE in Chapter Mode, **Direct Launch** lets you specify which chapter to launch directly into, bypassing the game's title screen. This is configured per-chapter by double-clicking a chapter tab in the Library. The selected chapter is stored in the `direct_launch_chapter` setting.

### PortProton (Linux)

On Linux, if PortProton is configured, G3M uses PortProton to run Windows game executables through a compatibility layer.

---

## Playtime Tracking

G3M tracks how long you play each game during a session. When the game exits, the session playtime is recorded in analytics (if opt-in is enabled) and logged.
