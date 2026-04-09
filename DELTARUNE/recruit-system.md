# Recruit System

Darkners spared in battle can be recruited to the Castle Town. Recruitment is tracked per-monster via `global.flag[]` and displayed via `scr_recruit_info`.

---

## Core Scripts

| Script | Purpose |
|---|---|
| `scr_recruit` | Processes recruitment after a successful spare |
| `scr_recruit_info` | Database of all recruitable monsters (stats, dialogue, sprite) |
| `scr_recruit_info_all` | Bulk-loads all recruit metadata |
| `scr_recruitchecks` | Validates recruitment state for Castle Town |
| `scr_recruited_all` | Checks if all monsters for a chapter are recruited |
| `scr_recruits_to_array` | Serializes recruit data for display |

---

## Recruitment Mechanic

```gml
function scr_recruit()
{
    if (recruitable == 1 && global.flag[61] == 0)
    {
        if (global.flag[global.monstertype[myself] + 600] >= 0
         && global.flag[global.monstertype[myself] + 600] < 1
         && recruitcount > 0)
        {
            global.flag[global.monstertype[myself] + 600] += 1 / recruitcount;
        }
    }
}
```

Key mechanics:

- Each monster type uses `global.flag[monstertype + 600]` as its recruitment meter
- The meter starts at 0 and fills to 1.0
- Each spare adds `1 / recruitcount` to the meter
- A monster with `recruitcount = 3` needs 3 spares to fully recruit
- `global.flag[61] == 0` must hold (no story block on recruitment)
- Monster must have `recruitable == 1`

When the meter reaches 1.0, the monster appears in Castle Town.

Visual feedback uses `obj_recruitanim` showing "X/Y" at the monster's position.

---

## Recruitment Database

### Chapter 1 Recruits

| Type ID | Name | Element | Level | AT | DF | Recruit Count | Placeable |
|---:|---|---|---:|---:|---:|---:|---:|
| 5 | Rudinn | JEWEL | 2 | 4 | 5 | 1 | ✓ |
| 6 | Hathy | HEART | 2 | 4 | 5 | 1 | ✓ |
| 11 | Ponman | ORDER | 3 | 4 | 5 | 1 | ✓ |
| 13 | Rabbick | RABBIT:DUST | 4 | 4 | 5 | 1 | ✓ |
| 14 | Bloxer | FIGHT | 4 | 4 | 5 | 1 | ✓ |
| 15 | Jigsawry | MOUSE:PUZZ | 1 | 4 | 5 | 1 | ✓ |
| 20 | JEVIL | CHAOS:CHAOS | ??? | 10 | 5 | 1 | ✗ |
| 22 | Rudinn Ranger | JEWEL:BLADE | 5 | 4 | 5 | 1 | ✓ |
| 23 | Head Hathy | HEART:ICE | 5 | 5 | 5 | 1 | ✓ |

### Chapter 2 Recruits

| Type ID | Name | Element | Level | AT | DF | Recruit Count | Placeable |
|---:|---|---|---:|---:|---:|---:|---:|
| 30 | Ambyu-Lance | ORDER:ELEC | 8 | 8 | 8 | 4 | ✓ |
| 31 | Poppup | VIRUS | 8 | 9 | 3 | 3 | ✓ |
| 32 | Tasque | CAT:ELEC | 7 | 8 | 6 | 5 | ✓ |
| 33 | Werewire | ELEC | 7 | 8 | 7 | 6 | ✓ |
| 34 | Maus | MOUSE:ELEC | 6 | 8 | 2 | 3 | ✓ |
| 35 | Virovirokun | VIRUS | 7 | 8 | 6 | 4 | ✓ |
| 36 | Swatchling | COLOR | 9 | 9 | 9 | 5 | ✓ |
| 40 | Werewerewire | ELEC:FIGHT | 14 | 11 | 11 | 1 | ✓ |
| 42 | Tasque Manager | CAT:ORDER | 10 | 10 | 7 | 1 | ✗ |
| 44 | Mauswheel | MOUSE:MOUSE:MOUSE | 13 | 10 | 11 | 1 | ✓ |

### Chapter 3 Recruits

| Type ID | Name | Element | Level | AT | DF | Recruit Count | Placeable |
|---:|---|---|---:|---:|---:|---:|---:|
| 54 | Shadowguy | CHAOS:MUSIC | 18 | 13 | 13 | 25 | ✓ |
| 55 | Shuttah | COPY | 20 | 14 | 20 | 2 | ✓ |
| 56 | Zapper | ORDER:ELEC | 19 | 16 | 18 | 2 | ✓ |
| 57 | Ribbick | FROG:DUST | 16 | 15 | 12 | 3 | ✓ |
| 58 | Watercooler | WATER | 24 | 20 | 12 | 1 | ✓ |
| 59 | Pippins | CHAOS:LUCK | 17 | 14 | 10 | 5 | ✓ |
| 60 | Elnina | WATER:ICE | 22 | 21 | 22 | 1 | paired (2) |
| 61 | Lanino | FIRE:WIND | 22 | 22 | 21 | 1 | paired (2) |

### Chapter 4 Recruits

| Type ID | Name | Element | Level | AT | DF | Recruit Count | Placeable |
|---:|---|---|---:|---:|---:|---:|---:|
| 62 | Guei | SPIRIT:FIRE | 26 | 20 | 14 | 3 | ✓ |
| 63 | Balthizard | STEEL:SMELL | 28 | 14 | 30 | 4 | ✓ |
| 64 | Bibliox | MAGIC | 20 | 14 | 14 | 3 | ✓ |
| 65 | Mizzle | WATER | 31 | 21 | 21 | 2 | ✓ |
| 66 | Wicabel | STEEL:MUSIC | 33 | 14 | 28 | 2 | ✓ |
| 67 | Winglade | BLADE | 32 | 28 | 12 | 2 | ✓ |
| 68 | Organikk | STEEL:MUSIC | 32 | 26 | 22 | 3 | ✓ |
| 69 | Miss Mizzle | WATER | 38 | 28 | 28 | 1 | paired (2) |

---

## Recruit Info Fields

`scr_recruit_info(type_id)` sets:

| Field | Type | Purpose |
|---|---|---|
| `_name` | string | Display name |
| `_desc` | string | Description |
| `_like` | string | Likes |
| `_dislike` | string | Dislikes |
| `_chapter` | int | Origin chapter |
| `_level` | int/string | Level |
| `_attack` | int | AT stat |
| `_defense` | int | DF stat |
| `_element` | string | Element tag (colon-separated) |
| `_sprite` | sprite | Overworld sprite |
| `_dialogue` | string[] | Castle Town dialogue lines |
| `_recruitcount` | int | Spares needed for full recruitment |
| `_placeable` | int | `0` = not placeable, `1` = placeable, `2` = paired placement |

---

## Flag Storage

Recruitment progress is stored in `global.flag[type_id + 600]`:

- `0.0` = not recruited
- `0.0 < value < 1.0` = partially recruited
- `1.0` = fully recruited

For a monster with `recruitcount = 5`, each spare adds `0.2`. So flags at `0.2`, `0.4`, `0.6`, `0.8`, `1.0`.

The current progress is computed as:

```gml
_recruitcountcurrent = round(global.flag[arg0 + 600] / (1 / _recruitcount));
```

---

## Placeable Values

| `_placeable` | Behavior |
|---:|---|
| 0 | Not placeable in Castle Town (bosses like JEVIL, Tasque Manager) |
| 1 | Standard Castle Town placement |
| 2 | Paired placement — Elnina+Lanino, Miss Mizzle |

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a recruitable monster | Add a case in `scr_recruit_info`, set `recruitable = 1` in the enemy object |
| Change recruitment speed | Change `_recruitcount` in `scr_recruit_info` |
| Check if a monster is recruited | Read `global.flag[monstertype + 600]` |
| Block recruitment globally | Set `global.flag[61] = 1` |
| Add Castle Town behavior | Edit `scr_recruitchecks` and the Castle Town room events |