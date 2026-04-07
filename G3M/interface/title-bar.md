# Title Bar

G3M uses a custom-drawn title bar instead of the operating system's native title bar. This allows the title bar to match the application's theme and include additional controls.

---

## Layout

The title bar is a horizontal strip at the top of the window. From left to right:

### Left Section

1. **Logo** — The G3M icon (or custom logo if set). Clicking the logo opens the About dialog.
2. **Title text** — "G3M" followed by the version suffix (e.g., "G3M 3.0.3stable").
3. **Online counter** — Shows "Online: N" with the number of active G3M users. The counter is refreshed periodically from the server.

### Center Section

4. **Tab bar** — The main navigation tabs:
   - **Mods Browser** — Browse and download mods from GameBanana.
   - **Library** — Manage installed mods and launch games.
   - **Settings** — Configure the application.

   Tabs can be hidden individually via Settings (e.g., "Hide Mods Browser tab"). Hidden tabs are not shown in the tab bar, and the remaining tabs fill the available space.

   The active tab is highlighted using the "Select" theme color. Hovering over an inactive tab shows the "Hover" theme color.

   An easter egg: the Library tab very rarely displays as "Librarby" instead of "Library".

### Right Section

5. **Chat button** — Opens the Chat dialog (speech bubble icon).
6. **Shortcut button** — Opens the Shortcut Creation dialog (scissors/link icon).
7. **Modding Tools button** — Opens the Modding Tools dialog (wrench icon).
8. **Social buttons** — Small icon buttons for:
   - **Telegram** — Opens the Telegram group link.
   - **Discord** — Opens the Discord server invite.
9. **Window controls** — Standard minimize, maximize/restore, and close buttons.

---

## Window Dragging

The title bar serves as the drag handle for moving the window:

- Click and hold anywhere on the title bar (except on buttons or tabs) to drag the window.
- The drag area includes the spaces between buttons and the title text region.
- Double-clicking the title bar toggles maximize/restore state.

---

## Resize Handles

The title bar includes invisible resize handles at the top edge and top corners of the window:

- **Top edge** — Drag to resize vertically.
- **Top-left corner** — Drag to resize diagonally.
- **Top-right corner** — Drag to resize diagonally.

These handles are a few pixels tall and overlay the title bar region. The cursor changes to a resize icon when hovering over them.

---

## Window Control Buttons

### Minimize

Minimizes the window to the taskbar. The window remains running in the background.

### Maximize / Restore

Toggles between maximized (fills the screen) and normal (windowed) state. When maximized:

- The window fills the screen.
- The border radius is set to 0 (square corners).
- The window control button icon changes from "maximize" to "restore".

### Close

Closes the application. Before closing:

1. Any active background music is stopped.
2. The current profile's mod selection state is saved.
3. Settings are written to disk.
4. Plugin hooks (if any) are cleaned up.
5. The window closes and the application exits.

If a game is currently running when you click Close, a confirmation dialog may appear asking if you want to close G3M (which will also restore game files and potentially terminate the game).

---

## Theme Integration

Every element in the title bar uses the current theme colors:

| Element | Color |
| --- | --- |
| Background | Background theme color (with transparency). |
| Title text | Main Text theme color. |
| Version text | Secondary Text theme color. |
| Online counter | Secondary Text theme color. |
| Tab text (inactive) | Secondary Text theme color. |
| Tab text (active) | Main Text theme color. |
| Tab background (active) | Select theme color. |
| Tab background (hover) | Hover theme color. |
| Button icons | Main Text theme color. |
| Button hover background | Hover theme color. |
| Close button hover | Red (always red for visibility). |

---

## Badge Indicators

Some title bar elements can display notification badges:

- **Downloads badge** — A small colored circle on the Downloads indicator (visible when downloads need attention).
- **Update badge** — An indicator when an app update is available.

Badges use a contrasting color (typically red or accent color) to stand out against the title bar background.

---

## Responsive Behavior

On narrow windows:

- The title bar compresses — buttons and tabs reduce their padding.
- At very narrow widths, some elements may be hidden (social buttons, online counter) to prevent overlap.
- The tab text remains visible as long as possible.
- Window control buttons are never hidden.

---

## Accessibility

- All title bar buttons have tooltips describing their function.
- The online counter has a tooltip explaining what it represents.
- Tab buttons are keyboard-focusable (Tab key navigation).
- The close button is always visible and reachable.
