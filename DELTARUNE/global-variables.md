# Global Variables

DELTARUNE stores almost all long-lived runtime state in `global.*` variables. If you want to understand how the shipped game actually works through UndertaleModTool, this is one of the most important pages in the entire wiki.

This page is written from the shipped runtime data, not from editor-side project assumptions.

The main initialization root is:

- `scripts/scr_gamestart/scr_gamestart.gml`

and the main persistence roots are:

- `scripts/scr_saveprocess/scr_saveprocess.gml`
- `scripts/scr_load/scr_load.gml`

Chapter 2, Chapter 3, and Chapter 4 heavily expand the global-state surface compared to Chapter 1.

For generic GameMaker variable-scope behavior, see:

- https://manual.gamemaker.io/monthly/en/GameMaker_Language/GML_Overview/Variables_And_Variable_Scope.htm
- https://manual.gamemaker.io/lts/en/GameMaker_Language/GML_Overview/Arrays.htm

---

## Why `global.*` Matters So Much In DELTARUNE

DELTARUNE is not architected around a small amount of encapsulated object state. Instead, many systems communicate through shared global arrays and flags.

That includes:

- save/load
- dialogue
- battle
- menus
- localization
- chapter progression
- overworld transitions
- item/equipment modifiers
- cutscene orchestration

This is why you can often understand an entire subsystem by locating:

1. where its globals are initialized in `scr_gamestart`
2. where they are rewritten in object events / helper scripts
3. where they are serialized in `scr_saveprocess`

---

## Initialization Roots By Chapter

### Chapter 1

Chapter 1 `scr_gamestart` is the smallest baseline. It directly initializes:

- chapter / story progression
- party and stats
- item / weapon / armor arrays
- spell arrays
- monster placeholders
- menu/dialogue globals
- `global.flag[0..9998]`
- legacy Light World arrays like `global.litem[]` and `global.phone[]`

### Chapter 2

Chapter 2 keeps the same broad shape but adds major new runtime groups:

- `global.townname`
- `global.ambush`
- `global.pocketitem[0..71]`
- 20-sized character/stat arrays
- 48-sized weapon / armor arrays
- elemental equipment arrays
- `global.monsterattackname[]`
- `global.smimage[]`
- `global.smimagespeed[]`
- `global.sminstance[]`
- `global.msgno`
- `global.battletyper`
- `global.cinstance[]`

### Chapter 3

Chapter 3 keeps the Chapter 2 base and adds more writer / presentation globals in `scr_gamestart`, including:

- `global.writerobj[]`
- `global.writerobjsettinga[]`
- `global.writerobjsettingb[]`
- `global.writerobjx[]`
- `global.writerobjy[]`

It also seeds more Chapter 3-related flags during startup.

### Chapter 4

Chapter 4 keeps the Chapter 3-era global layout and adds still more chapter-specific flag seeding and runtime-specific values later consumed by church, darkness, battle-special-case, and rhythm-related systems.

---

## Identity And Save-Slot Globals

### `global.chapter`

This is one of the most important globals in the whole game.

Set in `scr_gamestart`:

```gml
global.chapter = 1; // Chapter 1 runtime
global.chapter = 2; // Chapter 2 runtime
global.chapter = 3; // Chapter 3 runtime
global.chapter = 4; // Chapter 4 runtime
```

Used by:

- `scr_gamestart`
- `scr_spellinfo`
- `scr_spell`
- `scr_load`
- many chapter-conditional content branches

### `global.filechoice`

Active save slot index.

Initialized to:

```gml
global.filechoice = 0;
```

Used by:

- `scr_saveprocess`
- `scr_load`
- launcher/chapter handoff flows

### `global.truename`

Primary player name string written to save data.

Initialized to:

```gml
global.truename = "";
```

### `global.othername[0..6]`

Additional stored names.

In `scr_gamestart`, all are initialized explicitly:

```gml
global.othername[0] = "";
...
global.othername[6] = "";
```

These are part of save payloads in all numbered chapters.

---

## Story / Session Progression

### `global.plot`

Main story progression integer.

Initialized in every chapter runtime:

```gml
global.plot = 0;
```

This is one of the most referenced globals in the entire codebase. It controls:

- room access
- event sequencing
- chapter-specific presentation branches
- special dialogue
- some save/load correction logic

### `global.time`

Playtime counter / persistent time value.

Initialized as:

```gml
global.time = 0;
```

Written at the tail end of save files.

### `global.currentroom`

Persistent room-tracking value.

Important chapter difference:

- Chapter 1 initializes it later and often uses `scr_get_id_by_room_index(room)` when entering rooms
- Chapter 2 and Chapter 3 still rely heavily on room-id conversion helpers
- Chapter 4 `obj_mainchara` Create sets `global.currentroom = room` at that stage before later resolution logic elsewhere

Because room ids are chapter-dependent, this variable is central to save/load correctness.

### `global.darkzone`

Light World / Dark World state flag.

Initialized as:

```gml
global.darkzone = 0;
```

Then forced to `1` in battle controller Create.

Affects:

- movement speed / sprite selection in `obj_mainchara`
- writer font factor `f`
- many room and event branches

---

## Party Slot Mapping

### `global.char[0..2]`

This array does not store arbitrary data. It stores which character id occupies each active party slot.

Default new-game setup:

```gml
global.char[0] = 1;
global.char[1] = 0;
global.char[2] = 0;
```

So the game starts with slot 0 occupied by Kris (`1`) and the other two active slots empty.

Character ids used in battle/party logic:

- `1` = Kris
- `2` = Susie
- `3` = Ralsei
- `4` = Noelle

This array is used everywhere:

- battle hero spawning
- effective stat calculation
- target selection
- party-sensitive cutscenes

### `global.charselect`

Menu-focused selected character index.

Default:

```gml
global.charselect = -1;
```

### `global.charauto[]`

Auto-control flag array.

Chapter 1 explicitly sets:

```gml
global.charauto[0] = 0;
global.charauto[1] = 0;
global.charauto[2] = 1;
global.charauto[3] = 0;
```

Meaning Ralsei is initially auto-controlled in the older Chapter 1 flow.

Later chapter runtimes zero this family more broadly while keeping the array infrastructure.

### `global.charmove[]`

Per-slot movement permission / battle usability state.

Initialized to `0` in `scr_gamestart`, then set in battle bootstrap depending on whether a party slot is occupied.

### `global.charcantarget[]`

Per-slot targetability flag.

Important note: despite the name, in battle Create an occupied slot gets:

```gml
global.charcantarget[i] = 1;
```

so this array should be understood from actual usage context, not only from the variable name.

### `global.chardead[]`

Per-slot dead-state tracking.

Initialized to `0` in startup, then updated by battle damage/death logic.

### `global.invincible[]`

Per-slot invincibility flag array.

Startup default:

```gml
global.invincible[i] = 1;
```

Do not confuse this with:

- `global.inv`
- `global.invc`

which are a different invulnerability timing system.

### `global.charaction[]`

Current action selection per active party slot during battle.

Common values include:

- `0` none
- `1` attack / FIGHT path
- `2` spell-like followup state used by SPARE and some special actions
- `9` ACT-related usage depending on battle phase
- `10` DEFEND

### `global.faceaction[]`

Battle portrait / face state per party slot.

Written heavily by battle menu logic and forced-action scripts.

### `global.charcond[]`

Status/condition slot array.

Default:

```gml
global.charcond[i] = 0;
```

Used by battle and condition-sensitive logic.

---

## Character Stats And Equipment

### Chapter 1 array size

The original Chapter 1 startup loop initializes character stat arrays for `i < 4`.

### Chapter 2+ array size

Chapters 2, 3, and 4 initialize them for `i < 20`.

This is one of the biggest structural breaks in the runtime.

### Core stat globals

For each character id:

- `global.hp[i]`
- `global.maxhp[i]`
- `global.at[i]`
- `global.df[i]`
- `global.mag[i]`
- `global.guts[i]`

Chapter-specific starting values:

#### Chapter 1

- `global.hp[1] = 90`, `global.maxhp[1] = 90`, `global.at[1] = 10`
- `global.hp[2] = 110`, `global.maxhp[2] = 110`, `global.at[2] = 14`, `global.mag[2] = 1`
- `global.hp[3] = 70`, `global.maxhp[3] = 70`, `global.at[3] = 8`, `global.mag[3] = 7`

#### Chapter 2

- Kris: `120 / 120`, `AT 12`
- Susie: `140 / 140`, `AT 16`, `MAG 1`
- Ralsei: `100 / 100`, `AT 10`, `MAG 9`
- Noelle: `90 / 90`, `AT 3`, `DF 1`, `MAG 11`

#### Chapter 3

- Kris: `160 / 160`, `AT 14`
- Susie: `190 / 190`, `AT 18`, `MAG 2`
- Ralsei: `140 / 140`, `AT 12`, `MAG 11`

#### Chapter 4

- Kris: `200 / 200`, `AT 17`
- Susie: `230 / 230`, `AT 22`, `MAG 3`
- Ralsei: `180 / 180`, `AT 15`, `MAG 14`

### Equipped-id globals

- `global.charweapon[i]`
- `global.chararmor1[i]`
- `global.chararmor2[i]`

These store equipment ids, not final stat bonuses.

### `global.weaponstyle[i]`

Stores the current attack-style label / configuration for the character.

Chapter 1 initializes it to a localized slash-style string.

Chapters 2+ initialize it to `0` during base setup and then repopulate through later item/equipment info passes.

---

## Equipment Modifier Arrays

These arrays hold the precomputed bonus data actually consumed by battle logic.

For each character `i` and equipment slot `q`:

- `global.itemat[i][q]`
- `global.itemdf[i][q]`
- `global.itemmag[i][q]`
- `global.itembolts[i][q]`
- `global.itemgrazeamt[i][q]`
- `global.itemgrazesize[i][q]`
- `global.itemboltspeed[i][q]`
- `global.itemspecial[i][q]`

All are zeroed in startup loops.

### Chapter 2+ additions

Only Chapters 2, 3, and 4 add:

- `global.itemelement[i][q]`
- `global.itemelementamount[i][q]`

These are used by later damage reduction logic and make later equipment meaningfully more complex than Chapter 1 equipment.

---

## Spell Globals

### `global.spell[i][j]`

Stores spell ids per character id and spell slot.

Every chapter zeroes these first, then assigns initial spells explicitly.

Examples:

#### Chapter 1

```gml
global.spell[1][0] = 7; // Kris -> spell 7 (ACT)
global.spell[2][0] = 4; // Susie -> spell 4 (Rude Buster)
global.spell[3][0] = 3; // Ralsei -> spell 3 (Pacify)
global.spell[3][1] = 2; // Ralsei -> spell 2 (Heal Prayer)
```

#### Chapter 2

Adds Noelle:

```gml
global.spell[4][0] = 2; // Noelle -> Heal Prayer
global.spell[4][1] = 8; // Noelle -> SleepMist
global.spell[4][2] = 9; // Noelle -> IceShock
```

#### Chapters 3 and 4

Also give Susie:

```gml
global.spell[2][1] = 11;
```

### `global.spellcost`

Cached spell costs after `scr_spellinfo_all()`.

Used by battle menus and battle spell synthesis in later chapters.

---

## Inventory Globals

### Core inventory

All chapters have:

- `global.item[]`
- `global.keyitem[]`
- `global.weapon[]`
- `global.armor[]`

### Chapter 1 sizes

- item / keyitem / weapon / armor are in the older smaller layout

### Chapter 2+ sizes

- `global.item` remains 13 slots
- `global.weapon` expands to 48 slots
- `global.armor` expands to 48 slots
- `global.pocketitem[0..71]` is added

This is not a cosmetic change; it changes save format and item management logic.

### Gold / level progression

- `global.gold`
- `global.xp`
- `global.lv`

All initialized in startup:

```gml
global.gold = 0;
global.xp = 0;
global.lv = 1;
```

---

## Damage / Invulnerability Globals

### `global.inv`

Current invulnerability timer counter.

Startup:

```gml
global.inv = 0;
```

### `global.invc`

Invulnerability scaling factor.

Startup:

```gml
global.invc = 1;
```

Together they are used by damage scripts to determine post-hit invulnerability duration.

### Graze / bullet tuning globals

- `global.boltspeed = 100`
- `global.grazeamt = 100`
- `global.grazesize = 100`
- `global.grazetotal = 0`
- `global.grazeturn = 0`

These begin as global combat tuning values, then get used by battle and equipment systems.

### Tension / TP

- `global.tension = 0`
- `global.maxtension = 250`

Later chapters continue to use this same baseline even as spell and battle systems become more complex.

---

## Monster Globals

The battle system mirrors monster state into many globals.

Important arrays include:

- `global.monster[i]`
- `global.monstername[i]`
- `global.monstertype[i]`
- `global.monsterat[i]`
- `global.monsterdf[i]`
- `global.monsterhp[i]`
- `global.monstermaxhp[i]`
- `global.monsterinstance[i]`
- `global.monsterinstancetype[i]`
- `global.monstermakex[i]`
- `global.monstermakey[i]`
- `global.monsterx[i]`
- `global.monstery[i]`
- `global.monstergold[i]`
- `global.monsterexp[i]`
- `global.monstercomment[i]`
- `global.monsterstatus[i]`
- `global.sparepoint[i]`
- `global.mercymod[i]`
- `global.mercymax[i]`
- `global.hittarget[i]`

### Startup placeholder example

Chapter 1 gives the placeholder battle monster:

```gml
global.monstername[i] = scr_84_get_lang_string("scr_gamestart_slash_scr_gamestart_gml_206_0");
global.monstertype[i] = 1;
global.monsterat[i] = 3;
global.monsterdf[i] = 2;
global.monsterhp[i] = 20;
global.monstermaxhp[i] = 20;
```

Chapter 2 and Chapter 3 use localized placeholder name `ECHIDNA`.

Chapter 4 changes the placeholder name again to:

- `TERUTERUBOUZU`

### Chapter 2+ addition

- `global.monsterattackname[i] = " "`

This is a useful sign that later battle presentation becomes richer and more named-attack-aware.

---

## ACT Globals

The ACT system lives largely in arrays:

- `global.act[monster][actSlot]`
- `global.canact[monster][actSlot]`
- `global.actname[monster][actSlot]`
- `global.acttype[monster][actSlot]`
- `global.actspell[monster][actSlot]`
- `global.actactor[monster][actSlot]`
- `global.actdesc[monster][actSlot]`
- `global.actcost[monster][actSlot]`

### Chapter 2+ character-specific ACT arrays

Later chapters add separate families for non-Kris characters:

- `global.canactsus`
- `global.canactral`
- `global.canactnoe`
- `global.actnamesus`
- `global.actnameral`
- `global.actnamenoe`
- `global.actdescsus`
- `global.actdescral`
- `global.actcostsus`
- `global.actcostral`
- `global.actsimulsus`
- `global.actsimulral`
- `global.actsimulnoe`

These are consumed by `scr_spellmenu_setup()` to build later chapter battle menus.

---

## Battle Menu And Phase Globals

### Shared phase globals

- `global.myfight`
- `global.mnfight`
- `global.bmenuno`
- `global.charturn`
- `global.spelldelay`
- `global.chartarget[]`
- `global.charspecial[]`
- `global.targeted[]`

### Effective combat stat caches

- `global.battleat[]`
- `global.battledf[]`
- `global.battlemag[]`

These are recomputed from base stats plus item modifier arrays during battle bootstrap.

### Later chapter battle-menu synthesis globals

Chapter 2, 3, and 4 add:

- `global.battleactcount[]`
- `global.battlespell[][]`
- `global.battlespellname[][]`
- `global.battlespelldesc[][]`
- `global.battlespellcost[][]`
- `global.battlespelltarget[][]`
- `global.battlespellspecial[][]`

### Acting coordination globals

Later chapters also add:

- `global.currentactingchar`
- `global.actingsingle[]`
- `global.actingsimul[]`
- `global.actingtarget[]`
- `global.actingchoice[]`

These exist because the later ACT/battle-command layer is much more expressive than the Chapter 1 battle menu.

---

## Dialogue And Writer Globals

The dialogue system is heavily global-driven.

### Core text globals

- `global.msg[]`
- `global.msc`
- `global.typer`
- `global.fc`
- `global.fe`
- `global.choice`
- `global.choicemsg[]`

Startup examples:

```gml
global.typer = 5;
global.msc = 0;
global.choice = -1;
```

All chapters also initialize the message array broadly, often first with `"%%"` placeholders and then with `" "` reset values.

### Writer portrait / mini-face globals

All chapters initialize families like:

- `global.writersnd[]`
- `global.writerimg[]`
- `global.smdir[]`
- `global.smspeed[]`
- `global.smsprite[]`
- `global.smalarm[]`
- `global.smtype[]`
- `global.smxx[]`
- `global.smyy[]`
- `global.smcolor[]`
- `global.smstring[]`

### Chapter 2+ writer additions

- `global.smimage[]`
- `global.smimagespeed[]`
- `global.sminstance[]`
- `global.msgno`
- `global.battletyper`

### Chapter 3+ writer additions

- `global.writerobj[]`
- `global.writerobjsettinga[]`
- `global.writerobjsettingb[]`
- `global.writerobjx[]`
- `global.writerobjy[]`

This shows how later chapters let dialogue spawn or coordinate extra writer-linked visual objects such as funnytext effects.

---

## Menu And Interaction Globals

### `global.interact`

This is one of the most overloaded and important globals in overworld flow.

Initialized to:

```gml
global.interact = 0;
```

Then reused for:

- room transition entry state
- active event/dialogue lock
- menu-open state
- many other interaction modes

### `global.entrance`

Stores room-entry marker id.

Initialized to:

```gml
global.entrance = 0;
```

Consumed by `obj_mainchara` when placing Kris after a door transition.

### Menu coordinate globals

- `global.menucoord[]`
- `global.bmenucoord[][]`
- `global.submenucoord[]` and related menu families in older/later code

These arrays are reset frequently and are central to menu cursor memory.

---

## Legacy Globals

These remain present across chapter runtimes:

- `global.litem[]`
- `global.litemname[]`
- `global.phone[]`
- `global.phonename[]`
- `global.lcharname`
- `global.lweapon`
- `global.larmor`
- `global.lxp`
- `global.llv`
- `global.lgold`
- `global.lhp`
- `global.lmaxhp`
- `global.lat`
- `global.ldf`
- `global.lwstrength`
- `global.ladef`

Chapter 1 explicitly seeds examples like:

```gml
global.phone[0] = 201;
global.phonename[0] = scr_84_get_lang_string(...);
global.lweapon = 2;
global.larmor = 3;
```

Later chapters keep the structure, but localize with `stringsetloc(...)`.

---

## Localization Globals

### Core language globals

- `global.lang`
- `global.lang_map`
- `global.font_map`
- `global.chemg_sprite_map`
- `global.chemg_sound_map`

### Later missing-string tracking

Chapters 2+ also use:

- `global.lang_missing_map`

or related missing-string handling structures, especially in Chapters 3 and 4.

See [Localization System](localization.md).

---

## Input Globals

All numbered chapters initialize:

- `global.input_pressed[0..9]`
- `global.input_held[0..9]`
- `global.input_released[0..9]`

These form the lower-level input-state cache used by controller/helper scripts.

Many chapters also reference button globals such as:

- `global.button0`
- `global.button1`
- `global.button2`

and keyboard / gamepad helper state.

---

## `global.flag[0..9998]`

This is the giant catch-all persistent state array and one of the most important structures in DELTARUNE.

Chapter 1 explicitly zeros all 9999 entries:

```gml
for (i = 0; i < 9999; i += 1)
{
    global.flag[i] = 0;
}
```

Chapters 3 and 4 also perform full flag zeroing very early in startup.

### Known startup defaults

Examples visible in startup:

- `global.flag[15] = 1`
- `global.flag[16] = 0.85`
- `global.flag[17] = 0.6`

These are used for settings such as text / sound / music behavior.

### Chapter 2 cosmetic/randomized startup flags

Chapter 2+ seeds:

- `global.flag[220]`
- `global.flag[221]`
- `global.flag[222]`
- `global.flag[223]`
- `global.flag[224]`
- `global.flag[225]`

using `choose(...)` and `random(...)`.

### Chapter 3+ startup progression flags

Chapter 3 startup includes predefined enabled flags such as:

- `global.flag[605] = 1`
- `global.flag[606] = 1`
- `global.flag[611] = 1`
- `global.flag[613] = 1`
- `global.flag[614] = 1`
- `global.flag[615] = 1`
- `global.flag[622] = 1`
- `global.flag[623] = 1`
- `global.flag[800] = 15`
- `global.flag[801] = 5`
- `global.flag[802] = 6`
- `global.flag[803] = 5`

and additional Chapter 3+ values:

- `global.flag[457] = 1`
- `global.flag[632] = 1`
- `global.flag[633] = 1`
- `global.flag[636] = 1`
- `global.flag[642] = 1`

### Chapter 4 further startup flags

Chapter 4 keeps the above and adds more defaults such as:

- `global.flag[654] = 1`
- `global.flag[656] = 1`
- `global.flag[657] = 1`
- `global.flag[659] = 1`
- `global.flag[660] = 1`
- `global.flag[661] = 1`

This is exactly why a serious DELTARUNE wiki cannot treat `global.flag` as “just a generic story flag array” and move on.

---

## Audio Globals

Common audio globals:

- `global.currentsong[0]`
- `global.currentsong[1]`
- `global.batmusic[0]`
- `global.batmusic[1]`

Startup default:

```gml
global.currentsong[0] = snd_nosound;
global.currentsong[1] = snd_nosound;
global.batmusic[0] = snd_nosound;
global.batmusic[1] = snd_nosound;
```

Settings flags:

- `global.flag[16]` and `global.flag[17]`

are then used to restore audio volume, including:

```gml
audio_set_master_gain(0, global.flag[17]);
```

---

## `global.cinstance[]`

Added in later chapter runtimes.

Initialized to sentinel instance-like values after startup in Chapter 2+:

```gml
global.cinstance[0] = ...
global.cinstance[1] = ...
global.cinstance[2] = ...
```

These act as reusable cutscene/runtime instance handles and are part of the later orchestration stack.

---

## Empty But Important Save Hook

Later chapters include:

- `scr_save_global_vars()`

and it is currently empty in the extracted runtime.

That is important because it is an obvious extension point: the runtime has a named place for extra global-save handling even if the shipped build leaves it blank.

---

## Practical Reading Strategy

If you are tracing any system in DELTARUNE, first find which global family it uses:

- dialogue -> `global.msg`, `global.typer`, `global.fc`, `global.fe`
- battle -> `global.myfight`, `global.mnfight`, `global.battle*`, `global.monster*`
- save/load -> `global.filechoice`, `global.currentroom`, `global.flag`, inventory/stat arrays
- overworld -> `global.interact`, `global.entrance`, `global.facing`, `global.darkzone`
- localization -> `global.lang`, `global.lang_map`, `global.font_map`

That is usually the fastest way to understand how a script fits into the larger game.
