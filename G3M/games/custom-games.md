# Custom Games

G3M supports adding any GameMaker-based game as a **custom game**. Custom games appear alongside built-in games in all dropdowns, the Library, and (if they have a GameBanana ID) the Mods Browser.

---

## Adding a Custom Game

Open the **Game Manager** (Settings → Game → Game Manager button), then click **Add Game**. Fill in the fields:

| Field | Required | Description |
| --- | --- | --- |
| **Display Name** | Yes | The name shown in the UI (e.g., "My Custom Game"). Must be unique and non-empty. |
| **Primary Executable** | Yes | The filename of the game's main executable (e.g., `MyGame.exe`). G3M uses this to locate and launch the game. |
| **Data File Name** | Yes | The name of the game's main data file (e.g., `data.win`). This is the file that mods patch. |
| **Steam App ID** | No | If the game is on Steam, enter its App ID to enable "Launch via Steam" support. |
| **GameBanana Game ID** | No | If the game has a GameBanana page, enter its numeric game ID to enable Mods Browser integration. |

### ID Generation

When you create a custom game, G3M generates a unique internal ID based on the display name. The ID is a lowercase slug with special characters removed (e.g., "My Custom Game" becomes `my_custom_game`). This ID is permanent — it cannot be changed after creation.

### Validation

G3M validates the input:

- Display name must not be empty.
- Display name must not duplicate an existing game.
- Primary executable must not be empty.
- Data file name must not be empty.

If validation fails, an error message dialog appears.

---

## Custom Game Behavior

A custom game:

- Has a single content tab (no chapter splitting).
- Does **not** support Direct Launch (always launches normally).
- Does **not** support Full Install.
- Supports all mod operations: import, create, export, patch, launch.
- Appears in the Game Manager for reordering and visibility control.
- Stores its game path in a setting keyed as `custom_game_path_<id>` and its custom executable as `custom_game_exec_<id>`.
- Tracks used mods under `used_mods_<id>`.

---

## Editing a Custom Game

Currently, custom games cannot be edited after creation. If you need to change a custom game's settings, delete it and create a new one.

---

## Deleting a Custom Game

In the Game Manager, select the custom game and click **Delete**. A confirmation dialog appears. After deletion:

- The game is removed from all dropdowns, the Library, and the Mods Browser.
- Mods installed for that game remain on disk in the profile's mods folder but are no longer displayed.
- The game's settings (path, used mods) are cleaned up.

Built-in games cannot be deleted.

---

## Persistence

Custom game definitions are stored in `custom_games.json` in the user data folder. The file also stores the full game order (built-in + custom) and visibility states.
