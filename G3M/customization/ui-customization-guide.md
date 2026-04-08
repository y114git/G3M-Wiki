# UI Customization Guide

This step-by-step guide walks you through customizing every visual aspect of G3M.

---

## Quick Theme Setup

### Method 1: Import a Ready-Made Theme

1. Download a `.zip` theme file from the community (Discord, Telegram, etc.).
2. Go to Settings → Appearance.
3. Click **Import Theme**.
4. Select the `.zip` file.
5. Done — all colors, background, font, logo, and audio are applied.

### Method 2: Build Your Own Theme

Follow the sections below to customize each element individually.

---

## Step 1: Choose Your Colors

Go to Settings → Appearance.

### Recommended Approach

1. Start with the **Background** color — this sets the overall mood. Dark tones (e.g., `#1a1a2e`, `#282828`) work well as they let other elements stand out.
2. Set the **Elements** color slightly lighter than the background (e.g., `#2d2d4a`, `#3d3d3d`). This colors buttons, inputs, and cards.
3. Set the **Border** color to a subtle contrasting tone (e.g., `#4a4a6a`, `#555555`). Borders shouldn't be too prominent.
4. Set the **Hover** color between Elements and Select — it should feel like a "slightly brighter" version of Elements.
5. Set the **Select** color brighter still — it indicates active/selected state.
6. Set **Main Text** to a high-contrast color for readability (white `#ffffff` for dark themes, dark `#1a1a1a` for light themes).
7. Set **Secondary Text** to a lower-contrast variant (e.g., `#aaaaaa` for dark themes, `#666666` for light themes).

### Color Harmony Tips

- Use an online color palette generator (like coolors.co) to find harmonious colors.
- Keep text colors high-contrast against the background for readability.
- Test your colors by navigating through all tabs — some combinations look good in Settings but clash in the Library or Mods Browser.
- Use the **Reset** button (if enabled in General settings) to revert individual colors to defaults.

---

## Step 2: Set a Background

1. In Settings → Appearance, click **Custom Background**.
2. Choose an image or video file.
3. The background appears immediately behind the semi-transparent content panels.

### Background Tips

- **Images**: Use high-resolution images (at least 1920×1080). PNG or JPG work well.
- **Videos**: Short looping videos (5–30 seconds) work best as backgrounds. Keep file size reasonable (under 50 MB).
- **Dark images**: Work better with white/light text colors.
- **Bright images**: May need darker or more opaque panel colors to keep text readable.
- If the background is too distracting, increase the background color's opacity by choosing a less transparent color. The panel overlays use the background color at ~60% opacity.

### No Background

If you prefer a solid-color UI:

1. Check **Disable background** in Appearance settings.
2. The window shows only the background color as a flat surface.
3. This gives a cleaner, more minimalist look.

---

## Step 3: Customize the Font

1. In Appearance settings, click **Custom Font**.
2. Select a `.ttf` or `.otf` file.
3. Restart G3M to apply.

### Font Tips

- Monospace fonts give a "terminal" or retro aesthetic.
- Serif fonts give a more formal or classic look.
- Large/decorative fonts may not scale well at small UI sizes.
- Ensure the font supports the characters for your language (especially for CJK, Cyrillic, etc.).

---

## Step 4: Add a Custom Logo

1. In Appearance settings, click **Custom Logo**.
2. Select an image (ideally square, ~64×64 or ~128×128 pixels).
3. The logo replaces the G3M icon in the top-left of the title bar.

### Logo Tips

- Use a transparent PNG for the cleanest look.
- The logo is displayed at a small size, so simple designs with bold shapes work best.
- Avoid very tall or wide logos — they'll be scaled to fit the title bar height.

---

## Step 5: Add Audio (Optional)

### Startup Sound

1. In Appearance settings, click **Select startup sound**.
2. Choose a short audio clip (1–5 seconds recommended).
3. The clip plays on each app launch.

### Background Music

1. Click **Select background music**.
2. Choose an audio file.
3. The music loops continuously while G3M is open.
4. Optionally check **Pause when unfocused** to pause music when you switch to another app.

### Audio Tips

- Keep startup sounds short and not too loud — they play every time you open G3M.
- Background music should be ambient/calm so it doesn't interfere with concentration.
- Use `.mp3` for best compatibility and smaller file sizes.
- Adjust your system volume — G3M doesn't have a built-in volume slider.

---

## Step 6: Adjust Border Radius

1. In Appearance settings, find the **Border Radius** spin box.
2. Set a value from 0 to 20:
   - **0** — Completely square corners (sharp, modern look).
   - **7** (default) — Slightly rounded corners.
   - **15–20** — Very rounded corners (soft, bubbly look).
3. The change applies immediately.

---

## Step 7: Toggle Animations

- Check **Disable animations** for instant transitions and static UI.
- Uncheck it (default) for smooth color transitions and sliding panels.

---

## Step 8: Export Your Theme

Once you're happy with everything:

1. Click **Export Theme**.
2. Save the `.zip` file.
3. Share it with friends or the community!

---

## Example Themes

### Dark Ocean

| Channel | Color |
| --- | --- |
| Background | `#0d1b2a` |
| Elements | `#1b2838` |
| Border | `#2a3f5f` |
| Hover | `#2d4a6f` |
| Select | `#3a6b9f` |
| Main Text | `#e0f0ff` |
| Secondary Text | `#7a9ab5` |

### Warm Sunset

| Channel | Color |
| --- | --- |
| Background | `#2d1b0e` |
| Elements | `#3e2a18` |
| Border | `#5a3d28` |
| Hover | `#6b4a30` |
| Select | `#8b6040` |
| Main Text | `#fff0e0` |
| Secondary Text | `#b5967a` |

### Clean Light

| Channel | Color |
| --- | --- |
| Background | `#f0f0f0` |
| Elements | `#ffffff` |
| Border | `#d0d0d0` |
| Hover | `#e8e8e8` |
| Select | `#d0d8e0` |
| Main Text | `#1a1a1a` |
| Secondary Text | `#666666` |

### DELTARUNE Purple

| Channel | Color |
| --- | --- |
| Background | `#1a0a2e` |
| Elements | `#2d1848` |
| Border | `#4a2870` |
| Hover | `#5a3080` |
| Select | `#7040a0` |
| Main Text | `#e8d0ff` |
| Secondary Text | `#9a80b5` |
