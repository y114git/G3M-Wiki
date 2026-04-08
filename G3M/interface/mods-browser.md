# Mods Browser

The **Mods Browser** tab lets you search, browse, and download mods from GameBanana without leaving G3M.

---

## Layout

The Mods Browser has two areas:

1. **Filter Bar** (top) — Game selector, tag filters, search, sort, and NSFW toggle.
2. **Mod Grid** (below) — Cards showing available mods from GameBanana, loaded in pages.

---

## Filter Bar

### Game Selector

A dropdown that lists all visible games that have a GameBanana ID configured. Only games with a valid GameBanana ID appear here. Built-in games with GameBanana support:

| Game | GameBanana ID |
| --- | --- |
| DELTARUNE | 6755 |
| UNDERTALE | 5506 |
| UNDERTALE Yellow | 19606 |
| Pizza Tower | 7692 |
| Sugary Spire | 18218 |

Custom games also appear here if they have a GameBanana game ID set.

DELTARUNE DEMO does **not** have a GameBanana ID and does not appear in the Mods Browser game selector.

Changing the game clears the current mod list and reloads mods for the selected game.

### Tags

Four tag filter buttons:

- **Text Edit** — Mods that change text/dialogue.
- **Customization** — Visual or audio customization mods.
- **Gameplay** — Mods that alter gameplay mechanics.
- **Other** — Mods that don't fit the above categories.

Tags are derived from the mod's own tags and from its GameBanana category (mapped automatically). You can select multiple tags — only mods matching **all** selected tags are shown.

There is also a special tag **CYOP/AFOM** that appears on Pizza Tower custom level mods — CYOP stands for "Create Your Own Pizza" (the game's built-in custom level system) and AFOM stands for "Another Fixed Objects Mod".

### Search

A search button opens a text input. Type any text to filter mods by name, description, author, tags, category, and dates. The search is case-insensitive and matches all entered words (space-separated). A clear button appears when search is active, showing the current search term in its tooltip.

Search has a timeout of 10 seconds per request.

### Sort

A dropdown to choose sort order:

| Option | Description |
| --- | --- |
| **Relevant** | Sorts by download count (most downloaded first). This is the default. |
| **By creation date** | Sorts by when the mod was first published. |
| **By update date** | Sorts by the last update date. |

Next to the sort dropdown is a **sort direction** button that toggles between ascending and descending order.

### Show NSFW

A checkbox labeled **Show NSFW**. When unchecked (default), mods flagged as NSFW, adult, 18+, explicit, or mature are hidden from results. The NSFW check looks at:

- Explicit NSFW flags on the mod.
- Content rating fields.
- Tags and category names containing NSFW-related keywords (`nsfw`, `adult`, `18+`, `18plus`, `explicit`, `mature`).

---

## Mod Cards

Each mod is displayed as a card showing:

- **Icon** — The mod's icon image, loaded from GameBanana. Cached locally (up to 100 images in memory).
- **Name** — The mod's display name.
- **Author** — The mod author.
- **Short description** — A brief summary.
- **Tags** — Colored tag badges.
- **Downloads count** — Total GameBanana downloads.
- **Likes count** — Total likes (tooltip: "Number of likes").
- **Created / Updated dates** — When the mod was published and last updated.

### Clicking a Mod Card

Clicking a mod card opens the **Mod Details Overlay** — a large panel that slides in from the right covering part of the content area.

---

## Mod Details Overlay

The overlay shows full information about a selected mod:

- **Icon** (large).
- **Name**, **Author**, **Version**, **Game Version**.
- **Full description** — Loaded from the mod's GameBanana description URL. Rendered as rich HTML with image support. Images in the description are cached (up to a configurable limit). If the description fails to load, an error message is shown.
- **Screenshots** — A scrollable gallery of the mod's screenshots from GameBanana. Right-clicking a screenshot shows a context menu: "Open image in browser", "Copy image", "Copy image URL". If there are no screenshots, "No screenshots" is displayed.
- **Tags** — Listed as badges.
- **Homepage** — If the mod has a homepage URL, a clickable "Open Homepage" button is shown.
- **Download / Use buttons**:
  - **Download** — Queues the mod for download via the Downloads system. If the mod has multiple files on GameBanana, a file picker dialog appears letting you choose which archive to download (showing version, size, update date, download count, MD5, security status, and auto-install compatibility).
  - **Use** — If the mod is already installed locally, clicking Use selects it in the Library for the current chapter.
  - **Unuse** — If the mod is currently selected, clicking Unuse deselects it.

### GameBanana File Picker

When a mod has multiple downloadable files, G3M shows a picker dialog:

- Lists each available file with: file name, version, size, update date, download count, auto-install status (Yes/No), security scan status, and MD5 hash.
- A **Details** section shows the full description of each file.
- An "Open mod page" button opens the mod's GameBanana page in your browser.
- Only files detected as compatible with G3M (containing supported archive formats) can be downloaded.

### Mod Compatibility

Not all GameBanana mods are compatible with G3M. If a mod does not contain files in a supported format, G3M shows a message: "This mod does not support G3M format. You can download it manually or contact the mod author/leave a comment to request G3M support."

---

## Pagination

Mods load in pages of 15 items each (the GameBanana API page size). As you scroll down, more pages are loaded automatically. A loading indicator appears during fetches. The browser tracks which pages have been loaded per game to avoid duplicate requests.

If you reach the end of available mods, loading stops (indicated by an internal sentinel page value of 100).

---

## Rate Limiting

GameBanana enforces an API rate limit of 250 requests per hour. If this limit is reached, G3M shows a warning: "GameBanana API rate limit reached (250 requests/hour). Please wait and try again."

---

## Blocklist Integration

Mods that match any entry in the Blocklist Manager are automatically hidden from the Mods Browser results. See [Blocklist Manager](../features/blocklist.md) for details.

---

## Network Fallback

If the network request fails on initial load, G3M attempts to load a locally cached mod list and shows a status message: "Network error. Loaded local list." If the update itself fails later, the status shows: "Failed to update mod list."
