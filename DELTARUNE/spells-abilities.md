# Spells & Abilities

The spell system is defined in two core scripts:

- `scr_spellinfo` — spell metadata: name, cost, target mode, description
- `scr_spell` — spell execution: what happens when a spell is cast

Spell definitions live in the chapter payload. Each chapter extends the spell table.

---

## `scr_spellinfo` Output Fields

The script sets these variables in the caller's scope:

| Field | Type | Purpose |
|---|---|---|
| `spellname` | string | Full display name |
| `spellnameb` | string | Short/menu display name |
| `spelldesc` | string | Long description |
| `spelldescb` | string | Short description (menu) |
| `cost` | real | TP cost (out of `global.maxtension`, default 250) |
| `spelltarget` | int | `0` = no target, `1` = ally, `2` = enemy |
| `spellusable` | int | Usability flag |
| `spellanim` | int | Animation id |
| `spelltext` | string | Battle text override |

---

## Complete Spell Table (Chapter 4)

### Core Spells

| ID | Name | Cost | Target | Description |
|---:|---|---:|---|---|
| 0 | *(empty)* | -1 | none | Placeholder / no spell |
| 1 | Rude Sword | 125 | enemy | Moderate Rude-elemental damage. Depends on AT & MAG |
| 2 | Heal Prayer | 80 | ally | Restores a little HP to one party member. Depends on MAG |
| 3 | Pacify | 40 | enemy | SPARE a TIRED enemy by putting them to sleep |
| 4 | Rude Buster | 125 / **100** | enemy | Moderate Rude-elemental damage. Cost reduces to 100 if `global.charweapon[2] == 7` (Devilsknife equipped) |
| 5 | Red Buster | 0 | enemy | Red-elemental damage |
| 6 | Dual Heal | 0 | none | Heals all party members 30 HP |
| 7 | ACT | 0 | none | Execute various behaviors. Not magic |
| 8 | SleepMist | 80 | none | Spares all TIRED enemies |
| 9 | IceShock | 40 / **20** | enemy | Magical ICE damage. Cost halved if `global.charweapon[4] == 13` |
| 10 | SnowGrave | 500 / **250** | none | Fatal damage to all enemies. Cost = `global.maxtension * 2`, halved if `global.charweapon[4] == 13` |
| 100 | *(SPARE)* | — | — | Internal SPARE runtime code |

### Spell 11 — Progressive Heal

Spell 11 is unique: its name, cost, and description change based on runtime flags.

#### Default mode: `OKHeal`

Cost scales down with usage tracked in `global.flag[1045]`:

| `global.flag[1045]` | Cost |
|---:|---:|
| 0 | 212.5 |
| 1–3 | 210 |
| 4–6 | 207.5 |
| 7–9 | 205 |
| 10–12 | 202.5 |
| 13+ | 200 |

#### Story-locked mode: `Heal`

When `global.plot >= 110 && global.flag[850] < 6`:

- Name becomes `Heal`
- Description: "It seems the user doesn't want to use this spell."
- Cost forced to `255` (cannot be used — exceeds max TP)

#### Upgraded mode: `BetterHeal`

When `global.flag[1569] == 1 || global.flag[852] == 1`:

| `global.flag[1045]` | Cost |
|---:|---:|
| 0 | 200 |
| 1–3 | 197.5 |
| 4–6 | 195 |
| 7–9 | 192.5 |
| 10–12 | 190 |
| 13+ | 187.5 |

- Name: `BetterHeal`
- Description: "A healing spell that has grown with practice and confidence."

Target is always `1` (single ally).

---

## Spell Ownership by Chapter

### Chapter 1

| Character | Slot 0 | Slot 1 |
|---|---|---|
| Kris | ACT (7) | — |
| Susie | Rude Buster (4) | — |
| Ralsei | Pacify (3) | Heal Prayer (2) |

### Chapter 2

| Character | Slot 0 | Slot 1 | Slot 2 |
|---|---|---|---|
| Kris | ACT (7) | — | — |
| Susie | Rude Buster (4) | — | — |
| Ralsei | Pacify (3) | Heal Prayer (2) | — |
| Noelle | Heal Prayer (2) | SleepMist (8) | IceShock (9) |

### Chapters 3 & 4

| Character | Slot 0 | Slot 1 |
|---|---|---|
| Kris | ACT (7) | — |
| Susie | Rude Buster (4) | Spell 11 (OKHeal / BetterHeal) |
| Ralsei | Pacify (3) | Heal Prayer (2) |

Noelle structures are still initialized but the opening party centers on Kris / Susie / Ralsei.

---

## Item-Use Spell Codes

Battle item use is routed through `scr_spell` as spell cases in the `200+` range:

| Chapter | Highest item-spell case |
|---|---:|
| 2 | 233 |
| 3 | 239 |
| 4 | 263 |

Each consumable item id maps to a spell case that implements the effect (healing, TP gain, revival, etc.).

---

## `scr_spell` Execution

`scr_spell` is the runtime handler. When a spell is cast, the battle controller calls `scr_spell(spell_id)`.

Key responsibilities:

1. Resolve the target from `global.chartarget[]`
2. Calculate spell-specific effects (heal amount, damage amount)
3. Apply stat modifiers (MAG-based scaling for heals, AT+MAG for offensive spells)
4. Spawn visual effects and damage writers
5. Update battle state (spare enemies for Pacify/SleepMist, etc.)
6. Handle item-spell consumption for `200+` range cases

### SPARE Runtime (Case 100)

When a target enemy's `global.sparepoint[slot] >= global.mercymax[slot]`, the SPARE succeeds. Otherwise, Pacify requires the enemy to be in TIRED state.

---

## Spell Menu Synthesis (Chapter 2+)

The runtime spell menu is built by `scr_spellmenu_setup()`. It merges two sources:

### ACT-style commands (first)

Generated entries with `global.battlespell[slot][index] = -1`. Each party member has character-specific ACT arrays:

| Character | Permission | Cost | Name | Description |
|---|---|---|---|---|
| Kris | `global.canact[0][]` | `global.actcost[0][]` | `global.actname[0][]` | `global.actdesc[0][]` |
| Susie | `global.canactsus[]` | `global.actcostsus[]` | `global.actnamesus[]` | `global.actdescsus[]` |
| Ralsei | `global.canactral[]` | `global.actcostral[]` | `global.actnameral[]` | `global.actdescral[]` |
| Noelle | `global.canactnoe[]` | `global.actcostnoe[]` | `global.actnamenoe[]` | `global.actdescnoe[]` |

`global.battlespellspecial` identifies the character: `1` = Kris, `2` = Susie, `3` = Ralsei, `4` = Noelle.

When multiple monster types are present, character ACT names are replaced with generic labels: `S-Action`, `R-Action`, `N-Action`.

### Learned spells (second)

Appended after ACT entries:

```gml
__ib = global.battleactcount[__i] + __fj;
global.battlespell[__i][__ib] = global.spell[global.char[__i]][__fj];
global.battlespellcost[__i][__ib] = global.spellcost[global.char[__i]][__fj];
```

The final menu layout is: ACT commands, then learned spells.

---

## `scr_spellinfo_all`

Bulk-caches spell metadata for all characters:

```gml
function scr_spellinfo_all()
{
    for (i = 0; i < 20; i += 1)
    {
        for (j = 0; j < 12; j += 1)
        {
            scr_spellinfo(global.spell[i][j]);
            global.spellcost[i][j] = cost;
            global.spellnameb[i][j] = spellnameb;
            global.spelldescb[i][j] = spelldescb;
            global.spelltarget[i][j] = spelltarget;
        }
    }
}
```

Up to 20 characters × 12 spell slots.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a new spell | Add a case to `scr_spellinfo` AND `scr_spell` |
| Change spell cost | Edit the `cost` assignment in `scr_spellinfo` |
| Change spell execution | Edit the corresponding case in `scr_spell` |
| Change starting spells | Edit `scr_gamestart` — `global.spell[char][slot]` |
| Change ACT menu entries | Edit `scr_monstersetup` (sets ACT arrays per monster type) |
| Add item-use effects | Add a case in the `200+` range of `scr_spell` |
| Change spell 11 progression | Edit `global.flag[1045]` and `global.flag[1569]`/`global.flag[852]` branches in `scr_spellinfo` |

---

## Relationship To Other Pages

- [Battle System](battle-system.md) explains the controller that invokes spells.
- [Items & Equipment](items-equipment.md) explains the `200+` item-spell bridge.
- [Damage System](damage-system.md) explains the defense and element layers that spell damage feeds into.