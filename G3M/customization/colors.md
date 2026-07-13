# Theme Colors

G3M uses seven core color channels. Together they control almost everything the
player sees, so this is the fastest way to change the app's mood.

---

## The Seven Channels

- **Channel:** Background
  - **Setting Key:** `custom_background_color`
  - **Default:** `#282828`
  - **Typical Use:** Main surfaces behind panels and content

- **Channel:** Elements
  - **Setting Key:** `custom_elements_color`
  - **Default:** `#222222`
  - **Typical Use:** Buttons, inputs, cards, controls

- **Channel:** Border
  - **Setting Key:** `custom_border_color`
  - **Default:** `#039d5b`
  - **Typical Use:** Borders, dividers, outlines

- **Channel:** Hover
  - **Setting Key:** `custom_hover_color`
  - **Default:** `#616b78`
  - **Typical Use:** Hover state feedback

- **Channel:** Select
  - **Setting Key:** `custom_select_color`
  - **Default:** `#ecedef`
  - **Typical Use:** Active and selected UI state

- **Channel:** Main Text
  - **Setting Key:** `custom_main_text_color`
  - **Default:** `#e8e9eb`
  - **Typical Use:** Primary readable text

- **Channel:** Secondary Text
  - **Setting Key:** `custom_secondary_text_color`
  - **Default:** `#6de985`
  - **Typical Use:** Hints, softer labels, secondary details

---

## Good Practical Rule

If you want a theme that still feels readable:

- keep `Main Text` high-contrast
- keep `Elements` darker or calmer than `Select`
- use `Border` and `Secondary Text` as accents, not as the main reading color

---

## How Changes Apply

When you pick a color, G3M rewrites the active Qt stylesheet and updates the UI
immediately. These values are stored as hex strings in settings.

The background channel is intentionally translucent in several surfaces so a
custom background image or video can still show through.

---

## Resetting

If `Show reset buttons` is enabled, each color field gets its own reset control.
You can also get back to a cleaner baseline by importing a simpler theme package
or clearing your custom color values.
