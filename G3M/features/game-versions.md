# Game Versions

Game Versions lets you save restore points for a game installation and bring them back later. Use it when you want a clean baseline before modding, a backup before experimenting, or a quick way to roll a game folder back to a known state.

## Where to find it

1. Open G3M.
2. Pick the game you want from the game selector.
3. Click the small **Game Versions** button next to the game controls. The icon is a small version/archive-style button near the selected game area.
4. The **Game Versions** dialog opens for the currently selected game.

If you cannot find the button, first make sure the game is visible in **Settings -> Game Manager** and that a game folder is configured in **Settings -> Game Settings**.

## Storage paths

On Windows, saved versions are stored under:

`%LOCALAPPDATA%\G3M\game_versions\`

The saved-version index is:

`%LOCALAPPDATA%\G3M\game_versions\game_versions_data.json`

The actual version archives are also stored in:

`%LOCALAPPDATA%\G3M\game_versions\`

On Linux the same files are under `~/.local/share/G3M/game_versions/`. On macOS they are under `~/Library/Application Support/G3M/game_versions/`.

## What you can do

The current dialog and manager support:

- create a new saved version
- import an external `.zip`
- apply a saved version back to the game
- export a saved version
- delete a saved version

The create flow can also associate the saved version with a profile name.

## Create a saved version

1. Open **Game Versions**.
2. Click **Create** or the create/add button.
3. Enter a name that will still make sense later, for example `Clean install before Ch5 mods`.
4. Confirm.

G3M archives the current game folder and adds a record to `game_versions_data.json`. This does not enable or disable mods. It only saves the current files as a restorable snapshot.

Create a version when the game folder is in the state you want to keep. If the folder is already modded, the saved version will contain that modded state.

## Apply or restore a version

1. Open **Game Versions**.
2. Select the saved version in the list.
3. Click **Apply** or **Restore**.
4. Confirm the warning.

G3M replaces the current game files with the files from that saved version. This is intentionally destructive for the current game folder, so export or create another version first if you need to keep the current state.

## Import and export

Use **Import** when you already have a saved-version `.zip` and want G3M to add it to the list.

Use **Export** when you want to copy a saved version somewhere else, send it to another machine, or keep an external backup. Exporting does not remove the saved version from G3M.

## Delete a saved version

1. Select the version.
2. Click **Delete**.
3. Confirm.

Deleting removes the saved-version record and its archive from `%LOCALAPPDATA%\G3M\game_versions\`. It does not delete the game itself and does not remove installed mods from profiles.

## Why it is useful

Typical uses:

- keep a clean unmodded baseline
- keep a checkpoint before testing new mods
- quickly roll back to a known-good state

## Recovery behavior

Game version storage has startup recovery logic, so interrupted or broken records are cleaned up or normalized on the next start.

## Common confusion

Game Versions is not the same as launch-time backups. Launch-time backups are temporary safety files used while a modded session is running. Game Versions are user-managed snapshots that stay until you delete them.

Game Versions is also not the same as Mod Versions. Mod Versions are saved variants of a mod folder. Game Versions are saved variants of an installed game folder.
