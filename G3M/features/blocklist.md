# Blocklist

The blocklist hides mods you do not want to see in the browser or filtered
lists.

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

`%LOCALAPPDATA%\G3M\settings\blocklist.json`

## Where you manage it

G3M has a dedicated Blocklist dialog. Open it from **Settings** or from the Mods
Browser/search flow when a blocklist action is available.

Typical actions:

1. Open **Blocklist**.
2. Add a rule by mod ID, name text, or category.
3. Choose whether it applies globally or only to one game.
4. Save or close the dialog.

Blocked mods simply stop appearing in the affected browser/library results. The
blocklist does not uninstall mods that are already installed.
