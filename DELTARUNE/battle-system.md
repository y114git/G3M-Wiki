# Battle System

The numbered chapters all center battle flow around `obj_battlecontroller`, but the runtime grows in three clear stages:

- Chapter 1: compact original controller
- Chapter 2: major menu / spell / ACT / ambush expansion
- Chapters 3 and 4: Chapter 2 framework plus more forced-action, sprite-control, and encounter-specific overlays

This page documents the runtime objects and scripts as seen through UndertaleModTool.

For generic GameMaker engine behavior behind object events, alarms, and scope-changing with `with (...)`, see:

- https://manual.gamemaker.io/monthly/en/The_Asset_Editors/Object_Properties/Object_Events.htm
- https://manual.gamemaker.io/lts/en/GameMaker_Language/GML_Overview/Language_Features/with.htm
- https://manual.gamemaker.io/monthly/en/GameMaker_Language/GML_Overview/Variables_And_Variable_Scope.htm

---

## Core Runtime Pieces

### Main controller

- `objects/obj_battlecontroller/Create_0.gml`
- `objects/obj_battlecontroller/Step_0.gml`
- alarm and draw events on the same object

### Supporting scripts

- `scr_encountersetup`
- `scr_spellinfo_all`
- `scr_spellmenu_setup` in Chapter 2+
- `scr_damage`
- `scr_damage_enemy`
- `scr_dead`
- `scr_heal`
- `scr_battletext`

### Core battle objects

- `obj_battlecontroller`
- `obj_heart`
- `obj_tensionbar`
- `obj_herokris`
- `obj_herosusie`
- `obj_heroralsei`
- `obj_heronoelle` in Chapter 2+
- `obj_monsterparent`
- `obj_dmgwriter`
- `obj_face` / `obj_face_parent`

---

## Battle Boot Flow

The usual runtime sequence is:

1. overworld logic decides an encounter should begin
2. `scr_encountersetup(encounter_id)` fills monster spawn data and hero spawn positions
3. `obj_battlecontroller` is created
4. its Create event resets battle globals, spawns monsters and heroes, and builds menu data

### `scr_encountersetup`

This script is the encounter recipe layer.

It pre-populates:

- `global.heromakex[]`
- `global.heromakey[]`
- `global.monsterinstancetype[]`
- `global.monstertype[]`
- `global.monstermakex[]`
- `global.monstermakey[]`
- `global.battlemsg[0]`

The default setup always creates a 3-slot battle scaffold first, then overrides per encounter id.

Important chapter difference:

- Chapter 2 still uses `__view_get(e__VW.XView, 0)` / `YView`
- Chapter 3 does the same, but adds Chapter 3-specific runtime state like ranking values and board-era intro strings
- Chapter 4 switches to `camerax()` / `cameray()` for its encounter positioning baseline

Chapter 4 renames the controller to `obj_battlecontroller_ch4` with its own object hierarchy, not a shared parent.

---

## `obj_battlecontroller` Create Event

### Shared responsibilities across all numbered chapters

The Create event always does the same broad jobs:

1. start or loop battle music
2. set battle-global state
3. clear per-turn arrays
4. reset monster slots
5. instantiate monsters
6. compute effective party combat stats
7. instantiate battle hero objects
8. build menu state
9. create TP UI

### Chapter 1 baseline

The Chapter 1 controller is compact and direct. It explicitly resets many arrays in-place inside Create:

- `global.monster*`
- `global.act*`
- `global.acting`
- `global.charaction`
- `global.charspecial`
- `global.chartarget`
- `global.faceaction`
- `global.battleat`
- `global.battledf`
- `global.battlemag`

It spawns monsters directly with:

```gml
global.monsterinstance[i] = instance_create(global.monstermakex[i], global.monstermakey[i], global.monsterinstancetype[i]);
global.monsterinstance[i].myself = i;
with (global.monsterinstance[i]) { event_user(12); }
```

and spawns heroes by checking `global.char[i]` against character ids `1`, `2`, `3`.

### Chapter 2 expansion

Chapter 2 keeps the same skeleton, but moves several responsibilities into helper scripts and adds more per-battle state:

- `scr_monster_statreset(i)`
- `scr_monster_makeinstance(i)`
- `scr_spellmenu_setup()`

New state added or made explicit includes:

- `myfightreturntimer`
- `messagepriority`
- `attackpriority`
- `hidemercy`
- `global.turntimer`
- `spellpage`
- `global.currentactingchar`
- `global.actingsingle[]`
- `global.actingsimul[]`
- `global.actingtarget[]`
- `global.actingchoice[]`
- `global.battleactcount[]`
- `global.battlespell[][]`
- `global.battlespellname[][]`
- `global.battlespelldesc[][]`
- `global.battlespellcost[][]`
- `global.battlespelltarget[][]`
- `global.battlespellspecial[][]`

This is the point where the battle menu stops being “pick spell from `global.spell`” and becomes a synthesized runtime menu that mixes ACT-like commands and normal spells into one generated table.

### Chapter 3 additions

Chapter 3 largely inherits the Chapter 2 controller, then layers on encounter-specific and presentation-specific switches such as:

- `disablesusieact`
- `mercytotal`
- `idefendedthisturn`
- `ypostenna`
- `oopsallacts`
- `spadebuttonenabled`
- `spadebuttoncount`

It also introduces helper scripts outside the controller that can directly manipulate battle state:

- `scr_battle_force_action`
- `scr_battle_sprite_set`
- `scr_battle_sprite_reset`
- `scr_battle_sprite_actflash`

These are important for scripted battles and show sequences because they let cutscene logic drive the same hero battle objects the player normally controls.

### Chapter 4 additions

Chapter 4 keeps the Chapter 3 model and adds more special-case state inside Create:

- `questionmercy[]`
- `soundbattle`
- `hidestar`
- `disablesusieattack`
- chapter-4-only encounter branches that rewrite `global.char[]` before the battle fully starts

Examples:

- encounter `160` or `176` forces a Susie-only layout
- encounter `186` forces a Kris + Susie layout

By Chapter 4, party composition can be rewritten inside the controller itself for special battles, not only in overworld prep.

---

## Effective Combat Stats

All numbered chapters compute effective combat stats from base stats plus item modifiers:

```gml
global.battleat[i] = global.at[global.char[i]] + global.itemat[global.char[i]][0] + global.itemat[global.char[i]][1] + global.itemat[global.char[i]][2];
global.battledf[i] = global.df[global.char[i]] + global.itemdf[global.char[i]][0] + global.itemdf[global.char[i]][1] + global.itemdf[global.char[i]][2];
global.battlemag[i] = global.mag[global.char[i]] + global.itemmag[global.char[i]][0] + global.itemmag[global.char[i]][1] + global.itemmag[global.char[i]][2];
```

The important runtime detail is that the battle controller does not recalculate from equipment ids directly. It trusts the precomputed `global.itemat/itemdf/itemmag` modifier arrays.

if a mod changes equipment behavior, the battle layer usually does not need patching unless the way those arrays are populated also changes.

---

## Hero Spawn Logic

Hero battle objects are selected from `global.char[]`:

- `1` -> `obj_herokris`
- `2` -> `obj_herosusie`
- `3` -> `obj_heroralsei`
- `4` -> `obj_heronoelle` in Chapter 2+

Each spawned hero receives:

- `myself` = party slot
- `char` = character id
- `depth = 200 - (i * 20)`

That depth staggering is one of the small but important presentation rules to preserve if recreating battle visuals from scratch.

---

## Menu Runtime: Chapter 1 vs Chapter 2+

### Chapter 1

Chapter 1 is closer to a direct menu state machine:

- action flags live in `global.charaction[]`
- spell choices are read more directly from the fixed spell layout
- ACT data lives in the monster arrays

### Chapter 2+

`scr_spellmenu_setup()` becomes the key synthesis step.

It builds a chapter-era runtime menu per party slot by combining:

1. character-specific ACT-style commands
2. normal learned spells from `global.spell[char][slot]`

Important arrays filled here:

- `global.battlespell`
- `global.battlespellname`
- `global.battlespelldesc`
- `global.battlespellcost`
- `global.battlespelltarget`
- `global.battlespellspecial`

Special values:

- negative spell ids are used for generated ACT-like commands
- normal spell ids are appended after the ACT-generated segment

`scr_spellmenu_setup()` is the menu-integration layer for later spell, ACT, and party-command variants.

---

## Turn State Variables

The battle system is heavily global-state-driven.

Core variables include:

- `global.myfight`
- `global.mnfight`
- `global.charturn`
- `global.currentactingchar` in Chapter 2+
- `global.attacking`
- `global.acting`
- `global.spelldelay`
- `global.turntimer`
- `global.bmenuno`

Chapter 2+ adds finer-grained acting coordination through:

- `global.actingsingle`
- `global.actingsimul`
- `global.actingtarget`
- `global.actingchoice`

These are used to support more complex ACT choreography and later scripted interactions.

---

## `scr_spellmenu_setup()` Actual Layout

Chapter 2+ builds the spell/ACT menu in two passes.

### Pass 1: generated ACT-style commands

For each active battle slot `__i = 0 .. 2` and ACT slot `__fj = 0 .. 5`, the script checks character-specific ACT permission arrays and writes synthetic entries into the later battle menu arrays.

Kris path:

```gml
if (global.char[__i] == 1)
{
    if (global.canact[0][__fj] == 1)
    {
        global.battlespell[__i][__fj] = -1;
        global.battlespellcost[__i][__fj] = global.actcost[0][__fj];
        global.battlespellname[__i][__fj] = global.actname[0][__fj];
        global.battlespelldesc[__i][__fj] = global.actdesc[0][__fj];
        global.battlespelltarget[__i][__fj] = 0;
        global.battlespellspecial[__i][__fj] = 1;
    }
}
```

Susie, Ralsei, and Noelle use:

- `global.canactsus`, `global.actcostsus`, `global.actnamesus`, `global.actdescsus`
- `global.canactral`, `global.actcostral`, `global.actnameral`, `global.actdescral`
- `global.canactnoe`, `global.actcostnoe`, `global.actnamenoe`, `global.actdescnoe`

and write:

- `global.battlespell[slot][index] = -1`
- `global.battlespelltarget[slot][index] = 2`
- `global.battlespellspecial[slot][index] = 2`, `3`, or `4`

If more than one monster type is present, `__actnamecheck` forces:

- `S-Action`
- `R-Action`
- `N-Action`

### Pass 2: learned spells

After `scr_spellinfo_all()`, learned spells are appended after the ACT segment:

```gml
__ib = global.battleactcount[__i] + __fj;
global.battlespell[__i][__ib] = global.spell[global.char[__i]][__fj];
global.battlespellcost[__i][__ib] = global.spellcost[global.char[__i]][__fj];
global.battlespellname[__i][__ib] = global.spellnameb[global.char[__i]][__fj];
global.battlespelldesc[__i][__ib] = global.spelldescb[global.char[__i]][__fj];
global.battlespelltarget[__i][__ib] = global.spelltarget[global.char[__i]][__fj];
```

The menu layout is:

1. generated ACT-like commands first
2. normal learned spells second

---

## `obj_battlecontroller` Step Event: Top-Level Gates

Chapter 4 `Step_0.gml` begins with encounter-specific hard gates that can `exit;` before the normal battle state machine runs.

Examples:

- Gerson intro checks on `obj_balthizard_enemy`
- `obj_holywatercooler_enemy.introcon`
- `soundbattle == true`
- hammer/titan/rematch end-state checks

These branches live inside the controller, not only inside enemy objects.

---

## Victory Branch In Step

When `victory == 1 && victoried == 0`, Chapter 4 immediately sets:

```gml
global.faceaction[0] = 0;
global.faceaction[1] = 0;
global.faceaction[2] = 0;
global.battleend = 1;
global.mnfight = -1;
global.myfight = 7;
```

Then it destroys:

- `battlewriter`
- `obj_face`
- `obj_smallface`

and revives dead party members to one-eighth max HP:

```gml
if (global.hp[i] < 1)
{
    global.hp[i] = round(global.maxhp[i] / 8);
}
```

### Reward calculation

Chapter 4 modifies `global.monstergold[3]` before awarding it:

```gml
global.monstergold[3] += floor(global.tension / 10) * global.chapter;
if (global.charweapon[1] == 8)  global.monstergold[3] += floor(global.monstergold[3] / 20);
if (global.charweapon[1] == 53) global.monstergold[3] += floor(global.monstergold[3] / 20);
global.monstergold[3] *= 1 + (scr_armorcheck_equipped_party(8) * 0.05);
global.monstergold[3] *= 1 + (scr_armorcheck_equipped_party(21) * 0.3);
global.monstergold[3] -= global.monstergold[3] * (scr_armorcheck_equipped_party(54) * 0.1);
global.monstergold[3] = floor(global.monstergold[3]);
```

Then:

- `global.flag[37] == 1` forces zero gold
- `global.flag[63] == 1` uses alternate victory text and calls `scr_levelup()`

### Victory writer creation

The controller builds victory text directly:

```gml
global.battlemsg[0] = stringsetsubloc("* You won^1!&* Got ~1 EXP and ~2 D$./%", string(global.monsterexp[3]), string(global.monstergold[3]), ...);
global.msg[0] = global.battlemsg[0];
global.typer = global.battletyper;
lastbattlewriter = scr_battletext();
```

---

## Main Command Menu: `global.bmenuno == 0`

The root player-input branch is:

```gml
if (global.myfight == 0)
{
    if (global.bmenuno == 0)
    {
        ...
    }
}
```

This state uses `global.bmenucoord[0][global.charturn]` as the top-level command cursor.

### Horizontal navigation

Left/right input wraps between command ids `0 .. 4`.

Restrictions are applied directly at cursor time:

- `disableitembutton == 1` skips command `2`
- `disablesusieattack == 1` blocks command `0` when `global.charturn == 1`

### Confirm routing

Pressing confirm routes by command id:

- `0` -> `global.bmenuno = 1`
- `1` -> `global.bmenuno = 2` for non-Kris, `11` for Kris
- `2` -> `global.bmenuno = 4` if an item exists
- `3` -> `global.bmenuno = 12`
- `4` -> immediate defend commit

The defend path executes directly:

```gml
scr_tensionheal(40); // or 5 in some Chapter 4 encounters
global.faceaction[global.charturn] = 4;
global.charaction[global.charturn] = 10;
scr_nexthero();
```

---

## Spell Menu: `global.bmenuno == 2`

Chapter 4 still contains a direct spell-menu branch:

```gml
if (global.bmenuno == 2 && global.flag[34] == 1)
{
    ...
}
```

Inside this branch:

- `battlewriter.skipme = 1`
- writer/face/smallface depths are pushed to `10`
- spell cursor uses `global.bmenucoord[2][global.charturn]`
- the selected spell id comes from `global.spell[thischar][spellcoord]`
- current TP preview is written into `global.tensionselect`

Cursor motion is hand-authored around the spell-slot table:

- left/right move between odd/even neighbors
- up/down move by 2
- one branch special-cases slot `5` when spell `6` exists and spell `7` does not

---

## Battle Writer Recreation In Step

At root menu state, if the current battle writer no longer exists, Step recreates it:

```gml
global.msg[0] = global.battlemsg[0];
global.typer = global.battletyper;
scr_battletext();
```

Chapter 4 can also rewrite the current speaker just before recreation:

```gml
if (global.chapter == 4 && facevar == 1)
{
    scr_speaker("susie");
    global.fe = 17;
    facevar = 0;
}
```

---

## Monster Runtime Data

Battle monsters are mirrored across:

- monster instances
- many `global.monster*` arrays

Important arrays:

- `global.monster[]`
- `global.monsterinstance[]`
- `global.monstername[]`
- `global.monstertype[]`
- `global.monsterhp[]`
- `global.monstermaxhp[]`
- `global.monsterat[]`
- `global.monsterdf[]`
- `global.monsterx[]`
- `global.monstery[]`
- `global.monstergold[]`
- `global.monsterexp[]`
- `global.monsterstatus[]`
- `global.sparepoint[]`
- `global.mercymod[]`
- `global.mercymax[]`

And for ACT logic:

- `global.act[][]`
- `global.canact[][]`
- `global.actname[][]`
- `global.actdesc[][]`
- `global.actcost[][]`

Chapter 2+ further fans this out into character-specific ACT arrays like:

- `global.canactsus`
- `global.canactral`
- `global.canactnoe`

Which are consumed by `scr_spellmenu_setup()`.

---

## Forced Battle Scripting In Later Chapters

By Chapter 3, battle is no longer only player-driven.

### `scr_battle_force_action`

This helper can target a named party member (`"kris"`, `"susie"`, `"ralsei"`, `"noelle"`) and force states such as:

- `"hurt"`
- `"defend"`
- `"attack"`
- `"spell"`
- `"spare"`
- `"item"`
- `"act"`

It writes directly into:

- hero object state
- `global.faceaction`
- `global.chartarget`
- `global.charaction`
- `global.charspecial`
- `global.actingchoice`

This is critical for scripted boss fights and cinematic battle moments.

### `scr_battle_sprite_set`

This helper forcibly puts a battle hero object into state `8`, changes sprite and speed, and resets face state. It is pure battle presentation control and is heavily useful for staged scenes.

---

## Battle Text Layer

Battle UI text still goes through the same text runtime as overworld dialogue, but the battle controller sets:

- `global.typer = 4`
- `global.battletyper = 4`

and stores the returned writer in `battlewriter`.

Battle text uses the normal writer stack with battle-specific defaults.

See [Dialogue System](dialogue-system.md).

---

## Ambush And Special Openers

Chapter 2+ explicitly supports `global.ambush` values in Create.

Observed handling:

- `global.ambush == 1` calls `scr_ambush()`
- `global.ambush == 2` sets `firststrike = 1` on monsters and grants starting TP

Encounter openers can alter battle state before the first visible menu frame.

---

## Encounter-Specific Battle State

Chapter 3 and Chapter 4 `obj_battlecontroller/Create_0.gml` contain many encounter-specific branches.

Examples include:

- portrait and expression overrides through `global.fc`, `global.fe`, `global.flag[62]`
- special sound battle flags
- special mercy modes in Chapter 4
- battle-specific party rewrites in Chapter 4

Battle runtime behavior is split between the generic controller framework and many encounter-specific Create/Step branches.

---

## What To Patch For Mods

### To change generic battle flow

Inspect:

- `obj_battlecontroller`
- `scr_encountersetup`
- `scr_spellmenu_setup` in Chapter 2+

### To change damage / healing

Inspect:

- `scr_damage`
- `scr_damage_enemy`
- `scr_heal`

### To change ACT/spell menu composition in Chapter 2+

Inspect:

- `scr_spellmenu_setup`
- `scr_spellinfo`
- monster ACT arrays populated by monster init logic

### To change scripted battle cinematics in Chapter 3+

Inspect:

- `scr_battle_force_action`
- `scr_battle_sprite_set`
- related cutscene scripts that call them

---

## Related Pages

- [Damage System](damage-system.md) — full damage pipeline, defense formulas, element reduction, DEFEND mechanics
- [Tension / TP System](tension-system.md) — TP gain, graze, and cost mechanics
- [Spells & Abilities](spells-abilities.md) — spell costs, targets, and menu synthesis
- [Monster Runtime](monster-runtime.md) — complete monster roster, stats, ACT menus
- [Heart / SOUL Mechanics](heart-mechanics.md) — heart color modes and movement
- [Game Over System](game-over-system.md) — death, game over modes, and cantdie mechanic
- [Recruit System](recruit-system.md) — post-spare recruitment tracking