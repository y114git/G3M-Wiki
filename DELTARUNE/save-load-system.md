# Save & Load System

Save handling is not identical across all shipped DELTARUNE runtimes.

The core pattern is the same:

- each numbered chapter owns its own `scr_saveprocess` and `scr_load`
- launcher-visible metadata is stored separately from the main chapter payload
- chapter payloads read and write plain-text save files through `ossafe_*` wrappers

But the concrete filenames, payload size, and field layout differ between Chapter 1 and the later chapters.

---

## Save File Names

| Runtime | Main save file |
|---|---|
| Chapter 1 | `filech1_<slot>` |
| Chapter 2 | `filech2_<slot>` |
| Chapter 3 | `filech3_<slot>` |
| Chapter 4 | `filech4_<slot>` |

Chapter 1 hardcodes:

```gml
file = "filech1_" + string(arg0);
```

Chapters 2, 3, and 4 write more generically:

```gml
file = "filech" + string(global.chapter) + "_" + string(arg0);
```

This distinction matters when documenting runtime behavior or when testing modified chapter payloads outside the launcher.

---

## Shared Metadata Files

Two non-main-save files are important in practice:

### `dr.ini`

Used by `CHAPTER_SELECT` for save metadata and cross-chapter launcher UI state.

### `true_config.ini`

Used for launcher-visible settings such as language and fullscreen/window state.

From a player/modder perspective, the numbered chapter save files and the launcher metadata files are separate layers.

---

## Core Save Scripts

Every numbered chapter includes:

- `scr_saveprocess`
- `scr_load`

The launcher does not.

These scripts are part of the chapter runtime, meaning that any mod which changes chapter-specific inventory, flags, spells, or room handling must patch the relevant chapter payload directly.

---

## Chapter 1 Layout

Chapter 1 is the smallest save format documented here.

It writes, in broad terms:

- player names
- current party slots
- gold / XP / LV
- core character stats
- equipment ids
- per-slot equipment stat modifiers
- spell loadout
- basic inventory arrays
- tension and Light World legacy stats
- phone / legacy item arrays
- `global.flag[0..9998]`
- plot, room, and time

Important Chapter 1 traits:

- no `global.pocketitem`
- smaller weapon / armor inventory model
- older room remap assumptions

---

## Chapter 2+ Layout

Chapters 2, 3, and 4 extend the payload significantly.

In addition to the Chapter 1-style core data, later chapters also write:

- `global.itemelement[i][q]`
- `global.itemelementamount[i][q]`
- `global.pocketitem`
- expanded `global.weapon`
- expanded `global.armor`

The later save format is therefore not just “Chapter 1 with more content”; it is a larger runtime structure with new systems serialized into it.

---

## Key Later-Chapter Fields

In Chapters 3 and 4, `scr_saveprocess` clearly writes the following groups:

- `global.truename`
- `global.othername[]`
- `global.char[]`
- `global.gold`, `global.xp`, `global.lv`, `global.inv`, `global.invc`, `global.darkzone`
- full character stat blocks
- equipment stat modifiers
- elemental equipment data
- spell loadout
- `global.boltspeed`, `global.grazeamt`, `global.grazesize`
- `global.item[]`, `global.keyitem[]`, `global.weapon[]`, `global.armor[]`
- `global.pocketitem[]`
- tension values
- Light World legacy values
- `global.litem[]`, `global.phone[]`
- `global.flag[]`
- `global.plot`, `global.currentroom`, `global.time`

That makes the old Chapter 1-centric documentation insufficient for Chapters 3 and 4.

---

## `global.pocketitem`

This is one of the most important save-format differences.

- Chapter 1: not present
- Chapters 2, 3, and 4: present

Later runtimes even serialize `global.pocketitem` twice in practical terms:

- as its own long list block
- through per-index write handling alongside inventory groups

For modders, this means any custom inventory extension built on later chapters must respect the later save ordering exactly.

---

## Load Behavior

At a high level, `scr_load` in each chapter:

1. resets globals through `scr_gamestart()`
2. restores `global.filechoice`
3. opens the chapter-specific save file
4. reads values back in the exact order written
5. resolves / repairs room ids
6. restores runtime audio/config state
7. transfers the player to the loaded room

The exact room-id normalization differs by chapter.

---

## Room Resolution Differences

### Chapter 1

Uses the older remap logic documented in early references, including older room-index correction behavior.

### Chapter 2

Still uses chapter-based room id correction and validates loaded rooms through chapter-aware logic.

### Chapter 3

Uses `scr_get_id_by_room_index(...)` during recovery when the loaded room id is still in older compact form.

### Chapter 4

Continues the Chapter 3-era room resolution pattern, again using runtime validation instead of only the older fixed offset assumptions.

This is why a chapter-agnostic room-loading description is misleading for modern DELTARUNE builds.

---

## `ossafe_*` Wrappers

The numbered chapters consistently use `ossafe_*` wrappers around file and INI operations.

Common wrappers include:

- `ossafe_file_text_open_write`
- `ossafe_file_text_open_read`
- `ossafe_file_text_write_real`
- `ossafe_file_text_write_string`
- `ossafe_file_text_read_real`
- `ossafe_file_text_read_string`
- `ossafe_file_text_close`
- `ossafe_ini_open`
- `ossafe_ini_close`

For modding, this means save I/O patches should be made in the existing wrapper-based flow rather than trying to bypass it.

---

## Practical Modding Rule

If you add or remove saved variables in a chapter payload:

1. patch that chapter's `scr_saveprocess`
2. patch the matching `scr_load`
3. preserve ordering exactly
4. update defaults in that chapter's `scr_gamestart`

Never assume a Chapter 1 save doc automatically applies to Chapters 2, 3, or 4.
