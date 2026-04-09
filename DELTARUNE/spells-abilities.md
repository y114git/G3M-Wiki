# Spells & Abilities

The numbered chapter runtimes all contain:

- `scr_spellinfo`
- `scr_spell`

But the runtime behavior is no longer fully described by a Chapter 1 / Chapter 2 comparison. Chapters 3 and 4 keep extending the same spell and item-spell framework.

---

## Core Split

### Chapter 1

Smaller spell environment:

- early party spell set only
- no later Noelle combat spell progression
- no later item-spell expansion

### Chapters 2, 3, and 4

Shared later-era spell environment:

- Chapter 2-era battle spell framework remains in place
- Noelle-related spell ids remain defined
- later item-use spell codes continue expanding
- spell naming and some costs/branches continue changing by chapter

---

## Core Spell IDs

The main player-facing spell ids remain centered on:

| ID | Spell |
|---|---|
| `1` | Rude Sword |
| `2` | Heal Prayer |
| `3` | Pacify |
| `4` | Rude Buster |
| `5` | Red Buster |
| `6` | Dual Heal |
| `7` | ACT |
| `8` | SleepMist |
| `9` | IceShock |
| `10` | SnowGrave |
| `11` | later-chapter heal slot with chapter-dependent naming/behavior |
| `100` | SPARE runtime code |

Item-use spell ids sit above this range.

---

## Spell Growth By Chapter

### Chapter 1

Practical opening loadout:

- Kris: `7`
- Susie: `4`
- Ralsei: `3`, `2`

This is the early Chapter 1 spell set.

### Chapter 2

The big expansion point:

- Noelle is supported
- spells `8`, `9`, `10`, `11` become part of the broader runtime space
- item-use spell codes extend through `233`

`scr_spellinfo` names spell `11` as:

- `UltimatHeal`

### Chapter 3

The spell framework persists rather than resetting:

- initial setup gives Susie spell `11`
- item-use spell codes extend through `239`

`scr_spellinfo` names spell `11` as:

- `UltraHeal`

### Chapter 4

Chapter 4 continues changing the same slot instead of creating a wholly separate spell family.

Item-use spell codes extend through:

- `263`

For spell `11`, `scr_spellinfo` can assign multiple names depending on runtime conditions, including:

- `OKHeal`
- `Heal`
- `BetterHeal`

This is one of the clearest signs that Chapter 4 should be documented as an active spell-system evolution, not as “Chapter 2 again”.

---

## Important Cross-Chapter Corrections

### `scr_spell` case coverage

Observed runtime case ranges:

| Runtime | Highest observed item/spell case in `scr_spell` |
|---|---:|
| Chapter 2 | `233` |
| Chapter 3 | `239` |
| Chapter 4 | `263` |

So any page that stops item-spell coverage at the Chapter 2 range is incomplete for modern chapters.

### Spell 11 is not stable

Spell 11 is especially important because it changes across later builds:

- Chapter 2: `UltimatHeal`
- Chapter 3: `UltraHeal`
- Chapter 4: dynamic naming branches including `OKHeal`, `Heal`, and `BetterHeal`

Spell 11 is a chapter-sensitive runtime slot, not a single immutable definition.

---

## Ownership / Loadout Snapshot

Broadly:

- Kris keeps `ACT` as the fundamental special command slot
- Susie keeps buster-oriented offensive magic and later gains heal-slot usage in later chapters
- Ralsei keeps the healing / pacify core
- Noelle's later combat spell ids remain defined in the later-era runtime family even when she is not the opening active party in newer chapters

---

## SPARE And Item Codes

Two non-standard spell families are crucial:

### `100`

Used for SPARE behavior in battle runtime logic.

### `200+`

Used for item behavior routed through `scr_spell`.

Battle item use is partly encoded as spell-style runtime cases.

That becomes more important in Chapters 3 and 4 because the item-spell case range grows further.

---

## Practical Modding Notes

If you want to document or patch player spell behavior correctly, inspect all of the following in the target chapter:

- `scr_spellinfo`
- `scr_spell`
- `scr_gamestart`

If you want to document or patch item use in battle, also inspect:

- the `200+` cases in `scr_spell`
- `scr_iteminfo`

If you want cross-chapter accuracy, do not stop at Chapter 2. Chapters 3 and 4 materially extend the same runtime logic.
