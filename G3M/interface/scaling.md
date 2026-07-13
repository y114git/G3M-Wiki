# UI Scaling

G3M has its own UI scale setting on top of normal Qt and OS display scaling.

## Main control

The current settings UI exposes `ui_scale` as a percentage-style control.

This scale factor affects many parts of the interface, including:

- card sizing
- font sizing
- spacing
- title bar metrics
- dialog sizes

## Why it matters

If the default layout feels too small or too large on your display, changing the
UI scale is the intended way to rebalance the interface without changing the
app's behavior.
