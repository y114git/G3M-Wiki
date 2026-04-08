# Mod Filtering & Sorting

G3M provides extensive filtering and sorting capabilities in both the Mods Browser and the Library.

---

## Filter Criteria

### Search Text

A text search that matches against multiple fields simultaneously:

- Mod name / title
- Author name
- Description / tagline
- Tags (comma-separated)
- Category name (from GameBanana)
- Added date (formatted as text)
- Updated date (formatted as text)

The search is **case-insensitive**. Multiple space-separated terms must all match (AND logic) — each term can match in a different field. For example, "dark chapter 2" matches a mod named "Dark World" with description mentioning "chapter 2".

### Tag Filters

Four predefined tag categories can be toggled:

| Tag | Matches Mods With |
| --- | --- |
| **Text Edit** | Tags containing "text", "dialogue", "translation", or similar. Also matched via GameBanana categories related to text modifications. |
| **Customization** | Tags containing "customization", "visual", "audio", "sprite", "texture", "skin", or similar. |
| **Gameplay** | Tags containing "gameplay", "mechanic", "balance", "difficulty", or similar. |
| **Other** | Tags that don't fit the above categories, or mods with no tags. |

When multiple tags are selected, mods must match **all** selected tags (AND logic between tags).

### NSFW Filtering

When "Show NSFW" is unchecked (default), mods are hidden if any of these conditions are true:

- The mod has an explicit NSFW flag set to `true`.
- The mod's content rating indicates adult content.
- Any of the mod's tags or categories contain NSFW-related keywords:
  - `nsfw`
  - `adult`
  - `18+`
  - `18plus`
  - `explicit`
  - `mature`

The check is case-insensitive and looks at the tag/category as a substring.

### Game Filter

In the Mods Browser, the game selector dropdown restricts results to mods for the selected game (by GameBanana game ID).

In the Library, the game selector shows only mods installed for that game in the current profile.

### Blocklist Filter

Mods matching any blocklist rule (by ID, name, or category) for the current game or globally are excluded from results. This happens transparently — blocked mods simply don't appear. See [Blocklist Manager](../features/blocklist.md).

### Installation Status Filter

In the Library, only installed mods (mods with folders in the profile's `mods/` directory) are shown. The Mods Browser shows all mods from GameBanana regardless of installation status.

---

## Sort Options

### Mods Browser

| Sort | Description |
| --- | --- |
| **Relevant** (default) | Sorts by total download count, highest first. |
| **By creation date** | Sorts by the mod's original publication date. |
| **By update date** | Sorts by the most recent update date. |

Each sort has a **direction toggle** (ascending ↑ / descending ↓):

- Default direction for "Relevant": descending (most downloads first).
- Default direction for dates: descending (newest first).

### Library

The Library sorts mods by:

| Sort | Description |
| --- | --- |
| **Name** (default) | Alphabetical by mod name. |
| **Date added** | By when the mod was imported. |
| **Date updated** | By the last modification date. |
| **Author** | Alphabetical by author name. |

---

## Tag Canonicalization

G3M normalizes tags for consistent filtering:

- Tags are lowercased.
- Leading/trailing whitespace is stripped.
- Common separators (commas, semicolons) split multi-tag strings into individual tags.
- Empty tags are removed.
- GameBanana category names are mapped to G3M tag categories using an internal mapping table.

This ensures that "Customization", "customization", "CUSTOMIZATION", and "  Customization  " all match the same filter.

---

## Searchable Text Building

For each mod, G3M builds a "searchable text" blob by concatenating:

1. Mod name
2. Author
3. Description
4. All tags (joined with spaces)
5. Category name
6. Added date (formatted)
7. Updated date (formatted)

This blob is searched against the user's search terms. The search checks if each term appears as a substring in the blob.

---

## Performance

Filtering and sorting are performed in-memory on the full mod list. For large libraries (hundreds of mods), the operations are essentially instant. For the Mods Browser with thousands of mods, pagination limits the visible set to 15 mods per page, so filtering only applies to loaded pages.

---

## Filter Persistence

Filter selections (search text, active tags, sort order, NSFW toggle) are **not persisted** across sessions. They reset to defaults when G3M starts:

- Search: empty
- Tags: none selected (show all)
- Sort: Relevant / descending
- NSFW: hidden

The game selector does persist — G3M remembers the last selected game.
