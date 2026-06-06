# Theme Colors

G3M uses seven core color channels. Together they control almost everything the player sees, so this is the fastest way to change the app's mood.

---

## The Seven Channels

| Channel | Setting Key | Default | Typical Use |
| --- | --- | --- | --- |
| Background | `custom_background_color` | `#282828` | Main surfaces behind panels and content |
| Elements | `custom_elements_color` | `#222222` | Buttons, inputs, cards, controls |
| Border | `custom_border_color` | `#039d5b` | Borders, dividers, outlines |
| Hover | `custom_hover_color` | `#616b78` | Hover state feedback |
| Select | `custom_select_color` | `#ecedef` | Active and selected UI state |
| Main Text | `custom_main_text_color` | `#e8e9eb` | Primary readable text |
| Secondary Text | `custom_secondary_text_color` | `#6de985` | Hints, softer labels, secondary details |

---

## Good Practical Rule

If you want a theme that still feels readable:

- keep `Main Text` high-contrast
- keep `Elements` darker or calmer than `Select`
- use `Border` and `Secondary Text` as accents, not as the main reading color

---

## How Changes Apply

When you pick a color, G3M rewrites the active Qt stylesheet and updates the UI immediately. These values are stored as hex strings in settings.

The background channel is intentionally translucent in several surfaces so a custom background image or video can still show through.

---

## Resetting

If `Show reset buttons` is enabled, each color field gets its own reset control. You can also get back to a cleaner baseline by importing a simpler theme package or clearing your custom color values.
