# Mod Details Panel

When you click a mod card in the Mods Browser, a detailed overlay panel slides in from the right side. This panel shows complete information about the selected mod.

---

## Layout

The Mod Details panel is divided into sections from top to bottom:

### Header

- **Back button** — Closes the details panel and returns to the mod grid.
- **Mod icon** — Large version of the mod's icon image.
- **Mod name** — Large, bold title text.
- **Author** — The mod creator's name.
- **Version** — The mod's current version string.
- **Game version** — Which game version this mod was created for.

### Action Buttons

- **Download** — Starts downloading the mod. If the mod has multiple files available, opens the file picker dialog first (see below).
- **Use / Unuse** — If the mod is already installed in your library, toggles its selection state for the current chapter.
- **Open Homepage** — (If available) Opens the mod's homepage or GameBanana page in your browser.

### Tags

A row of colored tag badges showing the mod's categories: Customization, Gameplay, Text Edit, Other, CYOP/AFOM, etc.

### Statistics

- **Downloads** — Total download count from GameBanana. Displayed with a download icon.
- **Likes** — Total like count. Displayed with a heart icon. Tooltip: "Number of likes".
- **Created** — Date the mod was first published.
- **Updated** — Date the mod was last updated.

### Description

The full mod description, loaded from the mod's GameBanana description URL. This is rendered as rich HTML, which may include:

- Formatted text (bold, italic, headings, lists).
- Embedded images (loaded from external URLs, cached locally).
- Links (clickable, open in browser).
- Video embeds (may appear as links).

If the description fails to load (network error, timeout), a fallback message is shown: "Failed to load description."

The description has a loading spinner while it's being fetched.

### Screenshots

A horizontally scrollable gallery of the mod's screenshot images from GameBanana.

**Right-click context menu on screenshots:**

- **Open image in browser** — Opens the full-resolution image URL in your system browser.
- **Copy image** — Copies the image to the system clipboard.
- **Copy image URL** — Copies the image's URL to the clipboard.

If the mod has no screenshots, the text "No screenshots" is displayed.

### Files Section

If the mod has multiple downloadable files on GameBanana, the details panel may show a summary of available files below the description.

---

## File Picker Dialog

When downloading a mod with multiple files, the File Picker dialog appears:

### File List

Each available file is shown as a row with:

| Column | Description |
| --- | --- |
| **File name** | The archive file name (e.g., "MyMod_v1.2.zip"). |
| **Version** | The file's version string. |
| **Size** | The file size in human-readable format (KB, MB). |
| **Updated** | When this file was last updated. |
| **Downloads** | How many times this specific file was downloaded. |
| **Auto-install** | Whether G3M can automatically install this file. Shows "Yes" (green) or "No" (gray). Files that don't contain supported mod data are marked "No". |
| **Security** | The scan status from GameBanana's file scanner. Shows "Scanned" (safe) or other statuses. |
| **MD5** | The MD5 hash of the file for verification. |

### Details Pane

Below the file list, a details pane shows the full description of the currently selected file. This helps you choose between multiple download options (e.g., different quality levels, different game versions, different feature sets).

### Actions

- **Download** — Downloads the selected file.
- **Open mod page** — Opens the mod's full GameBanana page in your browser.
- **Cancel** — Closes the dialog without downloading.

### Auto-Install Detection

G3M examines each file's properties to determine if it can be automatically installed:

- Files containing `.zip`, `.7z`, or `.rar` archives are potentially auto-installable.
- Files containing `.g3mpatch`, `.xdelta`, `.vcdiff`, `.csx`, or data files are auto-installable.
- Files that are executables (`.exe`), installers, or unknown formats are marked as not auto-installable.
- The `auto_install` flag is displayed per-file so users know which files G3M can handle.

---

## Image Caching

The Mod Details panel caches images aggressively to improve performance:

- **Mod icons** — Up to 100 icons are cached in memory. Eviction uses LRU (least recently used) policy.
- **Description images** — Images embedded in descriptions are cached up to a configurable limit.
- **Screenshots** — Loaded on demand as the user scrolls through the gallery. Cached for the duration of the session.

---

## Installed Mod Detection

When viewing a mod's details, G3M checks if a mod with the same GameBanana ID is already installed in the current profile's library. If found:

- The **Download** button may change to **Update** if the online version is newer.
- A **Use** button appears to select the installed version in the Library.
- A badge or indicator shows "Installed" status.

---

## Closing the Panel

Click the **Back** button, press Escape, or click outside the panel to close it and return to the mod grid. The grid scroll position is preserved.
