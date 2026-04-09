# Damage System

The damage pipeline has one major breakpoint:

- Chapter 1 uses the older direct damage model
- Chapters 2, 3, and 4 use the newer layered model

Chapters 3 and 4 keep the Chapter 2 damage framework: `scr_damage_calculation`, `scr_element_damage_reduction`, and later armor-element fields remain in use.

---

## Core Runtime Scripts

Numbered chapters include:

- `scr_damage`
- `scr_damage_enemy`

Later chapters also rely on:

- `scr_damage_calculation`
- `scr_element_damage_reduction`

---

## Damage To Party Members

### Chapter 1

Chapter 1 uses the older direct `scr_damage` path:

- invincibility gate
- target resolution
- flat DEF subtraction
- DEFEND reduction
- HP subtraction
- death / game over checks
- damage-number and hurt-state side effects

The characteristic formula is the familiar flat defense reduction:

```gml
tdamage = ceil(tdamage - (global.battledf[target] * 3));
```

This is the Chapter 1-era baseline.

### Chapters 2, 3, and 4

Later runtimes move to the newer layered flow:

1. raw incoming damage is prepared
2. `scr_damage_calculation(...)` applies defense scaling
3. `scr_element_damage_reduction(...)` applies elemental reduction
4. DEFEND reduction is applied
5. HP is reduced
6. hurt / death / game-over side effects are triggered

The effective split is Chapter 1 vs Chapter 2+, not Chapter 1 vs Chapter 2 only.

---

## `scr_damage_calculation`

This helper exists in Chapters 2, 3, and 4.

It replaces the older simple `DEF * 3` subtraction with a per-point scaling model that depends on current incoming damage relative to the target's max HP.

Broadly:

- big incoming hits lose more per DEF point
- smaller incoming hits lose less per DEF point
- damage is still clamped to a minimum of 1

This makes later-chapter defense feel less linear than Chapter 1.

---

## Element Resistance

`scr_element_damage_reduction` is part of the later runtime family:

- Chapter 1: not part of the later resistance model
- Chapters 2, 3, 4: present and used

It works with:

- `global.itemelement[i][q]`
- `global.itemelementamount[i][q]`

This is one of the clearest mechanical differences between Chapter 1 and the later builds.

---

## DEFEND

Across the later runtime family, DEFEND still reduces incoming damage, but it is layered on top of the newer damage pipeline rather than standing alone.

So in practical terms:

- Chapter 1 DEFEND interacts with the old flat-defense model
- Chapters 2, 3, and 4 DEFEND interacts with the newer defense-plus-element system

---

## Damage To Enemies

`scr_damage_enemy(slot, damage)` remains the core enemy-damage entry point across the numbered chapters.

It performs the same high-level responsibilities:

- subtract HP from the targeted monster slot
- spawn `obj_dmgwriter`
- trigger monster hurt / shake state
- register hit offset tracking
- trigger dodge behavior on zero-damage hits where allowed
- call defeat logic when HP reaches zero

The entrypoint stays the same while later chapters add more enemy-specific and encounter-specific callers.

---

## Why Chapter 3 And 4 Matter Here

The old documentation problem is not that it described Chapter 1 and Chapter 2 incorrectly in spirit. The real problem is that it stopped too early.

Chapter 3 and Chapter 4 still inherit the Chapter 2-era damage architecture:

- defense scaling
- elemental reduction
- larger item / equipment influence
- much larger enemy object set using the same broad damage entry points

So for modding modern DELTARUNE builds, the correct split is:

- Chapter 1
- Chapter 2+

not:

- Chapter 1
- Chapter 2 only

---

## Practical Modding Notes

Incoming-damage edits in Chapter 2+ typically touch:

- `scr_damage`
- `scr_damage_calculation`
- `scr_element_damage_reduction`

If you want to change outgoing player damage against monsters, inspect:

- `scr_damage_enemy`
- `scr_spell`
- attack-specific enemy / hero scripts that decide the raw damage value before it reaches `scr_damage_enemy`

If you are patching Chapter 1, do not assume those later helper scripts exist or are used the same way.
