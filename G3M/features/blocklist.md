# Blocklist Manager

The Blocklist Manager lets you permanently hide specific mods from the Mods Browser and Library. Hidden mods are filtered out before they appear in any list.

---

## Opening the Blocklist Manager

Accessible from Settings or from the Library/Browser context menus.

---

## How It Works

The blocklist is a list of rules. Each rule has:

- **Scope** — Which game the rule applies to, or "global" (applies to all games).
- **Prefix Type** — What kind of value to match:
  - **ID** — Match by mod ID (exact match, case-insensitive).
  - **Name** — Match by mod name (substring match, case-insensitive). If the mod's name contains the value anywhere, it is blocked.
  - **Category** — Match by GameBanana category (exact match, case-insensitive).
- **Value** — The string to match against.

---

## Adding a Rule

1. Open the Blocklist Manager.
2. Choose a scope (a specific game or "global").
3. Select the prefix type (ID, Name, or Category).
4. Enter the value.
5. Click **Add**.

Duplicate rules (same scope, type, and value) are silently ignored.

### Quick Block from Context Menu

Right-clicking a mod card in the Library or Mods Browser shows an **Add to Blocklist** option. This pre-fills the blocklist rule with the mod's ID and the current game.

---

## Removing a Rule

In the Blocklist Manager, select a rule and click **Remove**. The mod will become visible again after the next list refresh.

---

## Matching Logic

When filtering mods, G3M checks each mod against all blocklist rules for the current game plus all "global" rules. If any rule matches:

- **ID match**: The mod's internal ID (e.g., `gb_mod_12345`) is compared case-insensitively. For GameBanana mods, the numeric GameBanana ID is also extracted and compared.
- **Name match**: The mod's name or title is checked for a case-insensitive substring match.
- **Category match**: The mod's GameBanana category (or `cat_name`) is compared case-insensitively.

If any rule matches, the mod is excluded from display.

---

## Persistence

The blocklist is stored in `settings/blocklist.json` inside the user data folder. The file structure is:

```json
{
  "global": [
    { "prefix_type": "name", "value": "unwanted mod" }
  ],
  "deltarune": [
    { "prefix_type": "id", "value": "12345" }
  ]
}
```

Each key is a game ID (or "global"), and the value is an array of rule objects.

---

## Display Names

In the Blocklist Manager UI, prefix types are displayed with human-readable labels:

| Internal | Display |
| --- | --- |
| `id` | "Mod ID" |
| `name` | "Mod Name" |
| `category` | "Category" |

These labels are localized.
