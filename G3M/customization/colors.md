# Theme Colors

G3M's entire interface is colored by seven customizable color channels. Changing any color immediately updates the UI.

---

## Color Channels

| Channel | Setting Key | Default | What It Affects |
| --- | --- | --- | --- |
| **Background** | `custom_background_color` | `#282828` | Frame background (applied with partial transparency, alpha ~150), tooltip backgrounds. |
| **Elements** | `custom_elements_color` | `#3d3d3d` | Buttons, input fields, dropdown backgrounds, card backgrounds, interactive controls. |
| **Border** | `custom_border_color` | `#555555` | Borders around panels, cards, inputs, dialogs, separators. |
| **Hover** | `custom_hover_color` | `#4a4a4a` | Color of elements when the mouse hovers over them. |
| **Select** | `custom_select_color` | `#5a5a5a` | Color of selected/active elements (active tab, selected list item, pressed button). |
| **Main Text** | `custom_main_text_color` | `#ffffff` | All primary text: labels, titles, button text, content text. |
| **Secondary Text** | `custom_secondary_text_color` | `#aaaaaa` | Less prominent text: version numbers, subtitles, hints, descriptions. |

---

## Setting a Color

1. Go to Settings → Appearance.
2. Click the color button next to the channel you want to change.
3. The system color picker dialog opens.
4. Select a color.
5. The UI updates immediately.

Colors are stored as hex strings (e.g., `#FF5500`) in the settings file.

---

## Resetting Colors

If **Show reset buttons** is enabled in Settings → General, a small reset button appears next to each color picker. Clicking it restores the color to its default value.

You can also reset all colors at once by importing the default theme or manually clearing the color values in settings.

---

## How Colors Are Applied

Colors are injected into a Qt stylesheet (QSS) that styles every widget in the application. The stylesheet is regenerated whenever a color changes. Dialogs opened from the main window inherit the theme colors.

The background color is applied with transparency (alpha ~150 for frame backgrounds, alpha ~230 for tooltips) so that a custom background image or video can show through.

---

## Legacy Color Key Migration

If you upgrade from an older version of G3M that used different color key names (e.g., `custom_color_background` instead of `custom_background_color`), the values are automatically migrated to the new key names on first load. The old keys are removed.

Legacy key mappings:

| Old Key | New Key |
| --- | --- |
| `custom_color_background` | `custom_background_color` |
| `custom_color_elements` | `custom_elements_color` |
| `custom_color_border` | `custom_border_color` |
| `custom_color_hover` | `custom_hover_color` |
| `custom_color_select` | `custom_select_color` |
| `custom_color_main_text` | `custom_main_text_color` |
| `custom_color_secondary_text` | `custom_secondary_text_color` |
| `custom_color_button` | `custom_elements_color` |
| `custom_color_button_hover` | `custom_hover_color` |
| `custom_color_button_select` | `custom_select_color` |
| `custom_color_text` | `custom_main_text_color` |
| `custom_color_version_text` | `custom_secondary_text_color` |
