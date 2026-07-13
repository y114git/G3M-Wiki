# Runtime Architecture

Build `24122389` is six independent GameMaker payloads: Chapter Select and five
numbered chapters. They share conventions and helpers, not one live object or
global-variable space.

## Windows Process Layout

The install root contains `DELTARUNE.exe` and the launcher's `data.win`.
`chapter1_windows` through `chapter5_windows` each contain another `data.win`
and runner configuration. Chapter Select calls `game_change()` with a chapter
directory and `-game data.win` plus handoff parameters. The selected payload
then performs its own initialization.

## Handoff Sequence

1. The launcher initializes config, language, input, and metadata.
2. It derives the visible state from ordinary and completed saves.
3. The user selects one of the five available chapters.
4. The launcher emits `launcher`, `switch_<id>`, and `returning_<value>`.
5. `game_change()` opens the platform-specific chapter payload.
6. The chapter parses those tokens, establishes its own globals, and enters its
   chapter startup, device-menu, or return flow.

A numbered payload launched cold still has a parser whose constructor defaults
`is_launcher` to true. Consequently, parameter presence alone is not a safe test
for reproducing every launcher state; the parsed return and platform data also
matter.

## Ownership Boundaries

| Concern | Owner |
| --- | --- |
| Chapter choice and transition | Chapter Select |
| Shared display and language configuration | Launcher plus per-chapter init |
| Primary and completion file visibility | Launcher and device menus |
| Save serialization and older-file conversion | Numbered chapter |
| Gameplay rooms, objects, and systems | Numbered chapter |
| Platform file backend | `ossafe_*` wrapper layer |

Chapter 5 follows the same boundary. It has its own startup parser, save/load
pair, Chapters 1-to-4 import helpers, localization initializer, and content
controllers. Its much larger code inventory does not make it an extension loaded
into Chapter 4's runtime.

## Configuration Layers

`true_config.ini` is shared behavioral configuration, while `dr.ini` is
launcher-facing metadata and `filech*` stores chapter state. The installed
`options.ini` files configure the GameMaker runner. These layers should not be
treated as interchangeable or edited with one serializer.

See [CHAPTER_SELECT](chapter-select.md), [Save and Load](save-load-system.md),
[Localization](localization.md), and
[Platform Differences](platform-differences.md).
