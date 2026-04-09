# Monster Runtime

This page documents the enemy-side battle runtime: how encounter ids become live monster instances, what stats and ACT menus they carry, and how the mercy system works.

---

## Core Scripts

| Script | Purpose |
|---|---|
| `scr_encountersetup` | Writes encounter recipe into global arrays |
| `scr_monster_makeinstance` | Creates the actual object instance |
| `scr_monster_statreset` | Normalizes battle-side fields |
| `scr_monstersetup` | Fills stats, names, ACT data, and special flags by type |
| `scr_monster_actreset` | Clears ACT arrays before setup |
| `scr_monsterdefeat` | Post-defeat cleanup, rewards, and progression |
| `scr_monster_make_tired` | Forces tired state |

---

## Setup Pipeline

1. `scr_encountersetup(encounter_id)` → populates `global.monstertype[]`, `global.monsterx[]`, `global.monstery[]`
2. `obj_battlecontroller` Create → spawns instances using those arrays
3. `scr_monster_makeinstance()` → creates the actual enemy object
4. `scr_monster_statreset()` → normalizes all battle fields
5. `scr_monstersetup()` → branches on `global.monstertype[myself]` to set stats and ACT menus

---

## Global Monster Arrays

| Array | Purpose |
|---|---|
| `global.monstertype[slot]` | Type ID |
| `global.monsterinstance[slot]` | Object instance |
| `global.monstername[slot]` | Display name |
| `global.monsterhp[slot]` | Current HP |
| `global.monstermaxhp[slot]` | Maximum HP |
| `global.monsterat[slot]` | Attack |
| `global.monsterdf[slot]` | Defense |
| `global.monsterexp[slot]` | EXP award (always 0 in DELTARUNE) |
| `global.monstergold[slot]` | Gold award |
| `global.monsterx[slot]` | X position |
| `global.monstery[slot]` | Y position |
| `global.sparepoint[slot]` | Starting mercy |
| `global.mercymod[slot]` | Mercy modifier |
| `global.mercymax[slot]` | Mercy threshold (100 for standard, 999 for bosses) |
| `global.monstertired[slot]` | Tired state |
| `global.monstermercy[slot]` | Current mercy % |

---

## ACT Menu Arrays

Per-monster ACT data is stored in parallel arrays:

| Array | Purpose |
|---|---|
| `global.canact[slot][i]` | ACT slot enabled (1/0) |
| `global.actname[slot][i]` | ACT name (Kris) |
| `global.actdesc[slot][i]` | ACT description |
| `global.actcost[slot][i]` | ACT TP cost |
| `global.actactor[slot][i]` | Required actor (1=party, 2=Susie, 3=Ralsei, 4=both, 5=Noelle+Kris) |
| `global.actsimul[slot][i]` | Simultaneous ACT flag |
| `global.canactsus[slot][i]` | Susie ACT enabled |
| `global.actnamesus[slot][i]` | Susie ACT name |
| `global.canactral[slot][i]` | Ralsei ACT enabled |
| `global.actnameral[slot][i]` | Ralsei ACT name |
| `global.canactnoe[slot][i]` | Noelle ACT enabled |
| `global.actnamenoe[slot][i]` | Noelle ACT name |

---

## Complete Monster Roster

### Chapter 1 Monsters

| Type | Name | HP | AT | DF | Gold | Mercy Max | Key ACTs |
|---:|---|---:|---:|---:|---:|---:|---|
| 1 | Enemy | 130 | 7 | 0 | 20 | 100 | Check, Warning, Victory, SimuDance |
| 2 | Lancer | 540 | 5 | 1 | 20 | 100 | Check, Warning, Compliment |
| 3 | Dummy | 450 | 0 | 0 | 0 | 100 | Check, Hug, Hug Ralsei |
| 4 | Ralsei | 90 | 8 | 6 | 0 | 100 | Check, Hug |
| 5 | Rudinn | 120 | 5 | 0 | 30 | 100 | Check, Convince, Lecture |
| 6 | Hathy | 150 | 6 | 0 | 28 | 100 | Check, Flatter, X-Flatter |
| 7 | Clover | 270 | 8 | 1 | 43 | 100 | Check + random topic trio |
| 9 | C.Round | 10 | 5 | 0 | 10 | 100 | Check |
| 10 | K.Round | 1300 | 7.5 | 3 | 100 | 100 | Check, Bow, Deep Bow |
| 11 | Ponman | 140 | 7 | 1 | 23 | 100 | Check, Goodnight, Lullaby |
| 12 | Lancer (boss) | 2400 | 4 | -40 | 0 | 100 | Check |
| 13 | Rabbick | 120 | 8 | 1 | 38 | 100 | Check, Blow On, BreathAll |
| 14 | Bloxer | 130 | 9 | 2 | 38 | 100 | Check, Rearrange |
| 15 | Jigsawry | 90 | 5 | 0 | 20 | 100 | Check, Befriend |
| 16 | Clover (Ch2) | 270 | 6 | 1 | 80 | 100 | Check, TalkBday, TalkBoys, TalkSports, TalkAnimals, TalkTrees |
| 17 | DoomTank | 700 | 6 | 0 | 0 | 100 | Check, Hug, Flatter, Diplomacy, Smile |
| 18 | Lancer (fight) | 800 | 6 | 1 | 0 | 100 | Check, Anything, X-Anything |
| 19 | Susie | 120 | 7 | varies | 0 | 100 | Check, Anything, Sing |
| 20 | JEVIL | 3500 | 10 | 5 | 0 | **999** | Check, Pirouette (50 TP), Hypnosis (125 TP) |
| 25 | King | 2800 | 8 | 0 | 0 | **999** | Check, Talk×3 → Courage/RedBuster/DualHeal |

### Chapter 2 Monsters

| Type | Name | HP | AT | DF | Gold | Key ACTs |
|---:|---|---:|---:|---:|---:|---|
| 21 | K.Round (Ch2) | 1300 | 8 | 3 | 100 | Check, Bow, Susie's Idea |
| 22 | Rudinn Ranger | 170 | 8 | 0 | 45 | Check, Convince, Compliment |
| 23 | Head Hathy | 190 | 8 | 0 | 40 | Check, Flirt, X-Flirt |
| 30 | Ambyu-Lance | 300 | 8 | 0 | 84 | Check, Avoid/GetHit or Hospitality |
| 31 | Poppup | 120 | 9 | 0 | 77 | Check, Click, Block |
| 32 | Tasque | 240 | 8 | 0 | 75 | Check, Petting, Roar/SoftVoice |
| 33 | Werewire | 240 | 5/8 | 0 | 79 | Check, JiggleJiggle, ThrowWire |
| 34 | Maus | 120 | 8 | 0 | 60 | Check, ClickOn, Squeak |
| 35 | Virovirokun | 200 | 8 | 0 | 88 | Check, Dark Humor, Air Quotes |
| 36 | Swatchling | 500 | 13 | 3 | 95 | Check, Toast, Serve |

### Chapter 3 Monsters

| Type | Name | HP | AT | DF | Gold | Key ACTs |
|---:|---|---:|---:|---:|---:|---|
| 52 | Jigsaw Joe | 1 | 8 | 0 | 0 | Check, Shave |
| 53 | Pipis | 200 | 8 | 0 | 0 | Check |
| 56 | Zapper | 421 | 11 | 0 | 80 | Check, VolumeUp, Mute (80 TP), OffButton (250 TP) |
| 57 | Ribbick | 421 | 11 | 0 | 72 | Check, CroakOn, CroakOnX |
| 59 | Pippins | 421 | 8 | 0 | 30 | Check, Bet, Cheat |

### Chapter 4 Monsters

| Type | Name | HP | AT | DF | Gold | Key ACTs |
|---:|---|---:|---:|---:|---:|---|
| 62 | Guei | 470 | 13 | 0 | 120 | Check, Exercism, Xercism, OldMan |
| 63 | Balthizard | 470 | 14 | 0 | 130 | Check, Shake, ShakeX, LightUp, OldMan |
| 64 | Bibliox | 470 | 14 | 0 | 125 | Check, Proofread, EasyProof |
| 65 | Mizzle | 470 | 13 | 0 | 110 | Check, Dazzle, Embezzle, Nuzzle, LullabyX |
| 66 | Wicabel | 470 | 9/13 | 0 | 160 | Check, Tuning, Tuningx2 |
| 67 | Winglade | 470 | 14 | 0 | 155 | Check, Spin, SpinS, Whirl (160 TP) |
| 68 | Organikk | 470 | 11/14 | 0 | 150 | Check, Perform, Harmonize×2 |
| 69 | HolywaterCooler | 1740 | 14 | 0 | 500 | Check, Flirt, BegForMercy, Chat |

### Chapter 4 Bosses

| Type | Name | HP | AT | DF | Gold | Key ACTs |
|---:|---|---:|---:|---:|---:|---|
| 105 | Hammer of Justice | 1350 | 14 | 0 | 0 | Check |
| 106 | ??? | 1350 | 14 | 0 | 0 | Talk |
| 107 | Jackenstein | 1350 | 14 | 0 | 0 | Check, Unleash (150 TP), ScaredyCat (5 TP) |
| 108 | Titan | **21000** | 18 | 0 | 0 | Check, Brighten (10 TP), DualHeal (40 TP), Unleash (200 TP) |
| 109 | Titan Spawn | 3000 | 18 | 0 | 0 | Check, Brighten (10 TP), DualHeal (40 TP), Banish (160 TP) |
| 110 | Elnina (boss) | 4440 | 16 | 0 | 0 | Check, Umbrella, WarmHat |
| 111 | Lanino (boss) | 4440 | 16 | 0 | 0 | Check, Telescope, Sunglasses |

---

## Conditional ACT Logic

ACT menus are not static. Common conditions include:

| Condition | Effect |
|---|---|
| `scr_havechar(2)` (Susie present) | Enables follower-specific ACTs (Warning, X-Flatter, Rival) |
| `scr_havechar(4)` (Noelle present) | Swaps ACT set entirely (e.g. Ambyu-Lance Hospitality) |
| `global.plot` threshold | Enables/disables ACTs by story point |
| `global.encounterno` | Per-encounter ACT variations |
| `global.tempflag[]` states | Boss phase-dependent ACT unlocks (King's Courage/RedBuster/DualHeal) |
| `global.flag[220]` | Switches Spamton NEO's mode-selection ACT |

---

## Mercy System

| Variable | Purpose |
|---|---|
| `global.sparepoint[slot]` | Starting mercy percentage |
| `global.mercymod[slot]` | Added to mercy during certain ACTs |
| `global.mercymax[slot]` | Threshold for spare (100 = standard, 999 = bosses) |

Standard enemies have `mercymax = 100`. ACTs that grant mercy add to `global.sparepoint[]`. When `sparepoint >= mercymax`, the enemy can be spared.

Bosses with `mercymax = 999` (JEVIL, King) require scripted spare conditions instead of a mercy meter.

---

## Tired State

When a monster becomes TIRED:

- `global.monstertired[slot] = 1`
- Pacify and SleepMist become effective
- Visual indicators appear on the monster

Tired is triggered by specific ACT results, HP thresholds, or monster-specific scripts.

---

## Debug Type 500-501

Types 500 and 501 (`Multiboss Example`, `Multiboss C Example`) are debug/test monsters with expanded ACT menus. They demonstrate the simultaneous-ACT system (`actsimul`) and per-character ACT arrays.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a new monster type | Add a case block in `scr_monstersetup` |
| Change monster stats | Edit the HP/AT/DF/Gold assignments in `scr_monstersetup` |
| Change ACT menu | Edit `global.canact[][]`, `global.actname[][]`, etc. |
| Change spare threshold | Edit `global.mercymax[]` |
| Add encounter-specific logic | Edit `scr_encountersetup` |
| Change defeat rewards | Edit `scr_monsterdefeat` |
| Make ACTs conditional | Add `scr_havechar()` / `global.plot` guards |

---

## Relationship To Other Pages

- [Battle System](battle-system.md) explains how the controller consumes monster data
- [Damage System](damage-system.md) explains how monster AT feeds into damage calculations
- [Recruit System](recruit-system.md) explains post-spare recruitment
- [Spells & Abilities](spells-abilities.md) explains how ACT commands integrate with the spell menu