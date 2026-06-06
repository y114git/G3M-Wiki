# Steam Integration

G3M can launch supported games through Steam when the current game has a Steam App ID and the Steam launch option is enabled.

## Built-in Steam-backed games

Current built-in Steam App IDs:

- DELTARUNE: `1671210`
- DELTARUNEdemo: `1690940`
- UNDERTALE: `391540`
- Pizza Tower: `2231450`

Games without a Steam App ID launch directly instead.

## How Steam launch works

When Steam launch is active, G3M uses:

`steam://rungameid/<app_id>`

The app still prepares the game files first, then hands the actual start over to Steam.

## Custom games

Custom games can also have an optional Steam App ID. If you set one, the same Steam launch path becomes available for that custom entry.

## Path detection

G3M also contains Steam-library path discovery helpers for supported platforms, which are used during game detection and setup.
