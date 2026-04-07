# Fonts & Logo

G3M lets you replace the application font and the title bar logo.

---

## Custom Font

### Setting a Custom Font

1. Go to Settings → Appearance.
2. Click the **Custom Font** button.
3. Select a `.ttf` or `.otf` font file.
4. The file is copied to the data folder as `custom_font.<ext>`.
5. A restart is required for the font to take effect across the entire UI.

### Supported Formats

`.ttf` (TrueType), `.otf` (OpenType)

### Removing the Font

Click the button again when a font is set. It changes to "Remove custom font". Click it to delete the file and revert to the default font on the next restart.

### Default Font

G3M bundles a default font file (`main.ttf`) used for all text rendering. Language-specific fonts may also be loaded — for example, Chinese language packs include CJK-compatible fonts.

---

## Custom Logo

### Setting a Custom Logo

1. Go to Settings → Appearance.
2. Click the **Custom Logo** button.
3. Select an image file.
4. The file is copied to the data folder as `custom_logo.<ext>`.
5. The logo in the title bar updates immediately.

### Supported Formats

`.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.ico`, `.webp`

### Removing the Logo

Click the button again when a logo is set. It changes to "Remove custom logo". Click it to delete the file and revert to the default G3M logo.

### Logo Behavior

The custom logo replaces the G3M icon in the top-left corner of the title bar. Clicking the logo always opens the About dialog, regardless of whether it is custom or default.

---

## Border Radius

The corner rounding of the main window and panels is controlled by the **Border Radius** setting:

- **Location**: Settings → Appearance → Border Radius spin box.
- **Default**: 7 pixels.
- **Range**: 0 (sharp corners) to 20 (heavily rounded).
- The change takes effect immediately.
- The value is stored as `custom_border_radius` in settings.
