# Status Bar

The status bar is the bottom area of the main window. It provides feedback about the current operation and houses the main action button.

---

## Layout

From left to right:

1. **Status label** — Text describing the current state or last operation result.
2. **Progress bar** — Horizontal bar showing operation progress (hidden when idle).
3. **Action button** — The large button for the primary action.

---

## Status Label

The status label shows context-sensitive messages:

### Message Types

| Category | Color | Example Messages |
| --- | --- | --- |
| **Info** | Default (white/gray) | "Ready", "Loading mods...", "Checking for updates..." |
| **Success** | Green | "Mod installed successfully!", "Game launched", "Original files restored" |
| **Warning** | Yellow | "GameBanana rate limit reached", "Mod may be incompatible", "No game path set" |
| **Error** | Red | "Failed to apply patch", "Download failed", "Permission denied" |

### Status Color Customization

The success/warning/error colors adapt to your theme. If you set a custom "Main Text" color, status messages use appropriate contrasting colors for visibility.

### Common Status Messages

| Message | Meaning |
| --- | --- |
| "Ready" | G3M is initialized and waiting for user action. |
| "Please wait..." | Initialization is in progress. |
| "Loading mods..." | Mods are being loaded from the profile's mods folder. |
| "Launching game..." | Game patching and launch is in progress. |
| "Game is running: DELTARUNE (0:05:32)" | The game is running with playtime counter. |
| "Original files restored" | Game exited and all files were successfully restored. |
| "Mod installed successfully!" | A mod was imported into the library. |
| "Download complete" | A file was downloaded from GameBanana or another source. |
| "Failed to apply patch: ..." | Patching failed with an error description. |
| "Game is currently running. Close it first." | A launch was attempted while the game is already running. |
| "No game path configured. Set it in Settings → Game." | Launch attempted without a game path. |
| "Cancelled" | The user cancelled an operation. |
| "Installation complete" | Full Install finished successfully. |

---

## Progress Bar

The progress bar appears during long-running operations:

| Operation | Progress Source |
| --- | --- |
| Mod patching | G3MTool reports percentage per chunk/step. |
| File download | HTTP response content-length vs bytes received. |
| Archive extraction | Files extracted vs total files. |
| Full Install download | Same as file download. |
| Game version archiving | Files processed vs total files. |
| App update download | Same as file download. |

The progress bar:

- Shows 0–100% with a smooth fill animation (unless animations are disabled).
- Is hidden when no operation is in progress.
- Resets to 0% when a new operation starts.
- Becomes indeterminate (pulsing animation) if the total size is unknown.

---

## Action Button

The action button is the primary control for launching games and managing operations. Its text and behavior change based on the current context:

### Button States

| Context | Text | Enabled | Click Behavior |
| --- | --- | --- | --- |
| Idle, game path set | **Launch** | Yes | Starts the game (with mods if selected). |
| Idle, no game path | **Set game path** | Yes | Scrolls to Settings → Game or shows game path dialog. |
| Full Install enabled | **Install** | Yes | Starts the Full Install download. |
| Selected mods have updates | **Update** | Yes | Updates the selected mods from GameBanana. |
| Game is running | **Close** | Yes | Terminates the running game process. |
| Patching in progress | **Cancel** | Yes | Cancels the patching/launch operation. |
| Download in progress | **Cancel** | Yes | Cancels the active download. |
| Initialization pending | **Please wait...** | No (disabled) | Nothing — button is disabled until init completes. |
| App update in progress | **Cancel** | Yes | Cancels the app update download. |

### Button Appearance

The button color adapts to the theme:

- **Normal state**: Uses the "Elements" theme color.
- **Hover state**: Uses the "Hover" theme color.
- **Pressed state**: Uses the "Select" theme color.
- **Disabled state**: Dimmed version of the "Elements" color.

When the game is running, the button text includes a playtime counter that updates in real-time (e.g., "Close (0:15:32)").

### Button Tooltip

The button has a tooltip showing additional context:

- When mods are selected: Shows the names of selected mods.
- When no mods are selected: "Launch the game without mods".
- When game is running: "Click to close the running game".

---

## Signal Flow

The status bar is driven by signals from various services:

1. **status_changed(text, color)** — Updates the status label with new text and color.
2. **progress_updated(percent)** — Updates the progress bar to the given percentage.
3. **action_button_text_changed(text)** — Changes the action button label.
4. **action_button_enabled_changed(enabled)** — Enables or disables the action button.
5. **progress_bar_visible_changed(visible)** — Shows or hides the progress bar.

These signals are emitted by the `GameLauncher`, `UpdateChecker`, `DownloadsManager`, and other services as they perform operations.
