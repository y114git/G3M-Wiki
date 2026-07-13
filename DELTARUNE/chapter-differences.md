# Chapter Differences

This page documents concrete runtime differences between the six shipped
DELTARUNE targets: `CHAPTER_1` through `CHAPTER_5`, plus `CHAPTER_SELECT`.

Baseline counts describe the resource collections shipped in each target.

---

## High-Level Scale

| Target         | Scripts | Objects | Rooms |
| -------------- | ------: | ------: | ----: |
| Chapter 1      |     692 |     353 |   147 |
| Chapter 2      |   1,645 |   1,328 |   278 |
| Chapter 3      |   2,632 |   1,732 |   246 |
| Chapter 4      |   2,918 |   1,576 |   328 |
| Chapter 5      |   7,308 |   1,733 |   252 |
| Chapter Select |     237 |      17 |     3 |

These are GameMaker resource counts from Steam build `24122389`. Earlier script
counts on this page used a narrower code-name measure rather than the payload's
`Scripts` collection.

The first structural breakpoint is Chapter 1 vs Chapter 2. Chapter 5 keeps the
later data layout, but its content package changes sharply from Chapter 4.

## Resource Inventory

`Code` means all code entries; `Scripts` in the earlier table is G3MTool's
payload collection and is intentionally a different measure.

| Target         |   Code | Objects | Rooms | Sprites |
| -------------- | -----: | ------: | ----: | ------: |
| Chapter 1      |  1,680 |     353 |   147 |   1,093 |
| Chapter 2      |  6,707 |   1,328 |   278 |   3,381 |
| Chapter 3      |  9,258 |   1,732 |   246 |   4,991 |
| Chapter 4      | 12,232 |   1,576 |   328 |   5,882 |
| Chapter 5      | 18,034 |   1,733 |   252 |   8,522 |
| Chapter Select |    283 |      17 |     3 |       8 |

| Target         | Sounds | Shaders | Fonts | Paths |
| -------------- | -----: | ------: | ----: | ----: |
| Chapter 1      |    151 |       0 |    12 |     0 |
| Chapter 2      |    345 |       5 |    13 |    14 |
| Chapter 3      |    516 |      21 |    17 |    31 |
| Chapter 4      |    591 |      41 |    19 |    14 |
| Chapter 5      |    764 |      66 |    16 |    14 |
| Chapter Select |      9 |       0 |    10 |     0 |

All six targets contain zero timelines. Item, spell, enemy-name, and flag
references, but those are reference inventories, not definitions or proof that
content is reachable.

## Adjacent-Chapter Resource Churn

These are exact name-set differences between adjacent numbered chapters.

| Transition    |   Objects +/− | Rooms +/− |   Sprites +/− | Sounds +/− |
| ------------- | ------------: | --------: | ------------: | ---------: |
| Chapter 1 → 2 |   1,093 / 118 |  227 / 96 |   2,503 / 215 |   213 / 19 |
| Chapter 2 → 3 |   1,314 / 910 | 158 / 190 | 2,781 / 1,171 |    180 / 9 |
| Chapter 3 → 4 | 1,047 / 1,203 | 229 / 147 | 3,195 / 2,304 |  215 / 140 |
| Chapter 4 → 5 |   1,120 / 963 | 145 / 221 | 5,798 / 3,158 |  355 / 182 |

---

## `global.chapter`

| Runtime   | `global.chapter` |
| --------- | ---------------: |
| Chapter 1 |              `1` |
| Chapter 2 |              `2` |
| Chapter 3 |              `3` |
| Chapter 4 |              `4` |
| Chapter 5 |              `5` |

Chapter 5 sets this directly in `scr_gamestart` and again in its initializer
handoff.

Many shared scripts branch directly on this value, especially:

- `scr_gamestart`
- `scr_spellinfo`
- `scr_spell`
- `scr_load`
- item / weapon / armor info scripts

---

## Starting Party Data

The chapter runtimes no longer share one fixed opening-state template.

### Chapter 1 starting party

| Character |  HP |  AT |  DF | MAG | Weapon |
| --------- | --: | --: | --: | --: | -----: |
| Kris      |  90 |  10 |   2 |   0 |      1 |
| Susie     | 110 |  14 |   2 |   1 |      2 |
| Ralsei    |  70 |   8 |   2 |   7 |      3 |

Notes:

- `global.char[0] = 1`, `global.char[1] = 0`, `global.char[2] = 0`
- Ralsei begins auto-controlled through `global.charauto[2] = 1`

### Chapter 2

| Character |  HP |  AT |  DF | MAG | Weapon | Armor 1 | Armor 2 |
| --------- | --: | --: | --: | --: | -----: | ------: | ------: |
| Kris      | 120 |  12 |   2 |   0 |      1 |       1 |       1 |
| Susie     | 140 |  16 |   2 |   1 |      2 |       1 |       1 |
| Ralsei    | 100 |  10 |   2 |   9 |      3 |       1 |       4 |
| Noelle    |  90 |   3 |   1 |  11 |     12 |      14 |      22 |

### Chapter 3

| Character |  HP |  AT |  DF | MAG | Weapon | Armor 1 | Armor 2 |
| --------- | --: | --: | --: | --: | -----: | ------: | ------: |
| Kris      | 160 |  14 |   2 |   0 |     16 |       1 |      10 |
| Susie     | 190 |  18 |   2 |   2 |     17 |       1 |      10 |
| Ralsei    | 140 |  12 |   2 |  11 |     18 |       1 |      10 |

Important:

- Chapter 3 `scr_gamestart` still initializes Noelle data structures, but the
  opening Chapter 3 party setup is built around Kris / Susie / Ralsei
- Susie gets spell 11 in the initial loadout in Chapter 3

### Chapter 4

| Character |  HP |  AT |  DF | MAG | Weapon | Armor 1 | Armor 2 |
| --------- | --: | --: | --: | --: | -----: | ------: | ------: |
| Kris      | 200 |  17 |   2 |   0 |     23 |      25 |      10 |
| Susie     | 230 |  22 |   2 |   3 |     24 |      25 |      10 |
| Ralsei    | 180 |  15 |   2 |  14 |     25 |      25 |      10 |

Chapter 4 keeps the expanded Chapter 2+ stat arrays and later-party data layout.
`scr_gamestart` still initializes Noelle-side structures even though the opening
Chapter 4 party state centers on Kris / Susie / Ralsei.

### Chapter 5

| Character |  HP |  AT |  DF | MAG | Weapon | Armor 1 | Armor 2 |
| --------- | --: | --: | --: | --: | -----: | ------: | ------: |
| Kris      | 240 |  12 |   2 |   0 |     53 |      25 |      25 |
| Susie     | 290 |  16 |   2 |   1 |     24 |      25 |      25 |
| Ralsei    | 210 |  10 |   2 |   9 |     25 |      25 |      25 |

These are Chapter 5 startup defaults, not values restored from an existing save.
The established constant diff shows that HP rises from Chapter 4, while the base
AT and MAG defaults do not progress monotonically.

## Changed Startup Constants

Comparable named assignments in `scr_gamestart` show changes across adjacent
chapters. Compatibility branches determine the last applicable assignment.

Meaningful established changes include:

- `global.chapter` advances from 1 through 5 at each startup root;
- Kris, Susie, and Ralsei `maxhp`, `at`, and `mag` startup defaults change
  across the numbered chapters as shown in the party tables;
- equipped weapon and armor IDs change in the later chapter startup blocks.

Coordinates, timings, resource IDs, sentinels, computed expressions, and
incomparable return-table literals do not establish startup-default changes.

---

## Array / Inventory Expansion

### Chapter 1 arrays

- character-stat arrays are initialized for 4 indices
- `global.item`, `global.keyitem`, `global.weapon`, `global.armor` use the
  original smaller layout
- no `global.pocketitem`

### Chapters 2–5

- character/stat arrays are initialized for 20 indices
- `global.pocketitem[0..71]` exists
- `global.weapon` and `global.armor` are expanded to 48 slots
- element data is stored in:
  - `global.itemelement[i][q]`
  - `global.itemelementamount[i][q]`

This is one of the biggest established systemic breakpoints between Chapter 1
and Chapters 2–5.

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

### Chapter 1 spells

- only the early spell set is present in practice
- no Noelle spell ownership
- no later item-spell expansion

### Chapter 2 spells

- adds Noelle battle support
- adds spells `8`, `9`, `10`, `11`
- `scr_spellinfo` names spell 11 as `UltimatHeal`
- item-use spell codes go through `200..233`

### Chapter 3 spells

- keeps the Chapter 2 spell core
- `scr_spellinfo` renames spell 11 to `UltraHeal`
- item-use spell handling expands through `239`

### Chapter 4 spells

- keeps the Chapter 3-era spell core
- spell 11 is now more conditional in `scr_spellinfo`, with multiple names such
  as `OKHeal`, `Heal`, and `BetterHeal` depending on runtime state
- item-use spell handling expands further through `263`

Chapter 3 and Chapter 4 keep extending the same spell-id space and item-spell
ranges, so Chapter 2-only spell documentation is incomplete.

## Secret Encounter Runtime Differences

Each numbered chapter maps one connected encounter to its secret-boss result
slot. The encounter controllers differ in route ownership, SOUL behavior, and
completion storage.

- Chapter 1: Jevil uses encounter `25` and stores flag `241` as `6` or `7`.
  Its room, enemy, ACT, and reward controllers have no explicit SOUL-mode
  switch.
- Chapter 2: Spamton NEO uses encounter `61`, result flag `571`, and
  progression flag `309`. It uses shared yellow-heart shooting.
- Chapter 3: the plot-320 snow-zone Knight uses encounter `115`, result flag
  `1047` as `1` or `2`, and `UraBoss`. Its enemy controller has no explicit
  SOUL-mode switch.
- Chapter 4: Hammer of Justice uses encounter `160`, completion flag `852`,
  and attempt flag `1629`. It uses an encounter-local directional shield,
  then restores the red heart.
- Chapter 5: Pink uses encounter `224` and stores result flag `1908` as `2`.
  It uses encounter-local purple lane, grid, maze, tunnel, and node controls.

The Chapter 5 Pink controller also checks `global.console` after battle startup
and calls `obj_border_controller.show_border()` on console builds. The Jevil,
Spamton NEO, Knight, and Hammer controllers described here contain no matching
encounter-local platform branch.

King, Queen, Tenna, Titan, and Flowery have implemented encounter dispatches in
their respective payloads. Those dispatches do not establish whether their
routes permit bypass, so they remain unclassified as mandatory, optional, or
secret here. See
[Enemies, Encounters, and Attacks](enemies-encounters-and-attacks.md) for the
controller-level details.

---

## Damage System Evolution

### Chapter 1 damage

- uses the older flat defense model
- direct `scr_damage` logic is much simpler
- no later element-resistance layer

### Chapters 2–4 damage

- use `scr_damage_calculation`
- apply `scr_element_damage_reduction`
- preserve the expanded armor-element system

From a runtime perspective, Chapter 2 establishes the defensive model still used
by Chapters 3 and 4.

---

## Localization Evolution

### Chapter 1 localization

- ships both `lang_en.json` and `lang_ja.json`
- many scripts directly call `scr_84_get_lang_string()`

### Chapter 2 localization

- introduces broad `stringsetloc(english_fallback, key)` usage
- ships `lang_ja.json`
- missing strings return `"--missing-string--"`

### Chapter 3 localization

- same general `stringsetloc` model
- missing string lookups also emit `show_debug_message(...)`

### Chapter 4 localization

- same Chapter 3-era model
- continues using inline English fallback plus Japanese lookup

### Chapter Select

- not part of the chapter string-map pipeline
- launcher text is mostly hardcoded behind `global.lang` checks

---

## Save File Naming

The older documentation that implies one universal Chapter 1 save naming scheme
is incomplete.

| Runtime   | Save writer path               | Main loader path |
| --------- | ------------------------------ | ---------------- |
| Chapter 1 | `filech1_<slot>`               | `filech1_<slot>` |
| Chapter 2 | `filech2_<slot>`               | `filech2_<slot>` |
| Chapter 3 | `filech3_<slot>`               | `filech3_<slot>` |
| Chapter 4 | `filech4_<slot>`               | `filech4_<slot>` |
| Chapter 5 | `filech5_<slot><route-suffix>` | `filech5_<slot>` |

Chapter 2 already generalizes writing with:

`"filech" + string(global.chapter) + "_" + string(arg0)`

and Chapters 3 and 4 keep that generalized save-write form.

Chapter 5 appends `global.filechoice_route` when writing, but `scr_load` opens
the unsuffixed chapter/slot path. The two paths are not symmetrical: a non-empty
route suffix writes a separate file that this main loader does not open
directly.

---

## Save Payload Structure

### Chapter 1 save payload

- smaller inventory structures
- no `pocketitem`
- older save layout

### Chapters 2–5 save payload

- save payload includes `pocketitem`
- save payload includes armor-element data
- the later chapter save format is larger and materially different from Chapter
  1

Chapters 3 through 5 still write:

- stats
- equipment
- per-slot item modifiers
- spells
- inventory
- pocket inventory
- flags
- room id
- playtime

but their runtime assumptions on room ids and valid room resolution are more
modern than Chapter 1.

---

## Runtime-Specific New Systems

### Chapter 2 systems

Primary new direction:

- Noelle support
- Weird Route hooks
- element-resistant battle layer
- much larger cutscene / content framework

### Chapter 3 systems

Major runtime additions:

- board-game overworld framework: many `scr_board_*` scripts and `obj_board_*`
  objects
- rhythm-game framework: `scr_rhythmgame_*`, `obj_rhythmgame*`
- Tenna / TV / game-show scripting objects and `c_tenna_*` commands
- further cutscene command expansion through many `c_*` scripts

### Chapter 4 systems

Major runtime additions:

- large church / prophecy / bell / piano / climb content stack
- Gerson-heavy battle and event-specific systems
- retained rhythm-game stack with additional save/load helpers
- more item-spell branches and more conditional spell naming / behavior

---

## `CHAPTER_SELECT` Is Not a Gameplay Chapter

Against all five analyzed numbered chapters, `CHAPTER_SELECT` differs
structurally in these ways:

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
