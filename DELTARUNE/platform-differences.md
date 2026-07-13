# Platform Differences

The frozen runtime basis is a Windows Steam installation. Platform branches
below are documented only where shipped GML names an explicit path or API; they
are not claims that console packages were inspected.

## Launcher Handoff

| Platform branch | `game_change()` target                    |
| --------------- | ----------------------------------------- |
| Windows         | `/chapterN_windows` with `-game data.win` |
| macOS           | `chapterN_mac`                            |
| Switch          | `rom:/chapterN_switch/`                   |
| PS4             | `-game /app0/games/chapterN_ps4/game.win` |
| PS5             | `-game /app0/games/chapterN_ps5/game.win` |

These strings confirm intended launcher branches. Only the Windows directories
and payload files were present for direct filesystem inspection.

## Windows Assumptions

The launcher enables borderless fullscreen support and computes windowed size
from integer multiples of 640 by 480. File and INI calls pass relative names to
the OS-safe layer; the GML does not hardcode a Steam user-data directory.
Therefore the physical writable directory is a runner/backend concern, not the
install path implied by the relative filename.

Chapter 5 uniquely ships `execute_program_pipe_x64.dll` and
`shader_replace_simple_x64.dll` in its Windows directory. shipped Chapter 5 code
initializes the shader helper with Direct3D 11 device/context handles. Their
presence is a Chapter 5 Windows dependency and should not be generalized to
Chapters 1 through 4.

## Console Backend

The launcher sets `global.is_console` for Switch, PS4, and PS5. Console startup
uses `obj_init_console`, platform save-data calls, and grouped DS-list save
serialization. Switch additionally carries `switch_<id>` and calls the Switch
desired-language API. Console storage, account, and import behavior therefore
cannot be reproduced by replacing only a Windows pathname.

## macOS Runtime Limits

The launcher contains a macOS chapter-directory branch. No macOS package was
included in the inspected Steam installation, so executable layout, helper
libraries, writable paths, and backend behavior remain unverified.

See [Runtime Architecture](runtime-architecture.md) for the common handoff and
[Save and Load](save-load-system.md) for representation differences.
