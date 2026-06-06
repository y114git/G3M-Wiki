# Blocklist

The blocklist hides mods you do not want to see in the browser or filtered lists.

## What can be blocked

The current blocklist service supports three rule types:

- `id`
- `name`
- `category`

Rules can be global or tied to a specific game.

## How matching works

- `id` matches a mod ID, including parsed GameBanana IDs where available
- `name` matches by case-insensitive text in the mod name
- `category` matches category-style metadata such as GameBanana category labels

If any rule matches, the mod is filtered out.

## Where it is stored

Blocklist rules are stored in:

`settings/blocklist.json`

## Where you manage it

G3M has a dedicated Blocklist dialog, and the search/browser flow can also open it directly.
