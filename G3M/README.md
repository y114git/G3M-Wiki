# G3M

G3M is a desktop mod manager for GameMaker games. In the current codebase it ships as a Python 3.14+ desktop application built with PyQt6 and focuses on mod browsing, library management, patching workflows, profiles, plugins, customization, and launch automation.

Current code version: **3.1.2**  
License: **GPL-3.0**  
UI framework: **PyQt6 6.7.1**

## Supported built-in games

- **DELTARUNE**
- **DELTARUNEdemo**
- **UNDERTALE**
- **UNDERTALE Yellow**
- **Pizza Tower**
- **Sugary Spire**
- **FRICKBEARS3**

G3M also supports custom single-tab games added through the in-app Game Manager.

## What G3M does

- Browses supported GameBanana sections and installs from GameBanana, URLs, local archives, raw folders, and one-click protocol links.
- Manages installed mods, profiles, mod versions, game versions, blocklist rules, downloads, and plugin state in the local data directory.
- Applies mods with built-in support for `.g3mpatch`, `.xdelta` / `.vcdiff`, `.csx`, raw data files, and extra-file overrides.
- Provides built-in tools for patch create/apply/merge/info/diff workflows through the Modding Tools dialog.
- Loads bundled and local plugins, validates API compatibility, and exposes plugin hooks, settings views, and main views.
- Supports theme import/export, external language files, startup sound and background customization, and bundled theme packages.
- Launches games directly, through Steam where configured, or through desktop shortcuts with captured launch state.

## Quick links

| Resource | URL |
| --- | --- |
| Discord | [discord.gg/2MFdvFfD9a](https://discord.gg/2MFdvFfD9a) |
| Telegram | [t.me/y_maintg](https://t.me/y_maintg) |
| GitHub | [github.com/y114git/G3M](https://github.com/y114git/G3M) |

## Wiki structure

- [**Getting Started**](getting-started.md) - install, first launch, data folder, and initial game setup.
- [**Interface**](interface/README.md) - tabs, panels, dialogs, and window behavior.
- [**Games**](games/README.md) - built-in games, custom games, detection, launch, Steam, and full install.
- [**Mods**](mods/README.md) - formats, importing, creating, editing, versions, and conversion flows.
- [**Features**](features/README.md) - profiles, downloads, shortcuts, plugins, updates, chat, and other app features.
- [**Customization**](customization/README.md) - themes, colors, audio, fonts, logo, background, and animations.
- [**Advanced**](advanced/README.md) - architecture, data layout, localization, networking, patching, and troubleshooting.
