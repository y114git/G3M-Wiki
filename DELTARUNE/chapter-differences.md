# Chapter Differences

This page documents concrete runtime differences between the shipped DELTARUNE targets: `CHAPTER_1`, `CHAPTER_2`, `CHAPTER_3`, `CHAPTER_4`, and `CHAPTER_SELECT`.

It is written from the perspective of the shipped game data that modders inspect through UndertaleModTool, not from original editor projects.

---

## High-Level Scale

| Target | Scripts | Objects | Rooms |
|---|---:|---:|---:|
| Chapter 1 | 306 | 353 | 147 |
| Chapter 2 | 777 | 1328 | 278 |
| Chapter 3 | 974 | 1732 | 246 |
| Chapter 4 | 955 | 1575 | 327 |
| Chapter Select | 56 | 18 | 3 |

The jump from Chapter 1 to Chapter 2 is the first major systemic expansion. Chapters 3 and 4 then continue on top of the Chapter 2-era runtime conventions rather than reverting to the Chapter 1 model.

---

## `global.chapter`

| Runtime | `global.chapter` |
|---|---:|
| Chapter 1 | `1` |
| Chapter 2 | `2` |
| Chapter 3 | `3` |
| Chapter 4 | `4` |

Many shared scripts branch directly on this value, especially:

- `scr_gamestart`
- `scr_spellinfo`
- `scr_spell`
- `scr_load`
- item / weapon / armor info scripts

---

## Starting Party Data

The chapter runtimes no longer share one fixed opening-state template.

### Chapter 1

| Character | HP | AT | DF | MAG | Weapon |
|---|---:|---:|---:|---:|---:|
| Kris | 90 | 10 | 2 | 0 | 1 |
| Susie | 110 | 14 | 2 | 1 | 2 |
| Ralsei | 70 | 8 | 2 | 7 | 3 |

Notes:
- `global.char[0] = 1`, `global.char[1] = 0`, `global.char[2] = 0`
- Ralsei begins auto-controlled through `global.charauto[2] = 1`

### Chapter 2

| Character | HP | AT | DF | MAG | Weapon | Armor 1 | Armor 2 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Kris | 120 | 12 | 2 | 0 | 1 | 1 | 1 |
| Susie | 140 | 16 | 2 | 1 | 2 | 1 | 1 |
| Ralsei | 100 | 10 | 2 | 9 | 3 | 1 | 4 |
| Noelle | 90 | 3 | 1 | 11 | 12 | 14 | 22 |

### Chapter 3

| Character | HP | AT | DF | MAG | Weapon | Armor 1 | Armor 2 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Kris | 160 | 14 | 2 | 0 | 16 | 1 | 10 |
| Susie | 190 | 18 | 2 | 2 | 17 | 1 | 10 |
| Ralsei | 140 | 12 | 2 | 11 | 18 | 1 | 10 |

Important:
- Chapter 3 `scr_gamestart` still initializes Noelle data structures, but the opening Chapter 3 party setup is built around Kris / Susie / Ralsei
- Susie gets spell 11 in the initial loadout in Chapter 3

### Chapter 4

| Character | HP | AT | DF | MAG | Weapon | Armor 1 | Armor 2 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Kris | 200 | 17 | 2 | 0 | 23 | 25 | 10 |
| Susie | 230 | 22 | 2 | 3 | 24 | 25 | 10 |
| Ralsei | 180 | 15 | 2 | 14 | 25 | 25 | 10 |

The Chapter 4 runtime keeps the same expanded stat-array infrastructure as Chapters 2 and 3, but applies a different opening equipment baseline again. Noelle data is still initialized in the later runtime structures, even though the opening Chapter 4 party setup centers on Kris / Susie / Ralsei.

---

## Array / Inventory Expansion

### Chapter 1

- character-stat arrays are initialized for 4 indices
- `global.item`, `global.keyitem`, `global.weapon`, `global.armor` use the original smaller layout
- no `global.pocketitem`

### Chapters 2, 3, and 4

- character/stat arrays are initialized for 20 indices
- `global.pocketitem[0..71]` exists
- `global.weapon` and `global.armor` are expanded to 48 slots
- element data is stored in:
  - `global.itemelement[i][q]`
  - `global.itemelementamount[i][q]`

This is one of the biggest systemic breakpoints between Chapter 1 and later runtimes.

---

## Battle / Spell Progression

### Core spell IDs

Shared player-facing spell IDs remain centered on:

- `1` Rude Sword
- `2` Heal Prayer
- `3` Pacify
- `4` Rude Buster
- `5` Red Buster
- `6` Dual Heal
- `7` ACT
- `8` SleepMist
- `9` IceShock
- `10` SnowGrave
- `11` late-game heal spell slot used differently by later chapters

### Chapter 1

- only the early spell set is present in practice
- no Noelle spell ownership
- no later item-spell expansion

### Chapter 2

- adds Noelle battle support
- adds spells `8`, `9`, `10`, `11`
- `scr_spellinfo` names spell 11 as `UltimatHeal`
- item-use spell codes go through `200..233`

### Chapter 3

- keeps the Chapter 2 spell core
- `scr_spellinfo` renames spell 11 to `UltraHeal`
- item-use spell handling expands through `239`

### Chapter 4

- keeps the Chapter 3-era spell core
- spell 11 is now more conditional in `scr_spellinfo`, with multiple names such as `OKHeal`, `Heal`, and `BetterHeal` depending on runtime state
- item-use spell handling expands further through `263`

This means the old documentation that effectively stops at Chapter 2 is no longer sufficient for modding battle behavior in Chapters 3 and 4.

---

## Damage System Evolution

### Chapter 1

- uses the older flat defense model
- direct `scr_damage` logic is much simpler
- no later element-resistance layer

### Chapters 2, 3, and 4

- use `scr_damage_calculation`
- apply `scr_element_damage_reduction`
- preserve the expanded armor-element system

From a runtime perspective, Chapter 2 establishes the defensive model still used by Chapters 3 and 4.

---

## Localization Evolution

### Chapter 1

- ships both `lang_en.json` and `lang_ja.json`
- many scripts directly call `scr_84_get_lang_string()`

### Chapter 2

- introduces broad `stringsetloc(english_fallback, key)` usage
- ships `lang_ja.json`
- missing strings return `"--missing-string--"`

### Chapter 3

- same general `stringsetloc` model
- missing string lookups also emit `show_debug_message(...)`

### Chapter 4

- same Chapter 3-era model
- continues using inline English fallback plus Japanese lookup

### Chapter Select

- not part of the chapter string-map pipeline
- launcher text is mostly hardcoded behind `global.lang` checks

---

## Save File Naming

The older documentation that implies one universal Chapter 1 save naming scheme is incomplete.

| Runtime | Main save file pattern |
|---|---|
| Chapter 1 | `filech1_<slot>` |
| Chapter 2 | `filech2_<slot>` |
| Chapter 3 | `filech3_<slot>` |
| Chapter 4 | `filech4_<slot>` |

Chapter 2 already generalizes writing with:

`"filech" + string(global.chapter) + "_" + string(arg0)`

and Chapters 3 and 4 keep that generalized save-write form.

---

## Save Payload Structure

### Chapter 1

- smaller inventory structures
- no `pocketitem`
- older save layout

### Chapters 2, 3, and 4

- save payload includes `pocketitem`
- save payload includes armor-element data
- the later chapter save format is larger and materially different from Chapter 1

Chapters 3 and 4 still write:
- stats
- equipment
- per-slot item modifiers
- spells
- inventory
- pocket inventory
- flags
- room id
- playtime

but their runtime assumptions on room ids and valid room resolution are more modern than Chapter 1.

---

## Runtime-Specific New Systems

### Chapter 2

Primary new direction:
- Noelle support
- Weird Route hooks
- element-resistant battle layer
- much larger cutscene / content framework

### Chapter 3

Major runtime additions:
- board-game overworld framework: many `scr_board_*` scripts and `obj_board_*` objects
- rhythm-game framework: `scr_rhythmgame_*`, `obj_rhythmgame*`
- Tenna / TV / show-specific orchestration
- further cutscene command expansion through many `c_*` scripts

### Chapter 4

Major runtime additions:
- large church / prophecy / bell / piano / climb content stack
- Gerson-heavy battle and event-specific systems
- retained rhythm-game stack with additional save/load helpers
- more item-spell branches and more conditional spell naming / behavior

---

## `CHAPTER_SELECT` Is Not a Gameplay Chapter

`CHAPTER_SELECT` differs structurally from all numbered chapters:

- no `scr_gamestart`, `scr_load`, `scr_saveprocess`, `scr_spell`, `scr_damage`
- no battle controller stack
- no overworld gameplay stack
- no chapter string-map runtime

Instead it focuses on:

- save slot display
- chapter visibility
- config handling
- language toggle
- launching the correct chapter payload with runtime parameters

See [CHAPTER_SELECT Launcher](chapter-select.md) for the dedicated breakdown.
