# DELTARUNE — Runtime Code Reference

This section documents how DELTARUNE is structured in its shipped form, as a player or modder actually encounters it in:

`C:\Program Files (x86)\Steam\steamapps\common\DELTARUNE`

The intended workflow is the runtime one:
- each chapter is a separate shipped game payload
- the launcher is a separate shipped payload
- code, objects, rooms, strings, sprites, sounds, and save logic are inspected from the compiled game data through UndertaleModTool

This wiki may reference decompiled script, object, and room names because that is what UndertaleModTool exposes from `data.win` and the chapter payloads. It does not assume access to original source projects.

DELTARUNE contains five shipped targets:

| Runtime target | Purpose | Scale |
|---|---|---|
| `CHAPTER_1` | Chapter 1 game payload | 306 scripts, 353 objects, 147 rooms |
| `CHAPTER_2` | Chapter 2 game payload | 777 scripts, 1328 objects, 278 rooms |
| `CHAPTER_3` | Chapter 3 game payload | 974 scripts, 1732 objects, 246 rooms |
| `CHAPTER_4` | Chapter 4 game payload | 955 scripts, 1575 objects, 327 rooms |
| `CHAPTER_SELECT` | Shared launcher / chapter selector | 56 scripts, 18 objects, 3 rooms |

---

## Runtime Layout

For players and modders, the important mental model is:

1. `CHAPTER_SELECT` is the front-end launcher.
2. It reads shared config and save metadata.
3. It transfers control to the chapter-specific runtime.
4. Each chapter then runs its own codebase, rooms, battle logic, save/load logic, and localization helpers.

On Windows, chapter switching uses `game_change()` and `-game data.win ...` style launch arguments. Launcher logic, save metadata, and chapter runtime logic therefore live in separate payloads.

---

## What Changes Between Builds

The current wiki is not just about Chapter 1 and Chapter 2.

The runtime data shows that Chapters 3 and 4 are not small extensions of Chapter 2. They expand the shipped codebase with major new systems:

- Chapter 3 adds the board-game overworld layer (`scr_board_*`, many `obj_board_*` objects)
- Chapter 3 adds a full rhythm-game stack (`scr_rhythmgame_*`, `obj_rhythmgame*`)
- Chapter 3 expands Tenna-, TV-, and game-show-specific orchestration heavily
- Chapter 4 keeps the rhythm stack and shifts major content into church / prophecy / Gerson / bell / piano / climb systems
- Chapter 4 adds further spell, item, room, and event-specific branches rather than reusing Chapter 2 unchanged
- `CHAPTER_SELECT` remains a lightweight launcher and metadata UI, not a gameplay chapter

---

## Localization Reality

The shipped runtime does not use one single localization strategy everywhere.

| Target | Runtime behavior |
|---|---|
| `CHAPTER_1` | Has `lang_en.json` and `lang_ja.json`; many scripts directly request localized strings |
| `CHAPTER_2` | Uses inline English plus localized lookup through `stringsetloc()`; ships `lang_ja.json` |
| `CHAPTER_3` | Same general model as Chapter 2, with stronger missing-string diagnostics |
| `CHAPTER_4` | Same general model as Chapter 3 |
| `CHAPTER_SELECT` | Does not use the chapter string-map system; most launcher text is hardcoded behind `global.lang` checks |

---

## Save / Config Reality

Save handling is chapter-specific at runtime.

- Chapter 1 writes `filech1_<slot>`
- Chapter 2 writes `filech2_<slot>`
- Chapter 3 writes `filech3_<slot>`
- Chapter 4 writes `filech4_<slot>`
- shared lightweight metadata and launcher-visible settings are coordinated through INI/config files such as `dr.ini` and `true_config.ini`

Save logic belongs to each numbered chapter payload. There is no single cross-chapter save script shared by all targets.

---

## Reading This Wiki

The pages below are written for two audiences at once:

- players who want to understand how the game actually works internally
- modders who need to know where data lives, how systems interact, and where chapter-specific behavior diverges

Whenever possible, pages should describe:

- what the player sees
- which runtime scripts / objects implement it
- which chapter payload owns that behavior
- what changed in later chapters

## Pages

- [Global Variables](global-variables.md)
- [Battle System](battle-system.md)
- [Damage System](damage-system.md)
- [Spells & Abilities](spells-abilities.md)
- [Items & Equipment](items-equipment.md)
- [Save & Load System](save-load-system.md)
- [Dialogue System](dialogue-system.md)
- [Cutscene System](cutscene-system.md)
- [Funnytext System](funnytext-system.md)
- [Overworld Movement](overworld.md)
- [Monster Runtime](monster-runtime.md)
- [Board System](board-system.md)
- [Rhythm System](rhythm-system.md)
- [Chapter Differences](chapter-differences.md)
- [CHAPTER_SELECT Launcher](chapter-select.md)
- [Localization System](localization.md)
