# Title Bar

G3M uses a custom Qt title bar widget instead of relying on the platform
default.

---

## Current Layout

The widget has two left-side menu buttons and three right-side window buttons.

Left side:

- `Windows` menu
- `Help` menu

Right side:

- minimize
- maximize or restore
- close

The `Windows` menu currently exposes the log viewer action. The `Help` menu
exposes changelog and about actions.

---

## Window Actions

Empty space in the title bar can:

- start a system window move on left-click drag
- toggle maximize or restore on double-click

Buttons themselves do not trigger dragging.

---

## Theming and Scaling

The title bar applies the current theme text color to the window control icons
and rescales its metrics from the UI scale setting. The widget updates:

- margins
- spacing
- button size
- icon size
- overall height
