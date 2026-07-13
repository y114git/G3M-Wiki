# CHAPTER_SELECT Launcher

`CHAPTER_SELECT` is a separate GameMaker payload. It owns the front end, shared
metadata, language and display setup, and chapter handoff; it does not contain
numbered-chapter gameplay systems.

## Startup Flow

1. `obj_CHAPTER_SELECT` calls `scr_init()` and parses launch parameters.
2. It creates `obj_init_console` on Switch, PS4, or PS5, and `obj_init_pc`
   otherwise.
3. Initialization resolves language, display settings, imported save data, and
   launcher metadata.
4. The controller scans Chapters 1 through 5 for primary and completed saves.
5. It opens the start, continue, next-chapter, or chapter-select screen.
6. A selection fades through `obj_screen_transition` and calls `game_change()`.

The launcher exposes five chapters in this build. Its internal maximum enum is
larger, but the availability loop stops at Chapter 5.

## Important Objects

| Object                  | Purpose                                           |
| ----------------------- | ------------------------------------------------- |
| `obj_CHAPTER_SELECT`    | State machine and chapter handoff                 |
| `obj_init_pc`           | PC language, display, and metadata initialization |
| `obj_init_console`      | Console account and save-data initialization      |
| `obj_screen_start`      | Start, continue, and import prompts               |
| `obj_screen_select`     | Chapter and slot selection                        |
| `obj_screen_transition` | Delayed handoff transition                        |
| `obj_input`             | Launcher input polling                            |

## Launch Parameters

`scr_init_launch_parameters()` recognizes three tokens:

- `launcher` marks launcher entry;
- `switch_<id>` carries a Switch account identifier, or `-1` elsewhere;
- `returning_<value>` distinguishes an original launcher start from a return.

`get_chapter_switch_parameters()` emits all three tokens. The same parser is
present in every numbered payload, including Chapter 5. See
[Runtime Architecture](runtime-architecture.md) for platform paths.

## Save Visibility and Metadata

The launcher scans `filech<chapter>_0` through `_2` for ordinary saves and
`filech<chapter>_3` through `_5` for completed copies. It uses these results to
choose its initial screen and unlock progression. `dr.ini` stores compact
launcher-facing slot and completion metadata; it is not the chapter save
payload. Launcher conversion also migrates secret-boss state into `[URA]`.

On consoles, `obj_init_console` additionally handles platform save-data import
and account selection. Those shipped branches are established, but this Windows
installation cannot establish console SDK behavior beyond the GML calls.

## Language and Display

`obj_init_pc` defaults from `os_get_language()`, then lets `true_config.ini`
`[LANG] LANG` override it. The same file's `[SCREEN] FULLSCREEN` value controls
the original launcher's display mode. Windowed mode chooses an integer multiple
of 640 by 480 that fits the display.

Launcher text is selected directly with `global.lang`; it does not use the
numbered chapters' JSON string map. Toggling language updates `true_config.ini`,
saves through the OS-safe backend, and restarts the room on PC.

## Modding Boundary

Patch this payload for launcher UI, visibility, import, metadata, or handoff.
Patch the numbered payload for gameplay, chapter initialization, or serialized
state. See [Save and Load](save-load-system.md),
[Localization](localization.md), and
[Platform Differences](platform-differences.md).
