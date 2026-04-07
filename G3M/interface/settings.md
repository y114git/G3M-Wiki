# Settings

The **Settings** tab is divided into sub-tabs (sections). Each section groups related configuration options.

---

## General

| Setting | Description |
| --- | --- |
| **Language** | Select the interface language. Options: English, Español (Spanish), Русский (Russian), 简体中文 (Chinese Simplified), 繁體中文 (Chinese Traditional). Changing language requires a restart. |
| **Check for updates** | Button that manually checks for a new G3M version. If an update is available, a dialog appears with release notes and an Install / Skip choice. |
| **Enable beta updates** | Checkbox. When enabled, G3M also checks for pre-release (beta) versions during update checks. |
| **UI Scale** | Spin box to adjust the interface scale. Affects all widget sizes, fonts, padding, and spacing proportionally. |
| **Fullscreen** | Checkbox. Toggles fullscreen mode (maximizes the window to fill the screen). |
| **About** | Opens the About dialog showing version, author (Y114), links (Discord, Telegram, GitHub, GameBanana), changelog button, and a copyright notice. |
| **Changelog** | Opens the Changelog dialog showing recent version history and changes. |
| **Hide Mods Browser tab** | Checkbox. Hides the Mods Browser tab from the tab bar. |
| **Hide Library tab** | Checkbox. Hides the Library tab from the tab bar. |
| **Hide Library filters** | Checkbox. Hides the search/filter bar in the Library tab. |
| **Show reset buttons** | Checkbox. Shows additional "Reset" buttons next to certain settings (e.g., color pickers) to restore defaults. |

---

## Game

The Game section lets you configure game paths and launch behavior for each supported game.

### Per-Game Settings

For each game (DELTARUNE, DELTARUNE DEMO, UNDERTALE, UNDERTALE Yellow, Pizza Tower, Sugary Spire, and any custom games):

| Setting | Description |
| --- | --- |
| **Game folder path** | Button to open a folder picker. Select the folder where the game is installed. G3M validates the folder by looking for the expected executable. |
| **Custom executable** | Toggle + path field. When enabled, G3M launches this specific executable instead of the auto-detected one. |
| **Full Install checkbox** | (Only for games that support it: DELTARUNE DEMO, UNDERTALE Yellow, Sugary Spire.) Download and install the game's base files from scratch. |

### Launch Options

| Setting | Description |
| --- | --- |
| **Launch via Steam** | Checkbox. When enabled, G3M launches the game through Steam using the `steam://rungameid/<app_id>` URL. This ensures Steam overlay and achievements work. Available only for games with a Steam App ID. |
| **Use PortProton** | Checkbox (Linux only). Launches the game using PortProton instead of native execution. Requires a PortProton installation path. |
| **PortProton path** | Text input for the path to PortProton (Linux only). |
| **Direct Launch chapter** | For DELTARUNE in Chapter Mode, you can set which specific chapter to launch directly into. Double-clicking a chapter tab in the Library sets it. This bypasses the game's title screen. |
| **Skip patching warnings** | Checkbox. When enabled, G3M skips the confirmation dialog that normally appears before applying patches. Useful for experienced users. |

### Game Manager

A **Game Manager** button opens the Game Manager dialog where you can:

- Reorder games by dragging them up/down.
- Toggle game visibility (hide games you don't use from dropdowns).
- Add custom games.
- Remove custom games.

See [Game Manager](../games/game-manager.md) for full details.

---

## Appearance

The Appearance section controls the visual look of G3M.

### Theme Colors

Seven customizable color values (hex format like `#RRGGBB`):

| Color | Controls |
| --- | --- |
| **Background** | The frame background color. Applied with partial transparency (alpha ~150). |
| **Elements** | Buttons, input fields, and interactive elements. |
| **Border** | Borders around panels, cards, and inputs. |
| **Hover** | The color of elements when hovered. |
| **Select** | The color of selected/active elements. |
| **Main Text** | Primary text color across the entire interface. |
| **Secondary Text** | Secondary/version text, less prominent labels. |

Each color has a color picker button and an optional reset button (if "Show reset buttons" is enabled). Clicking the color picker opens the system color dialog. After picking a color, it is applied immediately.

Default colors:

| Color | Default Hex |
| --- | --- |
| Background | `#282828` |
| Elements | `#3d3d3d` |
| Border | `#555555` |
| Hover | `#4a4a4a` |
| Select | `#5a5a5a` |
| Main Text | `#ffffff` |
| Secondary Text | `#aaaaaa` |

### Background Image / Video

| Setting | Description |
| --- | --- |
| **Custom Background** | Button to select a custom background image or video. Supported formats: `.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.ico`, `.webp`, `.mp4`, `.webm`, `.avi`, `.mkv`, `.mov`, `.m4v`, `.3gp`, `.mpg`, `.mpeg`, `.flv`, `.wmv`. Video backgrounds loop automatically. |
| **Disable background** | Checkbox. Disables the background entirely, leaving a solid-color backdrop. |

The background file is copied to the user data folder as `custom_background.<ext>`.

### Custom Logo

Select a custom logo image to replace the G3M logo in the title bar. Supported formats: `.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.ico`, `.webp`.

The file is copied to the data folder as `custom_logo.<ext>`.

### Custom Font

Select a custom `.ttf` or `.otf` font file. The font is applied to the entire interface. Copied as `custom_font.<ext>`.

### Border Radius

A spin box to set the corner radius (in pixels) for windows and panels. Default: 7. Range: 0 to 20.

### Startup Sound

| Setting | Description |
| --- | --- |
| **Custom Startup Sound** | Select a custom audio file to play when G3M opens. Supported formats: `.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, `.aac`. If a file is already set, the button changes to "Remove startup sound". |
| **Disable startup sound** | Checkbox. Disables the startup sound completely. |

### Background Music

| Setting | Description |
| --- | --- |
| **Custom Background Music** | Select a custom audio file that plays in a loop while G3M is open. Supported formats: `.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, `.aac`. If a file is already set, the button changes to "Remove background music". |
| **Pause when unfocused** | Checkbox. Pauses background music when G3M is not the focused window. Resumes when focused again. |

### Disable Animations

Checkbox. Disables all UI animations (transitions, fades, color animations). Useful on low-performance systems.

### Theme Import / Export

| Action | Description |
| --- | --- |
| **Export Theme** | Saves all theme settings (colors, background, font, logo, sounds, radius, flags) into a `.g3mtheme.zip` archive. |
| **Import Theme** | Loads a `.g3mtheme.zip` archive. Restores all colors, copies media files, and applies the theme immediately. A restart is required for some changes (fonts). |

The theme file is a `.zip` containing a `g3m_theme.json` manifest (schema version 1) and any media files (background, logo, font, startup sound, background music).

---

## Library (Settings Sub-Tab)

| Setting | Description |
| --- | --- |
| **Merge Properties** | Checkbox. When enabled, mod patches merge game object properties instead of replacing them entirely. |
| **Merge Code** | Checkbox. When enabled, mod patches merge game code blocks instead of replacing them. |
| **Chapter Mode** | (DELTARUNE only.) Toggle between Chapter Mode and Normal Mode. In Chapter Mode, each chapter has its own mod selection. In Normal Mode, one mod applies to all chapters. |

---

## Mods Browser (Settings Sub-Tab)

Settings specific to the Mods Browser tab:

| Setting | Description |
| --- | --- |
| **Show NSFW** | Checkbox. When unchecked, NSFW mods are hidden from the browser. Same as the filter in the Mods Browser. |

---

## Plugins (Settings Sub-Tab)

Shows all available and installed plugins. See [Plugins](../features/plugins.md) for details.

---

## Downloads (Settings Sub-Tab)

Settings for the Downloads system:

| Setting | Description |
| --- | --- |
| **No auto-use** | Checkbox. When enabled, downloaded mods are not automatically installed into the library. They stay in the Downloads panel as "Ready" until you manually use them. |
| **Delete after use** | Checkbox. When enabled, the downloaded archive file is deleted after the mod is successfully installed into the library. |
| **Save local imports** | Checkbox. When enabled, locally imported mods (via file picker or drag & drop) are also saved as download records. |
| **Downloads panel** | Shows the downloads queue and history. See [Downloads](../features/downloads.md). |

---

## Analytics

| Setting | Description |
| --- | --- |
| **Anonymous analytics opt-in** | Checkbox. When enabled, G3M sends anonymous usage statistics (launch count, mod installs, game played, language, platform, etc.) to help the developer understand how the app is used. No personal data is collected. |
