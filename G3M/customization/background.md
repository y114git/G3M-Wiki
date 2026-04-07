# Background

G3M supports custom background images and videos behind the main content area.

---

## Setting a Background

1. Go to Settings → Appearance.
2. Click the **Custom Background** button.
3. Select an image or video file.
4. The file is copied into your user data folder as `custom_background.<ext>`.
5. The background is displayed immediately.

---

## Supported Formats

### Images

`.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.ico`, `.webp`

### Videos

`.mp4`, `.webm`, `.avi`, `.mkv`, `.mov`, `.m4v`, `.3gp`, `.mpg`, `.mpeg`, `.flv`, `.wmv`

Video backgrounds loop automatically. They play silently (no audio from the video file).

---

## Removing a Background

Click the **Custom Background** button again. If a background is currently set, the button label changes to "Remove background". Clicking it removes the file and reverts to the default background.

Alternatively, enable the **Disable background** checkbox to hide the background without deleting the file.

---

## Disable Background

The **Disable background** checkbox in Settings → Appearance hides the background entirely. The window shows a solid-color backdrop using the Background theme color instead.

This is separate from removing the background file — disabling preserves the file so you can re-enable it later.

---

## Default Background

G3M ships with a default background image from the theme assets. If no custom background is set and the background is not disabled, this default image is used.

---

## Transparency

The content panels are drawn with semi-transparent backgrounds (controlled by the Background theme color's alpha value, ~150). This means the background image or video is partially visible behind the UI elements, creating a layered visual effect.
