# Tension / TP System

Tension Points (TP) are the primary resource for casting spells. The system centers on `global.tension` and `global.maxtension`.

---

## Core Variables

| Variable | Default | Purpose |
|---|---:|---|
| `global.tension` | 0 | Current TP |
| `global.maxtension` | 250 | Maximum TP |
| `global.grazeamt` | *(varies)* | Base TP gained per graze tick |
| `global.grazesize` | *(varies)* | Graze detection radius |
| `global.boltspeed` | *(varies)* | Base bolt approach speed |

---

## TP Sources

### Graze

Moving the SOUL near enemy bullets without touching them generates TP. The graze system uses `obj_grazebox`, which detects proximity to `obj_bulletparent` instances.

TP gained per graze tick is influenced by:
- `global.grazeamt` (base value)
- Equipment modifiers: `global.itemgrazeamt[char][slot]`
- Equipment graze size: `global.itemgrazesize[char][slot]`

### DEFEND

Choosing DEFEND in battle generates TP. The amount depends on the chapter runtime.

### ACT

Some ACT commands generate TP as a side effect.

### Battle Actions

Successful timing hits during the FIGHT minigame can generate bonus TP.

---

## `scr_tensionheal` — TP Addition

Present in all four chapters. The core logic adds `arg0` to `global.tension` and clamps to `global.maxtension`.

Chapter-specific additions:

| Chapter | Extra behavior |
|---|---|
| 1, 2 | Base add + clamp only |
| 3 | Adds `tpgained` tracking for `obj_gameshow_battlemanager`; adds `mercytotal` tracking on `obj_battlecontroller` |
| 4 | Jackenstein fight after 3+ deaths (`global.tempflag[89] >= 3`): adds `ceil(arg0 * 1.5)` instead of `arg0` — 50% TP bonus |

Chapter 4 source:

```gml
function scr_tensionheal(arg0)
{
    if (i_ex(obj_jackenstein_enemy) && global.tempflag[89] >= 3)
        global.tension += ceil(arg0 * 1.5);
    else
        global.tension += arg0;

    if (global.tension > global.maxtension)
        global.tension = global.maxtension;
}
```

- Standard: adds `arg0` to TP
- Jackenstein fight after 3+ deaths: adds `ceil(arg0 * 1.5)` — 50% TP bonus as a difficulty assist
- TP is clamped to `global.maxtension`

---

## TP Cost System

Spell costs are defined in `scr_spellinfo` and cached in `global.spellcost[char][slot]` by `scr_spellinfo_all`.

TP costs use `global.maxtension` (250) as the base. Common costs:

| Spell | Cost | % of Max |
|---|---:|---:|
| Pacify | 40 | 16% |
| IceShock | 40 (or 20) | 16% (8%) |
| Heal Prayer | 80 | 32% |
| SleepMist | 80 | 32% |
| Rude Buster | 125 (or 100) | 50% (40%) |
| Rude Sword | 125 | 50% |
| OKHeal | 200–212.5 | 80–85% |
| BetterHeal | 187.5–200 | 75–80% |
| SnowGrave | 500 | 200% (requires charged max) |

See [Spells & Abilities](spells-abilities.md) for the complete cost table.

---

## Equipment TP Modifiers

Per-character equipment slots can modify TP behavior:

| Array | Purpose |
|---|---|
| `global.itemgrazeamt[char][slot]` | Bonus TP per graze tick |
| `global.itemgrazesize[char][slot]` | Bonus graze detection radius |
| `global.itemboltspeed[char][slot]` | Bolt approach speed modifier |

These are saved/loaded per character per equipment subslot (4 subslots per character).

---

## Tension Bar Object

`obj_tensionbar` is the visual display for TP in battle:

- Displays current/max TP as a vertical bar
- Color changes based on fill level
- Shakes on TP gain
- In some Chapter 4 encounters, the tension bar slides offscreen (`hspeed = -10, friction = -0.4`)

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Change max TP | `global.maxtension` in `scr_gamestart` |
| Change graze TP gain | `global.grazeamt` and `global.itemgrazeamt[][]` |
| Change spell costs | `scr_spellinfo` — `cost` assignments |
| Add TP-generating actions | Call `scr_tensionheal(amount)` |
| Change TP display | `obj_tensionbar` |