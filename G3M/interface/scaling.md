# UI Scaling

G3M supports interface scaling for different screen resolutions and user preferences.

---

## Automatic Scaling

G3M reads the system's DPI (dots per inch) setting and scales the UI accordingly:

- **100% (96 DPI)** — Standard scale. Default sizes and spacing.
- **125% (120 DPI)** — All elements are 25% larger.
- **150% (144 DPI)** — All elements are 50% larger.
- **175% (168 DPI)** — All elements are 75% larger.
- **200% (192 DPI)** — All elements are doubled.

This scaling is automatic and based on the system's display settings. You do not need to configure anything in G3M.

---

## What Scales

| Element | Scales? |
| --- | --- |
| Window size | Yes — default window size adjusts. |
| Fonts | Yes — all text scales with the system DPI. |
| Icons | Yes — icon sizes adjust. |
| Buttons | Yes — button dimensions scale. |
| Spacing / margins | Yes — layout spacing adjusts. |
| Mod card sizes | Yes — card width and height scale. |
| Status bar | Yes — height and font size scale. |
| Title bar | Yes — height and button sizes scale. |
| Dialog sizes | Yes — minimum sizes adjust. |
| Border radius | No — uses the pixel value from settings (0–20px). |
| Custom background | No — the background image/video fills the window at any scale. |
| Mod icons | Partially — icons are loaded at a fixed resolution and may appear softer at high DPI. |

---

## Manual Scaling

G3M also provides a **UI Scale** slider or spin box in Settings → Appearance that allows you to override the system DPI scaling:

- **Minimum**: 80% (compact layout).
- **Maximum**: 200% (extra large).
- **Default**: 100% (follows system DPI).

When set:

1. The new scale factor is applied to the entire UI.
2. All widgets, fonts, and layouts recalculate their sizes.
3. The change takes effect immediately (no restart needed).
4. The value is stored in `settings.json` and persists across sessions.

---

## High-DPI Displays

On high-DPI displays (Retina on macOS, HiDPI on Linux, 4K monitors on Windows):

- Qt's built-in high-DPI support is enabled.
- Fonts and vector graphics render sharply.
- Raster images (mod icons, screenshots) may appear slightly soft if they are low-resolution originals. G3M displays them at their native resolution — it does not upscale them artificially.

### macOS Retina

On macOS, Qt automatically uses @2x rendering. The window and all widgets render at the display's native resolution, appearing sharp.

### Windows

On Windows, G3M respects the "Scale and layout" setting in Display Settings. If you set 150%, G3M scales to 150%.

### Linux

On Linux, G3M respects the `QT_SCALE_FACTOR` environment variable if set. Otherwise, it follows the desktop environment's scaling settings.

---

## Window Size

The default window size is approximately 1000×700 pixels (before scaling). The window is resizable:

- **Minimum size**: Approximately 800×600 pixels (before scaling).
- **Maximum size**: No upper limit — the window can be maximized or made fullscreen.

### Fullscreen Mode

G3M supports fullscreen mode, toggleable from Settings → General → **Fullscreen** checkbox or via the maximize button. In fullscreen:

- The title bar is still visible (it's a custom title bar, not the OS one).
- The content area fills the entire screen.
- The border radius is set to 0 (square corners) to avoid visual artifacts at screen edges.

---

## Font Scaling

The custom font (or default `main.ttf`) is loaded at a base size and then scaled by the DPI factor. If you set a custom font that looks too large or small, adjusting the UI Scale setting can compensate.

Language-specific fonts (e.g., CJK fonts for Chinese) are loaded at the same base size and scale identically.

---

## Performance Considerations

Higher DPI/scale values mean larger pixel buffers for rendering. On older GPUs or integrated graphics:

- Scaling above 150% may cause minor performance degradation.
- Disabling animations helps on slower systems at high DPI.
- Background video playback at high resolution may consume more resources.
