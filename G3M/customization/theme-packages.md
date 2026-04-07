# Theme Packages

G3M supports exporting and importing complete theme configurations as `.g3mtheme.zip` archives. This makes it easy to share your visual setup with others.

---

## Exporting a Theme

1. Go to Settings → Appearance.
2. Click **Export Theme**.
3. Choose a destination and file name.
4. G3M creates a `.g3mtheme.zip` archive.

### What Is Exported

The archive contains:

- **`g3m_theme.json`** — A JSON manifest with:
  - `theme_config_version`: Schema version (currently 1).
  - All seven color values.
  - `background_disabled` flag.
  - `disable_animations` flag.
  - `disable_startup_sound` flag.
  - `custom_border_radius` value.
  - References to included media files.
- **Media files** (if present):
  - Custom background image/video.
  - Custom logo image.
  - Custom font file.
  - Custom startup sound.
  - Custom background music.

Only files that exist at the time of export are included.

---

## Importing a Theme

1. Go to Settings → Appearance.
2. Click **Import Theme**.
3. Select a `.g3mtheme.zip` file.
4. G3M extracts and applies:
   - All color values are set immediately.
   - Media files are copied to the data folder.
   - Flags (background disabled, animations, etc.) are applied.
   - The border radius is set.
5. A restart may be required for font changes.

### Theme Config Discovery

When importing, G3M looks for the theme manifest file by checking these names in order: `g3m_theme.json`, `theme_config.json`, `deltahub_theme.json`, `theme.json`. The first one found is used.

### Compatibility

If the imported theme uses color keys from an older version (legacy key names), they are automatically migrated to current key names during import.

---

## Theme File Format

The `.g3mtheme.zip` is a standard ZIP archive. Inside:

```
g3m_theme.json
custom_background.png    (optional)
custom_logo.png          (optional)
custom_font.ttf          (optional)
custom_startup_sound.mp3 (optional)
custom_background_music.mp3 (optional)
```

The JSON manifest example:

```json
{
  "theme_config_version": 1,
  "custom_background_color": "#1a1a2e",
  "custom_elements_color": "#16213e",
  "custom_border_color": "#0f3460",
  "custom_hover_color": "#1a4080",
  "custom_select_color": "#2560a0",
  "custom_main_text_color": "#e0e0ff",
  "custom_secondary_text_color": "#8888bb",
  "custom_border_radius": 10,
  "background_disabled": false,
  "disable_animations": false,
  "disable_startup_sound": false
}
```
