# Settings

The Settings view is split into several sections and also mirrors some controls
that appear in the main window.

---

## Where to find it

1. Open G3M.
2. Open the **Settings** tab or settings view from the main interface.
3. Use the visible sections for general settings, game settings, appearance,
   library/browser options, downloads, tools, and plugin-provided settings.

Most settings are saved immediately or when the control changes. Shared settings
are stored on Windows in:

`%LOCALAPPDATA%\G3M\settings\settings.json`

---

## General

Current shared settings include:

- language
- update check button
- `beta_updates_enabled`
- UI scale
- fullscreen
- hide mods browser tab
- hide library tab
- hide library filters
- show reset buttons
- analytics opt-in
- disable Discord Rich Presence

Available bundled languages are currently:

- English
- Russian
- Spanish
- Korean
- Japanese
- Chinese Simplified
- Chinese Traditional

---

## Game Settings

Per-game settings are driven by the selected runtime game entry and include:

- game folder path
- custom executable override
- optional Steam launch
- PortProton options on Linux
- optional custom Wine path on Linux
- optional custom PortProton path on Linux
- visibility of the Full Install checkbox when the game supports it

The game manager dialog is also launched from this area.

Typical setup:

1. Select the game in the game selector.
2. Open **Settings**.
3. Set the game folder path.
4. Optionally choose a custom executable if G3M should launch a different
   executable inside that folder.
5. On Linux, decide whether Windows `.exe` launches should use Wine or
   PortProton.

If a Linux target executable is native and does not end in `.exe`, G3M launches
it directly instead of adding Wine or PortProton.

For Windows executables on Linux, G3M now resolves launchers in this order:

1. custom Wine path
2. `wine`
3. `wine64`

If G3M cannot find a usable launcher, it now reports a more specific error
instead of only surfacing a raw `errno 2`.

---

## Theme and Appearance

The current theme color keys are:

- `background`
- `elements`
- `border`
- `hover`
- `select`
- `main_text`
- `secondary_text`

Other appearance settings include:

- custom background path
- background disabled flag
- custom border radius
- disable animations
- custom font, logo, and theme package actions
- custom startup sound and background music
- pause background music when unfocused

The default border radius in settings is `7`.

Custom files selected here are copied to the G3M data folder using fixed names,
for example:

- `%LOCALAPPDATA%\G3M\custom_background.<ext>`
- `%LOCALAPPDATA%\G3M\custom_logo.<ext>`
- `%LOCALAPPDATA%\G3M\custom_font.<ext>`
- `%LOCALAPPDATA%\G3M\custom_startup_sound.<ext>`
- `%LOCALAPPDATA%\G3M\custom_background_music.<ext>`

---

## Library and Browser Options

Profile-aware and library-facing settings include:

- merge properties
- merge code
- chapter mode
- show NSFW in the browser
- blocklist manager

For DELTARUNE, chapter mode and direct launch behavior are profile-specific.

---

## Downloads and Tools

The Downloads section currently exposes:

- `downloads_no_auto_use`
- `downloads_delete_after_use`
- `downloads_save_local_imports`

The settings view also includes a **Clear G3MTool Cache** action that removes
cached G3MTool analysis files from:

`%LOCALAPPDATA%\G3M\cache\G3MTool\`

Use it when patch analysis seems stale or when you simply want to free cache
space. It does not delete installed mods or saved game versions.
