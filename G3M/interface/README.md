# Interface Overview

G3M has a single main window with a custom title bar, a tab bar, a status bar at the bottom, and content that changes depending on the active tab.

The window is frameless — it uses a custom-drawn title bar and rounded corners. The corner radius is configurable (default: 7 px). The window can be resized by dragging edges. It can be maximized, minimized, and restored using title bar buttons or standard OS shortcuts.

---

## Main Window Layout

From top to bottom:

1. **Custom Title Bar** — App name, minimize / maximize / close buttons, optional online counter, social links.
2. **Tab Bar** — Switches between **Mods Browser**, **Library**, and **Settings**. Individual tabs can be hidden in settings.
3. **Content Area** — The active tab's content fills this area.
4. **Status Bar** — Shows the current status message (color-coded), a progress bar during operations, and the main action button (Launch / Install / Update / Cancel / Close).

---

## Title Bar

The title bar contains, from left to right:

- **App logo** — Displays the default G3M logo or a custom logo if set in Appearance settings. Clicking the logo opens the About dialog.
- **App title** — Shows "G3M".
- **Online counter** — Shows the number of players currently playing via G3M (e.g., "Online: 5"). Tooltip: "This counter shows the number of players playing the game via the launcher." Updated every 30 minutes.
- **Social buttons** — Telegram and Discord icon buttons linking to the official communities.
- **Chat button** — Opens the built-in chat dialog.
- **Shortcut button** — Opens the shortcut creation dialog for the current game and mod selection.
- **Window controls** — Minimize, Maximize/Restore, Close buttons with tooltips.

---

## Tab Bar

The tab bar shows up to three tabs:

| Tab | Description |
| --- | --- |
| **Mods Browser** | Browse and search mods from GameBanana. Filterable by game, tags, search text, sort order. |
| **Library** | Manage your locally installed mods. Select mods to use, organize by profiles. |
| **Settings** | All application settings: General, Game, Appearance, Library, Mods Browser, Plugins. |

### Hiding Tabs

- **Hide Mods Browser tab** — Checkbox in Settings → General. When enabled, the Mods Browser tab is removed from the tab bar.
- **Hide Library tab** — Checkbox in Settings → General. When enabled, the Library tab is removed.
- If both are hidden, the content area shows a placeholder message: "But nobody came..."

### Easter Egg

The Library tab has a small easter egg: very rarely, its label shows "Librarby" instead of "Library". The same applies to the Library sub-tab in Settings.

---

## Status Bar

The status bar at the bottom of the window contains:

- **Status label** — Displays the current operation status (e.g., "Ready", "Launching game...", "Mod installed successfully!"). The text color changes based on context: green for success, yellow for warnings, red for errors, default for info.
- **Progress bar** — Appears during download, installation, patching, and update operations. Shows percentage progress. Hidden when not active.
- **Action button** — The large button on the right side of the status bar. Its label and behavior change depending on the current state:

| State | Button Label | Action |
| --- | --- | --- |
| Idle, no mods selected | **Launch** | Launches the game without mods (vanilla). |
| Idle, mods selected | **Launch** | Patches the selected mods into the game files, then launches. |
| Full Install enabled | **Install** | Starts the full game file download and installation. |
| Mods have updates available | **Update** | Updates the selected mods. |
| Game is running | **Close** | Terminates the running game process. |
| Installation/patching in progress | **Cancel** | Cancels the current operation. |
| Not yet initialized | **Please wait...** | Disabled until initialization completes. |

---

## Keyboard and Mouse

- **Fullscreen** — Toggled via Settings → General → Fullscreen, or by double-clicking the title bar.
- **Drag** — Click and drag the title bar to move the window.
- **Resize** — Drag window edges to resize.
- **Right-click on mod images** — Context menu with "Open image in browser", "Copy image", "Copy image URL".
- **Double-click chapter tab** (Library, DELTARUNE only) — Toggles direct launch for that chapter.

---

## Scaling

G3M supports UI scaling. In Settings → General, the **UI Scale** spin box lets you scale the entire interface up or down. This affects all widget sizes, fonts, padding, and icon dimensions proportionally.
