# Getting Started

## Requirements

G3M's source project currently targets:

- **Python:** `>=3.14`
- **UI:** `PyQt6==6.7.1`
- **Other pinned runtime dependencies:** `defusedxml`, `playsound3`, `psutil`, `py7zr`, `python-dotenv`, `rarfile`, `requests`, `urllib3`

The repository includes packaging for Windows, macOS, and Linux. The exact release artifact set is covered by the current project release process, while the source tree itself is cross-platform.

## Install from source

```bash
git clone https://github.com/y114git/G3M.git
cd G3M
python -m pip install -e ".[dev,test,build]"
python src/main.py
```

Useful extras from `pyproject.toml`:

- `.[build]` installs `pyinstaller`
- `.[test]` installs `pytest`, `pytest-qt`, `pytest-cov`, `pytest-html`, `pytest-mock`, and `responses`
- `.[dev]` installs `ruff`

## First launch behavior

- G3M enforces a **single running instance** using the key `g3m.single-instance-lock`.
- It accepts both `g3m://` and legacy `deltahub://` protocol links.
- On first startup it can migrate user data from the legacy **DELTAHUB** folder into the current **G3M** data directory.
- It attempts automatic game-path detection only for built-in games that have autodetection support in the current codebase.

## Built-in games

The built-in runtime registry currently includes:

- `deltarune`
- `deltarunedemo`
- `undertale`
- `undertaleyellow`
- `pizzatower`
- `sugaryspire`
- `frickbears3`

Only visible games appear in the main UI. Additional custom games can be created in the Game Manager and stored in `settings/custom_games.json`.

## Data directory

User data lives under the platform-specific G3M root:

| Platform | Default location |
| --- | --- |
| Windows | `%LOCALAPPDATA%\\G3M` |
| macOS | `~/Library/Application Support/G3M` |
| Linux | `~/.local/share/G3M` |

Important subpaths in the current code:

| Path | Purpose |
| --- | --- |
| `settings/settings.json` | Main app settings |
| `settings/blocklist.json` | Blocklist rules |
| `settings/custom_games.json` | Custom game registry |
| `settings/analytics_pending.json` | Pending analytics batch data |
| `profiles/` | Profile folders |
| `mods/` | Shared mod storage root |
| `downloads/downloads_history.json` | Download history and queue persistence |
| `game_versions/game_versions_data.json` | Saved game version index |
| `plugins/plugins_data.json` | Plugin state and settings |
| `lang/` | External language files |
| `themes/` | User theme archives |
| `cache/G3MTool/` | G3MTool cache files used by patching workflows |

## Configure a game

1. Open **Settings**.
2. Select the target game.
3. Set the game folder path.
4. Optionally set a custom executable path for that game.

Validation is game-aware. G3M checks executable candidates from the current built-in registry and resolves supported data files by platform.

## Full install support

Built-in full-install support is enabled in the current registry for:

- **DELTARUNEdemo**
- **UNDERTALE Yellow**
- **Sugary Spire**
- **FRICKBEARS3**

Games without that flag do not expose the same full-install workflow.
