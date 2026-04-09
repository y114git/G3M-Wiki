# Damage System

The damage pipeline differs between Chapter 1 and Chapters 2+. Chapter 1 uses a flat defense subtraction. Chapters 2, 3, and 4 use a scaled per-point model with elemental reduction.

---

## Core Scripts

| Script | Purpose |
|---|---|
| `scr_damage` | Incoming damage to party members (from enemy bullets) |
| `scr_damage_enemy` | Outgoing damage to enemies (from player attacks/spells) |
| `scr_damage_calculation` | Defense scaling helper (Ch2+) |
| `scr_element_damage_reduction` | Elemental resistance multiplier (Ch2+) |
| `scr_damage_all` | Area damage to all party members |
| `scr_damage_all_overworld` | Overworld-mode area damage |
| `scr_damage_cache` | Caches damage state before processing |
| `scr_dead` | Individual party member death handler |

---

## `scr_damage` — Full Pipeline

The party-damage script runs when `global.inv < 0` (invulnerability expired). The full sequence:

### 1. Element Resolution

```gml
var __element = 0;
if (variable_instance_exists(id, "element") && is_real(element))
{
    __element = element;
}
```

Enemy bullets can carry an `element` instance variable. If present, it feeds into elemental reduction later.

### 2. Encounter-Specific Modifiers

Chapter 4 applies pre-defense modifiers depending on the encounter:

| Condition | Effect |
|---|---|
| Encounter 157 solo Kris (no Susie/Ralsei heroes) | `damage *= 0.7` |
| Jackenstein enemy with `scaredycat == true` | `damage *= 1.5` |
| Titan enemy with `forcehitralsei == true` | `damage *= 0.5`, forced target Ralsei |
| Titan encounter with armor id 23 equipped | `damage *= 0.5` |

### 3. Target Resolution

The `target` variable determines who takes the hit:

| Target | Meaning |
|---:|---|
| `0` | Party slot 0 |
| `1` | Party slot 1 |
| `2` | Party slot 2 |
| `3` | All party members |
| `4` | Smart random — picks a target, rerolls if below 50% average HP, rerolls again for slot 0 if below 35% HP |

If the target is already at 0 HP, `scr_randomtarget_old()` picks a different living member.

### 4. Defense Calculation

#### Chapter 1

Flat subtraction:

```gml
Tdamage = ceil(tdamage - (global.battledf[target] * 3));
```

Each point of DEF removes 3 damage.

#### Chapters 2, 3, 4

The `scr_damage_calculation` function uses HP-aware per-point scaling:

```gml
function scr_damage_calculation(arg0, arg1)
{
    var _tdamage = arg0;
    var _tdef = global.battledf[arg1];
    var _tmaxhp = global.maxhp[global.char[arg1]];
    var _finaldamage = 1;
    var _hpthresholda = _tmaxhp / 5;   // 20% of max HP
    var _hpthresholdb = _tmaxhp / 8;   // 12.5% of max HP
    for (var _di = 0; _di < _tdef; _di++)
    {
        if (_tdamage > _hpthresholda)
            _tdamage -= 3;
        else if (_tdamage > _hpthresholdb)
            _tdamage -= 2;
        else
            _tdamage -= 1;
    }
    return max(_tdamage, _finaldamage);
}
```

Per point of DEF, damage is reduced by:
- **3** if remaining damage > 20% of target's max HP
- **2** if remaining damage > 12.5% of target's max HP
- **1** otherwise

Result is clamped to minimum 1.

### 5. DEFEND Action Reduction

If the target party member chose DEFEND (`global.charaction[target] == 10`):

| Target type | Formula |
|---|---|
| Single target (`target < 3`) | `tdamage = ceil((2 * tdamage) / 3)` — removes ~33% |
| All-party (`target == 3`) | `tdamage = ceil((3 * tdamage) / 4)` — removes ~25% |

### 6. Elemental Reduction

Applied after DEFEND:

```gml
Tdamage = ceil(tdamage * scr_element_damage_reduction(__element, global.char[target]));
```

Final damage is clamped to minimum 1.

---

## `scr_element_damage_reduction` — Full Algorithm

```gml
function scr_element_damage_reduction(arg0, arg1)
{
    var ___element = arg0;
    var ___char = arg1;
    var ___reduction = 1;
    if (___element != 0)
    {
        for (var ___itemi = 0; ___itemi < 2; ___itemi++)
        {
            if (global.itemelement[___char][___itemi + 1] != 0)
            {
                // Direct element match
                if (global.itemelement[___char][___itemi + 1] == ___element)
                    ___reduction -= global.itemelementamount[___char][___itemi + 1];

                // Element 9 covers elements 2 AND 8
                if (global.itemelement[___char][___itemi + 1] == 9)
                {
                    if (___element == 2 || ___element == 8)
                        ___reduction -= global.itemelementamount[___char][___itemi + 1];
                }

                // Element 10 is universal — reduces ALL elemental damage
                if (global.itemelement[___char][___itemi + 1] == 10)
                    ___reduction -= global.itemelementamount[___char][___itemi + 1];
            }
        }
    }
    if (___reduction < 0.25)
        ___reduction = 0.25;
    return ___reduction;
}
```

Key mechanics:

- Only armor slots 1 and 2 (index `___itemi + 1`) are checked — the weapon slot (0) is excluded
- Element 0 = no element (no reduction applied)
- Element 9 = dual-coverage, resists both element 2 and element 8
- Element 10 = universal resistance against all non-zero elements
- Minimum multiplier is `0.25` (75% maximum damage reduction)
- The return value multiplies the post-defense damage

---

## Invulnerability Timer

After damage is applied:

```gml
global.inv = global.invc * 40;
```

`global.invc` defaults to `1`, giving 40 frames of invulnerability. Equipment or battle state can modify `global.invc` to change the window.

Damage only processes when `global.inv < 0`. Each frame, `global.inv` is decremented by the battle system.

---

## Death Processing

When a party member's HP drops to 0 or below:

```gml
Hpdiff = abs(global.hp[chartarget] - (global.maxhp[chartarget] / 2));
doomtype = 4;
global.hp[chartarget] = round(-global.maxhp[chartarget] / 2);
scr_dead(target);
```

The downed HP is pinned to `-maxhp / 2`. Negative HP is displayed as the "downed" state.

If a downed character is hit again:

```gml
global.hp[chartarget] -= round(tdamage / 4);
```

Further damage to downed members deals 25% of the incoming value.

### `cantdie` Mechanic

Chapter 4 introduces encounters where Kris cannot die:

```gml
if (i_ex(obj_dw_church_trueclimbadventure))
    cantdie = true;
if (i_ex(obj_titan_enemy) && obj_titan_enemy.phase == 8)
    cantdie = true;
```

When `cantdie` is active, Kris's HP is clamped to minimum 1.

### Game Over Trigger

Game over fires when all occupied party slots have HP ≤ 0:

```gml
Gameover = 1;
if (global.char[0] != 0 && global.hp[global.char[0]] > 0) gameover = 0;
if (global.char[1] != 0 && global.hp[global.char[1]] > 0) gameover = 0;
if (global.char[2] != 0 && global.hp[global.char[2]] > 0) gameover = 0;
if (gameover == 1) scr_gameover();
```

---

## `scr_damage_enemy` — Outgoing Damage

This script applies processed damage to a monster slot:

1. Subtracts HP from `global.monsterhp[slot]`
2. Spawns `obj_dmgwriter` at the monster's position
3. Triggers hurt state / shake on the monster instance
4. Handles dodge behavior on zero-damage hits
5. Calls defeat logic when HP ≤ 0

The entry point remains the same across all chapters. Callers (spell scripts, attack scripts) determine the raw damage value.

---

## All-Party Damage Branch

When `target == 3`, the damage loop applies individually to each occupied slot:

```gml
for (hpi = 0; hpi < 3; hpi += 1)
{
    chartarget = global.char[hpi];
    if (global.hp[chartarget] >= 0)
    {
        tdamage = scr_damage_calculation(tdamage, hpi);
        tdamage = ceil(tdamage * scr_element_damage_reduction(__element, chartarget));
        if (global.charaction[hpi] == 10)
            global.hp[chartarget] -= ceil((3 * tdamage) / 4);
        else
            global.hp[chartarget] -= tdamage;
    }
}
```

Each member is calculated independently with their own DEF, element resistance, and DEFEND state.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Change defense scaling | `scr_damage_calculation` |
| Change element resistance caps/rules | `scr_element_damage_reduction` |
| Change invulnerability window | `global.invc` initialization in `scr_gamestart` |
| Change DEFEND reduction | `scr_damage` — charaction == 10 branches |
| Change encounter-specific modifiers | `scr_damage` — top-level Chapter 4 branches |
| Change death/downed behavior | `scr_damage` — HP ≤ 0 branches, `scr_dead` |
| Change enemy damage intake | `scr_damage_enemy` |