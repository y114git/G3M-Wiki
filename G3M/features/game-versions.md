# Game Versions

Game Versions lets you save restore points for a game installation and bring them back later.

## What it stores

Each saved version is tracked in:

`game_versions/game_versions_data.json`

The actual archives live in the `game_versions/` folder.

## What you can do

The current dialog and manager support:

- create a new saved version
- import an external `.zip`
- apply a saved version back to the game
- export a saved version
- delete a saved version

The create flow can also associate the saved version with a profile name.

## Why it is useful

Typical uses:

- keep a clean unmodded baseline
- keep a checkpoint before testing new mods
- quickly roll back to a known-good state

## Recovery behavior

Game version storage has startup recovery logic, so interrupted or broken records are cleaned up or normalized on the next start.
