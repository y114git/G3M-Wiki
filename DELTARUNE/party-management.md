# Party Management

Party composition is managed through `scr_setparty`, `scr_getchar`,
`scr_losechar`, and the caterpillar follower system.

---

## Core Scripts

The former wrapped summary table was removed. The records below list runtime
values.

---

## `scr_setparty`

Present in Chapters 1, 3, and 4. Chapter 2 does not have this script (party is
set through other means).

The former wrapped summary table was removed. The records below list runtime
values.

Arguments:

- `arg0` = include Susie (char id 2)
- `arg1` = include Ralsei (char id 3)
- `arg2` = include Noelle (char id 4) — Chapters 3 and 4 only

### Flow

1. Finds `obj_mainchara` (Kris)
2. Calls `scr_losechar()` to clear existing party
3. Destroys all `obj_caterpillarchara` instances
4. For each `true` argument:
   - Calls `scr_getchar(char_id)` to add to `global.char[]`
   - Creates a caterpillar follower at Kris's position
   - Sets alignment offsets per light/dark world

### Alignment Offsets

The former wrapped summary table was removed. The records below list runtime
values.

The offset positions the follower behind Kris. Larger offsets in Dark World
account for the doubled sprite scale.

---

## Character IDs

The former wrapped summary table was removed. The records below list runtime
values.

---

## `global.char[]` Array

The party array maps battle slots to character ids:

The former wrapped summary table was removed. The records below list runtime
values.

An empty slot has `global.char[i] = 0`.

---

## Caterpillar Follower System

Followers use the "caterpillar" pattern:

1. Each follower stores a history buffer of the leader's positions
2. The follower reads from the buffer with a delay
3. `scr_caterpillar_interpolate` smooths position updates
4. `scr_caterpillar_facing` synchronizes facing sprites

The system handles:

- Walking
- Running (delayed acceleration)
- Door transitions (instant teleport via `scr_caterpillar_stackandinterpolate`)
- Cutscene-driven movement (`c_actormoveparty`, `c_actormoveparty_single`)

---

## Related State

The former wrapped summary table was removed. The records below list runtime
values.

---

## Modding Reference

The former wrapped summary table was removed. The records below list runtime
values.

## Reachability and the three-slot limit

The three arguments in later `scr_setparty` do not mean four simultaneous battle
members. Kris remains in `global.char[0]`; the requested followers fill the
remaining positions of `global.char[0..2]`. Noelle's ID 4 support in Chapters
3–4 is **defined but not normally party-reachable** in the reviewed room and
event calls. IDs 5–19 are **placeholders**: arrays reserve them, but no complete
player actor, startup record, or production acquisition call was found. Chapter
5 must be read from its own startup and call sites; its larger definition tables
do not by themselves add a battle position.

To make a four-member battle party, a mod must extend every position-indexed
battle/UI loop and save-dependent structure; adding a follower alone is only an
overworld visual. See
[Characters, Stats, and Progression](characters-stats-and-progression.md) for
the canonical roster and chapter transitions.

## Party, stat, equipment, spell, and import assignments

### Party record 0001

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.char[0]`
- expression: `1`
- condition: `line 17; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0002

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.char[1]`
- expression: `0`
- condition: `line 18; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0003

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.char[2]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0004

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.hp[i]`
- expression: `200`
- condition: `line 47; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0005

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.maxhp[i]`
- expression: `250`
- condition: `line 48; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0006

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.at[i]`
- expression: `10`
- condition: `line 49; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0007

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.df[i]`
- expression: `2`
- condition: `line 50; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0008

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.mag[i]`
- expression: `0`
- condition: `line 51; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0009

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.guts[i]`
- expression: `0`
- condition: `line 52; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0010

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.charweapon[i]`
- expression: `1`
- condition: `line 53; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0011

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.chararmor1[i]`
- expression: `0`
- condition: `line 54; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0012

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.chararmor2[i]`
- expression: `0`
- condition: `line 55; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0013

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.spell[i][j]`
- expression: `0`
- condition: `line 70; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0014

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.charweapon[0]`
- expression: `0`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0015

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.chararmor1[0]`
- expression: `0`
- condition: `line 81; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0016

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.chararmor2[0]`
- expression: `0`
- condition: `line 82; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0017

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.hp[0]`
- expression: `0`
- condition: `line 83; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0018

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.maxhp[0]`
- expression: `0`
- condition: `line 84; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0019

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `90`
- condition: `line 85; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0020

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `90`
- condition: `line 86; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0021

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `10`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0022

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 88; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0023

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `110`
- condition: `line 89; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0024

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `110`
- condition: `line 90; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0025

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `14`
- condition: `line 91; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0026

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 92; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0027

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 93; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0028

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `70`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0029

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `70`
- condition: `line 95; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0030

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `8`
- condition: `line 96; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0031

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `7`
- condition: `line 97; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0032

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.spell[1][0]`
- expression: `7`
- condition: `line 98; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0033

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.spell[2][0]`
- expression: `4`
- condition: `line 99; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0034

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.spell[3][0]`
- expression: `3`
- condition: `line 100; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0035

- chapter: `1`
- phase: `scr_gamestart`
- field: `global.spell[3][1]`
- expression: `2`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0036

- chapter: `1`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `2`
- condition: `line 17; if (arg0 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0037

- chapter: `1`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `3`
- condition: `line 32; if (arg1 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0038

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0039

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0040

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0041

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[i]`
- expression: `200`
- condition: `line 82; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0042

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[i]`
- expression: `250`
- condition: `line 83; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0043

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[i]`
- expression: `10`
- condition: `line 84; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0044

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.df[i]`
- expression: `2`
- condition: `line 85; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0045

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.mag[i]`
- expression: `0`
- condition: `line 86; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0046

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.guts[i]`
- expression: `0`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0047

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[i]`
- expression: `1`
- condition: `line 88; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0048

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor1[i]`
- expression: `0`
- condition: `line 89; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0049

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor2[i]`
- expression: `0`
- condition: `line 90; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0050

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[i][j]`
- expression: `0`
- condition: `line 109; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0051

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[0]`
- expression: `0`
- condition: `line 116; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0052

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor1[0]`
- expression: `0`
- condition: `line 117; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0053

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor2[0]`
- expression: `0`
- condition: `line 118; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0054

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[0]`
- expression: `0`
- condition: `line 119; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0055

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[0]`
- expression: `0`
- condition: `line 120; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0056

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `90`
- condition: `line 123; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0057

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `90`
- condition: `line 124; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0058

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `10`
- condition: `line 125; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0059

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 126; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0060

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `110`
- condition: `line 127; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0061

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `110`
- condition: `line 128; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0062

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `14`
- condition: `line 129; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0063

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 130; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0064

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 131; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0065

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `70`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0066

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `70`
- condition: `line 133; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0067

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `8`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0068

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `7`
- condition: `line 135; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0069

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `120`
- condition: `line 139; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0070

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 140; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0071

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `12`
- condition: `line 141; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0072

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 142; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0073

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `1`
- condition: `line 143; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0074

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 144; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0075

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `140`
- condition: `line 145; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0076

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 146; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0077

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `16`
- condition: `line 147; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0078

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 148; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0079

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 149; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0080

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `1`
- condition: `line 150; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0081

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 151; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0082

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `100`
- condition: `line 152; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0083

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 153; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0084

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `10`
- condition: `line 154; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0085

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `9`
- condition: `line 155; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0086

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `1`
- condition: `line 156; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0087

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `4`
- condition: `line 157; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0088

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 158; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0089

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 159; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0090

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 160; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0091

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 161; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0092

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 162; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0093

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 163; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0094

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 164; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0095

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 165; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0096

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[1][0]`
- expression: `7`
- condition: `line 167; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0097

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[2][0]`
- expression: `4`
- condition: `line 168; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0098

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[3][0]`
- expression: `3`
- condition: `line 169; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0099

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[3][1]`
- expression: `2`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0100

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[4][0]`
- expression: `2`
- condition: `line 171; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0101

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[4][1]`
- expression: `8`
- condition: `line 172; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0102

- chapter: `2`
- phase: `scr_gamestart`
- field: `global.spell[4][2]`
- expression: `9`
- condition: `line 173; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0103

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0104

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0105

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0106

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0107

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0108

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0109

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0110

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0111

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0112

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0113

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0114

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0115

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0116

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0117

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0118

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0119

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0120

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0121

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0122

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0123

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0124

- chapter: `2`
- phase: `scr_load_chapter1`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0125

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0126

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0127

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0128

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[i]`
- expression: `200`
- condition: `line 82; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0129

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[i]`
- expression: `250`
- condition: `line 83; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0130

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[i]`
- expression: `10`
- condition: `line 84; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0131

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.df[i]`
- expression: `2`
- condition: `line 85; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0132

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[i]`
- expression: `0`
- condition: `line 86; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0133

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.guts[i]`
- expression: `0`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0134

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[i]`
- expression: `1`
- condition: `line 88; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0135

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[i]`
- expression: `0`
- condition: `line 89; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0136

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[i]`
- expression: `0`
- condition: `line 90; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0137

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[i][j]`
- expression: `0`
- condition: `line 109; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0138

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[0]`
- expression: `0`
- condition: `line 120; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0139

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[0]`
- expression: `0`
- condition: `line 121; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0140

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[0]`
- expression: `0`
- condition: `line 122; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0141

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[0]`
- expression: `0`
- condition: `line 123; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0142

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[0]`
- expression: `0`
- condition: `line 124; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0143

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `90`
- condition: `line 127; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0144

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `90`
- condition: `line 128; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0145

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `10`
- condition: `line 129; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0146

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 130; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0147

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `110`
- condition: `line 131; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0148

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `110`
- condition: `line 132; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0149

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `14`
- condition: `line 133; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0150

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0151

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 135; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0152

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `70`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0153

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `70`
- condition: `line 137; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0154

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `8`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0155

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `7`
- condition: `line 139; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0156

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `120`
- condition: `line 143; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0157

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 144; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0158

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `12`
- condition: `line 145; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0159

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 146; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0160

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `1`
- condition: `line 147; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0161

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 148; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0162

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `140`
- condition: `line 149; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0163

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 150; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0164

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `16`
- condition: `line 151; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0165

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 152; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0166

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 153; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0167

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `1`
- condition: `line 154; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0168

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 155; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0169

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `100`
- condition: `line 156; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0170

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 157; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0171

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `10`
- condition: `line 158; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0172

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `9`
- condition: `line 159; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0173

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `1`
- condition: `line 160; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0174

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `4`
- condition: `line 161; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0175

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 162; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0176

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 163; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0177

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 164; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0178

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 165; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0179

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0180

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 167; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0181

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 168; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0182

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 169; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0183

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `160`
- condition: `line 173; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0184

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 174; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0185

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `14`
- condition: `line 175; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0186

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[1]`
- expression: `16`
- condition: `line 176; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0187

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 177; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0188

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `10`
- condition: `line 178; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0189

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 179; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0190

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `190`
- condition: `line 180; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0191

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 181; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0192

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `18`
- condition: `line 182; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0193

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `2`
- condition: `line 183; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0194

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `17`
- condition: `line 184; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0195

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 185; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0196

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `10`
- condition: `line 186; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0197

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 187; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0198

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `140`
- condition: `line 188; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0199

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 189; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0200

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `12`
- condition: `line 190; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0201

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `11`
- condition: `line 191; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0202

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `18`
- condition: `line 192; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0203

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `1`
- condition: `line 193; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0204

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `10`
- condition: `line 194; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0205

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[1][0]`
- expression: `7`
- condition: `line 196; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0206

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[2][0]`
- expression: `4`
- condition: `line 197; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0207

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[2][1]`
- expression: `11`
- condition: `line 198; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0208

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[3][0]`
- expression: `3`
- condition: `line 199; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0209

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[3][1]`
- expression: `2`
- condition: `line 200; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0210

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[4][0]`
- expression: `2`
- condition: `line 201; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0211

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[4][1]`
- expression: `8`
- condition: `line 202; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0212

- chapter: `3`
- phase: `scr_gamestart`
- field: `global.spell[4][2]`
- expression: `9`
- condition: `line 203; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0213

- chapter: `3`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `2`
- condition: `line 14; if (arg0 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0214

- chapter: `3`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `3`
- condition: `line 29; if (arg1 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0215

- chapter: `3`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `4`
- condition: `line 44; if (arg2 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0216

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0217

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0218

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0219

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0220

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0221

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0222

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0223

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0224

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0225

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0226

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0227

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0228

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0229

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0230

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0231

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0232

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0233

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0234

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0235

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0236

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0237

- chapter: `3`
- phase: `scr_load_chapter1`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0238

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0239

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0240

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0241

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0242

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0243

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0244

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0245

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0246

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0247

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0248

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0249

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0250

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0251

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0252

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0253

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0254

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0255

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0256

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0257

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0258

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0259

- chapter: `3`
- phase: `scr_load_chapter2`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0260

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0261

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0262

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0263

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[i]`
- expression: `200`
- condition: `line 82; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0264

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[i]`
- expression: `250`
- condition: `line 83; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0265

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[i]`
- expression: `10`
- condition: `line 84; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0266

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.df[i]`
- expression: `2`
- condition: `line 85; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0267

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[i]`
- expression: `0`
- condition: `line 86; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0268

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.guts[i]`
- expression: `0`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0269

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[i]`
- expression: `1`
- condition: `line 88; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0270

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[i]`
- expression: `0`
- condition: `line 89; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0271

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[i]`
- expression: `0`
- condition: `line 90; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0272

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[i][j]`
- expression: `0`
- condition: `line 109; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0273

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[0]`
- expression: `0`
- condition: `line 120; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0274

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[0]`
- expression: `0`
- condition: `line 121; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0275

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[0]`
- expression: `0`
- condition: `line 122; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0276

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[0]`
- expression: `0`
- condition: `line 123; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0277

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[0]`
- expression: `0`
- condition: `line 124; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0278

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `90`
- condition: `line 127; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0279

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `90`
- condition: `line 128; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0280

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `10`
- condition: `line 129; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0281

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 130; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0282

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `110`
- condition: `line 131; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0283

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `110`
- condition: `line 132; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0284

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `14`
- condition: `line 133; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0285

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0286

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 135; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0287

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `70`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0288

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `70`
- condition: `line 137; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0289

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `8`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0290

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `7`
- condition: `line 139; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0291

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `120`
- condition: `line 143; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0292

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 144; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0293

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `12`
- condition: `line 145; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0294

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 146; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0295

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `1`
- condition: `line 147; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0296

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 148; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0297

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `140`
- condition: `line 149; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0298

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 150; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0299

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `16`
- condition: `line 151; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0300

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 152; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0301

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 153; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0302

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `1`
- condition: `line 154; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0303

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 155; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0304

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `100`
- condition: `line 156; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0305

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 157; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0306

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `10`
- condition: `line 158; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0307

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `9`
- condition: `line 159; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0308

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `1`
- condition: `line 160; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0309

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `4`
- condition: `line 161; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0310

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 162; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0311

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 163; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0312

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 164; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0313

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 165; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0314

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0315

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 167; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0316

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 168; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0317

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 169; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0318

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `160`
- condition: `line 173; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0319

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 174; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0320

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `14`
- condition: `line 175; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0321

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[1]`
- expression: `16`
- condition: `line 176; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0322

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 177; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0323

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `10`
- condition: `line 178; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0324

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 179; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0325

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `190`
- condition: `line 180; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0326

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 181; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0327

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `18`
- condition: `line 182; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0328

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `2`
- condition: `line 183; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0329

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `17`
- condition: `line 184; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0330

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 185; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0331

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `10`
- condition: `line 186; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0332

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 187; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0333

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `140`
- condition: `line 188; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0334

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 189; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0335

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `12`
- condition: `line 190; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0336

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `11`
- condition: `line 191; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0337

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `18`
- condition: `line 192; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0338

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `25`
- condition: `line 193; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0339

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `10`
- condition: `line 194; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0340

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 195; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0341

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 196; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0342

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 197; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0343

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 198; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0344

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 199; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0345

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 200; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0346

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 201; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0347

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 202; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0348

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `200`
- condition: `line 206; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0349

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 207; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0350

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `17`
- condition: `line 208; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0351

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[1]`
- expression: `23`
- condition: `line 209; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0352

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `25`
- condition: `line 210; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0353

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `10`
- condition: `line 211; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0354

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 212; if (global.chapter == 4)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0355

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `230`
- condition: `line 213; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0356

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 214; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0357

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `22`
- condition: `line 215; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0358

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `3`
- condition: `line 216; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0359

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `24`
- condition: `line 217; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0360

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `25`
- condition: `line 218; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0361

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `10`
- condition: `line 219; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0362

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 220; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0363

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `180`
- condition: `line 221; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0364

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 222; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0365

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `15`
- condition: `line 223; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0366

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `14`
- condition: `line 224; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0367

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `25`
- condition: `line 225; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0368

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `25`
- condition: `line 226; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0369

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `10`
- condition: `line 227; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0370

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 228; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0371

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 229; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0372

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 230; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0373

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 231; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0374

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 232; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0375

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 233; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0376

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 234; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0377

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 235; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0378

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[1][0]`
- expression: `7`
- condition: `line 237; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0379

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[2][0]`
- expression: `4`
- condition: `line 238; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0380

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[2][1]`
- expression: `11`
- condition: `line 239; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0381

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[3][0]`
- expression: `3`
- condition: `line 240; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0382

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[3][1]`
- expression: `2`
- condition: `line 241; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0383

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[4][0]`
- expression: `2`
- condition: `line 242; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0384

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[4][1]`
- expression: `8`
- condition: `line 243; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0385

- chapter: `4`
- phase: `scr_gamestart`
- field: `global.spell[4][2]`
- expression: `9`
- condition: `line 244; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0386

- chapter: `4`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `2`
- condition: `line 14; if (arg0 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0387

- chapter: `4`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `3`
- condition: `line 29; if (arg1 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0388

- chapter: `4`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `4`
- condition: `line 44; if (arg2 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0389

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0390

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0391

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0392

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0393

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0394

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0395

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0396

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0397

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0398

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0399

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0400

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0401

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0402

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0403

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0404

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0405

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0406

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0407

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0408

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0409

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0410

- chapter: `4`
- phase: `scr_load_chapter1`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0411

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0412

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0413

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0414

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0415

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0416

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0417

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0418

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0419

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0420

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0421

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0422

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0423

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0424

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0425

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0426

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0427

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0428

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0429

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0430

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0431

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0432

- chapter: `4`
- phase: `scr_load_chapter2`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0433

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0434

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0435

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0436

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0437

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0438

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0439

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0440

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0441

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0442

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0443

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0444

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0445

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0446

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0447

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0448

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0449

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0450

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0451

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0452

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0453

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0454

- chapter: `4`
- phase: `scr_load_chapter3`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0455

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0456

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0457

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0458

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[i]`
- expression: `200`
- condition: `line 82; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0459

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[i]`
- expression: `250`
- condition: `line 83; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0460

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[i]`
- expression: `10`
- condition: `line 84; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0461

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.df[i]`
- expression: `2`
- condition: `line 85; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0462

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[i]`
- expression: `0`
- condition: `line 86; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0463

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.guts[i]`
- expression: `0`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0464

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[i]`
- expression: `1`
- condition: `line 88; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0465

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[i]`
- expression: `0`
- condition: `line 89; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0466

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[i]`
- expression: `0`
- condition: `line 90; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0467

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[i][j]`
- expression: `0`
- condition: `line 109; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0468

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[0]`
- expression: `0`
- condition: `line 120; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0469

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[0]`
- expression: `0`
- condition: `line 121; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0470

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[0]`
- expression: `0`
- condition: `line 122; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0471

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[0]`
- expression: `0`
- condition: `line 123; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0472

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[0]`
- expression: `0`
- condition: `line 124; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0473

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `90`
- condition: `line 127; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0474

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `90`
- condition: `line 128; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0475

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `10`
- condition: `line 129; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0476

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 130; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0477

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `110`
- condition: `line 131; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0478

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `110`
- condition: `line 132; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0479

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `14`
- condition: `line 133; if (global.chapter == 1)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0480

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0481

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 135; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0482

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `70`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0483

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `70`
- condition: `line 137; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0484

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `8`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0485

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `7`
- condition: `line 139; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0486

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `120`
- condition: `line 143; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0487

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 144; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0488

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `12`
- condition: `line 145; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0489

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 146; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0490

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `1`
- condition: `line 147; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0491

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 148; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0492

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `140`
- condition: `line 149; if (global.chapter == 2)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0493

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 150; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0494

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `16`
- condition: `line 151; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0495

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 152; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0496

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 153; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0497

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `1`
- condition: `line 154; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0498

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 155; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0499

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `100`
- condition: `line 156; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0500

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 157; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0501

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `10`
- condition: `line 158; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0502

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `9`
- condition: `line 159; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0503

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `1`
- condition: `line 160; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0504

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `4`
- condition: `line 161; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0505

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 162; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0506

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 163; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0507

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 164; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0508

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 165; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0509

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0510

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 167; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0511

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 168; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0512

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 169; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0513

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `160`
- condition: `line 173; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0514

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 174; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0515

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `14`
- condition: `line 175; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0516

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[1]`
- expression: `16`
- condition: `line 176; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0517

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `1`
- condition: `line 177; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0518

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `10`
- condition: `line 178; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0519

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `2`
- condition: `line 179; if (global.chapter == 3)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0520

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `190`
- condition: `line 180; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0521

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 181; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0522

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `18`
- condition: `line 182; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0523

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `2`
- condition: `line 183; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0524

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `17`
- condition: `line 184; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0525

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `1`
- condition: `line 185; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0526

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `10`
- condition: `line 186; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0527

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `3`
- condition: `line 187; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0528

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `140`
- condition: `line 188; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0529

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 189; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0530

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `12`
- condition: `line 190; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0531

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `11`
- condition: `line 191; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0532

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `18`
- condition: `line 192; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0533

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `25`
- condition: `line 193; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0534

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `10`
- condition: `line 194; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0535

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 195; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0536

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 196; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0537

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 197; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0538

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 198; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0539

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 199; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0540

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 200; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0541

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 201; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0542

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 202; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0543

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[1]`
- expression: `53`
- condition: `line 206; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0544

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[1]`
- expression: `240`
- condition: `line 207; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0545

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[1]`
- expression: `global.maxhp[1]`
- condition: `line 208; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0546

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[1]`
- expression: `12`
- condition: `line 209; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0547

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[1]`
- expression: `25`
- condition: `line 210; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0548

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[1]`
- expression: `25`
- condition: `line 211; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0549

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[2]`
- expression: `24`
- condition: `line 212; if (global.chapter == 5)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0550

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[2]`
- expression: `290`
- condition: `line 213; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0551

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[2]`
- expression: `global.maxhp[2]`
- condition: `line 214; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0552

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[2]`
- expression: `16`
- condition: `line 215; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0553

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[2]`
- expression: `1`
- condition: `line 216; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0554

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[2]`
- expression: `25`
- condition: `line 217; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0555

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[2]`
- expression: `25`
- condition: `line 218; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0556

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[3]`
- expression: `25`
- condition: `line 219; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0557

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[3]`
- expression: `210`
- condition: `line 220; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0558

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[3]`
- expression: `global.maxhp[3]`
- condition: `line 221; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0559

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[3]`
- expression: `10`
- condition: `line 222; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0560

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[3]`
- expression: `9`
- condition: `line 223; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0561

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[3]`
- expression: `25`
- condition: `line 224; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0562

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[3]`
- expression: `25`
- condition: `line 225; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0563

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.charweapon[4]`
- expression: `12`
- condition: `line 226; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0564

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor1[4]`
- expression: `14`
- condition: `line 227; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0565

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.chararmor2[4]`
- expression: `22`
- condition: `line 228; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0566

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.hp[4]`
- expression: `90`
- condition: `line 229; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0567

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.maxhp[4]`
- expression: `90`
- condition: `line 230; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0568

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.at[4]`
- expression: `3`
- condition: `line 231; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0569

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.mag[4]`
- expression: `11`
- condition: `line 232; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0570

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.df[4]`
- expression: `1`
- condition: `line 233; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0571

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[1][0]`
- expression: `7`
- condition: `line 235; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0572

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[2][0]`
- expression: `4`
- condition: `line 236; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0573

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[2][1]`
- expression: `11`
- condition: `line 237; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0574

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[2][2]`
- expression: `13`
- condition: `line 238; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0575

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[3][0]`
- expression: `3`
- condition: `line 239; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0576

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[3][1]`
- expression: `2`
- condition: `line 240; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0577

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[3][2]`
- expression: `12`
- condition: `line 241; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0578

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[4][0]`
- expression: `2`
- condition: `line 242; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0579

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[4][1]`
- expression: `8`
- condition: `line 243; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0580

- chapter: `5`
- phase: `scr_gamestart`
- field: `global.spell[4][2]`
- expression: `9`
- condition: `line 244; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0581

- chapter: `5`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `2`
- condition: `line 14; if (arg0 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0582

- chapter: `5`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `3`
- condition: `line 29; if (arg1 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0583

- chapter: `5`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `4`
- condition: `line 44; if (arg2 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0584

- chapter: `5`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `2`
- condition: `line 72; if (arg0 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0585

- chapter: `5`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `3`
- condition: `line 87; if (arg1 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0586

- chapter: `5`
- phase: `scr_setparty`
- field: `active-party-add`
- expression: `4`
- condition: `line 102; if (arg2 == true)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0587

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0588

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0589

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0590

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0591

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0592

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0593

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0594

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0595

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0596

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0597

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0598

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0599

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0600

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0601

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0602

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0603

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0604

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0605

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0606

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0607

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0608

- chapter: `5`
- phase: `scr_load_chapter1`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 166; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0609

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0610

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0611

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0612

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0613

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0614

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0615

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0616

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0617

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0618

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0619

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0620

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0621

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0622

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0623

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0624

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0625

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0626

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0627

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0628

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0629

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0630

- chapter: `5`
- phase: `scr_load_chapter2`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0631

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0632

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0633

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0634

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0635

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0636

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0637

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0638

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0639

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0640

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0641

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0642

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0643

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0644

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0645

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0646

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0647

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0648

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0649

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0650

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0651

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0652

- chapter: `5`
- phase: `scr_load_chapter3`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0653

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0654

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0655

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0656

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.hp[i]`
- expression: `ds_list_find_value(hp_list, i)`
- condition: `line 52; if (global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0657

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.maxhp[i]`
- expression: `ds_list_find_value(maxhp_list, i)`
- condition: `line 59; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0658

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.at[i]`
- expression: `ds_list_find_value(at_list, i)`
- condition: `line 66; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0659

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.df[i]`
- expression: `ds_list_find_value(df_list, i)`
- condition: `line 73; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0660

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.mag[i]`
- expression: `ds_list_find_value(mag_list, i)`
- condition: `line 80; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0661

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.guts[i]`
- expression: `ds_list_find_value(guts_list, i)`
- condition: `line 87; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0662

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.charweapon[i]`
- expression: `ds_list_find_value(charweapon_list, i)`
- condition: `line 94; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0663

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.chararmor1[i]`
- expression: `ds_list_find_value(chararmor1_list, i)`
- condition: `line 101; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0664

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.chararmor2[i]`
- expression: `ds_list_find_value(chararmor2_list, i)`
- condition: `line 108; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0665

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.hp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 124; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0666

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.maxhp[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 126; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0667

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.at[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 128; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0668

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.df[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 130; if (!global.is_console)`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0669

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.mag[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 132; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0670

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.guts[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 134; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0671

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.charweapon[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 136; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0672

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.chararmor1[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 138; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0673

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.chararmor2[i]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 140; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0674

- chapter: `5`
- phase: `scr_load_chapter4`
- field: `global.spell[i][j]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 170; unconditional in entry`
- status: `initialization/import`
- rooms: `not room-owned`

### Party record 0675

- chapter: `1`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `arg0 = false, arg1 = false`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0676

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 10; if (!instance_exists(kris))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0677

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 17; if (arg0 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0678

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 32; if (arg1 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0679

- chapter: `1`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 if (global.cinstance[i].x !=`
  `s.x || global.cinstance[i].y != s.x)                 {`
  `global.cinstance[i].x = s.x`
- condition: `line 7; if (instance_exists(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0680

- chapter: `1`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 if (global.cinstance[i].x !=`
  `r.x || global.cinstance[i].y != r.x)                 {`
  `global.cinstance[i].x = r.x`
- condition: `line 44; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0681

- chapter: `1`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 s =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 9; if (instance_exists(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0682

- chapter: `1`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 r =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0683

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `arg0`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0684

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 0)     {         global.char[0] = arg0`
- condition: `line 4; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0685

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && getchar == 0)     {         global.char[1] = arg0`
- condition: `line 9; if (global.char[0] == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0686

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0 && getchar == 0)     {         global.char[2] = arg0`
- condition: `line 14; if (global.char[1] == 0 && getchar == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0687

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 32; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0688

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 37; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0689

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 42; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0690

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0691

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0692

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0693

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 22; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0694

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 27; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0695

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 32; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0696

- chapter: `1`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         charcan = 0`
- condition: `line 12; if (global.acting[arg0] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0697

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2)     {         sus = 0`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0698

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)     {         sus = 1`
- condition: `line 7; if (global.char[0] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0699

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)     {         sus = 2`
- condition: `line 11; if (global.char[1] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0700

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 && global.charauto[2] == 1)             {`
  `global.acting[0] = 1`
- condition: `line 89; if (skip == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0701

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         global.heromakey[0] =`
  `yy + 140`
- condition: `line 14; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0702

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         global.heromakey[0] = yy + 100`
- condition: `line 18; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0703

- chapter: `1`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(10)`
- condition: `line 250; case 212: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0704

- chapter: `1`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(90)`
- condition: `line 254; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0705

- chapter: `1`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(60)`
- condition: `line 258; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0706

- chapter: `1`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(80)`
- condition: `line 265; case 213: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0707

- chapter: `1`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(30)`
- condition: `line 269; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0708

- chapter: `1`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(30)`
- condition: `line 273; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0709

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)         {             suspos = i`
- condition: `line 13; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0710

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)         {             ralpos = i`
- condition: `line 17; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0711

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_101_0"))`
- condition: `line 110; case 8: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0712

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_105_0"))`
- condition: `line 114; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0713

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_115_0"))`
- condition: `line 122; case 9: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0714

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_119_0"))`
- condition: `line 126; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0715

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_129_0"))`
- condition: `line 134; case 10: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0716

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_133_0"))`
- condition: `line 138; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0717

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 157; case 12: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0718

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 161; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0719

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 166; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0720

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 174; case 13: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0721

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 178; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0722

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 183; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0723

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_188_0"))`
- condition: `line 192; case 14: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0724

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_192_0"))`
- condition: `line 196; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0725

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_202_0"))`
- condition: `line 204; case 15: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0726

- chapter: `1`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `scr_84_get_lang_string("scr_itemuse_slash_scr_itemuse_gml_206_0"))`
- condition: `line 208; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0727

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 17; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0728

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 18; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0729

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0730

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)                     {                         facetype =`
  `spr_headkris`
- condition: `line 34; if (itemtype[menuc[1]] == "weapon" || itemtype[menuc[1]]`
  `== "armor") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0731

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         facetype =`
  `spr_headsusie`
- condition: `line 38; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0732

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         facetype =`
  `spr_headralsei`
- condition: `line 42; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0733

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= arg0)     {         _rreturn = 1`
- condition: `line 4; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0734

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= arg0)     {         _rreturn = 1`
- condition: `line 8; if (global.char[0] == arg0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0735

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= arg0)     {         _rreturn = 1`
- condition: `line 12; if (global.char[1] == arg0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0736

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 37; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0737

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 39; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0738

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 41; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0739

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 483; if (con == 230)`
- status: `production`
- rooms: `room_cc_prison_cells`

### Party record 0740

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `2`
- condition: `line 484; if (con == 230)`
- status: `production`
- rooms: `room_cc_prison_cells`

### Party record 0741

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 640; if (con == 317)`
- status: `production`
- rooms: `room_cc_prison_cells`

### Party record 0742

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 641; if (con == 317)`
- status: `production`
- rooms: `room_cc_prison_cells`

### Party record 0743

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 642; if (con == 317)`
- status: `production`
- rooms: `room_cc_prison_cells`

### Party record 0744

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 643; if (con == 317)`
- status: `production`
- rooms: `room_cc_prison_cells`

### Party record 0745

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 805; if (s.x <= (r.x - 50))`
- status: `production`
- rooms: `room_forest_fightsusie`

### Party record 0746

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 806; if (s.x <= (r.x - 50))`
- status: `production`
- rooms: `room_forest_fightsusie`

### Party record 0747

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 807; if (s.x <= (r.x - 50))`
- status: `production`
- rooms: `room_forest_fightsusie`

### Party record 0748

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 984; if (con == 120)`
- status: `production`
- rooms: `room_forest_afterthrash2, room_forest_afterthrash3,`
  `room_forest_afterthrash4, room_forest_castleview`

### Party record 0749

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 156; if (walkcon == 1) > if (con == 13 && d_ex() == 0)`
- status: `production`
- rooms: `room_field_getsusie`

### Party record 0750

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 157; if (con == 13 && d_ex() == 0)`
- status: `production`
- rooms: `room_field_getsusie`

### Party record 0751

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 158; if (con == 13 && d_ex() == 0)`
- status: `production`
- rooms: `room_field_getsusie`

### Party record 0752

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 11; if (global.plot >= 31) > if (global.plot < 6)`
- status: `production`
- rooms: `room_castle_tutorial`

### Party record 0753

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 565; if (con == 72)`
- status: `production`
- rooms: `room_castle_front`

### Party record 0754

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 895; if (con == 108)`
- status: `production`
- rooms: `room_castle_front`

### Party record 0755

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 896; if (con == 108)`
- status: `production`
- rooms: `room_castle_front`

### Party record 0756

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 4; if (global.plot < 11)`
- status: `production`
- rooms: `room_dark1`

### Party record 0757

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 166; if (con == 31)`
- status: `production`
- rooms: `room_dark7`

### Party record 0758

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 242; if (con == 40)`
- status: `production`
- rooms: `room_dark7`

### Party record 0759

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 2987; if (global.plot < 240) > if (con == 305)`
- status: `production-subsystem`
- rooms: `room_cc_kingbattle`

### Party record 0760

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 2988; if (con == 305)`
- status: `production-subsystem`
- rooms: `room_cc_kingbattle`

### Party record 0761

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 3290; if (con == 378)`
- status: `production-subsystem`
- rooms: `room_cc_kingbattle`

### Party record 0762

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 3291; if (con == 378)`
- status: `production-subsystem`
- rooms: `room_cc_kingbattle`

### Party record 0763

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 29; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0764

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 33; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0765

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 c[i].sprite_index =`
  `spr_ralseib_battleintro`
- condition: `line 41; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0766

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 51; if (global.char[i] != 0) > if (`
- status: `production`
- rooms: `room_castle_darkdoor, room_castle_front, room_castle_outskirts,`
  `room_castle_town, room_castle_tutorial, room_cc_1f, room_cc_2f,`
  `room_cc_3f, room_cc_4f, room_cc_5f, room_cc_6f, room_cc_clover,`
  `room_cc_elevator, room_cc_entrance, room_cc_hathy, room_cc_joker,`
  `room_cc_kingbattle, room_cc_lancer, room_cc_prefountain,`
  `room_cc_preroof, room_cc_prison_cells, room_cc_prison_prejoker,`
  `room_cc_prison_to_elevator, room_cc_prison2, room_cc_prisonelevator,`
  `room_cc_prisonlancer, room_cc_rudinn, room_cc_rurus1, room_cc_rurus2,`
  `room_cc_throneroom, room_dark_chase1, room_dark_chase2,`
  `room_dark_eyepuzzle, room_dark_wobbles, room_dark1, room_dark1a,`
  `room_dark2, room_dark3, room_dark3a, room_dark7, room_DARKempty,`
  `room_field_boxpuzzle, room_field_checkers1, room_field_checkers2,`
  `room_field_checkers3, room_field_checkers4, room_field_checkers5,`
  `room_field_checkers6, room_field_checkers7, room_field_checkersboss,`
  `room_field_forest, room_field_getsusie, room_field_maze,`
  `room_field_puzzle1, room_field_puzzle2, room_field_puzzletutorial,`
  `room_field_secret1, room_field_shop1, room_field_start,`
  `room_field_topchef, room_field1, room_field2, room_field2A,`
  `room_field3, room_field4, room_forest_afterthrash2,`
  `room_forest_afterthrash3, room_forest_afterthrash4,`
  `room_forest_area0, room_forest_area1, room_forest_area2,`
  `room_forest_area2A, room_forest_area3, room_forest_area3A,`
  `room_forest_area4, room_forest_area5, room_forest_beforeclover,`
  `room_forest_castlefront, room_forest_castleview, room_forest_chase1,`
  `room_forest_chase2, room_forest_dancers1, room_forest_fightsusie,`
  `room_forest_maze_deadend, room_forest_maze_deadend2,`
  `room_forest_maze_susie, room_forest_maze1, room_forest_maze2,`
  `room_forest_puzzle1, room_forest_savepoint_relax,`
  `room_forest_savepoint1, room_forest_savepoint2,`
  `room_forest_savepoint3, room_forest_secret1, room_forest_smith,`
  `room_forest_starwalker, room_forest_thrashmaker, room_man`

### Party record 0767

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 56; if (global.char[i] == 1) > if (`
- status: `production`
- rooms: `room_castle_darkdoor, room_castle_front, room_castle_outskirts,`
  `room_castle_town, room_castle_tutorial, room_cc_1f, room_cc_2f,`
  `room_cc_3f, room_cc_4f, room_cc_5f, room_cc_6f, room_cc_clover,`
  `room_cc_elevator, room_cc_entrance, room_cc_hathy, room_cc_joker,`
  `room_cc_kingbattle, room_cc_lancer, room_cc_prefountain,`
  `room_cc_preroof, room_cc_prison_cells, room_cc_prison_prejoker,`
  `room_cc_prison_to_elevator, room_cc_prison2, room_cc_prisonelevator,`
  `room_cc_prisonlancer, room_cc_rudinn, room_cc_rurus1, room_cc_rurus2,`
  `room_cc_throneroom, room_dark_chase1, room_dark_chase2,`
  `room_dark_eyepuzzle, room_dark_wobbles, room_dark1, room_dark1a,`
  `room_dark2, room_dark3, room_dark3a, room_dark7, room_DARKempty,`
  `room_field_boxpuzzle, room_field_checkers1, room_field_checkers2,`
  `room_field_checkers3, room_field_checkers4, room_field_checkers5,`
  `room_field_checkers6, room_field_checkers7, room_field_checkersboss,`
  `room_field_forest, room_field_getsusie, room_field_maze,`
  `room_field_puzzle1, room_field_puzzle2, room_field_puzzletutorial,`
  `room_field_secret1, room_field_shop1, room_field_start,`
  `room_field_topchef, room_field1, room_field2, room_field2A,`
  `room_field3, room_field4, room_forest_afterthrash2,`
  `room_forest_afterthrash3, room_forest_afterthrash4,`
  `room_forest_area0, room_forest_area1, room_forest_area2,`
  `room_forest_area2A, room_forest_area3, room_forest_area3A,`
  `room_forest_area4, room_forest_area5, room_forest_beforeclover,`
  `room_forest_castlefront, room_forest_castleview, room_forest_chase1,`
  `room_forest_chase2, room_forest_dancers1, room_forest_fightsusie,`
  `room_forest_maze_deadend, room_forest_maze_deadend2,`
  `room_forest_maze_susie, room_forest_maze1, room_forest_maze2,`
  `room_forest_puzzle1, room_forest_savepoint_relax,`
  `room_forest_savepoint1, room_forest_savepoint2,`
  `room_forest_savepoint3, room_forest_secret1, room_forest_smith,`
  `room_forest_starwalker, room_forest_thrashmaker, room_man`

### Party record 0768

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 66; if (i > 0) > if (`
- status: `production`
- rooms: `room_castle_darkdoor, room_castle_front, room_castle_outskirts,`
  `room_castle_town, room_castle_tutorial, room_cc_1f, room_cc_2f,`
  `room_cc_3f, room_cc_4f, room_cc_5f, room_cc_6f, room_cc_clover,`
  `room_cc_elevator, room_cc_entrance, room_cc_hathy, room_cc_joker,`
  `room_cc_kingbattle, room_cc_lancer, room_cc_prefountain,`
  `room_cc_preroof, room_cc_prison_cells, room_cc_prison_prejoker,`
  `room_cc_prison_to_elevator, room_cc_prison2, room_cc_prisonelevator,`
  `room_cc_prisonlancer, room_cc_rudinn, room_cc_rurus1, room_cc_rurus2,`
  `room_cc_throneroom, room_dark_chase1, room_dark_chase2,`
  `room_dark_eyepuzzle, room_dark_wobbles, room_dark1, room_dark1a,`
  `room_dark2, room_dark3, room_dark3a, room_dark7, room_DARKempty,`
  `room_field_boxpuzzle, room_field_checkers1, room_field_checkers2,`
  `room_field_checkers3, room_field_checkers4, room_field_checkers5,`
  `room_field_checkers6, room_field_checkers7, room_field_checkersboss,`
  `room_field_forest, room_field_getsusie, room_field_maze,`
  `room_field_puzzle1, room_field_puzzle2, room_field_puzzletutorial,`
  `room_field_secret1, room_field_shop1, room_field_start,`
  `room_field_topchef, room_field1, room_field2, room_field2A,`
  `room_field3, room_field4, room_forest_afterthrash2,`
  `room_forest_afterthrash3, room_forest_afterthrash4,`
  `room_forest_area0, room_forest_area1, room_forest_area2,`
  `room_forest_area2A, room_forest_area3, room_forest_area3A,`
  `room_forest_area4, room_forest_area5, room_forest_beforeclover,`
  `room_forest_castlefront, room_forest_castleview, room_forest_chase1,`
  `room_forest_chase2, room_forest_dancers1, room_forest_fightsusie,`
  `room_forest_maze_deadend, room_forest_maze_deadend2,`
  `room_forest_maze_susie, room_forest_maze1, room_forest_maze2,`
  `room_forest_puzzle1, room_forest_savepoint_relax,`
  `room_forest_savepoint1, room_forest_savepoint2,`
  `room_forest_savepoint3, room_forest_secret1, room_forest_smith,`
  `room_forest_starwalker, room_forest_thrashmaker, room_man`

### Party record 0769

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3 || global.char[1] == 3)                 {`
  `global.interact = 1`
- condition: `line 135; if (throwitem == 4) > if (`
- status: `production`
- rooms: `room_castle_darkdoor, room_castle_front, room_castle_outskirts,`
  `room_castle_town, room_castle_tutorial, room_cc_1f, room_cc_2f,`
  `room_cc_3f, room_cc_4f, room_cc_5f, room_cc_6f, room_cc_clover,`
  `room_cc_elevator, room_cc_entrance, room_cc_hathy, room_cc_joker,`
  `room_cc_kingbattle, room_cc_lancer, room_cc_prefountain,`
  `room_cc_preroof, room_cc_prison_cells, room_cc_prison_prejoker,`
  `room_cc_prison_to_elevator, room_cc_prison2, room_cc_prisonelevator,`
  `room_cc_prisonlancer, room_cc_rudinn, room_cc_rurus1, room_cc_rurus2,`
  `room_cc_throneroom, room_dark_chase1, room_dark_chase2,`
  `room_dark_eyepuzzle, room_dark_wobbles, room_dark1, room_dark1a,`
  `room_dark2, room_dark3, room_dark3a, room_dark7, room_DARKempty,`
  `room_field_boxpuzzle, room_field_checkers1, room_field_checkers2,`
  `room_field_checkers3, room_field_checkers4, room_field_checkers5,`
  `room_field_checkers6, room_field_checkers7, room_field_checkersboss,`
  `room_field_forest, room_field_getsusie, room_field_maze,`
  `room_field_puzzle1, room_field_puzzle2, room_field_puzzletutorial,`
  `room_field_secret1, room_field_shop1, room_field_start,`
  `room_field_topchef, room_field1, room_field2, room_field2A,`
  `room_field3, room_field4, room_forest_afterthrash2,`
  `room_forest_afterthrash3, room_forest_afterthrash4,`
  `room_forest_area0, room_forest_area1, room_forest_area2,`
  `room_forest_area2A, room_forest_area3, room_forest_area3A,`
  `room_forest_area4, room_forest_area5, room_forest_beforeclover,`
  `room_forest_castlefront, room_forest_castleview, room_forest_chase1,`
  `room_forest_chase2, room_forest_dancers1, room_forest_fightsusie,`
  `room_forest_maze_deadend, room_forest_maze_deadend2,`
  `room_forest_maze_susie, room_forest_maze1, room_forest_maze2,`
  `room_forest_puzzle1, room_forest_savepoint_relax,`
  `room_forest_savepoint1, room_forest_savepoint2,`
  `room_forest_savepoint3, room_forest_secret1, room_forest_smith,`
  `room_forest_starwalker, room_forest_thrashmaker, room_man`

### Party record 0770

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 || global.char[1] == 2 || global.char[2] == 2)     {`
  `sus = 0`
- condition: `line 245; if (global.charauto[2] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0771

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)         {             sus = 1`
- condition: `line 248; if (global.char[0] == 2 || global.char[1] == 2 ||`
  `global.char[2] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0772

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)         {             sus = 2`
- condition: `line 252; if (global.char[1] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0773

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 169; if (global.char[i] != 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0774

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 178; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0775

- chapter: `1`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 187; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0776

- chapter: `1`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)             {                 onebuffer = 1`
- condition: `line 140; if (global.bmenucoord[0][global.charturn] == 1 &&`
  `global.char[global.charturn] != 1) > if`
  `(global.bmenucoord[0][global.charturn] == 1 &&`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0777

- chapter: `1`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 3; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0778

- chapter: `1`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `2`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0779

- chapter: `1`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 5; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0780

- chapter: `1`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 928; if (global.flag[215] == 1)`
- status: `production`
- rooms: `room_field_checkersboss`

### Party record 0781

- chapter: `1`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 929; if (global.flag[215] == 1)`
- status: `production`
- rooms: `room_field_checkersboss`

### Party record 0782

- chapter: `1`
- phase: `global.char[dx]`
- field: `global.char[dx]`
- expression: `= 2)                 {                     if`
  `(global.charcond[dx] != 5)                     {`
  `global.charcond[dx] = 5`
- condition: `line 245; if (scr_monsterpop() > 1 && scr_havechar(2)) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0783

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 21; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0784

- chapter: `2`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 if (global.cinstance[i].x !=`
  `s.x || global.cinstance[i].y != s.x)                 {`
  `global.cinstance[i].x = s.x`
- condition: `line 7; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0785

- chapter: `2`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 if (global.cinstance[i].x !=`
  `r.x || global.cinstance[i].y != r.x)                 {`
  `global.cinstance[i].x = r.x`
- condition: `line 44; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0786

- chapter: `2`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 s =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 9; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0787

- chapter: `2`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 r =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0788

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `arg0`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0789

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 0)     {         global.char[0] = arg0`
- condition: `line 4; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0790

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && getchar == 0)     {         global.char[1] = arg0`
- condition: `line 9; if (global.char[0] == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0791

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0 && getchar == 0)     {         global.char[2] = arg0`
- condition: `line 14; if (global.char[1] == 0 && getchar == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0792

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 33; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0793

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 38; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0794

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 43; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0795

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 48; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0796

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0797

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0798

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0799

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 19; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0800

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 24; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0801

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 29; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0802

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 34; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0803

- chapter: `2`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         charcan = 0`
- condition: `line 12; if (global.acting[arg0] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0804

- chapter: `2`
- phase: `global.char[caster]`
- field: `global.char[caster]`
- expression: `= 4)         {             dm.type = 6`
- condition: `line 7; if (caster < 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0805

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2)     {         sus = 0`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0806

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)     {         sus = 1`
- condition: `line 7; if (global.char[0] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0807

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)     {         sus = 2`
- condition: `line 11; if (global.char[1] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0808

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 && global.charauto[2] == 1)             {`
  `global.acting[0] = 1`
- condition: `line 111; if (skip == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0809

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             with (obj_monsterparent)`
  `{                 actingnoe = 0`
- condition: `line 28; if (moveswapped == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0810

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             with (obj_monsterparent)`
  `{                 actingral = 0`
- condition: `line 35; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0811

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             with (obj_monsterparent)`
  `{                 actingsus = 0`
- condition: `line 42; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0812

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         global.heromakey[0] =`
  `yy + 140`
- condition: `line 16; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0813

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         global.heromakey[0] = yy + 100`
- condition: `line 20; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0814

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(20)`
- condition: `line 378; case 212: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0815

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(80)`
- condition: `line 382; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0816

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(50)`
- condition: `line 386; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0817

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {                 scr_healitemspell(30)`
- condition: `line 390; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0818

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(80)`
- condition: `line 397; case 213: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0819

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(20)`
- condition: `line 401; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0820

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(50)`
- condition: `line 405; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0821

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {                 scr_healitemspell(70)`
- condition: `line 409; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0822

- chapter: `2`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1) ? 100 : 90`
- condition: `line 462; case 225: > case 226:`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0823

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)         {             suspos = i`
- condition: `line 15; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0824

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)         {             ralpos = i`
- condition: `line 19; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0825

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)         {             noepos = i`
- condition: `line 23; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0826

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cooked to`
  `perfection!", "scr_itemuse_slash_scr_itemuse_gml_123_0"))`
- condition: `line 145; case 8: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0827

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("A bit`
  `burnt...?", "scr_itemuse_slash_scr_itemuse_gml_127_0"))`
- condition: `line 149; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0828

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 153; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0829

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Mmm... face",`
  `"scr_itemuse_slash_scr_itemuse_gml_143_0"))`
- condition: `line 163; case 9: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0830

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `stringsetloc("(uncomfortable)",`
  `"scr_itemuse_slash_scr_itemuse_gml_147_0"))`
- condition: `line 167; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0831

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Umm, what is`
  `this? It's cute...", "scr_itemuse_slash_scr_itemuse_gml_151_0"))`
- condition: `line 171; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0832

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Why this!?",`
  `"scr_itemuse_slash_scr_itemuse_gml_161_0"))`
- condition: `line 179; case 10: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0833

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Let's be`
  `healthy!", "scr_itemuse_slash_scr_itemuse_gml_165_0"))`
- condition: `line 183; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0834

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Something to`
  `graze on!", "scr_itemuse_slash_scr_itemuse_gml_169_0"))`
- condition: `line 187; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0835

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 212; case 12: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0836

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 216; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0837

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 221; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0838

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_healitem(global.charselect, 30)`
- condition: `line 226; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0839

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 234; case 13: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0840

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 238; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0841

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 243; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0842

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_healitem(0, 35)`
- condition: `line 248; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0843

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(It's SO`
  `good!)", "scr_itemuse_slash_scr_itemuse_gml_239_0"))`
- condition: `line 258; case 14: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0844

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("K-Kris!? I...",`
  `"scr_itemuse_slash_scr_itemuse_gml_243_0"))`
- condition: `line 262; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0845

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Huh? I didn't`
  `know Kris liked this flavor.)",`
  `"scr_itemuse_slash_scr_itemuse_gml_247_0"))`
- condition: `line 266; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0846

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cool, it's`
  `wriggling.", "scr_itemuse_slash_scr_itemuse_gml_257_0"))`
- condition: `line 274; case 15: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0847

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Yum, is this`
  `spaghetti?", "scr_itemuse_slash_scr_itemuse_gml_261_0"))`
- condition: `line 278; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0848

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Tastes like...`
  `jumprope?", "scr_itemuse_slash_scr_itemuse_gml_265_0"))`
- condition: `line 282; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0849

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (scr_havechar(2))`
  `{                     scr_itemcomment(suspos, stringsetloc("(No`
  `reaction?)", "scr_itemuse_slash_scr_itemuse_gml_303_0"))`
- condition: `line 319; case 18: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0850

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell yeah,`
  `apple juice!!", "scr_itemuse_slash_scr_itemuse_gml_309_0"))`
- condition: `line 330; if (scr_havechar(4)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0851

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Tastes like`
  `blueberries!", "scr_itemuse_slash_scr_itemuse_gml_315_0"))`
- condition: `line 338; if (scr_havechar(3)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0852

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Tastes like`
  `cinnamon! (What is this aftertaste...?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_320_0"))`
- condition: `line 346; if (scr_havechar(2)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0853

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (scr_havechar(2))`
  `{                     scr_itemcomment(suspos, stringsetloc("(...`
  `do they like it?)", "scr_itemuse_slash_scr_itemuse_gml_332_0"))`
- condition: `line 355; case 19: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0854

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell yeah,`
  `eggnog!!", "scr_itemuse_slash_scr_itemuse_gml_339_0"))`
- condition: `line 370; if (scr_havechar(4)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0855

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It's soft and`
  `sweet.", "scr_itemuse_slash_scr_itemuse_gml_345_0"))`
- condition: `line 378; if (scr_havechar(3)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0856

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("... this is`
  `just water! You're pranking me, right?!",`
  `"scr_itemuse_slash_scr_itemuse_gml_349_0"))`
- condition: `line 382; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0857

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (scr_havechar(2))`
  `{                     scr_itemcomment(suspos, stringsetloc("(No`
  `reaction?)", "scr_itemuse_slash_scr_itemuse_gml_361_0"))`
- condition: `line 391; case 20: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0858

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hey, it's like`
  `marshmallows!!", "scr_itemuse_slash_scr_itemuse_gml_367_0"))`
- condition: `line 402; if (scr_havechar(3)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0859

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Um... isn't`
  `this water?", "scr_itemuse_slash_scr_itemuse_gml_373_0"))`
- condition: `line 410; if (scr_havechar(3)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0860

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("There's nothing`
  `in here!", "scr_itemuse_slash_scr_itemuse_gml_377_0"))`
- condition: `line 414; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0861

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (scr_havechar("susie"))`
  `{                     scr_itemcomment(suspos, stringsetloc("STOP`
  `LOOKING AT ME!", "scr_itemuse_slash_scr_itemuse_gml_389_0"))`
- condition: `line 423; case 21: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0862

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("... this is`
  `tea?", "scr_itemuse_slash_scr_itemuse_gml_395_0"))`
- condition: `line 434; if (scr_havechar("ralsei")) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0863

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It's grape`
  `juice!", "scr_itemuse_slash_scr_itemuse_gml_400_0"))`
- condition: `line 438; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0864

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Wonder if they`
  `sell this in gallons?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_405_0"))`
- condition: `line 446; if (scr_havechar("susie")) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0865

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("C'mon, gimme`
  `the rest!", "scr_itemuse_slash_scr_itemuse_gml_418_0"))`
- condition: `line 456; case 22: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0866

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("M-maybe give`
  `Susie the rest?", "scr_itemuse_slash_scr_itemuse_gml_422_0"))`
- condition: `line 460; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0867

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 464; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0868

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hey, this`
  `rules!", "scr_itemuse_slash_scr_itemuse_gml_438_0"))`
- condition: `line 474; case 23: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0869

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Nice and`
  `chalky.", "scr_itemuse_slash_scr_itemuse_gml_442_0"))`
- condition: `line 478; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0870

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I-isn't this`
  `the chalk I gave her?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_446_0"))`
- condition: `line 482; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0871

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell'd you call`
  `this!?", "scr_itemuse_slash_scr_itemuse_gml_456_0"))`
- condition: `line 490; case 24: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0872

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I made this.",`
  `"scr_itemuse_slash_scr_itemuse_gml_460_0"))`
- condition: `line 494; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0873

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("B-Brainfreeze!`
  `... kidding!", "scr_itemuse_slash_scr_itemuse_gml_464_0"))`
- condition: `line 498; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0874

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 heal_amount = 100`
- condition: `line 522; case 26: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0875

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says GUTS!",`
  `"scr_itemuse_slash_scr_itemuse_gml_487_0"))`
- condition: `line 526; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0876

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says`
  `Fluffy...", "scr_itemuse_slash_scr_itemuse_gml_491_0"))`
- condition: `line 530; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0877

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I... I can't`
  `read these symbols...",`
  `"scr_itemuse_slash_scr_itemuse_gml_495_0"))`
- condition: `line 534; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0878

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ugh! ...tastes`
  `good?", "scr_itemuse_slash_scr_itemuse_gml_553_0"))`
- condition: `line 600; if (global.char[global.charselect] != 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0879

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ow... er,`
  `thanks, Kris!", "scr_itemuse_slash_scr_itemuse_gml_557_0"))`
- condition: `line 604; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0880

- chapter: `2`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I'll... just`
  `pretend to drink it...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_561_0"))`
- condition: `line 608; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0881

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0882

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0883

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0884

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0885

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0886

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0887

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)                     {                         facetype =`
  `spr_headkris`
- condition: `line 34; if (itemtype[menuc[1]] == "weapon" || itemtype[menuc[1]]`
  `== "armor") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0888

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         facetype =`
  `spr_headsusie`
- condition: `line 38; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0889

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         facetype =`
  `spr_headralsei`
- condition: `line 42; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0890

- chapter: `2`
- phase: `global.char[__findchar]`
- field: `global.char[__findchar]`
- expression: `= arg0)         {             __charslot = __findchar`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0891

- chapter: `2`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 2)                 {                     with (__minstance)`
  `{                         actconsus = 1`
- condition: `line 25; if (global.actingsingle[global.currentactingchar] == 1)`
  `> if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0892

- chapter: `2`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 3)                 {                     with (__minstance)`
  `{                         actconral = 1`
- condition: `line 37; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0893

- chapter: `2`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 4)                 {                     with (__minstance)`
  `{                         actconnoe = 1`
- condition: `line 49; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0894

- chapter: `2`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 1 &&`
  `global.actsimul[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderkri = __simulcount`
- condition: `line 9; if (global.actingsingle[__ii] == 1 &&`
  `instance_exists(obj_monsterparent)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0895

- chapter: `2`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 2 &&`
  `global.actsimulsus[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordersus = __simulcount`
- condition: `line 18; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0896

- chapter: `2`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 3 &&`
  `global.actsimulral[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderral = __simulcount`
- condition: `line 27; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0897

- chapter: `2`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 4 &&`
  `global.actsimulnoe[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordernoe = __simulcount`
- condition: `line 36; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0898

- chapter: `2`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 1)             {                 if (global.canact[0][__fj] ==`
  `1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0899

- chapter: `2`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 2)             {                 if (global.canactsus[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 33; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0900

- chapter: `2`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 3)             {                 if (global.canactral[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 53; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0901

- chapter: `2`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 4)             {                 if (global.canactnoe[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 73; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0902

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             global.monsterinstance[arg0].acting =`
  `arg1 + 1`
- condition: `line 5; if (i_ex(global.monsterinstance[arg0])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0903

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {`
  `global.monsterinstance[arg0].actingsus = arg1 + 1`
- condition: `line 9; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0904

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {`
  `global.monsterinstance[arg0].actingral = arg1 + 1`
- condition: `line 13; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0905

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {`
  `global.monsterinstance[arg0].actingnoe = arg1 + 1`
- condition: `line 17; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0906

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)     {         global.actingsimul[0] = actsimul[arg1]`
- condition: `line 22; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0907

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[arg0][__acti]`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0908

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[arg0][__acti]`
- condition: `line 12; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0909

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[arg0][__acti]`
- condition: `line 18; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0910

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[arg0][__acti]`
- condition: `line 24; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0911

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0912

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0913

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0914

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 17; if (checker == "noelle" || checker == "no" || checker ==`
  `"n") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0915

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 21; if (global.char[0] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0916

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 25; if (global.char[1] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0917

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 12; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0918

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 12; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0919

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0920

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 5; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0921

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 0922

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 35; if (global.char[i] != 4) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0923

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 39; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0924

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 c[i].sprite_index =`
  `spr_ralsei_battleintro`
- condition: `line 47; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0925

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 53; if (global.char[i] != 0) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_castle_town,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_DARKempty, room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_castle_area_1,`
  `room_dw_castle_area_2, room_dw_castle_area_2_transformed,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_hallway, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_lancer, room_dw_castle_rooms_susie,`
  `room_dw_castle_west_cliff, room_dw_castle_west_cliff_old,`
  `room_dw_city_baseball, room_dw_city_berdly, room_dw_city_big_1,`
  `room_dw_city_big_1_original, room_dw_city_big_2,`
  `room_dw_city_big_2_OG, room_dw_city_big_3,`
  `room_dw_city_big_3_backup_2exits, room_dw_city_big_3_og,`
  `room_dw_city_carnival, room_dw_city_cheese, room_dw_city_cheesemaze,`
  `room_dw_city_dog_traffic, room_dw_city_entrance, room_dw_city_hacker,`
  `room_dw_city_intro, room_dw_city_man, room_dw_city_mansion_front,`
  `room_dw_city_mice, room_dw_city_mice2, room_dw_city_mice2_og,`
  `room_dw_city_mice3, room_dw_city_mirrorfriend,`
  `room_dw_city_monologue, room_dw_city_monologue_old,`
  `room_dw_city_moss, room_dw_city_noelle_fight_intro,`
  `room_dw_city_poppup, room_dw_city_postbaseball_1,`
  `room_dw_city_postbaseball_2, room_dw_city_postbaseball_3,`
  `room_dw_city_prototype_01, room_dw_city_prototype_02,`
  `room_dw_city_queen_drunk, room_dw_city_roadblock,`
  `room_dw_city_savepoint, room_dw_city_sidewayscars,`
  `room_dw_city_spamton_alley, room_dw_city_spamton_house,`
  `room_dw_city_spamton_shop_exterior,`
  `room_dw_city_spamton_shop_interior, room_dw_city_split,`
  `room_dw_city_susie_ralsei_fun_1, room_dw_city_traffic_1,`
  `room_dw_city_traffic_2, room_dw_city_traffic_2_old,`
  `room_dw_city_traffic_3, room_dw_city_traffic_3_2Entrances,`
  `room_dw_city_traffic_3_backup, room_dw_city_traffic_4,`
  `room_dw_city_traffic_5_old, room_dw_city_treasure,`
  `room_dw_cyber_battle_maze_1, room_dw_cyber_battle_maze_1_Original,`
  `room_dw_cyber_battle_maze_2, room_dw_cyber_battle_maze_2_old,`
  `room_dw_cyber_battle_maze_2_toby, room_dw_cyber_battle_maze_3,`
  `room_dw_cyber_escalator_slide, room_dw_cyber_intro_1,`
  `room_dw_cyber_intro_2, room_dw_cyber_intro_connector,`
  `room_dw_cyber_keyboard_puzzle_1, room_dw_cyber_keyboard_puzzle_1_old,`
  `room_dw_cyber_keyboard_puzzle_2, room_dw_cyber_keyboard_puzzle_3,`
  `room_dw_cyber_keyboardexample, room_dw_cyber_maze_fireworks,`
  `room_dw_cyber_maze_queenscreen, room_dw_cyber_maze_rhythm,`
  `room_dw_cyber_maze_tasque, room_dw_cyber_maze_virokun,`
  `room_dw_cyber_maze_virokun_backuo, room_dw_cyber_music_bullet,`
  `room_dw_cyber_music_bullet_original, room_dw_cyber_music_fight,`
  `room_dw_cyber_music_final, room_dw_cyber_musical_door,`
  `room_dw_cyber_musical_shop, room_dw_cyber_nuberts_treasure,`
  `room_dw_cyber_post_music_boss_slide, room_dw_cyber_queen_boxing,`
  `room_dw_cyber_rhythm_slide, room_dw_cyber_rollercoaster,`
  `room_dw_cyber_savepoint, room_dw_cyber_savepoint_original,`
  `room_dw_cyber_shaunsmusicalbullettunnel, room_dw_cyber_tasque_battle,`
  `room_dw_cyber_tasque_battle_og, room_dw_cyber_teacup_1,`
  `room_dw_cyber_teacup_2, room_dw_cyber_teacup_final,`
  `room_dw_cyber_viro_ring, room_dw_cyber_viromaze2,`
  `room_dw_cyber_virovirokun_fight, room_dw_mansion_acid_tunnel,`
  `room_dw_mansion_acid_tunnel_exit,`
  `room_dw_mansion_acid_tunnel_loop_rouxls,`
  `room_dw_mansion_acid_tunnel_old,`
  `room_dw_mansion_acid_tunnel_puzzle_entrance,`
  `room_dw_mansion_b_central, room_dw_mansion_b_east,`
  `room_dw_mansion_b_east_a, room_dw_mansion_b_east_b,`
  `room_dw_mansion_b_east_transformed, room_dw_mansion_b_entrance,`
  `room_dw_mansion_b_stairs, room_dw_mansion_b_west_1f,`
  `room_dw_mansion_b_west_1f_a, room_dw_mansion_b_west_1f_b,`
  `room_dw_mansion_b_west_2f, room_dw_mansion_bridges,`
  `room_dw_mansion_bridges_funny, room_dw_mansion_bridgesold,`
  `room_dw_mansion_darkbulb_1, room_dw_mansion_darkbulb_2,`
  `room_dw_mansion_darkbulb_3, room_dw_mansion_dining_a,`
  `room_dw_mansion_dining_storage, room_dw_mansion_dining_storage_old,`
  `room_dw_mansion_dining3, room_dw_mansion_dininghall,`
  `room_dw_mansion_east_1f_a, room_dw_mansion_east_1f_b,`
  `room_dw_mansion_east_1f_c, room_dw_mansion_east_1f_d,`
  `room_dw_mansion_east_1f_e, room_dw_mansion_east_1f_secret,`
  `room_dw_mansion_east_2f_a, room_dw_mansion_east_2f_c,`
  `room_dw_mansion_east_2f_c_a, room_dw_mansion_east_2f_c_b,`
  `room_dw_mansion_east_2f_d, room_dw_mansion_east_2f_d_backup,`
  `room_dw_mansion_east_2f_shortcut, room_dw_mansion_east_2f_teacup,`
  `room_dw_mansion_east_2f_transformed_new,`
  `room_dw_mansion_east_2f_ufo_old, room_dw_mansion_east_3f,`
  `room_dw_mansion_east_3f_projection, room_dw_mansion_east_3f_toilet,`
  `room_dw_mansion_east_4f_a, room_dw_mansion_east_4f_b,`
  `room_dw_mansion_east_4f_c, room_dw_mansion_east_4f_d,`
  `room_dw_mansion_east_4f_e, room_dw_mansion_east_teacup,`
  `room_dw_mansion_east_teacup_2, room_dw_mansion_east_teacup_3,`
  `room_dw_mansion_east_teacup_4, room_dw_mansion_east_teacup_4_old,`
  `room_dw_mansion_elevator, room_dw_mansion_entrance,`
  `room_dw_mansion_ferris_wheel, room_dw_mansion_ferris_wheel_post,`
  `room_dw_mansion_fire_paintings, room_dw_mansion_fountain,`
  `room_dw_mansion_hands, room_dw_mansion_kitchen,`
  `room_dw_mansion_krisroom, room_dw_mansion_lightner_hallway,`
  `room_dw_mansion_mouseLottery, room_dw_mansion_noelle_room,`
  `room_dw_mansion_potBalance, room_dw_mansion_prefountain,`
  `room_dw_mansion_single_pot, room_dw_mansion_sparks,`
  `room_dw_mansion_susieroom, room_dw_mansion_tasquePaintings,`
  `room_dw_mansion_top, room_dw_mansion_top_post,`
  `room_dw_mansion_top_post_old, room_dw_mansion_traffic,`
  `room_dw_mansion_traffic_original, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_front,`
  `room_GMS2_test, room_shaun_puzzle, room_teacup_demoauto,`
  `room_teacup_demobullets`

### Party record 0926

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 58; if (global.char[i] == 1) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_castle_town,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_DARKempty, room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_castle_area_1,`
  `room_dw_castle_area_2, room_dw_castle_area_2_transformed,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_hallway, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_lancer, room_dw_castle_rooms_susie,`
  `room_dw_castle_west_cliff, room_dw_castle_west_cliff_old,`
  `room_dw_city_baseball, room_dw_city_berdly, room_dw_city_big_1,`
  `room_dw_city_big_1_original, room_dw_city_big_2,`
  `room_dw_city_big_2_OG, room_dw_city_big_3,`
  `room_dw_city_big_3_backup_2exits, room_dw_city_big_3_og,`
  `room_dw_city_carnival, room_dw_city_cheese, room_dw_city_cheesemaze,`
  `room_dw_city_dog_traffic, room_dw_city_entrance, room_dw_city_hacker,`
  `room_dw_city_intro, room_dw_city_man, room_dw_city_mansion_front,`
  `room_dw_city_mice, room_dw_city_mice2, room_dw_city_mice2_og,`
  `room_dw_city_mice3, room_dw_city_mirrorfriend,`
  `room_dw_city_monologue, room_dw_city_monologue_old,`
  `room_dw_city_moss, room_dw_city_noelle_fight_intro,`
  `room_dw_city_poppup, room_dw_city_postbaseball_1,`
  `room_dw_city_postbaseball_2, room_dw_city_postbaseball_3,`
  `room_dw_city_prototype_01, room_dw_city_prototype_02,`
  `room_dw_city_queen_drunk, room_dw_city_roadblock,`
  `room_dw_city_savepoint, room_dw_city_sidewayscars,`
  `room_dw_city_spamton_alley, room_dw_city_spamton_house,`
  `room_dw_city_spamton_shop_exterior,`
  `room_dw_city_spamton_shop_interior, room_dw_city_split,`
  `room_dw_city_susie_ralsei_fun_1, room_dw_city_traffic_1,`
  `room_dw_city_traffic_2, room_dw_city_traffic_2_old,`
  `room_dw_city_traffic_3, room_dw_city_traffic_3_2Entrances,`
  `room_dw_city_traffic_3_backup, room_dw_city_traffic_4,`
  `room_dw_city_traffic_5_old, room_dw_city_treasure,`
  `room_dw_cyber_battle_maze_1, room_dw_cyber_battle_maze_1_Original,`
  `room_dw_cyber_battle_maze_2, room_dw_cyber_battle_maze_2_old,`
  `room_dw_cyber_battle_maze_2_toby, room_dw_cyber_battle_maze_3,`
  `room_dw_cyber_escalator_slide, room_dw_cyber_intro_1,`
  `room_dw_cyber_intro_2, room_dw_cyber_intro_connector,`
  `room_dw_cyber_keyboard_puzzle_1, room_dw_cyber_keyboard_puzzle_1_old,`
  `room_dw_cyber_keyboard_puzzle_2, room_dw_cyber_keyboard_puzzle_3,`
  `room_dw_cyber_keyboardexample, room_dw_cyber_maze_fireworks,`
  `room_dw_cyber_maze_queenscreen, room_dw_cyber_maze_rhythm,`
  `room_dw_cyber_maze_tasque, room_dw_cyber_maze_virokun,`
  `room_dw_cyber_maze_virokun_backuo, room_dw_cyber_music_bullet,`
  `room_dw_cyber_music_bullet_original, room_dw_cyber_music_fight,`
  `room_dw_cyber_music_final, room_dw_cyber_musical_door,`
  `room_dw_cyber_musical_shop, room_dw_cyber_nuberts_treasure,`
  `room_dw_cyber_post_music_boss_slide, room_dw_cyber_queen_boxing,`
  `room_dw_cyber_rhythm_slide, room_dw_cyber_rollercoaster,`
  `room_dw_cyber_savepoint, room_dw_cyber_savepoint_original,`
  `room_dw_cyber_shaunsmusicalbullettunnel, room_dw_cyber_tasque_battle,`
  `room_dw_cyber_tasque_battle_og, room_dw_cyber_teacup_1,`
  `room_dw_cyber_teacup_2, room_dw_cyber_teacup_final,`
  `room_dw_cyber_viro_ring, room_dw_cyber_viromaze2,`
  `room_dw_cyber_virovirokun_fight, room_dw_mansion_acid_tunnel,`
  `room_dw_mansion_acid_tunnel_exit,`
  `room_dw_mansion_acid_tunnel_loop_rouxls,`
  `room_dw_mansion_acid_tunnel_old,`
  `room_dw_mansion_acid_tunnel_puzzle_entrance,`
  `room_dw_mansion_b_central, room_dw_mansion_b_east,`
  `room_dw_mansion_b_east_a, room_dw_mansion_b_east_b,`
  `room_dw_mansion_b_east_transformed, room_dw_mansion_b_entrance,`
  `room_dw_mansion_b_stairs, room_dw_mansion_b_west_1f,`
  `room_dw_mansion_b_west_1f_a, room_dw_mansion_b_west_1f_b,`
  `room_dw_mansion_b_west_2f, room_dw_mansion_bridges,`
  `room_dw_mansion_bridges_funny, room_dw_mansion_bridgesold,`
  `room_dw_mansion_darkbulb_1, room_dw_mansion_darkbulb_2,`
  `room_dw_mansion_darkbulb_3, room_dw_mansion_dining_a,`
  `room_dw_mansion_dining_storage, room_dw_mansion_dining_storage_old,`
  `room_dw_mansion_dining3, room_dw_mansion_dininghall,`
  `room_dw_mansion_east_1f_a, room_dw_mansion_east_1f_b,`
  `room_dw_mansion_east_1f_c, room_dw_mansion_east_1f_d,`
  `room_dw_mansion_east_1f_e, room_dw_mansion_east_1f_secret,`
  `room_dw_mansion_east_2f_a, room_dw_mansion_east_2f_c,`
  `room_dw_mansion_east_2f_c_a, room_dw_mansion_east_2f_c_b,`
  `room_dw_mansion_east_2f_d, room_dw_mansion_east_2f_d_backup,`
  `room_dw_mansion_east_2f_shortcut, room_dw_mansion_east_2f_teacup,`
  `room_dw_mansion_east_2f_transformed_new,`
  `room_dw_mansion_east_2f_ufo_old, room_dw_mansion_east_3f,`
  `room_dw_mansion_east_3f_projection, room_dw_mansion_east_3f_toilet,`
  `room_dw_mansion_east_4f_a, room_dw_mansion_east_4f_b,`
  `room_dw_mansion_east_4f_c, room_dw_mansion_east_4f_d,`
  `room_dw_mansion_east_4f_e, room_dw_mansion_east_teacup,`
  `room_dw_mansion_east_teacup_2, room_dw_mansion_east_teacup_3,`
  `room_dw_mansion_east_teacup_4, room_dw_mansion_east_teacup_4_old,`
  `room_dw_mansion_elevator, room_dw_mansion_entrance,`
  `room_dw_mansion_ferris_wheel, room_dw_mansion_ferris_wheel_post,`
  `room_dw_mansion_fire_paintings, room_dw_mansion_fountain,`
  `room_dw_mansion_hands, room_dw_mansion_kitchen,`
  `room_dw_mansion_krisroom, room_dw_mansion_lightner_hallway,`
  `room_dw_mansion_mouseLottery, room_dw_mansion_noelle_room,`
  `room_dw_mansion_potBalance, room_dw_mansion_prefountain,`
  `room_dw_mansion_single_pot, room_dw_mansion_sparks,`
  `room_dw_mansion_susieroom, room_dw_mansion_tasquePaintings,`
  `room_dw_mansion_top, room_dw_mansion_top_post,`
  `room_dw_mansion_top_post_old, room_dw_mansion_traffic,`
  `room_dw_mansion_traffic_original, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_front,`
  `room_GMS2_test, room_shaun_puzzle, room_teacup_demoauto,`
  `room_teacup_demobullets`

### Party record 0927

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 68; if (i > 0) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_castle_town,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_DARKempty, room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_castle_area_1,`
  `room_dw_castle_area_2, room_dw_castle_area_2_transformed,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_hallway, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_lancer, room_dw_castle_rooms_susie,`
  `room_dw_castle_west_cliff, room_dw_castle_west_cliff_old,`
  `room_dw_city_baseball, room_dw_city_berdly, room_dw_city_big_1,`
  `room_dw_city_big_1_original, room_dw_city_big_2,`
  `room_dw_city_big_2_OG, room_dw_city_big_3,`
  `room_dw_city_big_3_backup_2exits, room_dw_city_big_3_og,`
  `room_dw_city_carnival, room_dw_city_cheese, room_dw_city_cheesemaze,`
  `room_dw_city_dog_traffic, room_dw_city_entrance, room_dw_city_hacker,`
  `room_dw_city_intro, room_dw_city_man, room_dw_city_mansion_front,`
  `room_dw_city_mice, room_dw_city_mice2, room_dw_city_mice2_og,`
  `room_dw_city_mice3, room_dw_city_mirrorfriend,`
  `room_dw_city_monologue, room_dw_city_monologue_old,`
  `room_dw_city_moss, room_dw_city_noelle_fight_intro,`
  `room_dw_city_poppup, room_dw_city_postbaseball_1,`
  `room_dw_city_postbaseball_2, room_dw_city_postbaseball_3,`
  `room_dw_city_prototype_01, room_dw_city_prototype_02,`
  `room_dw_city_queen_drunk, room_dw_city_roadblock,`
  `room_dw_city_savepoint, room_dw_city_sidewayscars,`
  `room_dw_city_spamton_alley, room_dw_city_spamton_house,`
  `room_dw_city_spamton_shop_exterior,`
  `room_dw_city_spamton_shop_interior, room_dw_city_split,`
  `room_dw_city_susie_ralsei_fun_1, room_dw_city_traffic_1,`
  `room_dw_city_traffic_2, room_dw_city_traffic_2_old,`
  `room_dw_city_traffic_3, room_dw_city_traffic_3_2Entrances,`
  `room_dw_city_traffic_3_backup, room_dw_city_traffic_4,`
  `room_dw_city_traffic_5_old, room_dw_city_treasure,`
  `room_dw_cyber_battle_maze_1, room_dw_cyber_battle_maze_1_Original,`
  `room_dw_cyber_battle_maze_2, room_dw_cyber_battle_maze_2_old,`
  `room_dw_cyber_battle_maze_2_toby, room_dw_cyber_battle_maze_3,`
  `room_dw_cyber_escalator_slide, room_dw_cyber_intro_1,`
  `room_dw_cyber_intro_2, room_dw_cyber_intro_connector,`
  `room_dw_cyber_keyboard_puzzle_1, room_dw_cyber_keyboard_puzzle_1_old,`
  `room_dw_cyber_keyboard_puzzle_2, room_dw_cyber_keyboard_puzzle_3,`
  `room_dw_cyber_keyboardexample, room_dw_cyber_maze_fireworks,`
  `room_dw_cyber_maze_queenscreen, room_dw_cyber_maze_rhythm,`
  `room_dw_cyber_maze_tasque, room_dw_cyber_maze_virokun,`
  `room_dw_cyber_maze_virokun_backuo, room_dw_cyber_music_bullet,`
  `room_dw_cyber_music_bullet_original, room_dw_cyber_music_fight,`
  `room_dw_cyber_music_final, room_dw_cyber_musical_door,`
  `room_dw_cyber_musical_shop, room_dw_cyber_nuberts_treasure,`
  `room_dw_cyber_post_music_boss_slide, room_dw_cyber_queen_boxing,`
  `room_dw_cyber_rhythm_slide, room_dw_cyber_rollercoaster,`
  `room_dw_cyber_savepoint, room_dw_cyber_savepoint_original,`
  `room_dw_cyber_shaunsmusicalbullettunnel, room_dw_cyber_tasque_battle,`
  `room_dw_cyber_tasque_battle_og, room_dw_cyber_teacup_1,`
  `room_dw_cyber_teacup_2, room_dw_cyber_teacup_final,`
  `room_dw_cyber_viro_ring, room_dw_cyber_viromaze2,`
  `room_dw_cyber_virovirokun_fight, room_dw_mansion_acid_tunnel,`
  `room_dw_mansion_acid_tunnel_exit,`
  `room_dw_mansion_acid_tunnel_loop_rouxls,`
  `room_dw_mansion_acid_tunnel_old,`
  `room_dw_mansion_acid_tunnel_puzzle_entrance,`
  `room_dw_mansion_b_central, room_dw_mansion_b_east,`
  `room_dw_mansion_b_east_a, room_dw_mansion_b_east_b,`
  `room_dw_mansion_b_east_transformed, room_dw_mansion_b_entrance,`
  `room_dw_mansion_b_stairs, room_dw_mansion_b_west_1f,`
  `room_dw_mansion_b_west_1f_a, room_dw_mansion_b_west_1f_b,`
  `room_dw_mansion_b_west_2f, room_dw_mansion_bridges,`
  `room_dw_mansion_bridges_funny, room_dw_mansion_bridgesold,`
  `room_dw_mansion_darkbulb_1, room_dw_mansion_darkbulb_2,`
  `room_dw_mansion_darkbulb_3, room_dw_mansion_dining_a,`
  `room_dw_mansion_dining_storage, room_dw_mansion_dining_storage_old,`
  `room_dw_mansion_dining3, room_dw_mansion_dininghall,`
  `room_dw_mansion_east_1f_a, room_dw_mansion_east_1f_b,`
  `room_dw_mansion_east_1f_c, room_dw_mansion_east_1f_d,`
  `room_dw_mansion_east_1f_e, room_dw_mansion_east_1f_secret,`
  `room_dw_mansion_east_2f_a, room_dw_mansion_east_2f_c,`
  `room_dw_mansion_east_2f_c_a, room_dw_mansion_east_2f_c_b,`
  `room_dw_mansion_east_2f_d, room_dw_mansion_east_2f_d_backup,`
  `room_dw_mansion_east_2f_shortcut, room_dw_mansion_east_2f_teacup,`
  `room_dw_mansion_east_2f_transformed_new,`
  `room_dw_mansion_east_2f_ufo_old, room_dw_mansion_east_3f,`
  `room_dw_mansion_east_3f_projection, room_dw_mansion_east_3f_toilet,`
  `room_dw_mansion_east_4f_a, room_dw_mansion_east_4f_b,`
  `room_dw_mansion_east_4f_c, room_dw_mansion_east_4f_d,`
  `room_dw_mansion_east_4f_e, room_dw_mansion_east_teacup,`
  `room_dw_mansion_east_teacup_2, room_dw_mansion_east_teacup_3,`
  `room_dw_mansion_east_teacup_4, room_dw_mansion_east_teacup_4_old,`
  `room_dw_mansion_elevator, room_dw_mansion_entrance,`
  `room_dw_mansion_ferris_wheel, room_dw_mansion_ferris_wheel_post,`
  `room_dw_mansion_fire_paintings, room_dw_mansion_fountain,`
  `room_dw_mansion_hands, room_dw_mansion_kitchen,`
  `room_dw_mansion_krisroom, room_dw_mansion_lightner_hallway,`
  `room_dw_mansion_mouseLottery, room_dw_mansion_noelle_room,`
  `room_dw_mansion_potBalance, room_dw_mansion_prefountain,`
  `room_dw_mansion_single_pot, room_dw_mansion_sparks,`
  `room_dw_mansion_susieroom, room_dw_mansion_tasquePaintings,`
  `room_dw_mansion_top, room_dw_mansion_top_post,`
  `room_dw_mansion_top_post_old, room_dw_mansion_traffic,`
  `room_dw_mansion_traffic_original, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_front,`
  `room_GMS2_test, room_shaun_puzzle, room_teacup_demoauto,`
  `room_teacup_demobullets`

### Party record 0928

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 97; if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_castle_town,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_DARKempty, room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_castle_area_1,`
  `room_dw_castle_area_2, room_dw_castle_area_2_transformed,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_hallway, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_lancer, room_dw_castle_rooms_susie,`
  `room_dw_castle_west_cliff, room_dw_castle_west_cliff_old,`
  `room_dw_city_baseball, room_dw_city_berdly, room_dw_city_big_1,`
  `room_dw_city_big_1_original, room_dw_city_big_2,`
  `room_dw_city_big_2_OG, room_dw_city_big_3,`
  `room_dw_city_big_3_backup_2exits, room_dw_city_big_3_og,`
  `room_dw_city_carnival, room_dw_city_cheese, room_dw_city_cheesemaze,`
  `room_dw_city_dog_traffic, room_dw_city_entrance, room_dw_city_hacker,`
  `room_dw_city_intro, room_dw_city_man, room_dw_city_mansion_front,`
  `room_dw_city_mice, room_dw_city_mice2, room_dw_city_mice2_og,`
  `room_dw_city_mice3, room_dw_city_mirrorfriend,`
  `room_dw_city_monologue, room_dw_city_monologue_old,`
  `room_dw_city_moss, room_dw_city_noelle_fight_intro,`
  `room_dw_city_poppup, room_dw_city_postbaseball_1,`
  `room_dw_city_postbaseball_2, room_dw_city_postbaseball_3,`
  `room_dw_city_prototype_01, room_dw_city_prototype_02,`
  `room_dw_city_queen_drunk, room_dw_city_roadblock,`
  `room_dw_city_savepoint, room_dw_city_sidewayscars,`
  `room_dw_city_spamton_alley, room_dw_city_spamton_house,`
  `room_dw_city_spamton_shop_exterior,`
  `room_dw_city_spamton_shop_interior, room_dw_city_split,`
  `room_dw_city_susie_ralsei_fun_1, room_dw_city_traffic_1,`
  `room_dw_city_traffic_2, room_dw_city_traffic_2_old,`
  `room_dw_city_traffic_3, room_dw_city_traffic_3_2Entrances,`
  `room_dw_city_traffic_3_backup, room_dw_city_traffic_4,`
  `room_dw_city_traffic_5_old, room_dw_city_treasure,`
  `room_dw_cyber_battle_maze_1, room_dw_cyber_battle_maze_1_Original,`
  `room_dw_cyber_battle_maze_2, room_dw_cyber_battle_maze_2_old,`
  `room_dw_cyber_battle_maze_2_toby, room_dw_cyber_battle_maze_3,`
  `room_dw_cyber_escalator_slide, room_dw_cyber_intro_1,`
  `room_dw_cyber_intro_2, room_dw_cyber_intro_connector,`
  `room_dw_cyber_keyboard_puzzle_1, room_dw_cyber_keyboard_puzzle_1_old,`
  `room_dw_cyber_keyboard_puzzle_2, room_dw_cyber_keyboard_puzzle_3,`
  `room_dw_cyber_keyboardexample, room_dw_cyber_maze_fireworks,`
  `room_dw_cyber_maze_queenscreen, room_dw_cyber_maze_rhythm,`
  `room_dw_cyber_maze_tasque, room_dw_cyber_maze_virokun,`
  `room_dw_cyber_maze_virokun_backuo, room_dw_cyber_music_bullet,`
  `room_dw_cyber_music_bullet_original, room_dw_cyber_music_fight,`
  `room_dw_cyber_music_final, room_dw_cyber_musical_door,`
  `room_dw_cyber_musical_shop, room_dw_cyber_nuberts_treasure,`
  `room_dw_cyber_post_music_boss_slide, room_dw_cyber_queen_boxing,`
  `room_dw_cyber_rhythm_slide, room_dw_cyber_rollercoaster,`
  `room_dw_cyber_savepoint, room_dw_cyber_savepoint_original,`
  `room_dw_cyber_shaunsmusicalbullettunnel, room_dw_cyber_tasque_battle,`
  `room_dw_cyber_tasque_battle_og, room_dw_cyber_teacup_1,`
  `room_dw_cyber_teacup_2, room_dw_cyber_teacup_final,`
  `room_dw_cyber_viro_ring, room_dw_cyber_viromaze2,`
  `room_dw_cyber_virovirokun_fight, room_dw_mansion_acid_tunnel,`
  `room_dw_mansion_acid_tunnel_exit,`
  `room_dw_mansion_acid_tunnel_loop_rouxls,`
  `room_dw_mansion_acid_tunnel_old,`
  `room_dw_mansion_acid_tunnel_puzzle_entrance,`
  `room_dw_mansion_b_central, room_dw_mansion_b_east,`
  `room_dw_mansion_b_east_a, room_dw_mansion_b_east_b,`
  `room_dw_mansion_b_east_transformed, room_dw_mansion_b_entrance,`
  `room_dw_mansion_b_stairs, room_dw_mansion_b_west_1f,`
  `room_dw_mansion_b_west_1f_a, room_dw_mansion_b_west_1f_b,`
  `room_dw_mansion_b_west_2f, room_dw_mansion_bridges,`
  `room_dw_mansion_bridges_funny, room_dw_mansion_bridgesold,`
  `room_dw_mansion_darkbulb_1, room_dw_mansion_darkbulb_2,`
  `room_dw_mansion_darkbulb_3, room_dw_mansion_dining_a,`
  `room_dw_mansion_dining_storage, room_dw_mansion_dining_storage_old,`
  `room_dw_mansion_dining3, room_dw_mansion_dininghall,`
  `room_dw_mansion_east_1f_a, room_dw_mansion_east_1f_b,`
  `room_dw_mansion_east_1f_c, room_dw_mansion_east_1f_d,`
  `room_dw_mansion_east_1f_e, room_dw_mansion_east_1f_secret,`
  `room_dw_mansion_east_2f_a, room_dw_mansion_east_2f_c,`
  `room_dw_mansion_east_2f_c_a, room_dw_mansion_east_2f_c_b,`
  `room_dw_mansion_east_2f_d, room_dw_mansion_east_2f_d_backup,`
  `room_dw_mansion_east_2f_shortcut, room_dw_mansion_east_2f_teacup,`
  `room_dw_mansion_east_2f_transformed_new,`
  `room_dw_mansion_east_2f_ufo_old, room_dw_mansion_east_3f,`
  `room_dw_mansion_east_3f_projection, room_dw_mansion_east_3f_toilet,`
  `room_dw_mansion_east_4f_a, room_dw_mansion_east_4f_b,`
  `room_dw_mansion_east_4f_c, room_dw_mansion_east_4f_d,`
  `room_dw_mansion_east_4f_e, room_dw_mansion_east_teacup,`
  `room_dw_mansion_east_teacup_2, room_dw_mansion_east_teacup_3,`
  `room_dw_mansion_east_teacup_4, room_dw_mansion_east_teacup_4_old,`
  `room_dw_mansion_elevator, room_dw_mansion_entrance,`
  `room_dw_mansion_ferris_wheel, room_dw_mansion_ferris_wheel_post,`
  `room_dw_mansion_fire_paintings, room_dw_mansion_fountain,`
  `room_dw_mansion_hands, room_dw_mansion_kitchen,`
  `room_dw_mansion_krisroom, room_dw_mansion_lightner_hallway,`
  `room_dw_mansion_mouseLottery, room_dw_mansion_noelle_room,`
  `room_dw_mansion_potBalance, room_dw_mansion_prefountain,`
  `room_dw_mansion_single_pot, room_dw_mansion_sparks,`
  `room_dw_mansion_susieroom, room_dw_mansion_tasquePaintings,`
  `room_dw_mansion_top, room_dw_mansion_top_post,`
  `room_dw_mansion_top_post_old, room_dw_mansion_traffic,`
  `room_dw_mansion_traffic_original, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_front,`
  `room_GMS2_test, room_shaun_puzzle, room_teacup_demoauto,`
  `room_teacup_demobullets`

### Party record 0929

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3 || global.char[1] == 3)                 {`
  `global.interact = 1`
- condition: `line 143; if (throwitem == 4) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_castle_town,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_DARKempty, room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_castle_area_1,`
  `room_dw_castle_area_2, room_dw_castle_area_2_transformed,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_hallway, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_lancer, room_dw_castle_rooms_susie,`
  `room_dw_castle_west_cliff, room_dw_castle_west_cliff_old,`
  `room_dw_city_baseball, room_dw_city_berdly, room_dw_city_big_1,`
  `room_dw_city_big_1_original, room_dw_city_big_2,`
  `room_dw_city_big_2_OG, room_dw_city_big_3,`
  `room_dw_city_big_3_backup_2exits, room_dw_city_big_3_og,`
  `room_dw_city_carnival, room_dw_city_cheese, room_dw_city_cheesemaze,`
  `room_dw_city_dog_traffic, room_dw_city_entrance, room_dw_city_hacker,`
  `room_dw_city_intro, room_dw_city_man, room_dw_city_mansion_front,`
  `room_dw_city_mice, room_dw_city_mice2, room_dw_city_mice2_og,`
  `room_dw_city_mice3, room_dw_city_mirrorfriend,`
  `room_dw_city_monologue, room_dw_city_monologue_old,`
  `room_dw_city_moss, room_dw_city_noelle_fight_intro,`
  `room_dw_city_poppup, room_dw_city_postbaseball_1,`
  `room_dw_city_postbaseball_2, room_dw_city_postbaseball_3,`
  `room_dw_city_prototype_01, room_dw_city_prototype_02,`
  `room_dw_city_queen_drunk, room_dw_city_roadblock,`
  `room_dw_city_savepoint, room_dw_city_sidewayscars,`
  `room_dw_city_spamton_alley, room_dw_city_spamton_house,`
  `room_dw_city_spamton_shop_exterior,`
  `room_dw_city_spamton_shop_interior, room_dw_city_split,`
  `room_dw_city_susie_ralsei_fun_1, room_dw_city_traffic_1,`
  `room_dw_city_traffic_2, room_dw_city_traffic_2_old,`
  `room_dw_city_traffic_3, room_dw_city_traffic_3_2Entrances,`
  `room_dw_city_traffic_3_backup, room_dw_city_traffic_4,`
  `room_dw_city_traffic_5_old, room_dw_city_treasure,`
  `room_dw_cyber_battle_maze_1, room_dw_cyber_battle_maze_1_Original,`
  `room_dw_cyber_battle_maze_2, room_dw_cyber_battle_maze_2_old,`
  `room_dw_cyber_battle_maze_2_toby, room_dw_cyber_battle_maze_3,`
  `room_dw_cyber_escalator_slide, room_dw_cyber_intro_1,`
  `room_dw_cyber_intro_2, room_dw_cyber_intro_connector,`
  `room_dw_cyber_keyboard_puzzle_1, room_dw_cyber_keyboard_puzzle_1_old,`
  `room_dw_cyber_keyboard_puzzle_2, room_dw_cyber_keyboard_puzzle_3,`
  `room_dw_cyber_keyboardexample, room_dw_cyber_maze_fireworks,`
  `room_dw_cyber_maze_queenscreen, room_dw_cyber_maze_rhythm,`
  `room_dw_cyber_maze_tasque, room_dw_cyber_maze_virokun,`
  `room_dw_cyber_maze_virokun_backuo, room_dw_cyber_music_bullet,`
  `room_dw_cyber_music_bullet_original, room_dw_cyber_music_fight,`
  `room_dw_cyber_music_final, room_dw_cyber_musical_door,`
  `room_dw_cyber_musical_shop, room_dw_cyber_nuberts_treasure,`
  `room_dw_cyber_post_music_boss_slide, room_dw_cyber_queen_boxing,`
  `room_dw_cyber_rhythm_slide, room_dw_cyber_rollercoaster,`
  `room_dw_cyber_savepoint, room_dw_cyber_savepoint_original,`
  `room_dw_cyber_shaunsmusicalbullettunnel, room_dw_cyber_tasque_battle,`
  `room_dw_cyber_tasque_battle_og, room_dw_cyber_teacup_1,`
  `room_dw_cyber_teacup_2, room_dw_cyber_teacup_final,`
  `room_dw_cyber_viro_ring, room_dw_cyber_viromaze2,`
  `room_dw_cyber_virovirokun_fight, room_dw_mansion_acid_tunnel,`
  `room_dw_mansion_acid_tunnel_exit,`
  `room_dw_mansion_acid_tunnel_loop_rouxls,`
  `room_dw_mansion_acid_tunnel_old,`
  `room_dw_mansion_acid_tunnel_puzzle_entrance,`
  `room_dw_mansion_b_central, room_dw_mansion_b_east,`
  `room_dw_mansion_b_east_a, room_dw_mansion_b_east_b,`
  `room_dw_mansion_b_east_transformed, room_dw_mansion_b_entrance,`
  `room_dw_mansion_b_stairs, room_dw_mansion_b_west_1f,`
  `room_dw_mansion_b_west_1f_a, room_dw_mansion_b_west_1f_b,`
  `room_dw_mansion_b_west_2f, room_dw_mansion_bridges,`
  `room_dw_mansion_bridges_funny, room_dw_mansion_bridgesold,`
  `room_dw_mansion_darkbulb_1, room_dw_mansion_darkbulb_2,`
  `room_dw_mansion_darkbulb_3, room_dw_mansion_dining_a,`
  `room_dw_mansion_dining_storage, room_dw_mansion_dining_storage_old,`
  `room_dw_mansion_dining3, room_dw_mansion_dininghall,`
  `room_dw_mansion_east_1f_a, room_dw_mansion_east_1f_b,`
  `room_dw_mansion_east_1f_c, room_dw_mansion_east_1f_d,`
  `room_dw_mansion_east_1f_e, room_dw_mansion_east_1f_secret,`
  `room_dw_mansion_east_2f_a, room_dw_mansion_east_2f_c,`
  `room_dw_mansion_east_2f_c_a, room_dw_mansion_east_2f_c_b,`
  `room_dw_mansion_east_2f_d, room_dw_mansion_east_2f_d_backup,`
  `room_dw_mansion_east_2f_shortcut, room_dw_mansion_east_2f_teacup,`
  `room_dw_mansion_east_2f_transformed_new,`
  `room_dw_mansion_east_2f_ufo_old, room_dw_mansion_east_3f,`
  `room_dw_mansion_east_3f_projection, room_dw_mansion_east_3f_toilet,`
  `room_dw_mansion_east_4f_a, room_dw_mansion_east_4f_b,`
  `room_dw_mansion_east_4f_c, room_dw_mansion_east_4f_d,`
  `room_dw_mansion_east_4f_e, room_dw_mansion_east_teacup,`
  `room_dw_mansion_east_teacup_2, room_dw_mansion_east_teacup_3,`
  `room_dw_mansion_east_teacup_4, room_dw_mansion_east_teacup_4_old,`
  `room_dw_mansion_elevator, room_dw_mansion_entrance,`
  `room_dw_mansion_ferris_wheel, room_dw_mansion_ferris_wheel_post,`
  `room_dw_mansion_fire_paintings, room_dw_mansion_fountain,`
  `room_dw_mansion_hands, room_dw_mansion_kitchen,`
  `room_dw_mansion_krisroom, room_dw_mansion_lightner_hallway,`
  `room_dw_mansion_mouseLottery, room_dw_mansion_noelle_room,`
  `room_dw_mansion_potBalance, room_dw_mansion_prefountain,`
  `room_dw_mansion_single_pot, room_dw_mansion_sparks,`
  `room_dw_mansion_susieroom, room_dw_mansion_tasquePaintings,`
  `room_dw_mansion_top, room_dw_mansion_top_post,`
  `room_dw_mansion_top_post_old, room_dw_mansion_traffic,`
  `room_dw_mansion_traffic_original, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_front,`
  `room_GMS2_test, room_shaun_puzzle, room_teacup_demoauto,`
  `room_teacup_demobullets`

### Party record 0930

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         myx[i] += 15`
- condition: `line 23; if (i_ex(global.charinstance[i])) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0931

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         myx[i] += 15`
- condition: `line 27; if (global.char[i] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0932

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 6; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_postbaseball_1, room_dw_city_postbaseball_2,`
  `room_dw_city_postbaseball_3`

### Party record 0933

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 8; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_postbaseball_1, room_dw_city_postbaseball_2,`
  `room_dw_city_postbaseball_3`

### Party record 0934

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 9; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_postbaseball_1, room_dw_city_postbaseball_2,`
  `room_dw_city_postbaseball_3`

### Party record 0935

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 || global.char[1] == 2 || global.char[2] == 2)     {`
  `sus = 0`
- condition: `line 245; if (global.charauto[2] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0936

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)         {             sus = 1`
- condition: `line 248; if (global.char[0] == 2 || global.char[1] == 2 ||`
  `global.char[2] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0937

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)         {             sus = 2`
- condition: `line 252; if (global.char[1] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0938

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 199; if (global.char[i] != 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0939

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 208; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0940

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 217; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0941

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 226; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0942

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             if`
  `(global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoor...`
  `== 2 ||`
  `global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoord...`
  `== 4)             {                 if (havechar[1] == 0 ||`
  `global.hp[2] <= 0)                 {`
  `canpress = 0`
- condition: `line 765; if (cango == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0943

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)                     {                         for (i = 0`
- condition: `line 998; if (global.bmenuno == 11) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0944

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         for (i = 0`
- condition: `line 1011; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0945

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         for (i = 0`
- condition: `line 1024; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0946

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         for (i = 0`
- condition: `line 1037; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0947

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         __actname =`
  `global.actnamesus[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 194; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0948

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         __actname =`
  `global.actnameral[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 198; if (global.char[global.charturn] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0949

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         __actname =`
  `global.actnamenoe[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 202; if (global.char[global.charturn] == 3) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0950

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[thisenemy][__acti]`
- condition: `line 454; if (global.bmenuno == 9 && global.myfight == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0951

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[thisenemy][__acti]`
- condition: `line 462; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0952

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[thisenemy][__acti]`
- condition: `line 470; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0953

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[thisenemy][__acti]`
- condition: `line 478; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0954

- chapter: `2`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             chartime =`
  `global.actactor[global.bmenucoord[11][global.charturn]][i]`
- condition: `line 508; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0955

- chapter: `2`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0956

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `2`
- condition: `line 5; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0957

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0958

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 928; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0959

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 929; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0960

- chapter: `2`
- phase: `global.char[dx]`
- field: `global.char[dx]`
- expression: `= 2)                 {                     if`
  `(global.charcond[dx] != 5)                     {`
  `global.charcond[dx] = 5`
- condition: `line 245; if (scr_monsterpop() > 1 && scr_havechar(2)) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0961

- chapter: `2`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 3)                     {                         acttriggered`
  `= 1`
- condition: `line 440; if ((global.actingtarget[__i] == myself &&`
  `global.char[__i] > 0 && global.charspecial[__i] == 0) ||`
  `(global.chartarget[__i] == myself && (global.charspecial[__i] ==`
  `100 || global.charspecial[__i] == 3))) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0962

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 835; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0963

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)             {                 continue`
- condition: `line 154; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0964

- chapter: `2`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)                 {                     continue`
- condition: `line 1014; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0965

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0)                 {                     _cherub.healer = true`
- condition: `line 1032; else if (i == 2) > if (i == 0 &&`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0966

- chapter: `2`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 0)                     {`
  `_cherub.healer = true`
- condition: `line 1041; if (i == 2 ||`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 0967

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 30; if (global.fighting == 0) > if`
  `(keyboard_check_pressed(ord("6")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0968

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 31; if (global.fighting == 0) > if`
  `(keyboard_check_pressed(ord("6")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0969

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 32; if (global.fighting == 0) > if`
  `(keyboard_check_pressed(ord("6")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0970

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 36; if (keyboard_check_pressed(ord("7")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0971

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 40; if (keyboard_check_pressed(ord("7"))) > if`
  `(keyboard_check_pressed(ord("8")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0972

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 41; if (keyboard_check_pressed(ord("7"))) > if`
  `(keyboard_check_pressed(ord("8")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0973

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 45; if (keyboard_check_pressed(ord("8"))) > if`
  `(keyboard_check_pressed(ord("9")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0974

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 46; if (keyboard_check_pressed(ord("9")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 0975

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 470; if (global.plot < 7)`
- status: `production`
- rooms: `room_schooldoor, room_schoollobby, room_town_krisyard`

### Party record 0976

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 471; if (global.plot < 7)`
- status: `production`
- rooms: `room_schooldoor, room_schoollobby, room_town_krisyard`

### Party record 0977

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 7; ﻿if (con == 0 && global.plot == 7)`
- status: `production`
- rooms: `room_castle_town, room_dw_castle_area_2`

### Party record 0978

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 171; unconditional in entry`
- status: `production`
- rooms: `room_castle_town, room_dw_castle_area_2`

### Party record 0979

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 420; if (con == 5) > if`
  `(!instance_exists(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Party record 0980

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 424; if (!instance_exists(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Party record 0981

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 449; if (con == 51)`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Party record 0982

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 454; if (con == 51) > if`
  `(instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Party record 0983

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 455; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Party record 0984

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 147; if (con == 2 && !instance_exists(obj_cutscene_master))`
- status: `production`
- rooms: `room_library`

### Party record 0985

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 148; if (con == 2 && !instance_exists(obj_cutscene_master))`
- status: `production`
- rooms: `room_library`

### Party record 0986

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 588; unconditional in entry`
- status: `production`
- rooms: `room_dw_cyber_intro_2`

### Party record 0987

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 589; unconditional in entry`
- status: `production`
- rooms: `room_dw_cyber_intro_2`

### Party record 0988

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 590; unconditional in entry`
- status: `production`
- rooms: `room_dw_cyber_intro_2`

### Party record 0989

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 69; if (global.plot == 16 && global.chapter == 2)`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 0990

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 38; else if (global.plot == 65)`
- status: `production`
- rooms: `room_dw_city_intro`

### Party record 0991

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 43; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_intro`

### Party record 0992

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 44; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_intro`

### Party record 0993

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 18; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_split`

### Party record 0994

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 106; if (con == 50 && !i_ex(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_city_split`

### Party record 0995

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 17; if (global.chapter != 2 || global.plot >= 100)`
- status: `production`
- rooms: `room_dw_mansion_krisroom`

### Party record 0996

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 36; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_darkbulb_1`

### Party record 0997

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 21; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_dining_a`

### Party record 0998

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 13; if (obj_mainchara.x > x && con == -1)`
- status: `production`
- rooms: `room_dw_mansion_dining_a`

### Party record 0999

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 14; if (obj_mainchara.x > x && con == -1)`
- status: `production`
- rooms: `room_dw_mansion_dining_a`

### Party record 1000

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 15; if (obj_mainchara.x > x && con == -1)`
- status: `production`
- rooms: `room_dw_mansion_dining_a`

### Party record 1001

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 32; if (global.chapter != 2 || global.flag[319] > 0)`
- status: `production`
- rooms: `room_dw_mansion_noelle_room`

### Party record 1002

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 17; if (global.flag[343] == 0) > if (global.plot < 140)`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_puzzle_entrance`

### Party record 1003

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 19; if (global.flag[343] == 0) > if (global.plot < 140)`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_puzzle_entrance`

### Party record 1004

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 18; if (!snd_is_playing(global.currentsong[1]))`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_loop_rouxls`

### Party record 1005

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 23; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_loop_rouxls`

### Party record 1006

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 9; if (global.chapter != 2 || global.flag[319] > 1)`
- status: `production`
- rooms: `room_dw_mansion_ferris_wheel`

### Party record 1007

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 9; if (global.chapter != 2 || global.flag[319] > 2)`
- status: `production`
- rooms: `room_dw_mansion_ferris_wheel_post`

### Party record 1008

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 31; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1009

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 32; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1010

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 34; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1011

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 50; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1012

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 179; if (con == 10 && !d_ex())`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1013

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 187; if (i_ex(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1014

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 188; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_acid_tunnel_exit`

### Party record 1015

- chapter: `2`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 804; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_top`

### Party record 1016

- chapter: `2`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 805; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_top`

### Party record 1017

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1089; if (make_npc_b)`
- status: `production`
- rooms: `room_dw_mansion_top`

### Party record 1018

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 10; if (global.chapter != 2 || global.plot >= 171)`
- status: `legacy`
- rooms: `room_dw_mansion_top_post, room_dw_mansion_top_post_old`

### Party record 1019

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 9; if (global.chapter != 2 || global.plot < 200 ||`
  `global.plot >= 205)`
- status: `production`
- rooms: `room_town_south`

### Party record 1020

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 9; unconditional in entry`
- status: `production`
- rooms: `room_town_south`

### Party record 1021

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 12; if (global.chapter != 2 || global.plot < 205 ||`
  `global.plot >= 210)`
- status: `production`
- rooms: `room_torhouse`

### Party record 1022

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 13; if (global.chapter != 2 || global.plot >= 211 ||`
  `global.plot < 205)`
- status: `production`
- rooms: `room_torbathroom`

### Party record 1023

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 14; if (global.chapter != 2 || global.plot < 211)`
- status: `production`
- rooms: `room_torhouse`

### Party record 1024

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 28; else if (global.flag[358] > 1) > if (!scr_havechar(2))`
- status: `production`
- rooms: `room_dw_mansion_east_1f_secret`

### Party record 1025

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 32; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_mansion_east_1f_secret`

### Party record 1026

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 79; if (con == 5 && !i_ex(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_mansion_east_1f_secret`

### Party record 1027

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 91; if (con == 10)`
- status: `production`
- rooms: `room_dw_mansion_east_1f_secret`

### Party record 1028

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 92; if (con == 10)`
- status: `production`
- rooms: `room_dw_mansion_east_1f_secret`

### Party record 1029

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 41; if (global.tempflag[32] == 1)`
- status: `production`
- rooms: `room_dw_mansion_b_east`

### Party record 1030

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 85; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_b_east`

### Party record 1031

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 86; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_b_east`

### Party record 1032

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 11; if (global.chapter != 2 || global.flag[309] < 8 ||`
  `global.flag[309] >= 9)`
- status: `production`
- rooms: `room_dw_mansion_b_east_a`

### Party record 1033

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 16; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_mansion_b_east_a`

### Party record 1034

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 17; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_mansion_b_east_a`

### Party record 1035

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 7; if (global.chapter != 2 || global.flag[309] < 8 ||`
  `global.flag[324] > 0) > if (global.flag[324] == 0)`
- status: `production`
- rooms: `room_dw_mansion_b_entrance`

### Party record 1036

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 13; if (global.chapter != 2) > else if (global.plot < 70)`
- status: `production`
- rooms: `room_dw_city_hacker`

### Party record 1037

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 6; ﻿if (obj_mainchara.x > x && con == -1)`
- status: `production`
- rooms: `room_dw_city_hacker`

### Party record 1038

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 7; ﻿if (obj_mainchara.x > x && con == -1)`
- status: `production`
- rooms: `room_dw_city_hacker`

### Party record 1039

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 9; if (global.chapter != 2 || global.plot >= 83)`
- status: `legacy`
- rooms: `room_dw_city_traffic_5_old`

### Party record 1040

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 37; else if (global.plot >= 95) > if (global.plot < 99)`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1041

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 42; if (global.plot < 99) > if`
  `(instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1042

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 43; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1043

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 44; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1044

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 8; ﻿if (obj_mainchara.x > (x - 60) && con == -1)`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1045

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 10; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1046

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 11; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_baseball`

### Party record 1047

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 19; if (global.chapter != 2 || global.plot >= 99) > else if`
  `(weird == false)`
- status: `production`
- rooms: `room_dw_city_mansion_front`

### Party record 1048

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 21; else if (weird == false)`
- status: `production`
- rooms: `room_dw_city_mansion_front`

### Party record 1049

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 22; else if (weird == false)`
- status: `production`
- rooms: `room_dw_city_mansion_front`

### Party record 1050

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 23; else if (weird == false)`
- status: `production`
- rooms: `room_dw_city_mansion_front`

### Party record 1051

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `1`
- condition: `line 367; if (con == 0) > if (obj_mainchara.x < 1200)`
- status: `production`
- rooms: `room_dw_city_mansion_front`

### Party record 1052

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 368; if (con == 0) > if (obj_mainchara.x < 1200)`
- status: `production`
- rooms: `room_dw_city_mansion_front`

### Party record 1053

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 387; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_berdly`

### Party record 1054

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 71; unconditional in entry`
- status: `production`
- rooms: `room_dw_city_traffic_4`

### Party record 1055

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 76; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_traffic_4`

### Party record 1056

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 5; ﻿if (obj_mainchara.x > x && con == -1)`
- status: `production`
- rooms: `room_dw_city_traffic_4`

### Party record 1057

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 33; if (global.chapter != 2 || global.plot < 85 ||`
  `global.plot >= 90)`
- status: `production`
- rooms: `room_dw_city_traffic_4`

### Party record 1058

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 8; ﻿if (global.plot >= 85 && global.plot < 90) > if (con ==`
  `0)`
- status: `production`
- rooms: `room_dw_city_traffic_4`

### Party record 1059

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 28; if (global.flag[7] == 1) > if (!scr_havechar(4))`
- status: `production`
- rooms: `room_dw_city_monologue`

### Party record 1060

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 33; if (!scr_havechar(4)) > if`
  `(instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_city_monologue`

### Party record 1061

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 7; ﻿if (scr_havechar(2) && obj_mainchara.x < x && con == -1`
  `&& global.flag[336] == 0)`
- status: `production`
- rooms: `room_town_south`

### Party record 1062

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 40; if (obj_mainchara.x > x && global.flag[336] == 1 &&`
  `!scr_havechar(2))`
- status: `production`
- rooms: `room_town_south`

### Party record 1063

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 41; if (obj_mainchara.x > x && global.flag[336] == 1 &&`
  `!scr_havechar(2))`
- status: `production`
- rooms: `room_town_south`

### Party record 1064

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 50; if (obj_mainchara.x < x && global.flag[336] == 1 &&`
  `scr_havechar(2))`
- status: `production`
- rooms: `room_town_south`

### Party record 1065

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 12; if (global.chapter != 2 || global.flag[316] == 1)`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1066

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 17; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1067

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 18; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1068

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 26; if (global.chapter != 2 || global.plot >= 15)`
- status: `production`
- rooms: `room_dw_castle_rooms_susie`

### Party record 1069

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 31; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_castle_rooms_susie`

### Party record 1070

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 32; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_castle_rooms_susie`

### Party record 1071

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 9; if (global.flag[915] == 7 && global.flag[916] == 0)`
- status: `production`
- rooms: `room_dw_mansion_entrance`

### Party record 1072

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 10; if (global.flag[915] == 7 && global.flag[916] == 0)`
- status: `production`
- rooms: `room_dw_mansion_entrance`

### Party record 1073

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 11; if (global.flag[915] == 7 && global.flag[916] == 0)`
- status: `production`
- rooms: `room_dw_mansion_entrance`

### Party record 1074

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 12; unconditional in entry`
- status: `production`
- rooms: `room_dw_mansion_east_3f`

### Party record 1075

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 137; if (con == 50 && !d_ex() && customcon == 1)`
- status: `production`
- rooms: `room_dw_mansion_east_3f`

### Party record 1076

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 4; if (global.plot < 50)`
- status: `production`
- rooms: `room_dw_cyber_intro_1`

### Party record 1077

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 9; if (global.plot < 50) > if`
  `(instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_cyber_intro_1`

### Party record 1078

- chapter: `2`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 5; if (global.plot >= 200 && global.flag[387] == 0)`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 1079

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 10; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 1080

- chapter: `2`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 188; if (con == 4 && !i_ex(obj_cutscene_master)) > if`
  `(!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 1081

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `arg0, arg1, arg2`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1082

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 10; if (!i_ex(kris))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1083

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 14; if (arg0 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1084

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 29; if (arg1 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1085

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 44; if (arg2 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1086

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 21; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1087

- chapter: `3`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 if (global.cinstance[i].x !=`
  `s.x || global.cinstance[i].y != s.x)                 {`
  `global.cinstance[i].x = s.x`
- condition: `line 7; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1088

- chapter: `3`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 if (global.cinstance[i].x !=`
  `r.x || global.cinstance[i].y != r.x)                 {`
  `global.cinstance[i].x = r.x`
- condition: `line 44; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1089

- chapter: `3`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 s =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 9; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1090

- chapter: `3`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 r =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1091

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `arg0`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1092

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 0)     {         global.char[0] = characterToGet`
- condition: `line 24; case "noelle": > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1093

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && getchar == 0)     {         global.char[1] =`
  `characterToGet`
- condition: `line 29; if (global.char[0] == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1094

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0 && getchar == 0)     {         global.char[2] =`
  `characterToGet`
- condition: `line 34; if (global.char[1] == 0 && getchar == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1095

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 53; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1096

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 58; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1097

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 63; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1098

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 68; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1099

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1100

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1101

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1102

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 19; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1103

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 24; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1104

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 29; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1105

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 34; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1106

- chapter: `3`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         charcan = 0`
- condition: `line 12; if (global.acting[arg0] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1107

- chapter: `3`
- phase: `global.char[caster]`
- field: `global.char[caster]`
- expression: `= 4)         {             dm.type = 6`
- condition: `line 7; if (caster < 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1108

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2)     {         sus = 0`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1109

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)     {         sus = 1`
- condition: `line 7; if (global.char[0] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1110

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)     {         sus = 2`
- condition: `line 11; if (global.char[1] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1111

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 && global.charauto[2] == 1)             {`
  `global.acting[0] = 1`
- condition: `line 134; if (skip == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1112

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             with (obj_monsterparent)`
  `{                 actingnoe = 0`
- condition: `line 28; if (moveswapped == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1113

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             with (obj_monsterparent)`
  `{                 actingral = 0`
- condition: `line 35; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1114

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             with (obj_monsterparent)`
  `{                 actingsus = 0`
- condition: `line 42; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1115

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         global.heromakey[0] =`
  `yy + 140`
- condition: `line 16; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1116

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         global.heromakey[0] = yy + 100`
- condition: `line 20; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1117

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(20)`
- condition: `line 377; case 212: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1118

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(80)`
- condition: `line 381; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1119

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(50)`
- condition: `line 385; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1120

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {                 scr_healitemspell(30)`
- condition: `line 389; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1121

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(80)`
- condition: `line 396; case 213: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1122

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(20)`
- condition: `line 400; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1123

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(50)`
- condition: `line 404; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1124

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {                 scr_healitemspell(70)`
- condition: `line 408; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1125

- chapter: `3`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1) ? 100 : 90`
- condition: `line 461; case 225: > case 226:`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1126

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)         {             suspos = i`
- condition: `line 15; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1127

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)         {             ralpos = i`
- condition: `line 19; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1128

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)         {             noepos = i`
- condition: `line 23; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1129

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cooked to`
  `perfection!", "scr_itemuse_slash_scr_itemuse_gml_123_0"))`
- condition: `line 151; case 8: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1130

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("A bit`
  `burnt...?", "scr_itemuse_slash_scr_itemuse_gml_127_0"))`
- condition: `line 155; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1131

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 159; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1132

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Mmm... face",`
  `"scr_itemuse_slash_scr_itemuse_gml_143_0"))`
- condition: `line 169; case 9: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1133

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `stringsetloc("(uncomfortable)",`
  `"scr_itemuse_slash_scr_itemuse_gml_147_0"))`
- condition: `line 173; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1134

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Umm, what is`
  `this? It's cute...", "scr_itemuse_slash_scr_itemuse_gml_151_0"))`
- condition: `line 177; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1135

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Why this!?",`
  `"scr_itemuse_slash_scr_itemuse_gml_161_0"))`
- condition: `line 185; case 10: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1136

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Let's be`
  `healthy!", "scr_itemuse_slash_scr_itemuse_gml_165_0"))`
- condition: `line 189; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1137

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Something to`
  `graze on!", "scr_itemuse_slash_scr_itemuse_gml_169_0"))`
- condition: `line 193; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1138

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 218; case 12: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1139

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 222; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1140

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 227; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1141

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_healitem(global.charselect, 30)`
- condition: `line 232; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1142

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 240; case 13: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1143

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 244; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1144

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 249; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1145

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_healitem(0, 35)`
- condition: `line 254; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1146

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(It's SO`
  `good!)", "scr_itemuse_slash_scr_itemuse_gml_239_0"))`
- condition: `line 264; case 14: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1147

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("K-Kris!? I...",`
  `"scr_itemuse_slash_scr_itemuse_gml_243_0"))`
- condition: `line 268; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1148

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Huh? I didn't`
  `know Kris liked this flavor.)",`
  `"scr_itemuse_slash_scr_itemuse_gml_247_0"))`
- condition: `line 272; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1149

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cool, it's`
  `wriggling.", "scr_itemuse_slash_scr_itemuse_gml_257_0"))`
- condition: `line 280; case 15: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1150

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Yum, is this`
  `spaghetti?", "scr_itemuse_slash_scr_itemuse_gml_261_0"))`
- condition: `line 284; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1151

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Tastes like...`
  `jumprope?", "scr_itemuse_slash_scr_itemuse_gml_265_0"))`
- condition: `line 288; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1152

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 325; case 18: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1153

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 329; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1154

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 333; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1155

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 342; case 19: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1156

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 346; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1157

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 350; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1158

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 359; case 20: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1159

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 363; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1160

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 367; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1161

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 376; case 21: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1162

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 380; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1163

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 384; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1164

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("C'mon, gimme`
  `the rest!", "scr_itemuse_slash_scr_itemuse_gml_418_0"))`
- condition: `line 394; case 22: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1165

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("M-maybe give`
  `Susie the rest?", "scr_itemuse_slash_scr_itemuse_gml_422_0"))`
- condition: `line 398; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1166

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 402; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1167

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hey, this`
  `rules!", "scr_itemuse_slash_scr_itemuse_gml_438_0"))`
- condition: `line 412; case 23: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1168

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Nice and`
  `chalky.", "scr_itemuse_slash_scr_itemuse_gml_442_0"))`
- condition: `line 416; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1169

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I-isn't this`
  `the chalk I gave her?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_446_0"))`
- condition: `line 420; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1170

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell'd you call`
  `this!?", "scr_itemuse_slash_scr_itemuse_gml_456_0"))`
- condition: `line 428; case 24: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1171

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I made this.",`
  `"scr_itemuse_slash_scr_itemuse_gml_460_0"))`
- condition: `line 432; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1172

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("B-Brainfreeze!`
  `... kidding!", "scr_itemuse_slash_scr_itemuse_gml_464_0"))`
- condition: `line 436; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1173

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 heal_amount = 100`
- condition: `line 460; case 26: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1174

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says GUTS!",`
  `"scr_itemuse_slash_scr_itemuse_gml_487_0"))`
- condition: `line 464; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1175

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says`
  `Fluffy...", "scr_itemuse_slash_scr_itemuse_gml_491_0"))`
- condition: `line 468; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1176

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I... I can't`
  `read these symbols...",`
  `"scr_itemuse_slash_scr_itemuse_gml_495_0"))`
- condition: `line 472; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1177

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ugh! ...tastes`
  `good?", "scr_itemuse_slash_scr_itemuse_gml_553_0"))`
- condition: `line 538; if (global.char[global.charselect] != 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1178

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ow... er,`
  `thanks, Kris!", "scr_itemuse_slash_scr_itemuse_gml_557_0"))`
- condition: `line 542; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1179

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I'll... just`
  `pretend to drink it...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_561_0"))`
- condition: `line 546; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1180

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (global.filechoice == 1 &&`
  `scr_havechar("noelle"))                 {`
  `scr_itemcomment(noepos, stringsetloc("What are you, a unicorn?`
  `Faha.", "scr_itemuse_slash_scr_itemuse_gml_580_0"))`
- condition: `line 559; case 34: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1181

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {                     item_comment =`
  `stringsetloc("Butterscotch, nice!",`
  `"scr_itemuse_slash_scr_itemuse_gml_588_0")`
- condition: `line 569; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1182

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {                     item_comment =`
  `stringsetloc("Wow, what a nice flavor!",`
  `"scr_itemuse_slash_scr_itemuse_gml_600_0")`
- condition: `line 581; else if (global.filechoice == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1183

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {                     item_comment =`
  `stringsetloc("Mmm, butterscotch!",`
  `"scr_itemuse_slash_scr_itemuse_gml_612_0")`
- condition: `line 593; else if (global.filechoice == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1184

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 usable = 1`
- condition: `line 610; case 35: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1185

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell no.",`
  `"scr_itemuse_slash_scr_itemuse_gml_654_0"))`
- condition: `line 630; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1186

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Is... that, um,`
  `nutritious?", "scr_itemuse_slash_scr_itemuse_gml_658_0"))`
- condition: `line 634; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1187

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("C... Can we`
  `keep it?", "scr_itemuse_slash_scr_itemuse_gml_662_0"))`
- condition: `line 638; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1188

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Fine, I'll`
  `finish it.", "scr_itemuse_slash_scr_itemuse_gml_674_0"))`
- condition: `line 647; case 36: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1189

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Aw, you saved`
  `me half?", "scr_itemuse_slash_scr_itemuse_gml_678_0"))`
- condition: `line 651; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1190

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Whatever, it's`
  `just Kris's...)", "scr_itemuse_slash_scr_itemuse_gml_682_0"))`
- condition: `line 655; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1191

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Like my old`
  `school.", "scr_itemuse_slash_scr_itemuse_gml_693_0"))`
- condition: `line 663; case 37: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1192

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Is this`
  `legal?", "scr_itemuse_slash_scr_itemuse_gml_697_0"))`
- condition: `line 667; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1193

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Here, I`
  `refreezed it!", "scr_itemuse_slash_scr_itemuse_gml_701_0"))`
- condition: `line 671; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1194

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Look, I'm a`
  `roach.", "scr_itemuse_slash_scr_itemuse_gml_722_0"))`
- condition: `line 695; case 39: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1195

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'm a comfy`
  `caterpillar!", "scr_itemuse_slash_scr_itemuse_gml_726_0"))`
- condition: `line 699; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1196

- chapter: `3`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'm, um, an`
  `alien?", "scr_itemuse_slash_scr_itemuse_gml_730_0"))`
- condition: `line 703; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1197

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1198

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1199

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1200

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1201

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1202

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1203

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)                     {                         facetype =`
  `spr_headkris`
- condition: `line 34; if (itemtype[menuc[1]] == "weapon" || itemtype[menuc[1]]`
  `== "armor") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1204

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         facetype =`
  `spr_headsusie`
- condition: `line 38; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1205

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         facetype =`
  `spr_headralsei`
- condition: `line 42; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1206

- chapter: `3`
- phase: `global.char[__findchar]`
- field: `global.char[__findchar]`
- expression: `= arg0)         {             __charslot = __findchar`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1207

- chapter: `3`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 2)                 {                     with (__minstance)`
  `{                         actconsus = 1`
- condition: `line 25; if (global.actingsingle[global.currentactingchar] == 1)`
  `> if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1208

- chapter: `3`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 3)                 {                     with (__minstance)`
  `{                         actconral = 1`
- condition: `line 37; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1209

- chapter: `3`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 4)                 {                     with (__minstance)`
  `{                         actconnoe = 1`
- condition: `line 49; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1210

- chapter: `3`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 1 &&`
  `global.actsimul[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderkri = __simulcount`
- condition: `line 9; if (global.actingsingle[__ii] == 1 &&`
  `instance_exists(obj_monsterparent)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1211

- chapter: `3`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 2 &&`
  `global.actsimulsus[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordersus = __simulcount`
- condition: `line 18; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1212

- chapter: `3`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 3 &&`
  `global.actsimulral[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderral = __simulcount`
- condition: `line 27; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1213

- chapter: `3`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 4 &&`
  `global.actsimulnoe[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordernoe = __simulcount`
- condition: `line 36; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1214

- chapter: `3`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 1)             {                 if (global.canact[0][__fj] ==`
  `1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1215

- chapter: `3`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 2)             {                 if (global.canactsus[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 33; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1216

- chapter: `3`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 3)             {                 if (global.canactral[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 57; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1217

- chapter: `3`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 4)             {                 if (global.canactnoe[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 81; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1218

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             global.monsterinstance[arg0].acting =`
  `arg1 + 1`
- condition: `line 5; if (i_ex(global.monsterinstance[arg0])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1219

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {`
  `global.monsterinstance[arg0].actingsus = arg1 + 1`
- condition: `line 9; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1220

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {`
  `global.monsterinstance[arg0].actingral = arg1 + 1`
- condition: `line 13; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1221

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {`
  `global.monsterinstance[arg0].actingnoe = arg1 + 1`
- condition: `line 17; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1222

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)     {         global.actingsimul[0] = actsimul[arg1]`
- condition: `line 22; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1223

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[arg0][__acti]`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1224

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[arg0][__acti]`
- condition: `line 12; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1225

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[arg0][__acti]`
- condition: `line 18; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1226

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[arg0][__acti]`
- condition: `line 24; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1227

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1228

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1229

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1230

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 17; if (checker == "noelle" || checker == "no" || checker ==`
  `"n") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1231

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 21; if (global.char[0] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1232

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 25; if (global.char[1] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1233

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1234

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1235

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1236

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 12; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1237

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 12; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1238

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1239

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 5; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1240

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1241

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 5; ﻿if (scr_debug()) > if (!(scr_havechar(2) &&`
  `scr_havechar(3)))`
- status: `debug`
- rooms: `room_adventureboardtest, room_board_1, room_board_2, room_board_3,`
  `room_board_3b, room_board_boattest, room_board_designTest,`
  `room_board_gsa02_b0, room_board_intro, room_board_tests,`
  `room_board1_oldtest, room_boardtest, room_boardtest_old`

### Party record 1242

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 6; ﻿if (scr_debug()) > if (!(scr_havechar(2) &&`
  `scr_havechar(3)))`
- status: `debug`
- rooms: `room_adventureboardtest, room_board_1, room_board_2, room_board_3,`
  `room_board_3b, room_board_boattest, room_board_designTest,`
  `room_board_gsa02_b0, room_board_intro, room_board_tests,`
  `room_board1_oldtest, room_boardtest, room_boardtest_old`

### Party record 1243

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 7; ﻿if (scr_debug()) > if (!(scr_havechar(2) &&`
  `scr_havechar(3)))`
- status: `debug`
- rooms: `room_adventureboardtest, room_board_1, room_board_2, room_board_3,`
  `room_board_3b, room_board_boattest, room_board_designTest,`
  `room_board_gsa02_b0, room_board_intro, room_board_tests,`
  `room_board1_oldtest, room_boardtest, room_boardtest_old`

### Party record 1244

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1585; unconditional in entry`
- status: `production`
- rooms: `room_dw_snow_zone`

### Party record 1245

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_teevie_maze`

### Party record 1246

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 13; if (con == 0 && !i_ex(obj_writer))`
- status: `production`
- rooms: `room_dw_nondescript_hallway`

### Party record 1247

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 10; unconditional in entry`
- status: `production`
- rooms: `room_dw_teevie_bonus_zone`

### Party record 1248

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 12; unconditional in entry`
- status: `production`
- rooms: `room_dw_teevie_shadow_guys`

### Party record 1249

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_teevie_large_01`

### Party record 1250

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 28; unconditional in entry`
- status: `production`
- rooms: `room_dw_nondescript_field`

### Party record 1251

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_ch3_man`

### Party record 1252

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 8; if (global.plot >= 200) > if (global.flag[1057] == 1)`
- status: `production`
- rooms: `room_dw_b3bs_intro`

### Party record 1253

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"susie"`
- condition: `line 304; if (con == 19)`
- status: `production`
- rooms: `room_board_postshadowmantle`

### Party record 1254

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 646; unconditional in entry`
- status: `production`
- rooms: `room_board_postshadowmantle`

### Party record 1255

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 18; if (global.plot < 80)`
- status: `debug`
- rooms: `room_ch3_gameshowroom, room_ch3_gameshowroom_tennatest`

### Party record 1256

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production`
- rooms: `room_dw_inbetween`

### Party record 1257

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_b3bs_zapper_b`

### Party record 1258

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 15; if (global.flag[encounterflag] == 1)`
- status: `production`
- rooms: `room_dw_teevie_ribbicks_a`

### Party record 1259

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 8; if (!scr_havechar(2))`
- status: `production`
- rooms: `room_dw_green_room`

### Party record 1260

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 12; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_green_room`

### Party record 1261

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 448; unconditional in entry`
- status: `production`
- rooms: `room_dw_green_room`

### Party record 1262

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 149; unconditional in entry`
- status: `production`
- rooms: `room_dw_green_room`

### Party record 1263

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 29; if (global.plot < 10)`
- status: `production`
- rooms: `room_dw_couch_overworld_intro`

### Party record 1264

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 15; if (!scr_havechar(2))`
- status: `production`
- rooms: `room_dw_couch_overworld_intro`

### Party record 1265

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 332; if (!scr_havechar(2))`
- status: `production`
- rooms: `room_dw_couch_overworld_intro`

### Party record 1266

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 336; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_couch_overworld_intro`

### Party record 1267

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_teevie_shuttahmaze`

### Party record 1268

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 15; if (global.flag[encounterflag] == 1)`
- status: `production`
- rooms: `room_dw_teevie_ribbicks_b`

### Party record 1269

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 26; if (scr_debug()) > if (!scr_havechar(2) ||`
  `!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_rhythm`

### Party record 1270

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 27; if (scr_debug()) > if (!scr_havechar(2) ||`
  `!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_rhythm`

### Party record 1271

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 28; if (scr_debug()) > if (!scr_havechar(2) ||`
  `!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_rhythm`

### Party record 1272

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 14; if (global.plot < 350)`
- status: `production`
- rooms: `room_town_krisyard_dark`

### Party record 1273

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 14; unconditional in entry`
- status: `production`
- rooms: `room_dw_teevie_cowboy_zone_02_after`

### Party record 1274

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 6; if (global.plot >= 140 && global.plot < 150)`
- status: `debug`
- rooms: `room_ch3_gameshowroom, room_ch3_gameshowroom_tennatest`

### Party record 1275

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `0`
- condition: `line 4; if (scr_debug())`
- status: `debug`
- rooms: `room_adventureboardtest, room_board_1, room_board_1_sword,`
  `room_board_1_sword_trees, room_board_2, room_board_2_sword,`
  `room_board_3, room_board_3_sword, room_board_3b, room_board_boattest,`
  `room_board_designTest, room_board_dungeon_2, room_board_dungeon_3,`
  `room_board_gsa02_b0, room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_extrapuzzle, room_dw_b3bs_idcardpuzzle,`
  `room_dw_b3bs_intro, room_dw_b3bs_lancerget,`
  `room_dw_b3bs_mysterypuzzle, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bstest, room_dw_b3bstest_big, room_dw_puzzlecloset_1,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_teevie_shadow_guys, room_dw_teevie_susiebridge,`
  `room_shadowmantle`

### Party record 1276

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 29; else if (scr_flag_get(1056) == 0)`
- status: `production`
- rooms: `room_board_empty`

### Party record 1277

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 29; if (variable_global_exists("pause_follow")) > if`
  `(global.pause_follow)`
- status: `production`
- rooms: `room_dw_couch_overworld_01, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_intro_left, room_dw_couch_points`

### Party record 1278

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; unconditional in entry`
- status: `production`
- rooms: `room_dw_ranking_z_hallway`

### Party record 1279

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 100; unconditional in entry`
- status: `production`
- rooms: `room_dw_ranking_z_hallway`

### Party record 1280

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_b3bs_mysterypuzzle`

### Party record 1281

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 global.charinstance[i].depth`
  `= 200 - (i * 20)`
- condition: `line 785; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1282

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 global.charinstance[i].depth`
  `= 200 - (i * 20)`
- condition: `line 789; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1283

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 global.charinstance[i].depth`
  `= 200 - (i * 20)`
- condition: `line 793; if (global.char[i] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1284

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 40; unconditional in entry`
- status: `production`
- rooms: `room_dw_couch_overworld_05`

### Party record 1285

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 146; if (room_exists(roomtarg)) > if (roomtarg == 182)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1286

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 150; if (roomtarg == 182)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1287

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 159; if (room == room_dw_b3bs_zapper_c) > if (roomtarg ==`
  `182)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1288

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 163; if (roomtarg == 182)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1289

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 15; unconditional in entry`
- status: `production`
- rooms: `room_dw_tv_cutscene1g`

### Party record 1290

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 59; if (global.plot < 250)`
- status: `production`
- rooms: `room_dw_backstage`

### Party record 1291

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_b3bs_extrapuzzle`

### Party record 1292

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 8; ﻿if (con == 0 && obj_mainchara.x >= 1260 &&`
  `obj_mainchara.y >= 1050 && global.interact == 0)`
- status: `production`
- rooms: `room_dw_couch_overworld_01`

### Party record 1293

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 17; unconditional in entry`
- status: `production`
- rooms: `room_dw_puzzlecloset_1`

### Party record 1294

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 10; if (dostuff) > if (scr_debug())`
- status: `production`
- rooms: `room_dw_b3bs_zapper_c`

### Party record 1295

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 83; if (global.pause_follow) > if (!scr_havechar(2))`
- status: `production`
- rooms: `room_dw_couch_overworld_02`

### Party record 1296

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 87; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_couch_overworld_02`

### Party record 1297

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_puzzlecloset_0, room_dw_puzzlecloset_1,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3`

### Party record 1298

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_teevie_stealth_d`

### Party record 1299

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 35; if (global.flag[1123] == 1)`
- status: `production`
- rooms: `room_dw_puzzlecloset_0`

### Party record 1300

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 13; if (scr_debug())`
- status: `debug`
- rooms: `room_board_1_sword, room_board_1_sword_trees, room_board_2_sword,`
  `room_board_3_sword, room_board_dungeon_2, room_board_dungeon_3,`
  `room_board_postshadowmantle, room_board_postshadowmantle_test,`
  `room_board_prepostshadowmantle, room_board_preshadowmantle,`
  `room_board_preshadowmantle_repeat, room_board_sword_intro,`
  `room_shadowmantle`

### Party record 1301

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 5; if (global.plot >= 170 && global.plot < 180)`
- status: `debug`
- rooms: `room_ch3_gameshowroom, room_ch3_gameshowroom_tennatest`

### Party record 1302

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production`
- rooms: `room_ch3_gacharoom_unknown`

### Party record 1303

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `legacy`
- rooms: `room_dw_b3bs_zapper_a, room_dw_b3bs_zapper_a_old`

### Party record 1304

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_teevie_susiezilla`

### Party record 1305

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 5; if (global.plot >= 110 && global.plot < 120)`
- status: `debug`
- rooms: `room_ch3_gameshowroom, room_ch3_gameshowroom_tennatest`

### Party record 1306

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 7; if (con == 0)`
- status: `production`
- rooms: `room_dw_snow_zone_east_door`

### Party record 1307

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 8; if (con == 0)`
- status: `production`
- rooms: `room_dw_snow_zone_east_door`

### Party record 1308

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 266; if (!scr_havechar(2))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1309

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 270; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1310

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 14; if (ver == 0)`
- status: `production`
- rooms: `room_dw_ranking_hub`

### Party record 1311

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 9; ﻿if (scr_flag_get(1214) > 0)`
- status: `production`
- rooms: `room_dw_puzzlecloset_1a`

### Party record 1312

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 68; else if (scr_flag_get(1056) == 0)`
- status: `production`
- rooms: `room_dw_b3bs_interstitial`

### Party record 1313

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 35; if (global.char[i] != 4) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1314

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 39; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1315

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 c[i].sprite_index =`
  `spr_ralsei_battleintro`
- condition: `line 47; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1316

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 53; if (global.char[i] != 0) > if (`
- status: `debug`
- rooms: `room_adventureboardtest, room_battletest, room_board_1,`
  `room_board_1_sword, room_board_1_sword_trees, room_board_2,`
  `room_board_2_sword, room_board_3, room_board_3_sword, room_board_3b,`
  `room_board_boattest, room_board_designTest, room_board_dungeon_2,`
  `room_board_dungeon_3, room_board_empty, room_board_gsa02_b0,`
  `room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_bullettest,`
  `room_bullettest_new, room_castle_tutorial, room_cc_clover,`
  `room_cc_lancer, room_ch3_gacharoom_unknown, room_ch3_gameshowroom,`
  `room_ch3_gameshowroom_tennatest, room_cutscene_tester,`
  `room_cutscene_tester_b, room_DARKbase_GMS2, room_DARKempty,`
  `room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_cooltrashy, room_dw_b3bs_extrapuzzle,`
  `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_interstitial,`
  `room_dw_b3bs_intro, room_dw_b3bs_jail1, room_dw_b3bs_jail2,`
  `room_dw_b3bs_lancerget, room_dw_b3bs_mysterypuzzle,`
  `room_dw_b3bs_rabbick_a, room_dw_b3bs_rabbick_b,`
  `room_dw_b3bs_rouxls_boss, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bs_sadshadowguys, room_dw_b3bs_shop, room_dw_b3bs_template,`
  `room_dw_b3bs_watercooler, room_dw_b3bs_zapper_a,`
  `room_dw_b3bs_zapper_a_old, room_dw_b3bs_zapper_b,`
  `room_dw_b3bs_zapper_c, room_dw_b3bs_zapper_d, room_dw_b3bstest,`
  `room_dw_b3bstest_big, room_dw_backstage, room_dw_castle_area_1,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_kris, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_west_cliff, room_dw_ch3_man,`
  `room_dw_changing_room, room_dw_channelchange_test, room_dw_chef,`
  `room_dw_chef_empty, room_dw_console_room, room_dw_couch_overworld_01,`
  `room_dw_couch_overworld_02, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_04, room_dw_couch_overworld_05,`
  `room_dw_couch_overworld_intro, room_dw_couch_overworld_intro_left,`
  `room_dw_couch_points, room_dw_green_room, room_dw_inbetween,`
  `room_dw_inbetweenhall, room_dw_puzzlecloset_0,`
  `room_dw_puzzlecloset_1, room_dw_puzzlecloset_1a,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_dw_ralsei_castle_front, room_dw_ranking_a, room_dw_ranking_b,`
  `room_dw_ranking_c, room_dw_ranking_hub, room_dw_ranking_t,`
  `room_dw_ranking_z, room_dw_ranking_z_hallway, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rhythm_empty, room_dw_snow_zone,`
  `room_dw_snow_zone_battle, room_dw_snow_zone_east_door,`
  `room_dw_susiezilla, room_dw_susiezilla_empty,`
  `room_dw_teevie_audiencepits, room_dw_teevie_bonus_zone,`
  `room_dw_teevie_chef, room_dw_teevie_cowboy_zone_01_after,`
  `room_dw_teevie_cowboy_zone_01_intro,`
  `room_dw_teevie_cowboy_zone_02_after,`
  `room_dw_teevie_cowboy_zone_02_intro, room_dw_teevie_cutscene_final,`
  `room_dw_teevie_dust, room_dw_teevie_dust_south,`
  `room_dw_teevie_failure_cage, room_dw_teevie_intro,`
  `room_dw_teevie_large_01, room_dw_teevie_large_02,`
  `room_dw_teevie_lightmaze, room_dw_teevie_maze,`
  `room_dw_teevie_maze_chef, room_dw_teevie_maze_final,`
  `room_dw_teevie_maze_points, room_dw_teevie_maze_quiz,`
  `room_dw_teevie_preview, room_dw_teevie_preview_south,`
  `room_dw_teevie_rhythm, room_dw_teevie_ribbick,`
  `room_dw_teevie_ribbicks_a, room_dw_teevie_ribbicks_b,`
  `room_dw_teevie_sams, room_dw_teevie_shadow_guys,`
  `room_dw_teevie_shuttahmaze, room_dw_teevie_stealth,`
  `room_dw_teevie_stealth_c, room_dw_teevie_stealth_d,`
  `room_dw_teevie_susiebridge, room_dw_teevie_susiezilla,`
  `room_dw_teevie_watercooler, room_dw_tv_closet, room_dw_tv_curtain,`
  `room_dw_tv_cutscene1g, room_genanimtest, room_GMS2_test,`
  `room_overworldBulletEnemyTest, room_perspective_testing,`
  `room_rhythmgame_editor, room_rhythmgame_tenna_test,`
  `room_shadowmantle, room_shootout, room_susiezilla,`
  `room_susiezilla_singleScreenMockup, room_tennaAnimTest,`
  `room_tennaCutsceneTest`

### Party record 1317

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 58; if (global.char[i] == 1) > if (`
- status: `debug`
- rooms: `room_adventureboardtest, room_battletest, room_board_1,`
  `room_board_1_sword, room_board_1_sword_trees, room_board_2,`
  `room_board_2_sword, room_board_3, room_board_3_sword, room_board_3b,`
  `room_board_boattest, room_board_designTest, room_board_dungeon_2,`
  `room_board_dungeon_3, room_board_empty, room_board_gsa02_b0,`
  `room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_bullettest,`
  `room_bullettest_new, room_castle_tutorial, room_cc_clover,`
  `room_cc_lancer, room_ch3_gacharoom_unknown, room_ch3_gameshowroom,`
  `room_ch3_gameshowroom_tennatest, room_cutscene_tester,`
  `room_cutscene_tester_b, room_DARKbase_GMS2, room_DARKempty,`
  `room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_cooltrashy, room_dw_b3bs_extrapuzzle,`
  `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_interstitial,`
  `room_dw_b3bs_intro, room_dw_b3bs_jail1, room_dw_b3bs_jail2,`
  `room_dw_b3bs_lancerget, room_dw_b3bs_mysterypuzzle,`
  `room_dw_b3bs_rabbick_a, room_dw_b3bs_rabbick_b,`
  `room_dw_b3bs_rouxls_boss, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bs_sadshadowguys, room_dw_b3bs_shop, room_dw_b3bs_template,`
  `room_dw_b3bs_watercooler, room_dw_b3bs_zapper_a,`
  `room_dw_b3bs_zapper_a_old, room_dw_b3bs_zapper_b,`
  `room_dw_b3bs_zapper_c, room_dw_b3bs_zapper_d, room_dw_b3bstest,`
  `room_dw_b3bstest_big, room_dw_backstage, room_dw_castle_area_1,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_kris, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_west_cliff, room_dw_ch3_man,`
  `room_dw_changing_room, room_dw_channelchange_test, room_dw_chef,`
  `room_dw_chef_empty, room_dw_console_room, room_dw_couch_overworld_01,`
  `room_dw_couch_overworld_02, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_04, room_dw_couch_overworld_05,`
  `room_dw_couch_overworld_intro, room_dw_couch_overworld_intro_left,`
  `room_dw_couch_points, room_dw_green_room, room_dw_inbetween,`
  `room_dw_inbetweenhall, room_dw_puzzlecloset_0,`
  `room_dw_puzzlecloset_1, room_dw_puzzlecloset_1a,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_dw_ralsei_castle_front, room_dw_ranking_a, room_dw_ranking_b,`
  `room_dw_ranking_c, room_dw_ranking_hub, room_dw_ranking_t,`
  `room_dw_ranking_z, room_dw_ranking_z_hallway, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rhythm_empty, room_dw_snow_zone,`
  `room_dw_snow_zone_battle, room_dw_snow_zone_east_door,`
  `room_dw_susiezilla, room_dw_susiezilla_empty,`
  `room_dw_teevie_audiencepits, room_dw_teevie_bonus_zone,`
  `room_dw_teevie_chef, room_dw_teevie_cowboy_zone_01_after,`
  `room_dw_teevie_cowboy_zone_01_intro,`
  `room_dw_teevie_cowboy_zone_02_after,`
  `room_dw_teevie_cowboy_zone_02_intro, room_dw_teevie_cutscene_final,`
  `room_dw_teevie_dust, room_dw_teevie_dust_south,`
  `room_dw_teevie_failure_cage, room_dw_teevie_intro,`
  `room_dw_teevie_large_01, room_dw_teevie_large_02,`
  `room_dw_teevie_lightmaze, room_dw_teevie_maze,`
  `room_dw_teevie_maze_chef, room_dw_teevie_maze_final,`
  `room_dw_teevie_maze_points, room_dw_teevie_maze_quiz,`
  `room_dw_teevie_preview, room_dw_teevie_preview_south,`
  `room_dw_teevie_rhythm, room_dw_teevie_ribbick,`
  `room_dw_teevie_ribbicks_a, room_dw_teevie_ribbicks_b,`
  `room_dw_teevie_sams, room_dw_teevie_shadow_guys,`
  `room_dw_teevie_shuttahmaze, room_dw_teevie_stealth,`
  `room_dw_teevie_stealth_c, room_dw_teevie_stealth_d,`
  `room_dw_teevie_susiebridge, room_dw_teevie_susiezilla,`
  `room_dw_teevie_watercooler, room_dw_tv_closet, room_dw_tv_curtain,`
  `room_dw_tv_cutscene1g, room_genanimtest, room_GMS2_test,`
  `room_overworldBulletEnemyTest, room_perspective_testing,`
  `room_rhythmgame_editor, room_rhythmgame_tenna_test,`
  `room_shadowmantle, room_shootout, room_susiezilla,`
  `room_susiezilla_singleScreenMockup, room_tennaAnimTest,`
  `room_tennaCutsceneTest`

### Party record 1318

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 83; if (`
- status: `debug`
- rooms: `room_adventureboardtest, room_battletest, room_board_1,`
  `room_board_1_sword, room_board_1_sword_trees, room_board_2,`
  `room_board_2_sword, room_board_3, room_board_3_sword, room_board_3b,`
  `room_board_boattest, room_board_designTest, room_board_dungeon_2,`
  `room_board_dungeon_3, room_board_empty, room_board_gsa02_b0,`
  `room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_bullettest,`
  `room_bullettest_new, room_castle_tutorial, room_cc_clover,`
  `room_cc_lancer, room_ch3_gacharoom_unknown, room_ch3_gameshowroom,`
  `room_ch3_gameshowroom_tennatest, room_cutscene_tester,`
  `room_cutscene_tester_b, room_DARKbase_GMS2, room_DARKempty,`
  `room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_cooltrashy, room_dw_b3bs_extrapuzzle,`
  `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_interstitial,`
  `room_dw_b3bs_intro, room_dw_b3bs_jail1, room_dw_b3bs_jail2,`
  `room_dw_b3bs_lancerget, room_dw_b3bs_mysterypuzzle,`
  `room_dw_b3bs_rabbick_a, room_dw_b3bs_rabbick_b,`
  `room_dw_b3bs_rouxls_boss, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bs_sadshadowguys, room_dw_b3bs_shop, room_dw_b3bs_template,`
  `room_dw_b3bs_watercooler, room_dw_b3bs_zapper_a,`
  `room_dw_b3bs_zapper_a_old, room_dw_b3bs_zapper_b,`
  `room_dw_b3bs_zapper_c, room_dw_b3bs_zapper_d, room_dw_b3bstest,`
  `room_dw_b3bstest_big, room_dw_backstage, room_dw_castle_area_1,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_kris, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_west_cliff, room_dw_ch3_man,`
  `room_dw_changing_room, room_dw_channelchange_test, room_dw_chef,`
  `room_dw_chef_empty, room_dw_console_room, room_dw_couch_overworld_01,`
  `room_dw_couch_overworld_02, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_04, room_dw_couch_overworld_05,`
  `room_dw_couch_overworld_intro, room_dw_couch_overworld_intro_left,`
  `room_dw_couch_points, room_dw_green_room, room_dw_inbetween,`
  `room_dw_inbetweenhall, room_dw_puzzlecloset_0,`
  `room_dw_puzzlecloset_1, room_dw_puzzlecloset_1a,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_dw_ralsei_castle_front, room_dw_ranking_a, room_dw_ranking_b,`
  `room_dw_ranking_c, room_dw_ranking_hub, room_dw_ranking_t,`
  `room_dw_ranking_z, room_dw_ranking_z_hallway, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rhythm_empty, room_dw_snow_zone,`
  `room_dw_snow_zone_battle, room_dw_snow_zone_east_door,`
  `room_dw_susiezilla, room_dw_susiezilla_empty,`
  `room_dw_teevie_audiencepits, room_dw_teevie_bonus_zone,`
  `room_dw_teevie_chef, room_dw_teevie_cowboy_zone_01_after,`
  `room_dw_teevie_cowboy_zone_01_intro,`
  `room_dw_teevie_cowboy_zone_02_after,`
  `room_dw_teevie_cowboy_zone_02_intro, room_dw_teevie_cutscene_final,`
  `room_dw_teevie_dust, room_dw_teevie_dust_south,`
  `room_dw_teevie_failure_cage, room_dw_teevie_intro,`
  `room_dw_teevie_large_01, room_dw_teevie_large_02,`
  `room_dw_teevie_lightmaze, room_dw_teevie_maze,`
  `room_dw_teevie_maze_chef, room_dw_teevie_maze_final,`
  `room_dw_teevie_maze_points, room_dw_teevie_maze_quiz,`
  `room_dw_teevie_preview, room_dw_teevie_preview_south,`
  `room_dw_teevie_rhythm, room_dw_teevie_ribbick,`
  `room_dw_teevie_ribbicks_a, room_dw_teevie_ribbicks_b,`
  `room_dw_teevie_sams, room_dw_teevie_shadow_guys,`
  `room_dw_teevie_shuttahmaze, room_dw_teevie_stealth,`
  `room_dw_teevie_stealth_c, room_dw_teevie_stealth_d,`
  `room_dw_teevie_susiebridge, room_dw_teevie_susiezilla,`
  `room_dw_teevie_watercooler, room_dw_tv_closet, room_dw_tv_curtain,`
  `room_dw_tv_cutscene1g, room_genanimtest, room_GMS2_test,`
  `room_overworldBulletEnemyTest, room_perspective_testing,`
  `room_rhythmgame_editor, room_rhythmgame_tenna_test,`
  `room_shadowmantle, room_shootout, room_susiezilla,`
  `room_susiezilla_singleScreenMockup, room_tennaAnimTest,`
  `room_tennaCutsceneTest`

### Party record 1319

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 124; if (`
- status: `debug`
- rooms: `room_adventureboardtest, room_battletest, room_board_1,`
  `room_board_1_sword, room_board_1_sword_trees, room_board_2,`
  `room_board_2_sword, room_board_3, room_board_3_sword, room_board_3b,`
  `room_board_boattest, room_board_designTest, room_board_dungeon_2,`
  `room_board_dungeon_3, room_board_empty, room_board_gsa02_b0,`
  `room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_bullettest,`
  `room_bullettest_new, room_castle_tutorial, room_cc_clover,`
  `room_cc_lancer, room_ch3_gacharoom_unknown, room_ch3_gameshowroom,`
  `room_ch3_gameshowroom_tennatest, room_cutscene_tester,`
  `room_cutscene_tester_b, room_DARKbase_GMS2, room_DARKempty,`
  `room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_cooltrashy, room_dw_b3bs_extrapuzzle,`
  `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_interstitial,`
  `room_dw_b3bs_intro, room_dw_b3bs_jail1, room_dw_b3bs_jail2,`
  `room_dw_b3bs_lancerget, room_dw_b3bs_mysterypuzzle,`
  `room_dw_b3bs_rabbick_a, room_dw_b3bs_rabbick_b,`
  `room_dw_b3bs_rouxls_boss, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bs_sadshadowguys, room_dw_b3bs_shop, room_dw_b3bs_template,`
  `room_dw_b3bs_watercooler, room_dw_b3bs_zapper_a,`
  `room_dw_b3bs_zapper_a_old, room_dw_b3bs_zapper_b,`
  `room_dw_b3bs_zapper_c, room_dw_b3bs_zapper_d, room_dw_b3bstest,`
  `room_dw_b3bstest_big, room_dw_backstage, room_dw_castle_area_1,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_kris, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_west_cliff, room_dw_ch3_man,`
  `room_dw_changing_room, room_dw_channelchange_test, room_dw_chef,`
  `room_dw_chef_empty, room_dw_console_room, room_dw_couch_overworld_01,`
  `room_dw_couch_overworld_02, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_04, room_dw_couch_overworld_05,`
  `room_dw_couch_overworld_intro, room_dw_couch_overworld_intro_left,`
  `room_dw_couch_points, room_dw_green_room, room_dw_inbetween,`
  `room_dw_inbetweenhall, room_dw_puzzlecloset_0,`
  `room_dw_puzzlecloset_1, room_dw_puzzlecloset_1a,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_dw_ralsei_castle_front, room_dw_ranking_a, room_dw_ranking_b,`
  `room_dw_ranking_c, room_dw_ranking_hub, room_dw_ranking_t,`
  `room_dw_ranking_z, room_dw_ranking_z_hallway, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rhythm_empty, room_dw_snow_zone,`
  `room_dw_snow_zone_battle, room_dw_snow_zone_east_door,`
  `room_dw_susiezilla, room_dw_susiezilla_empty,`
  `room_dw_teevie_audiencepits, room_dw_teevie_bonus_zone,`
  `room_dw_teevie_chef, room_dw_teevie_cowboy_zone_01_after,`
  `room_dw_teevie_cowboy_zone_01_intro,`
  `room_dw_teevie_cowboy_zone_02_after,`
  `room_dw_teevie_cowboy_zone_02_intro, room_dw_teevie_cutscene_final,`
  `room_dw_teevie_dust, room_dw_teevie_dust_south,`
  `room_dw_teevie_failure_cage, room_dw_teevie_intro,`
  `room_dw_teevie_large_01, room_dw_teevie_large_02,`
  `room_dw_teevie_lightmaze, room_dw_teevie_maze,`
  `room_dw_teevie_maze_chef, room_dw_teevie_maze_final,`
  `room_dw_teevie_maze_points, room_dw_teevie_maze_quiz,`
  `room_dw_teevie_preview, room_dw_teevie_preview_south,`
  `room_dw_teevie_rhythm, room_dw_teevie_ribbick,`
  `room_dw_teevie_ribbicks_a, room_dw_teevie_ribbicks_b,`
  `room_dw_teevie_sams, room_dw_teevie_shadow_guys,`
  `room_dw_teevie_shuttahmaze, room_dw_teevie_stealth,`
  `room_dw_teevie_stealth_c, room_dw_teevie_stealth_d,`
  `room_dw_teevie_susiebridge, room_dw_teevie_susiezilla,`
  `room_dw_teevie_watercooler, room_dw_tv_closet, room_dw_tv_curtain,`
  `room_dw_tv_cutscene1g, room_genanimtest, room_GMS2_test,`
  `room_overworldBulletEnemyTest, room_perspective_testing,`
  `room_rhythmgame_editor, room_rhythmgame_tenna_test,`
  `room_shadowmantle, room_shootout, room_susiezilla,`
  `room_susiezilla_singleScreenMockup, room_tennaAnimTest,`
  `room_tennaCutsceneTest`

### Party record 1320

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3 || global.char[1] == 3)                 {`
  `global.interact = 1`
- condition: `line 143; if (throwitem == 4) > if (`
- status: `debug`
- rooms: `room_adventureboardtest, room_battletest, room_board_1,`
  `room_board_1_sword, room_board_1_sword_trees, room_board_2,`
  `room_board_2_sword, room_board_3, room_board_3_sword, room_board_3b,`
  `room_board_boattest, room_board_designTest, room_board_dungeon_2,`
  `room_board_dungeon_3, room_board_empty, room_board_gsa02_b0,`
  `room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_bullettest,`
  `room_bullettest_new, room_castle_tutorial, room_cc_clover,`
  `room_cc_lancer, room_ch3_gacharoom_unknown, room_ch3_gameshowroom,`
  `room_ch3_gameshowroom_tennatest, room_cutscene_tester,`
  `room_cutscene_tester_b, room_DARKbase_GMS2, room_DARKempty,`
  `room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_cooltrashy, room_dw_b3bs_extrapuzzle,`
  `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_interstitial,`
  `room_dw_b3bs_intro, room_dw_b3bs_jail1, room_dw_b3bs_jail2,`
  `room_dw_b3bs_lancerget, room_dw_b3bs_mysterypuzzle,`
  `room_dw_b3bs_rabbick_a, room_dw_b3bs_rabbick_b,`
  `room_dw_b3bs_rouxls_boss, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bs_sadshadowguys, room_dw_b3bs_shop, room_dw_b3bs_template,`
  `room_dw_b3bs_watercooler, room_dw_b3bs_zapper_a,`
  `room_dw_b3bs_zapper_a_old, room_dw_b3bs_zapper_b,`
  `room_dw_b3bs_zapper_c, room_dw_b3bs_zapper_d, room_dw_b3bstest,`
  `room_dw_b3bstest_big, room_dw_backstage, room_dw_castle_area_1,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_kris, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_west_cliff, room_dw_ch3_man,`
  `room_dw_changing_room, room_dw_channelchange_test, room_dw_chef,`
  `room_dw_chef_empty, room_dw_console_room, room_dw_couch_overworld_01,`
  `room_dw_couch_overworld_02, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_04, room_dw_couch_overworld_05,`
  `room_dw_couch_overworld_intro, room_dw_couch_overworld_intro_left,`
  `room_dw_couch_points, room_dw_green_room, room_dw_inbetween,`
  `room_dw_inbetweenhall, room_dw_puzzlecloset_0,`
  `room_dw_puzzlecloset_1, room_dw_puzzlecloset_1a,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_dw_ralsei_castle_front, room_dw_ranking_a, room_dw_ranking_b,`
  `room_dw_ranking_c, room_dw_ranking_hub, room_dw_ranking_t,`
  `room_dw_ranking_z, room_dw_ranking_z_hallway, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rhythm_empty, room_dw_snow_zone,`
  `room_dw_snow_zone_battle, room_dw_snow_zone_east_door,`
  `room_dw_susiezilla, room_dw_susiezilla_empty,`
  `room_dw_teevie_audiencepits, room_dw_teevie_bonus_zone,`
  `room_dw_teevie_chef, room_dw_teevie_cowboy_zone_01_after,`
  `room_dw_teevie_cowboy_zone_01_intro,`
  `room_dw_teevie_cowboy_zone_02_after,`
  `room_dw_teevie_cowboy_zone_02_intro, room_dw_teevie_cutscene_final,`
  `room_dw_teevie_dust, room_dw_teevie_dust_south,`
  `room_dw_teevie_failure_cage, room_dw_teevie_intro,`
  `room_dw_teevie_large_01, room_dw_teevie_large_02,`
  `room_dw_teevie_lightmaze, room_dw_teevie_maze,`
  `room_dw_teevie_maze_chef, room_dw_teevie_maze_final,`
  `room_dw_teevie_maze_points, room_dw_teevie_maze_quiz,`
  `room_dw_teevie_preview, room_dw_teevie_preview_south,`
  `room_dw_teevie_rhythm, room_dw_teevie_ribbick,`
  `room_dw_teevie_ribbicks_a, room_dw_teevie_ribbicks_b,`
  `room_dw_teevie_sams, room_dw_teevie_shadow_guys,`
  `room_dw_teevie_shuttahmaze, room_dw_teevie_stealth,`
  `room_dw_teevie_stealth_c, room_dw_teevie_stealth_d,`
  `room_dw_teevie_susiebridge, room_dw_teevie_susiezilla,`
  `room_dw_teevie_watercooler, room_dw_tv_closet, room_dw_tv_curtain,`
  `room_dw_tv_cutscene1g, room_genanimtest, room_GMS2_test,`
  `room_overworldBulletEnemyTest, room_perspective_testing,`
  `room_rhythmgame_editor, room_rhythmgame_tenna_test,`
  `room_shadowmantle, room_shootout, room_susiezilla,`
  `room_susiezilla_singleScreenMockup, room_tennaAnimTest,`
  `room_tennaCutsceneTest`

### Party record 1321

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         myx[i] += 15`
- condition: `line 23; if (i_ex(global.charinstance[i])) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1322

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         myx[i] += 15`
- condition: `line 27; if (global.char[i] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1323

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 || global.char[1] == 2 || global.char[2] == 2)     {`
  `sus = 0`
- condition: `line 245; if (global.charauto[2] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1324

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)         {             sus = 1`
- condition: `line 248; if (global.char[0] == 2 || global.char[1] == 2 ||`
  `global.char[2] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1325

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)         {             sus = 2`
- condition: `line 252; if (global.char[1] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1326

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 185; if (global.char[i] != 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1327

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 194; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1328

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 203; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1329

- chapter: `3`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 212; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1330

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             if`
  `(global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoor...`
  `== 2 ||`
  `global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoord...`
  `== 4)             {                 if (havechar[1] == 0 ||`
  `global.hp[2] <= 0)                 {`
  `canpress = 0`
- condition: `line 1088; if (cango == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1331

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)                     {                         for (i = 0`
- condition: `line 1341; if (global.bmenuno == 11) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1332

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         for (i = 0`
- condition: `line 1354; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1333

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         for (i = 0`
- condition: `line 1367; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1334

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         for (i = 0`
- condition: `line 1380; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1335

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         __actname =`
  `global.actnamesus[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 782; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1336

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         __actname =`
  `global.actnameral[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 786; if (global.char[global.charturn] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1337

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         __actname =`
  `global.actnamenoe[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 790; if (global.char[global.charturn] == 3) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1338

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[thisenemy][__acti]`
- condition: `line 1063; if (global.bmenuno == 9 && global.myfight == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1339

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[thisenemy][__acti]`
- condition: `line 1071; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1340

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[thisenemy][__acti]`
- condition: `line 1079; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1341

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[thisenemy][__acti]`
- condition: `line 1087; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1342

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             chartime =`
  `global.actactor[global.bmenucoord[11][global.charturn]][i]`
- condition: `line 1147; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1343

- chapter: `3`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             if (!havejeviltail == true)`
  `{                 if (i == 1 && i_ex(obj_tenna_enemy_bg) &&`
  `obj_tenna_enemy_bg.myscore < 20)                 {`
  `cant = 1`
- condition: `line 1210; if (i == 3 && global.monstertype[thisenemy] == 59 &&`
  `global.flag[1044] < 150) > if (global.monstertype[thisenemy] ==`
  `103 &&`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1344

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1499; if (triptickettimer >= 120)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1345

- chapter: `3`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1346

- chapter: `3`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `2`
- condition: `line 5; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1347

- chapter: `3`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1348

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 928; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1349

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 929; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1350

- chapter: `3`
- phase: `global.char[dx]`
- field: `global.char[dx]`
- expression: `= 2)                 {                     if`
  `(global.charcond[dx] != 5)                     {`
  `global.charcond[dx] = 5`
- condition: `line 245; if (scr_monsterpop() > 1 && scr_havechar(2)) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1351

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 416; if (!scr_havechar(2))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1352

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 420; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1353

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 448; if (!scr_havechar(2))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1354

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 452; if (!scr_havechar(2)) > if (!scr_havechar(3))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1355

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 38; if (global.fighting == 0) > if`
  `(sunkus_kb_check_pressed(ord("6")) ||`
  `gamepad_button_check_pressed(0, gp_shoulderlb))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1356

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 39; if (global.fighting == 0) > if`
  `(sunkus_kb_check_pressed(ord("6")) ||`
  `gamepad_button_check_pressed(0, gp_shoulderlb))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1357

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 40; if (global.fighting == 0) > if`
  `(sunkus_kb_check_pressed(ord("6")) ||`
  `gamepad_button_check_pressed(0, gp_shoulderlb))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1358

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 44; if (sunkus_kb_check_pressed(ord("7")) ||`
  `gamepad_button_check_pressed(0, gp_shoulderrb))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1359

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 48; if (sunkus_kb_check_pressed(ord("7")) ||`
  `gamepad_button_check_pressed(0, gp_shoulderrb)) > if`
  `(sunkus_kb_check_pressed(ord("8")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1360

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 49; if (sunkus_kb_check_pressed(ord("7")) ||`
  `gamepad_button_check_pressed(0, gp_shoulderrb)) > if`
  `(sunkus_kb_check_pressed(ord("8")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1361

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 53; if (sunkus_kb_check_pressed(ord("8"))) > if`
  `(sunkus_kb_check_pressed(ord("9")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1362

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 54; if (sunkus_kb_check_pressed(ord("9")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1363

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 69; if (global.plot == 16 && global.chapter == 2)`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 1364

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 7; ﻿if (scr_havechar(2) && obj_mainchara.x < x && con == -1`
  `&& global.flag[336] == 0)`
- status: `production`
- rooms: `room_town_south`

### Party record 1365

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 40; if (obj_mainchara.x > x && global.flag[336] == 1 &&`
  `!scr_havechar(2))`
- status: `production`
- rooms: `room_town_south`

### Party record 1366

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 41; if (obj_mainchara.x > x && global.flag[336] == 1 &&`
  `!scr_havechar(2))`
- status: `production`
- rooms: `room_town_south`

### Party record 1367

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 50; if (obj_mainchara.x < x && global.flag[336] == 1 &&`
  `scr_havechar(2))`
- status: `production`
- rooms: `room_town_south`

### Party record 1368

- chapter: `3`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 12; if (global.chapter != 2 || global.flag[316] == 1)`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1369

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 17; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1370

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 18; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1371

- chapter: `3`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 240; if (sprite_index == spr_shine_white)`
- status: `production`
- rooms: `room_dw_ranking_b`

### Party record 1372

- chapter: `3`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 3; ﻿if (!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 1373

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1374

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1375

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1376

- chapter: `4`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         exit`
- condition: `line 10; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1377

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `arg0 = false, arg1 = false, arg2 = false`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1378

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 10; if (!i_ex(kris))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1379

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 14; if (arg0 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1380

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 29; if (arg1 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1381

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 44; if (arg2 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1382

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1383

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 6; if (arg0)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1384

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 10; if (arg0) > if (arg1)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1385

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 14; if (arg1) > if (arg2)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1386

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1387

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1388

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1389

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)             {                 continue`
- condition: `line 35; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1390

- chapter: `4`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 if (global.cinstance[i].x !=`
  `s.x || global.cinstance[i].y != s.x)                 {`
  `global.cinstance[i].x = s.x`
- condition: `line 7; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1391

- chapter: `4`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 if (global.cinstance[i].x !=`
  `r.x || global.cinstance[i].y != r.x)                 {`
  `global.cinstance[i].x = r.x`
- condition: `line 44; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1392

- chapter: `4`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 s =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 9; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1393

- chapter: `4`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 r =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1394

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `arg0`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1395

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 0)     {         global.char[0] = characterToGet`
- condition: `line 24; case "noelle": > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1396

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && getchar == 0)     {         global.char[1] =`
  `characterToGet`
- condition: `line 29; if (global.char[0] == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1397

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0 && getchar == 0)     {         global.char[2] =`
  `characterToGet`
- condition: `line 34; if (global.char[1] == 0 && getchar == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1398

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 53; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1399

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 58; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1400

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 63; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1401

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 68; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1402

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1403

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1404

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1405

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 19; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1406

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 24; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1407

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 29; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1408

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 34; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1409

- chapter: `4`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         charcan = 0`
- condition: `line 12; if (global.acting[arg0] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1410

- chapter: `4`
- phase: `global.char[caster]`
- field: `global.char[caster]`
- expression: `= 4)         {             dm.type = 6`
- condition: `line 7; if (caster < 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1411

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2)     {         sus = 0`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1412

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)     {         sus = 1`
- condition: `line 7; if (global.char[0] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1413

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)     {         sus = 2`
- condition: `line 11; if (global.char[1] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1414

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 && global.charauto[2] == 1)             {`
  `global.acting[0] = 1`
- condition: `line 115; if (skip == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1415

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             with (obj_monsterparent)`
  `{                 actingnoe = 0`
- condition: `line 28; if (moveswapped == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1416

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             with (obj_monsterparent)`
  `{                 actingral = 0`
- condition: `line 35; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1417

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             with (obj_monsterparent)`
  `{                 actingsus = 0`
- condition: `line 42; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1418

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3)         {             global.monsterat[myself] = 13`
- condition: `line 1728; if (global.monstertype[myself] == 66) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1419

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3)         {             global.monsterat[myself] = 14`
- condition: `line 1797; if (global.monstertype[myself] == 68) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1420

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         partyconfig = 1`
- condition: `line 6; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1421

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         partyconfig = 2`
- condition: `line 10; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1422

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         global.heromakey[0] =`
  `yy + 140`
- condition: `line 25; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1423

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         global.heromakey[0] = yy + 100`
- condition: `line 29; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1424

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(20))`
- condition: `line 491; case 212: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1425

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(80))`
- condition: `line 495; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1426

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(50))`
- condition: `line 499; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1427

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(30))`
- condition: `line 503; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1428

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(80))`
- condition: `line 510; case 213: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1429

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(20))`
- condition: `line 514; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1430

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(50))`
- condition: `line 518; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1431

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(70))`
- condition: `line 522; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1432

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1) ? 100 : 90`
- condition: `line 575; case 225: > case 226:`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1433

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(400))`
- condition: `line 654; case 260: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1434

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(40))`
- condition: `line 658; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1435

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(40))`
- condition: `line 662; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1436

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(40))`
- condition: `line 666; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1437

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {                 scr_healitemspell(160)`
- condition: `line 677; case 262: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1438

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {                 scr_healitemspell(160)`
- condition: `line 681; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1439

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {                 scr_healitemspell(160)`
- condition: `line 685; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1440

- chapter: `4`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(155))`
- condition: `line 689; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1441

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)         {             suspos = i`
- condition: `line 15; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1442

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)         {             ralpos = i`
- condition: `line 19; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1443

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)         {             noepos = i`
- condition: `line 23; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1444

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cooked to`
  `perfection!", "scr_itemuse_slash_scr_itemuse_gml_123_0"))`
- condition: `line 151; case 8: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1445

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("A bit`
  `burnt...?", "scr_itemuse_slash_scr_itemuse_gml_127_0"))`
- condition: `line 155; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1446

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 159; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1447

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Mmm... face",`
  `"scr_itemuse_slash_scr_itemuse_gml_143_0"))`
- condition: `line 169; case 9: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1448

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `stringsetloc("(uncomfortable)",`
  `"scr_itemuse_slash_scr_itemuse_gml_147_0"))`
- condition: `line 173; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1449

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Umm, what is`
  `this? It's cute...", "scr_itemuse_slash_scr_itemuse_gml_151_0"))`
- condition: `line 177; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1450

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Why this!?",`
  `"scr_itemuse_slash_scr_itemuse_gml_161_0"))`
- condition: `line 185; case 10: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1451

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Let's be`
  `healthy!", "scr_itemuse_slash_scr_itemuse_gml_165_0"))`
- condition: `line 189; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1452

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Something to`
  `graze on!", "scr_itemuse_slash_scr_itemuse_gml_169_0"))`
- condition: `line 193; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1453

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 218; case 12: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1454

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 222; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1455

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 227; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1456

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_healitem(global.charselect, 30)`
- condition: `line 232; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1457

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 240; case 13: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1458

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 244; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1459

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 249; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1460

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_healitem(0, 35)`
- condition: `line 254; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1461

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(It's SO`
  `good!)", "scr_itemuse_slash_scr_itemuse_gml_239_0"))`
- condition: `line 264; case 14: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1462

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("K-Kris!? I...",`
  `"scr_itemuse_slash_scr_itemuse_gml_243_0"))`
- condition: `line 268; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1463

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Huh? I didn't`
  `know Kris liked this flavor.)",`
  `"scr_itemuse_slash_scr_itemuse_gml_247_0"))`
- condition: `line 272; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1464

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cool, it's`
  `wriggling.", "scr_itemuse_slash_scr_itemuse_gml_257_0"))`
- condition: `line 280; case 15: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1465

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Yum, is this`
  `spaghetti?", "scr_itemuse_slash_scr_itemuse_gml_261_0"))`
- condition: `line 284; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1466

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Tastes like...`
  `jumprope?", "scr_itemuse_slash_scr_itemuse_gml_265_0"))`
- condition: `line 288; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1467

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 325; case 18: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1468

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 329; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1469

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 333; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1470

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 342; case 19: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1471

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 346; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1472

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 350; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1473

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 359; case 20: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1474

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 363; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1475

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 367; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1476

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 376; case 21: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1477

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 380; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1478

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 384; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1479

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("C'mon, gimme`
  `the rest!", "scr_itemuse_slash_scr_itemuse_gml_418_0"))`
- condition: `line 394; case 22: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1480

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("M-maybe give`
  `Susie the rest?", "scr_itemuse_slash_scr_itemuse_gml_422_0"))`
- condition: `line 398; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1481

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 402; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1482

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hey, this`
  `rules!", "scr_itemuse_slash_scr_itemuse_gml_438_0"))`
- condition: `line 412; case 23: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1483

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Nice and`
  `chalky.", "scr_itemuse_slash_scr_itemuse_gml_442_0"))`
- condition: `line 416; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1484

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I-isn't this`
  `the chalk I gave her?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_446_0"))`
- condition: `line 420; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1485

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell'd you call`
  `this!?", "scr_itemuse_slash_scr_itemuse_gml_456_0"))`
- condition: `line 428; case 24: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1486

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I made this.",`
  `"scr_itemuse_slash_scr_itemuse_gml_460_0"))`
- condition: `line 432; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1487

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("B-Brainfreeze!`
  `... kidding!", "scr_itemuse_slash_scr_itemuse_gml_464_0"))`
- condition: `line 436; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1488

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 heal_amount = 100`
- condition: `line 460; case 26: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1489

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says GUTS!",`
  `"scr_itemuse_slash_scr_itemuse_gml_487_0"))`
- condition: `line 464; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1490

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says`
  `Fluffy...", "scr_itemuse_slash_scr_itemuse_gml_491_0"))`
- condition: `line 468; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1491

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I... I can't`
  `read these symbols...",`
  `"scr_itemuse_slash_scr_itemuse_gml_495_0"))`
- condition: `line 472; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1492

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ugh! ...tastes`
  `good?", "scr_itemuse_slash_scr_itemuse_gml_553_0"))`
- condition: `line 538; if (global.char[global.charselect] != 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1493

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ow... er,`
  `thanks, Kris!", "scr_itemuse_slash_scr_itemuse_gml_557_0"))`
- condition: `line 542; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1494

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I'll... just`
  `pretend to drink it...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_561_0"))`
- condition: `line 546; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1495

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (global.filechoice == 1 &&`
  `scr_havechar("noelle"))                 {`
  `scr_itemcomment(noepos, stringsetloc("What are you, a unicorn?`
  `Faha.", "scr_itemuse_slash_scr_itemuse_gml_580_0"))`
- condition: `line 559; case 34: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1496

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {                     item_comment =`
  `stringsetloc("Butterscotch, nice!",`
  `"scr_itemuse_slash_scr_itemuse_gml_588_0")`
- condition: `line 569; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1497

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {                     item_comment =`
  `stringsetloc("Wow, what a nice flavor!",`
  `"scr_itemuse_slash_scr_itemuse_gml_600_0")`
- condition: `line 581; else if (global.filechoice == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1498

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {                     item_comment =`
  `stringsetloc("Mmm, butterscotch!",`
  `"scr_itemuse_slash_scr_itemuse_gml_612_0")`
- condition: `line 593; else if (global.filechoice == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1499

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 usable = 1`
- condition: `line 610; case 35: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1500

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell no.",`
  `"scr_itemuse_slash_scr_itemuse_gml_654_0"))`
- condition: `line 630; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1501

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Is... that, um,`
  `nutritious?", "scr_itemuse_slash_scr_itemuse_gml_658_0"))`
- condition: `line 634; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1502

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("C... Can we`
  `keep it?", "scr_itemuse_slash_scr_itemuse_gml_662_0"))`
- condition: `line 638; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1503

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Fine, I'll`
  `finish it.", "scr_itemuse_slash_scr_itemuse_gml_674_0"))`
- condition: `line 647; case 36: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1504

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Aw, you saved`
  `me half?", "scr_itemuse_slash_scr_itemuse_gml_678_0"))`
- condition: `line 651; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1505

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Whatever, it's`
  `just Kris's...)", "scr_itemuse_slash_scr_itemuse_gml_682_0"))`
- condition: `line 655; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1506

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Like my old`
  `school.", "scr_itemuse_slash_scr_itemuse_gml_693_0"))`
- condition: `line 663; case 37: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1507

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Is this`
  `legal?", "scr_itemuse_slash_scr_itemuse_gml_697_0"))`
- condition: `line 667; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1508

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Here, I`
  `refreezed it!", "scr_itemuse_slash_scr_itemuse_gml_701_0"))`
- condition: `line 671; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1509

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Look, I'm a`
  `roach.", "scr_itemuse_slash_scr_itemuse_gml_722_0"))`
- condition: `line 695; case 39: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1510

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'm a comfy`
  `caterpillar!", "scr_itemuse_slash_scr_itemuse_gml_726_0"))`
- condition: `line 699; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1511

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'm, um, an`
  `alien?", "scr_itemuse_slash_scr_itemuse_gml_730_0"))`
- condition: `line 703; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1512

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1) ? 400 : 40`
- condition: `line 710; if (global.char[global.charselect] == 4) > case 60:`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1513

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ugh! How old is`
  `this?!", "scr_itemuse_slash_scr_itemuse_gml_741_0"))`
- condition: `line 711; case 60: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1514

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Aww Kris,`
  `y-your favorite...", "scr_itemuse_slash_scr_itemuse_gml_745_0"))`
- condition: `line 715; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1515

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'd... I'd`
  `rather eat meat...", "scr_itemuse_slash_scr_itemuse_gml_749_0"))`
- condition: `line 719; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1516

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Sounds kinda`
  `like Noelle.", "scr_itemuse_slash_scr_itemuse_gml_760_0"))`
- condition: `line 728; case 61: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1517

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("... the hymn of`
  `the prophecy.", "scr_itemuse_slash_scr_itemuse_gml_764_0"))`
- condition: `line 732; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1518

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(... Kris would`
  `never join choir...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_768_0"))`
- condition: `line 736; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1519

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell yeah!`
  `Cheers!", "scr_itemuse_slash_scr_itemuse_gml_780_0"))`
- condition: `line 745; case 62: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1520

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Y-yuck! Er,`
  `mmm, medicine?", "scr_itemuse_slash_scr_itemuse_gml_784_0"))`
- condition: `line 749; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1521

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healamount = 155`
- condition: `line 753; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1522

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("... Isn't that`
  `rain?", "scr_itemuse_slash_scr_itemuse_gml_809_0"))`
- condition: `line 765; case 63: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1523

- chapter: `4`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It's like when`
  `we ate snow.", "scr_itemuse_slash_scr_itemuse_gml_813_0"))`
- condition: `line 769; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1524

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1525

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1526

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1527

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1528

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1529

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1530

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)                     {                         facetype =`
  `spr_headkris`
- condition: `line 34; if (itemtype[menuc[1]] == "weapon" || itemtype[menuc[1]]`
  `== "armor") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1531

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         facetype =`
  `spr_headsusie`
- condition: `line 38; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1532

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         facetype =`
  `spr_headralsei`
- condition: `line 42; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1533

- chapter: `4`
- phase: `global.char[__findchar]`
- field: `global.char[__findchar]`
- expression: `= arg0)         {             __charslot = __findchar`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1534

- chapter: `4`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 2)                 {                     with (__minstance)`
  `{                         actconsus = 1`
- condition: `line 25; if (global.actingsingle[global.currentactingchar] == 1)`
  `> if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1535

- chapter: `4`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 3)                 {                     with (__minstance)`
  `{                         actconral = 1`
- condition: `line 37; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1536

- chapter: `4`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 4)                 {                     with (__minstance)`
  `{                         actconnoe = 1`
- condition: `line 49; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1537

- chapter: `4`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 1 &&`
  `global.actsimul[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderkri = __simulcount`
- condition: `line 9; if (global.actingsingle[__ii] == 1 &&`
  `instance_exists(obj_monsterparent)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1538

- chapter: `4`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 2 &&`
  `global.actsimulsus[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordersus = __simulcount`
- condition: `line 18; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1539

- chapter: `4`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 3 &&`
  `global.actsimulral[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderral = __simulcount`
- condition: `line 27; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1540

- chapter: `4`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 4 &&`
  `global.actsimulnoe[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordernoe = __simulcount`
- condition: `line 36; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1541

- chapter: `4`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 1)             {                 if (global.canact[0][__fj] ==`
  `1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1542

- chapter: `4`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 2)             {                 if (global.canactsus[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 33; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1543

- chapter: `4`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 3)             {                 if (global.canactral[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 53; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1544

- chapter: `4`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 4)             {                 if (global.canactnoe[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 73; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1545

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             global.monsterinstance[arg0].acting =`
  `arg1 + 1`
- condition: `line 5; if (i_ex(global.monsterinstance[arg0])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1546

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {`
  `global.monsterinstance[arg0].actingsus = arg1 + 1`
- condition: `line 9; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1547

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {`
  `global.monsterinstance[arg0].actingral = arg1 + 1`
- condition: `line 13; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1548

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {`
  `global.monsterinstance[arg0].actingnoe = arg1 + 1`
- condition: `line 17; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1549

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)     {         global.actingsimul[0] = actsimul[arg1]`
- condition: `line 22; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1550

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[arg0][__acti]`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1551

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[arg0][__acti]`
- condition: `line 12; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1552

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[arg0][__acti]`
- condition: `line 18; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1553

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[arg0][__acti]`
- condition: `line 24; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1554

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1555

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1556

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1557

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 17; if (checker == "noelle" || checker == "no" || checker ==`
  `"n") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1558

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 21; if (global.char[0] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1559

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 25; if (global.char[1] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1560

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 32; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1561

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 12; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1562

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1563

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 5; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1564

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1565

- chapter: `4`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         debug_print("No party member in slot " +`
  `string(arg0))`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1566

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_secretpiano`

### Party record 1567

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 10; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_rotatingtower2`

### Party record 1568

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 28; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchc_encounter2`

### Party record 1569

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_libraryconnector`

### Party record 1570

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 26; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_escherstaircase`

### Party record 1571

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 105; if (global.plot >= 260 && global.plot < 270)`
- status: `production`
- rooms: `room_dw_churchc_final_prophecy`

### Party record 1572

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 334; if (con == 8 && !i_ex(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_churchc_final_prophecy`

### Party record 1573

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 10; if (con == 0)`
- status: `production`
- rooms: `room_dw_church_waterfalltearoom`

### Party record 1574

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 39; if (con == 2)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1575

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 39; unconditional in entry`
- status: `production-subsystem`
- rooms: `room_cc_fountain`

### Party record 1576

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 39; if (global.plot < 150) > if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_darkmaze`

### Party record 1577

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchc_titandefeated`

### Party record 1578

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 160; if (con == 2 && !i_ex(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_churchc_titandefeated`

### Party record 1579

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_shadowgerson`

### Party record 1580

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 35; if (global.char[i] != 4) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1581

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 39; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1582

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 c[i].sprite_index =`
  `spr_ralsei_battleintro`
- condition: `line 47; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1583

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_biblioxencounter`

### Party record 1584

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 28; if (global.plot >= 240 && global.plot < 250)`
- status: `production`
- rooms: `room_dw_churchc_pretitan`

### Party record 1585

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 139; unconditional in entry`
- status: `production`
- rooms: `room_dw_ralsei_castle_3f`

### Party record 1586

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 70; if (scr_flag_get(852) == 0 && scr_flag_get(851) < 3) >`
  `if (scr_flag_get(851) == 1)`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1587

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `2`
- condition: `line 437; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1588

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 438; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1589

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 439; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1590

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `0`
- condition: `line 571; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1591

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 572; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1592

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 573; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1593

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"kris"`
- condition: `line 574; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1594

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"ralsei"`
- condition: `line 575; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1595

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"susie"`
- condition: `line 576; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_arena`

### Party record 1596

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1010; if (heart_catch_scene) > if (heart_catch_con == 0)`
- status: `production`
- rooms: `room_lw_noellehouse_basement`

### Party record 1597

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 9; if (scr_debug())`
- status: `legacy`
- rooms: `room_dw_churchb_prophecymaze, room_dw_churchb_prophecymaze_old`

### Party record 1598

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 4; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_nongerson`

### Party record 1599

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `2`
- condition: `line 164; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_nongerson`

### Party record 1600

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 165; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_nongerson`

### Party record 1601

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 166; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_nongerson`

### Party record 1602

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 315; if (con == 48 && !d_ex() && customcon == 1)`
- status: `production`
- rooms: `room_dw_churchb_nongerson`

### Party record 1603

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 8; if (global.plot >= 127) > if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_intro_gerson`

### Party record 1604

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 23; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_windows`

### Party record 1605

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 26; if (global.plot >= 242)`
- status: `production`
- rooms: `room_dw_churchb_windows`

### Party record 1606

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2 || global.char[2] == 2`
- condition: `line 98; unconditional in entry`
- status: `unplaced-or-presentation`
- rooms: `room_dw_rhythm`

### Party record 1607

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 3 || global.char[2] == 3`
- condition: `line 113; unconditional in entry`
- status: `unplaced-or-presentation`
- rooms: `room_dw_rhythm`

### Party record 1608

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 142; if (room_exists(roomtarg)) > if (roomtarg ==`
  `room_dw_b3bs_zapper_d)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1609

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 146; if (roomtarg == room_dw_b3bs_zapper_d)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1610

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 97; if (facing != -1) > if (room_exists(roomtarg))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1611

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_sideclimb`

### Party record 1612

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_waterfallroom`

### Party record 1613

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 6; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_darkclimb`

### Party record 1614

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 13; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchc_titanclimb2_post`

### Party record 1615

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 18; if (global.plot >= 5 && global.plot < 10)`
- status: `production`
- rooms: `room_torhouse`

### Party record 1616

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 6; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_lantern_hallway`

### Party record 1617

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 9; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_ripseq2`

### Party record 1618

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_pianopiece_right`

### Party record 1619

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 26; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_bellroom`

### Party record 1620

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 8; if (global.plot == 105)`
- status: `production`
- rooms: `room_dw_church_intro1`

### Party record 1621

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 9; if (global.plot < 240)`
- status: `production`
- rooms: `room_dw_churchb_nongerson_post`

### Party record 1622

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 32; if (scr_debug())`
- status: `production`
- rooms: `room_lw_noellehouse_dess`

### Party record 1623

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 178; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchc_darkswords`

### Party record 1624

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 25; if (keyboard_check(ord("2")))`
- status: `production`
- rooms: `room_dw_churchc_angelprophecy_encounter`

### Party record 1625

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 70; if (global.plot < 231) > if (global.plot < 231)`
- status: `production`
- rooms: `room_dw_churchb_staircaseintro`

### Party record 1626

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 93; if (global.plot >= 240)`
- status: `production`
- rooms: `room_dw_churchb_staircaseintro`

### Party record 1627

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1628

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 21; if (global.flag[930]) > if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_churchb_moneyfountain`

### Party record 1629

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_stairspreview`

### Party record 1630

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 11; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_library, room_dw_churchb_library_alternate`

### Party record 1631

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 97; if (scr_debug()) > if (keyboard_check(ord("P")))`
- status: `production`
- rooms: `room_dw_churchb_extinguisher`

### Party record 1632

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 100; if (keyboard_check(ord("P"))) > if (global.plot >= 240)`
- status: `production`
- rooms: `room_dw_churchb_extinguisher`

### Party record 1633

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 112; unconditional in entry`
- status: `production`
- rooms: `room_torhouse`

### Party record 1634

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 58; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_gersonstudy`

### Party record 1635

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 11; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchc_finalclimb`

### Party record 1636

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 33; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1637

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 11; if (scr_debug()) > if (keyboard_check(ord("P")))`
- status: `production`
- rooms: `room_dw_churchc_slidingpiano`

### Party record 1638

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 12; if (global.plot < 210)`
- status: `production`
- rooms: `room_lw_church_entrance`

### Party record 1639

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 10; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_fireplace`

### Party record 1640

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1702; if (endingtimer == 210)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1641

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 6; if (scr_debug())`
- status: `debug`
- rooms: `room_debug_pianotest, room_dw_church_bellhall_central,`
  `room_dw_church_organpuzzle, room_test_pianoGimmick`

### Party record 1642

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 724; if (set_party)`
- status: `debug`
- rooms: `room_debug_pianotest, room_dw_church_bellhall_central,`
  `room_dw_church_organpuzzle, room_test_pianoGimmick`

### Party record 1643

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_pianopuzzle`

### Party record 1644

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 6; if (global.plot >= 225 && global.plot < 230)`
- status: `production`
- rooms: `room_dw_church_b_intro`

### Party record 1645

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 24; if (global.plot < 195)`
- status: `production`
- rooms: `room_dw_church_knightclimb_post`

### Party record 1646

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 56; if (global.plot >= 240) > if (global.plot < 243)`
- status: `production`
- rooms: `room_dw_church_knightclimb_post`

### Party record 1647

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 68; if (global.flag[1658] == 1)`
- status: `production`
- rooms: `room_dw_church_knightclimb_post`

### Party record 1648

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 104; if (global.tempflag[58] == 1)`
- status: `production`
- rooms: `room_dw_church_knightclimb_post`

### Party record 1649

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 763; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_knightclimb_post`

### Party record 1650

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 11; if (con == 0)`
- status: `production`
- rooms: `room_dw_church_glass`

### Party record 1651

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_claw, room_dw_church_jackenstein`

### Party record 1652

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_holywatercooler`

### Party record 1653

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0`
- condition: `line 14; if (scr_debug())`
- status: `production`
- rooms: `room_lw_church_entrance`

### Party record 1654

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 184; unconditional in entry`
- status: `production`
- rooms: `room_lw_noellehouse_dess`

### Party record 1655

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 243; unconditional in entry`
- status: `production`
- rooms: `room_lw_noellehouse_dess`

### Party record 1656

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 343; if (con == 1)`
- status: `production`
- rooms: `room_lw_noellehouse_dess`

### Party record 1657

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 36; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_ripplepuzzle`

### Party record 1658

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 35; unconditional in entry`
- status: `production-subsystem`
- rooms: `room_dw_church_fountain`

### Party record 1659

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 136; unconditional in entry`
- status: `production`
- rooms: `room_lw_noellehouse_closet`

### Party record 1660

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 23; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_gersonchase`

### Party record 1661

- chapter: `4`
- phase: `global.char[target - 1]`
- field: `global.char[target - 1]`
- expression: `= 0) {     lasttarget = target`
- condition: `line 41; if (target <= 0 || target > 3) > if (global.hp[target]`
  `<= 0 || global.hp[target] != lasthp ||`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1662

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_pianopiece_left`

### Party record 1663

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1664

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 14; if (!i_ex(obj_caterpillarchara)) > if (!scr_havechar(2))`
- status: `production`
- rooms: `room_torhouse`

### Party record 1665

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 9; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_ripseq1`

### Party record 1666

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; unconditional in entry`
- status: `production`
- rooms: `room_dw_castle_rooms_ralsei`

### Party record 1667

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_tallbookcases`

### Party record 1668

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 31; if (global.char[i] != 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1669

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 40; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1670

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 49; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1671

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 58; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1672

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 30; if (con == 0)`
- status: `production`
- rooms: `room_town_noellehouse`

### Party record 1673

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 363; unconditional in entry`
- status: `production`
- rooms: `room_town_noellehouse`

### Party record 1674

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_mizzleencounter`

### Party record 1675

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `—`
- condition: `line 12; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_man`

### Party record 1676

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 21; if (keyboard_check(ord("P"))) > if`
  `(keyboard_check(ord("1")))`
- status: `legacy`
- rooms: `room_dw_churchb_rotatingtower, room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled`

### Party record 1677

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 30; if (keyboard_check(ord("2"))) > if (global.tempflag[90]`
  `== 0.1)`
- status: `legacy`
- rooms: `room_dw_churchb_rotatingtower, room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled`

### Party record 1678

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 37; if (global.plot < 238.5) > if (scr_debug())`
- status: `legacy`
- rooms: `room_dw_churchb_rotatingtower, room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled`

### Party record 1679

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 47; if (scr_debug()) > if (keyboard_check(ord("W")) &&`
  `keyboard_check_pressed(ord("1")))`
- status: `legacy`
- rooms: `room_dw_churchb_rotatingtower, room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled`

### Party record 1680

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 74; if (keyboard_check(ord("W")) &&`
  `keyboard_check_pressed(ord("2")))`
- status: `legacy`
- rooms: `room_dw_churchb_rotatingtower, room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled`

### Party record 1681

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 191; if (con == 1) > if`
  `(!instance_exists(obj_cutscene_master))`
- status: `legacy`
- rooms: `room_dw_churchb_rotatingtower, room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled`

### Party record 1682

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 2; unconditional in entry`
- status: `production`
- rooms: `room_dw_church_turtles`

### Party record 1683

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 24; else if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_knightclimb`

### Party record 1684

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 404; if (con == 4 && !i_ex(obj_cutscene_master))`
- status: `production`
- rooms: `room_dw_church_knightclimb`

### Party record 1685

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 8; if (scr_debug()) > if (keyboard_check(ord("P")))`
- status: `production`
- rooms: `room_dw_church_northprophecies`

### Party record 1686

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 44; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1687

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 7; if (global.plot >= 280 && global.plot < 290)`
- status: `production`
- rooms: `room_lw_church_main`

### Party record 1688

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 45; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1689

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 9; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_trueclimbadventure`

### Party record 1690

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 28; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchc_superprophecies`

### Party record 1691

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 30; if (global.plot < 170) > if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_bellhall_bookroom`

### Party record 1692

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 6; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_bookcase`

### Party record 1693

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_pianopiece_rightprophecy`

### Party record 1694

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 40; if (snd_is_playing(global.currentsong[1]))`
- status: `legacy`
- rooms: `room_dw_church_chase_old, room_dw_church_staircase`

### Party record 1695

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 233; if (con == 2 && customcon == 1 && !d_ex())`
- status: `legacy`
- rooms: `room_dw_church_chase_old, room_dw_church_staircase`

### Party record 1696

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"ralsei"`
- condition: `line 444; if (!scr_havechar("ralsei"))`
- status: `legacy`
- rooms: `room_dw_church_chase_old, room_dw_church_staircase`

### Party record 1697

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 9; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchc_angelprophecy`

### Party record 1698

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 17; if (keyboard_check(ord("P")))`
- status: `production`
- rooms: `room_dw_churchc_titanclimb1_post`

### Party record 1699

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 20; if (global.tempflag[90] == 1 ||`
  `keyboard_check(ord("2")))`
- status: `production`
- rooms: `room_dw_church_intro_guei`

### Party record 1700

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 27; if (keyboard_check(vk_shift))`
- status: `production`
- rooms: `room_dw_church_intro_guei`

### Party record 1701

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 15; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchc_encounter1`

### Party record 1702

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_darkclimb_scene`

### Party record 1703

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 15; if (global.plot < 108)`
- status: `production`
- rooms: `room_dw_church_intropiano`

### Party record 1704

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 19; if (global.plot < 108) > if (global.plot >= 120)`
- status: `production`
- rooms: `room_dw_church_intropiano`

### Party record 1705

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 35; if (global.char[i] != 4) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1706

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 39; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1707

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 c[i].sprite_index =`
  `spr_ralsei_battleintro`
- condition: `line 47; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1708

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 37; if (appearance == 1) > if (appearance == 1)`
- status: `debug`
- rooms: `room_dw_church_dogclimb, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_tiled, room_dw_churchc_titanclimb2,`
  `room_dw_churchc_titanclimb2_old, room_dw_churchc_titanclimb2_old2,`
  `room_dw_churchc_titanclimb2_tiled, room_rotating_tower_new_example,`
  `room_rotating_tower_new_test`

### Party record 1709

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 13; if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_churchb_fountain`

### Party record 1710

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 28; if (global.plot >= 225 && global.plot < 230)`
- status: `production-subsystem`
- rooms: `room_dw_churchb_fountain`

### Party record 1711

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 7; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_pianopiece_left_b`

### Party record 1712

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 64; if (global.flag[891] == 1 || global.flag[891] == -1) >`
  `if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_pianopiece_left_b`

### Party record 1713

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 7; if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_church_minorlegend`

### Party record 1714

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 17; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_darkclimb`

### Party record 1715

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 27; if (global.tempflag[90] == 1)`
- status: `production`
- rooms: `room_dw_churchb_darkclimb`

### Party record 1716

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 53; if (keyboard_check(ord("W")) || global.tempflag[90] == 4`
  `|| global.tempflag[90] == 3) > if`
  `(keyboard_check_pressed(ord("1")) || global.tempflag[90] == 3)`
- status: `production`
- rooms: `room_dw_churchb_darkclimb`

### Party record 1717

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 86; if (keyboard_check_pressed(ord("2")) ||`
  `global.tempflag[90] == 4)`
- status: `production`
- rooms: `room_dw_churchb_darkclimb`

### Party record 1718

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 381; unconditional in entry`
- status: `production`
- rooms: `room_dw_churchb_darkclimb`

### Party record 1719

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 29; if (con == 0)`
- status: `production`
- rooms: `room_town_noellehouse`

### Party record 1720

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 37; if (i_ex(obj_caterpillarchara))`
- status: `production`
- rooms: `room_town_noellehouse`

### Party record 1721

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 38; unconditional in entry`
- status: `production`
- rooms: `room_town_noellehouse`

### Party record 1722

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 168; if (con == 0 && !d_ex() && global.interact == 0) > if`
  `(!scr_havechar(2))`
- status: `production`
- rooms: `room_lw_church_main`

### Party record 1723

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 35; if (global.char[i] != 4) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1724

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 39; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1725

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 c[i].sprite_index =`
  `spr_ralsei_battleintro`
- condition: `line 47; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1726

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 54; if (global.char[i] != 0) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_dark_twostoryTest,`
  `room_DARKbase_GMS2, room_DARKempty, room_darkness_example,`
  `room_darkness_example_2, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_layeredLevelTest,`
  `room_debug_pianotest, room_debug_smallface_dark,`
  `room_debug_windowEffect, room_dw_3d_tower_test,`
  `room_dw_castle_area_1, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_dungeon, room_dw_castle_east_door,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_kris_susie, room_dw_castle_rooms_queen,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_rooms_tenna, room_dw_castle_town, room_dw_castle_tv,`
  `room_dw_castle_tv_rhythm, room_dw_castle_tv_zone_1,`
  `room_dw_castle_tv_zone_2, room_dw_castle_tv_zone_3,`
  `room_dw_castle_tv_zone_battle, room_dw_castle_tv_zone_minigame,`
  `room_dw_castle_west_cliff, room_dw_church_arena,`
  `room_dw_church_b_intro, room_dw_church_bellclimb,`
  `room_dw_church_bellhall_bookroom, room_dw_church_bellhall_central,`
  `room_dw_church_bellhall_curtain, room_dw_church_bellhall_east,`
  `room_dw_church_bellhall_west, room_dw_church_bellplay,`
  `room_dw_church_bellsareawest, room_dw_church_biblioxencounter,`
  `room_dw_church_bookcase, room_dw_church_bookenemywest,`
  `room_dw_church_bookshelfpuzzle, room_dw_church_bookshelfpuzzle_rev,`
  `room_dw_church_bookshelfpuzzle1, room_dw_church_bookshelfpuzzle2,`
  `room_dw_church_candlelighting, room_dw_church_candlesroom1,`
  `room_dw_church_chase_old, room_dw_church_claw,`
  `room_dw_church_climbtut, room_dw_church_crumbletower,`
  `room_dw_church_dark_fire_puzzle, room_dw_church_darkbell_old,`
  `room_dw_church_darkclimb, room_dw_church_darkmaze,`
  `room_dw_church_darkroom_old, room_dw_church_darkroom1_old,`
  `room_dw_church_dogclimb, room_dw_church_fastwater,`
  `room_dw_church_fountainconnection, room_dw_church_gersonstudy,`
  `room_dw_church_glass, room_dw_church_guei, room_dw_church_gueitest,`
  `room_dw_church_holywatercooler, room_dw_church_intro_gerson,`
  `room_dw_church_intro_guei, room_dw_church_intro1,`
  `room_dw_church_intro3, room_dw_church_intropiano,`
  `room_dw_church_jackenstein, room_dw_church_knightclimb,`
  `room_dw_church_knightclimb_post, room_dw_church_lantern_hallway,`
  `room_dw_church_lantern_hallway_old, room_dw_church_lantern1_old,`
  `room_dw_church_lantern1_old_old, room_dw_church_lantern2,`
  `room_dw_church_librarybookenemy, room_dw_church_minorlegend,`
  `room_dw_church_mizzleencounter, room_dw_church_moneyfountain,`
  `room_dw_church_northprophecies, room_dw_church_npcroom_pools1,`
  `room_dw_church_npcroom_shelfclimb, room_dw_church_nwconnect,`
  `room_dw_church_offering, room_dw_church_organpuzzle,`
  `room_dw_church_pianopiece_left, room_dw_church_pianopiece_left_b,`
  `room_dw_church_pianopiece_right,`
  `room_dw_church_pianopiece_rightprophecy, room_dw_church_pianopuzzle,`
  `room_dw_church_poolsroom1, room_dw_church_poolsroom1_east,`
  `room_dw_church_poolsroom2, room_dw_church_poolsroom2south,`
  `room_dw_church_quicktest, room_dw_church_rightconnect,`
  `room_dw_church_ripplepuzzle, room_dw_church_ripplepuzzle_postgers,`
  `room_dw_church_rippletest, room_dw_church_rippleworship,`
  `room_dw_church_ripseq1, room_dw_church_ripseq2,`
  `room_dw_church_savepoint, room_dw_church_secretpiano,`
  `room_dw_church_shadowgerson, room_dw_church_shelfclimb1,`
  `room_dw_church_shelfclimb2, room_dw_church_shiftclimb,`
  `room_dw_church_sideclimb, room_dw_church_slidingbookshelf,`
  `room_dw_church_smallbells, room_dw_church_solowaterfall,`
  `room_dw_church_stainedglasspreview, room_dw_church_staircase,`
  `room_dw_church_stairs_stainedglass, room_dw_church_stairs_topleft,`
  `room_dw_church_stairs_topright, room_dw_church_stairs_west_bell,`
  `room_dw_church_stairspreview, room_dw_church_statueclimb,`
  `room_dw_church_statueclimb_npcroom, room_dw_church_statueroom,`
  `room_dw_church_statueroom_old, room_dw_church_swingingbell,`
  `room_dw_church_tallbookcases, room_dw_church_tallbookcases_backup,`
  `room_dw_church_tower1, room_dw_church_trueclimbadventure,`
  `room_dw_church_turtles, room_dw_church_waterfallroom,`
  `room_dw_church_waterfalltearoom, room_dw_church_worshiproom,`
  `room_dw_churchb_bellroom, room_dw_churchb_bookshelf,`
  `room_dw_churchb_darkclimb, room_dw_churchb_darkclimb_scene,`
  `room_dw_churchb_escherstaircase, room_dw_churchb_extinguisher,`
  `room_dw_churchb_fireplace, room_dw_churchb_fountain,`
  `room_dw_churchb_gallery, room_dw_churchb_gersonchase,`
  `room_dw_churchb_gersonstudy, room_dw_churchb_library,`
  `room_dw_churchb_library_alternate, room_dw_churchb_libraryconnector,`
  `room_dw_churchb_man, room_dw_churchb_moneyfountain,`
  `room_dw_churchb_nongerson, room_dw_churchb_nongerson_post,`
  `room_dw_churchb_prophecyencounter, room_dw_churchb_prophecymaze,`
  `room_dw_churchb_prophecymaze_old, room_dw_churchb_ripple1,`
  `room_dw_churchb_ripplepost, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchb_savepoint, room_dw_churchb_staircaseintro,`
  `room_dw_churchb_windows, room_dw_churchb_worshiproom,`
  `room_dw_churchc_angelprophecy,`
  `room_dw_churchc_angelprophecy_encounter, room_dw_churchc_darkswords,`
  `room_dw_churchc_dodge, room_dw_churchc_encounter1,`
  `room_dw_churchc_encounter2, room_dw_churchc_final_prophecy,`
  `room_dw_churchc_finalclimb, room_dw_churchc_insidetitan,`
  `room_dw_churchc_prepretitan, room_dw_churchc_pretitan,`
  `room_dw_churchc_prophecies, room_dw_churchc_prophecies_backup,`
  `room_dw_churchc_ripplesneak_poc, room_dw_churchc_savepoint,`
  `room_dw_churchc_slidingpiano, room_dw_churchc_superprophecies,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_post, room_dw_churchc_titanclimb1_tiled,`
  `room_dw_churchc_titanclimb2, room_dw_churchc_titanclimb2_old,`
  `room_dw_churchc_titanclimb2_old2, room_dw_churchc_titanclimb2_post,`
  `room_dw_churchc_titanclimb2_tiled, room_dw_churchc_titandefeated,`
  `room_dw_churchc_treasurechest, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_front, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rotating_tower,`
  `room_dw_titan_tower_test, room_gersonbattleroomtest, room_GMS2_test,`
  `room_overworld_darkmaku_blocks, room_overworld_darkmaku_ring,`
  `room_overworld_darkmakumaze, room_overworldBulletEnemyTest,`
  `room_overworldDarknessBulletTest, room_ripple_test,`
  `room_rotating_tower_new_example, room_rotating_tower_new_test,`
  `room_shapetest, room_test_climb_0001, room_test_climb_cameratest,`
  `room_test_climb_enterexit, room_test_climb_new, room_test_climb_new2,`
  `room_test_pianoGimmick, room_test_remotePiano`

### Party record 1727

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 59; if (global.char[i] == 1) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_dark_twostoryTest,`
  `room_DARKbase_GMS2, room_DARKempty, room_darkness_example,`
  `room_darkness_example_2, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_layeredLevelTest,`
  `room_debug_pianotest, room_debug_smallface_dark,`
  `room_debug_windowEffect, room_dw_3d_tower_test,`
  `room_dw_castle_area_1, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_dungeon, room_dw_castle_east_door,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_kris_susie, room_dw_castle_rooms_queen,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_rooms_tenna, room_dw_castle_town, room_dw_castle_tv,`
  `room_dw_castle_tv_rhythm, room_dw_castle_tv_zone_1,`
  `room_dw_castle_tv_zone_2, room_dw_castle_tv_zone_3,`
  `room_dw_castle_tv_zone_battle, room_dw_castle_tv_zone_minigame,`
  `room_dw_castle_west_cliff, room_dw_church_arena,`
  `room_dw_church_b_intro, room_dw_church_bellclimb,`
  `room_dw_church_bellhall_bookroom, room_dw_church_bellhall_central,`
  `room_dw_church_bellhall_curtain, room_dw_church_bellhall_east,`
  `room_dw_church_bellhall_west, room_dw_church_bellplay,`
  `room_dw_church_bellsareawest, room_dw_church_biblioxencounter,`
  `room_dw_church_bookcase, room_dw_church_bookenemywest,`
  `room_dw_church_bookshelfpuzzle, room_dw_church_bookshelfpuzzle_rev,`
  `room_dw_church_bookshelfpuzzle1, room_dw_church_bookshelfpuzzle2,`
  `room_dw_church_candlelighting, room_dw_church_candlesroom1,`
  `room_dw_church_chase_old, room_dw_church_claw,`
  `room_dw_church_climbtut, room_dw_church_crumbletower,`
  `room_dw_church_dark_fire_puzzle, room_dw_church_darkbell_old,`
  `room_dw_church_darkclimb, room_dw_church_darkmaze,`
  `room_dw_church_darkroom_old, room_dw_church_darkroom1_old,`
  `room_dw_church_dogclimb, room_dw_church_fastwater,`
  `room_dw_church_fountainconnection, room_dw_church_gersonstudy,`
  `room_dw_church_glass, room_dw_church_guei, room_dw_church_gueitest,`
  `room_dw_church_holywatercooler, room_dw_church_intro_gerson,`
  `room_dw_church_intro_guei, room_dw_church_intro1,`
  `room_dw_church_intro3, room_dw_church_intropiano,`
  `room_dw_church_jackenstein, room_dw_church_knightclimb,`
  `room_dw_church_knightclimb_post, room_dw_church_lantern_hallway,`
  `room_dw_church_lantern_hallway_old, room_dw_church_lantern1_old,`
  `room_dw_church_lantern1_old_old, room_dw_church_lantern2,`
  `room_dw_church_librarybookenemy, room_dw_church_minorlegend,`
  `room_dw_church_mizzleencounter, room_dw_church_moneyfountain,`
  `room_dw_church_northprophecies, room_dw_church_npcroom_pools1,`
  `room_dw_church_npcroom_shelfclimb, room_dw_church_nwconnect,`
  `room_dw_church_offering, room_dw_church_organpuzzle,`
  `room_dw_church_pianopiece_left, room_dw_church_pianopiece_left_b,`
  `room_dw_church_pianopiece_right,`
  `room_dw_church_pianopiece_rightprophecy, room_dw_church_pianopuzzle,`
  `room_dw_church_poolsroom1, room_dw_church_poolsroom1_east,`
  `room_dw_church_poolsroom2, room_dw_church_poolsroom2south,`
  `room_dw_church_quicktest, room_dw_church_rightconnect,`
  `room_dw_church_ripplepuzzle, room_dw_church_ripplepuzzle_postgers,`
  `room_dw_church_rippletest, room_dw_church_rippleworship,`
  `room_dw_church_ripseq1, room_dw_church_ripseq2,`
  `room_dw_church_savepoint, room_dw_church_secretpiano,`
  `room_dw_church_shadowgerson, room_dw_church_shelfclimb1,`
  `room_dw_church_shelfclimb2, room_dw_church_shiftclimb,`
  `room_dw_church_sideclimb, room_dw_church_slidingbookshelf,`
  `room_dw_church_smallbells, room_dw_church_solowaterfall,`
  `room_dw_church_stainedglasspreview, room_dw_church_staircase,`
  `room_dw_church_stairs_stainedglass, room_dw_church_stairs_topleft,`
  `room_dw_church_stairs_topright, room_dw_church_stairs_west_bell,`
  `room_dw_church_stairspreview, room_dw_church_statueclimb,`
  `room_dw_church_statueclimb_npcroom, room_dw_church_statueroom,`
  `room_dw_church_statueroom_old, room_dw_church_swingingbell,`
  `room_dw_church_tallbookcases, room_dw_church_tallbookcases_backup,`
  `room_dw_church_tower1, room_dw_church_trueclimbadventure,`
  `room_dw_church_turtles, room_dw_church_waterfallroom,`
  `room_dw_church_waterfalltearoom, room_dw_church_worshiproom,`
  `room_dw_churchb_bellroom, room_dw_churchb_bookshelf,`
  `room_dw_churchb_darkclimb, room_dw_churchb_darkclimb_scene,`
  `room_dw_churchb_escherstaircase, room_dw_churchb_extinguisher,`
  `room_dw_churchb_fireplace, room_dw_churchb_fountain,`
  `room_dw_churchb_gallery, room_dw_churchb_gersonchase,`
  `room_dw_churchb_gersonstudy, room_dw_churchb_library,`
  `room_dw_churchb_library_alternate, room_dw_churchb_libraryconnector,`
  `room_dw_churchb_man, room_dw_churchb_moneyfountain,`
  `room_dw_churchb_nongerson, room_dw_churchb_nongerson_post,`
  `room_dw_churchb_prophecyencounter, room_dw_churchb_prophecymaze,`
  `room_dw_churchb_prophecymaze_old, room_dw_churchb_ripple1,`
  `room_dw_churchb_ripplepost, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchb_savepoint, room_dw_churchb_staircaseintro,`
  `room_dw_churchb_windows, room_dw_churchb_worshiproom,`
  `room_dw_churchc_angelprophecy,`
  `room_dw_churchc_angelprophecy_encounter, room_dw_churchc_darkswords,`
  `room_dw_churchc_dodge, room_dw_churchc_encounter1,`
  `room_dw_churchc_encounter2, room_dw_churchc_final_prophecy,`
  `room_dw_churchc_finalclimb, room_dw_churchc_insidetitan,`
  `room_dw_churchc_prepretitan, room_dw_churchc_pretitan,`
  `room_dw_churchc_prophecies, room_dw_churchc_prophecies_backup,`
  `room_dw_churchc_ripplesneak_poc, room_dw_churchc_savepoint,`
  `room_dw_churchc_slidingpiano, room_dw_churchc_superprophecies,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_post, room_dw_churchc_titanclimb1_tiled,`
  `room_dw_churchc_titanclimb2, room_dw_churchc_titanclimb2_old,`
  `room_dw_churchc_titanclimb2_old2, room_dw_churchc_titanclimb2_post,`
  `room_dw_churchc_titanclimb2_tiled, room_dw_churchc_titandefeated,`
  `room_dw_churchc_treasurechest, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_front, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rotating_tower,`
  `room_dw_titan_tower_test, room_gersonbattleroomtest, room_GMS2_test,`
  `room_overworld_darkmaku_blocks, room_overworld_darkmaku_ring,`
  `room_overworld_darkmakumaze, room_overworldBulletEnemyTest,`
  `room_overworldDarknessBulletTest, room_ripple_test,`
  `room_rotating_tower_new_example, room_rotating_tower_new_test,`
  `room_shapetest, room_test_climb_0001, room_test_climb_cameratest,`
  `room_test_climb_enterexit, room_test_climb_new, room_test_climb_new2,`
  `room_test_pianoGimmick, room_test_remotePiano`

### Party record 1728

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 69; if (i > 0) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_dark_twostoryTest,`
  `room_DARKbase_GMS2, room_DARKempty, room_darkness_example,`
  `room_darkness_example_2, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_layeredLevelTest,`
  `room_debug_pianotest, room_debug_smallface_dark,`
  `room_debug_windowEffect, room_dw_3d_tower_test,`
  `room_dw_castle_area_1, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_dungeon, room_dw_castle_east_door,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_kris_susie, room_dw_castle_rooms_queen,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_rooms_tenna, room_dw_castle_town, room_dw_castle_tv,`
  `room_dw_castle_tv_rhythm, room_dw_castle_tv_zone_1,`
  `room_dw_castle_tv_zone_2, room_dw_castle_tv_zone_3,`
  `room_dw_castle_tv_zone_battle, room_dw_castle_tv_zone_minigame,`
  `room_dw_castle_west_cliff, room_dw_church_arena,`
  `room_dw_church_b_intro, room_dw_church_bellclimb,`
  `room_dw_church_bellhall_bookroom, room_dw_church_bellhall_central,`
  `room_dw_church_bellhall_curtain, room_dw_church_bellhall_east,`
  `room_dw_church_bellhall_west, room_dw_church_bellplay,`
  `room_dw_church_bellsareawest, room_dw_church_biblioxencounter,`
  `room_dw_church_bookcase, room_dw_church_bookenemywest,`
  `room_dw_church_bookshelfpuzzle, room_dw_church_bookshelfpuzzle_rev,`
  `room_dw_church_bookshelfpuzzle1, room_dw_church_bookshelfpuzzle2,`
  `room_dw_church_candlelighting, room_dw_church_candlesroom1,`
  `room_dw_church_chase_old, room_dw_church_claw,`
  `room_dw_church_climbtut, room_dw_church_crumbletower,`
  `room_dw_church_dark_fire_puzzle, room_dw_church_darkbell_old,`
  `room_dw_church_darkclimb, room_dw_church_darkmaze,`
  `room_dw_church_darkroom_old, room_dw_church_darkroom1_old,`
  `room_dw_church_dogclimb, room_dw_church_fastwater,`
  `room_dw_church_fountainconnection, room_dw_church_gersonstudy,`
  `room_dw_church_glass, room_dw_church_guei, room_dw_church_gueitest,`
  `room_dw_church_holywatercooler, room_dw_church_intro_gerson,`
  `room_dw_church_intro_guei, room_dw_church_intro1,`
  `room_dw_church_intro3, room_dw_church_intropiano,`
  `room_dw_church_jackenstein, room_dw_church_knightclimb,`
  `room_dw_church_knightclimb_post, room_dw_church_lantern_hallway,`
  `room_dw_church_lantern_hallway_old, room_dw_church_lantern1_old,`
  `room_dw_church_lantern1_old_old, room_dw_church_lantern2,`
  `room_dw_church_librarybookenemy, room_dw_church_minorlegend,`
  `room_dw_church_mizzleencounter, room_dw_church_moneyfountain,`
  `room_dw_church_northprophecies, room_dw_church_npcroom_pools1,`
  `room_dw_church_npcroom_shelfclimb, room_dw_church_nwconnect,`
  `room_dw_church_offering, room_dw_church_organpuzzle,`
  `room_dw_church_pianopiece_left, room_dw_church_pianopiece_left_b,`
  `room_dw_church_pianopiece_right,`
  `room_dw_church_pianopiece_rightprophecy, room_dw_church_pianopuzzle,`
  `room_dw_church_poolsroom1, room_dw_church_poolsroom1_east,`
  `room_dw_church_poolsroom2, room_dw_church_poolsroom2south,`
  `room_dw_church_quicktest, room_dw_church_rightconnect,`
  `room_dw_church_ripplepuzzle, room_dw_church_ripplepuzzle_postgers,`
  `room_dw_church_rippletest, room_dw_church_rippleworship,`
  `room_dw_church_ripseq1, room_dw_church_ripseq2,`
  `room_dw_church_savepoint, room_dw_church_secretpiano,`
  `room_dw_church_shadowgerson, room_dw_church_shelfclimb1,`
  `room_dw_church_shelfclimb2, room_dw_church_shiftclimb,`
  `room_dw_church_sideclimb, room_dw_church_slidingbookshelf,`
  `room_dw_church_smallbells, room_dw_church_solowaterfall,`
  `room_dw_church_stainedglasspreview, room_dw_church_staircase,`
  `room_dw_church_stairs_stainedglass, room_dw_church_stairs_topleft,`
  `room_dw_church_stairs_topright, room_dw_church_stairs_west_bell,`
  `room_dw_church_stairspreview, room_dw_church_statueclimb,`
  `room_dw_church_statueclimb_npcroom, room_dw_church_statueroom,`
  `room_dw_church_statueroom_old, room_dw_church_swingingbell,`
  `room_dw_church_tallbookcases, room_dw_church_tallbookcases_backup,`
  `room_dw_church_tower1, room_dw_church_trueclimbadventure,`
  `room_dw_church_turtles, room_dw_church_waterfallroom,`
  `room_dw_church_waterfalltearoom, room_dw_church_worshiproom,`
  `room_dw_churchb_bellroom, room_dw_churchb_bookshelf,`
  `room_dw_churchb_darkclimb, room_dw_churchb_darkclimb_scene,`
  `room_dw_churchb_escherstaircase, room_dw_churchb_extinguisher,`
  `room_dw_churchb_fireplace, room_dw_churchb_fountain,`
  `room_dw_churchb_gallery, room_dw_churchb_gersonchase,`
  `room_dw_churchb_gersonstudy, room_dw_churchb_library,`
  `room_dw_churchb_library_alternate, room_dw_churchb_libraryconnector,`
  `room_dw_churchb_man, room_dw_churchb_moneyfountain,`
  `room_dw_churchb_nongerson, room_dw_churchb_nongerson_post,`
  `room_dw_churchb_prophecyencounter, room_dw_churchb_prophecymaze,`
  `room_dw_churchb_prophecymaze_old, room_dw_churchb_ripple1,`
  `room_dw_churchb_ripplepost, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchb_savepoint, room_dw_churchb_staircaseintro,`
  `room_dw_churchb_windows, room_dw_churchb_worshiproom,`
  `room_dw_churchc_angelprophecy,`
  `room_dw_churchc_angelprophecy_encounter, room_dw_churchc_darkswords,`
  `room_dw_churchc_dodge, room_dw_churchc_encounter1,`
  `room_dw_churchc_encounter2, room_dw_churchc_final_prophecy,`
  `room_dw_churchc_finalclimb, room_dw_churchc_insidetitan,`
  `room_dw_churchc_prepretitan, room_dw_churchc_pretitan,`
  `room_dw_churchc_prophecies, room_dw_churchc_prophecies_backup,`
  `room_dw_churchc_ripplesneak_poc, room_dw_churchc_savepoint,`
  `room_dw_churchc_slidingpiano, room_dw_churchc_superprophecies,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_post, room_dw_churchc_titanclimb1_tiled,`
  `room_dw_churchc_titanclimb2, room_dw_churchc_titanclimb2_old,`
  `room_dw_churchc_titanclimb2_old2, room_dw_churchc_titanclimb2_post,`
  `room_dw_churchc_titanclimb2_tiled, room_dw_churchc_titandefeated,`
  `room_dw_churchc_treasurechest, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_front, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rotating_tower,`
  `room_dw_titan_tower_test, room_gersonbattleroomtest, room_GMS2_test,`
  `room_overworld_darkmaku_blocks, room_overworld_darkmaku_ring,`
  `room_overworld_darkmakumaze, room_overworldBulletEnemyTest,`
  `room_overworldDarknessBulletTest, room_ripple_test,`
  `room_rotating_tower_new_example, room_rotating_tower_new_test,`
  `room_shapetest, room_test_climb_0001, room_test_climb_cameratest,`
  `room_test_climb_enterexit, room_test_climb_new, room_test_climb_new2,`
  `room_test_pianoGimmick, room_test_remotePiano`

### Party record 1729

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 98; if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_dark_twostoryTest,`
  `room_DARKbase_GMS2, room_DARKempty, room_darkness_example,`
  `room_darkness_example_2, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_layeredLevelTest,`
  `room_debug_pianotest, room_debug_smallface_dark,`
  `room_debug_windowEffect, room_dw_3d_tower_test,`
  `room_dw_castle_area_1, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_dungeon, room_dw_castle_east_door,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_kris_susie, room_dw_castle_rooms_queen,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_rooms_tenna, room_dw_castle_town, room_dw_castle_tv,`
  `room_dw_castle_tv_rhythm, room_dw_castle_tv_zone_1,`
  `room_dw_castle_tv_zone_2, room_dw_castle_tv_zone_3,`
  `room_dw_castle_tv_zone_battle, room_dw_castle_tv_zone_minigame,`
  `room_dw_castle_west_cliff, room_dw_church_arena,`
  `room_dw_church_b_intro, room_dw_church_bellclimb,`
  `room_dw_church_bellhall_bookroom, room_dw_church_bellhall_central,`
  `room_dw_church_bellhall_curtain, room_dw_church_bellhall_east,`
  `room_dw_church_bellhall_west, room_dw_church_bellplay,`
  `room_dw_church_bellsareawest, room_dw_church_biblioxencounter,`
  `room_dw_church_bookcase, room_dw_church_bookenemywest,`
  `room_dw_church_bookshelfpuzzle, room_dw_church_bookshelfpuzzle_rev,`
  `room_dw_church_bookshelfpuzzle1, room_dw_church_bookshelfpuzzle2,`
  `room_dw_church_candlelighting, room_dw_church_candlesroom1,`
  `room_dw_church_chase_old, room_dw_church_claw,`
  `room_dw_church_climbtut, room_dw_church_crumbletower,`
  `room_dw_church_dark_fire_puzzle, room_dw_church_darkbell_old,`
  `room_dw_church_darkclimb, room_dw_church_darkmaze,`
  `room_dw_church_darkroom_old, room_dw_church_darkroom1_old,`
  `room_dw_church_dogclimb, room_dw_church_fastwater,`
  `room_dw_church_fountainconnection, room_dw_church_gersonstudy,`
  `room_dw_church_glass, room_dw_church_guei, room_dw_church_gueitest,`
  `room_dw_church_holywatercooler, room_dw_church_intro_gerson,`
  `room_dw_church_intro_guei, room_dw_church_intro1,`
  `room_dw_church_intro3, room_dw_church_intropiano,`
  `room_dw_church_jackenstein, room_dw_church_knightclimb,`
  `room_dw_church_knightclimb_post, room_dw_church_lantern_hallway,`
  `room_dw_church_lantern_hallway_old, room_dw_church_lantern1_old,`
  `room_dw_church_lantern1_old_old, room_dw_church_lantern2,`
  `room_dw_church_librarybookenemy, room_dw_church_minorlegend,`
  `room_dw_church_mizzleencounter, room_dw_church_moneyfountain,`
  `room_dw_church_northprophecies, room_dw_church_npcroom_pools1,`
  `room_dw_church_npcroom_shelfclimb, room_dw_church_nwconnect,`
  `room_dw_church_offering, room_dw_church_organpuzzle,`
  `room_dw_church_pianopiece_left, room_dw_church_pianopiece_left_b,`
  `room_dw_church_pianopiece_right,`
  `room_dw_church_pianopiece_rightprophecy, room_dw_church_pianopuzzle,`
  `room_dw_church_poolsroom1, room_dw_church_poolsroom1_east,`
  `room_dw_church_poolsroom2, room_dw_church_poolsroom2south,`
  `room_dw_church_quicktest, room_dw_church_rightconnect,`
  `room_dw_church_ripplepuzzle, room_dw_church_ripplepuzzle_postgers,`
  `room_dw_church_rippletest, room_dw_church_rippleworship,`
  `room_dw_church_ripseq1, room_dw_church_ripseq2,`
  `room_dw_church_savepoint, room_dw_church_secretpiano,`
  `room_dw_church_shadowgerson, room_dw_church_shelfclimb1,`
  `room_dw_church_shelfclimb2, room_dw_church_shiftclimb,`
  `room_dw_church_sideclimb, room_dw_church_slidingbookshelf,`
  `room_dw_church_smallbells, room_dw_church_solowaterfall,`
  `room_dw_church_stainedglasspreview, room_dw_church_staircase,`
  `room_dw_church_stairs_stainedglass, room_dw_church_stairs_topleft,`
  `room_dw_church_stairs_topright, room_dw_church_stairs_west_bell,`
  `room_dw_church_stairspreview, room_dw_church_statueclimb,`
  `room_dw_church_statueclimb_npcroom, room_dw_church_statueroom,`
  `room_dw_church_statueroom_old, room_dw_church_swingingbell,`
  `room_dw_church_tallbookcases, room_dw_church_tallbookcases_backup,`
  `room_dw_church_tower1, room_dw_church_trueclimbadventure,`
  `room_dw_church_turtles, room_dw_church_waterfallroom,`
  `room_dw_church_waterfalltearoom, room_dw_church_worshiproom,`
  `room_dw_churchb_bellroom, room_dw_churchb_bookshelf,`
  `room_dw_churchb_darkclimb, room_dw_churchb_darkclimb_scene,`
  `room_dw_churchb_escherstaircase, room_dw_churchb_extinguisher,`
  `room_dw_churchb_fireplace, room_dw_churchb_fountain,`
  `room_dw_churchb_gallery, room_dw_churchb_gersonchase,`
  `room_dw_churchb_gersonstudy, room_dw_churchb_library,`
  `room_dw_churchb_library_alternate, room_dw_churchb_libraryconnector,`
  `room_dw_churchb_man, room_dw_churchb_moneyfountain,`
  `room_dw_churchb_nongerson, room_dw_churchb_nongerson_post,`
  `room_dw_churchb_prophecyencounter, room_dw_churchb_prophecymaze,`
  `room_dw_churchb_prophecymaze_old, room_dw_churchb_ripple1,`
  `room_dw_churchb_ripplepost, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchb_savepoint, room_dw_churchb_staircaseintro,`
  `room_dw_churchb_windows, room_dw_churchb_worshiproom,`
  `room_dw_churchc_angelprophecy,`
  `room_dw_churchc_angelprophecy_encounter, room_dw_churchc_darkswords,`
  `room_dw_churchc_dodge, room_dw_churchc_encounter1,`
  `room_dw_churchc_encounter2, room_dw_churchc_final_prophecy,`
  `room_dw_churchc_finalclimb, room_dw_churchc_insidetitan,`
  `room_dw_churchc_prepretitan, room_dw_churchc_pretitan,`
  `room_dw_churchc_prophecies, room_dw_churchc_prophecies_backup,`
  `room_dw_churchc_ripplesneak_poc, room_dw_churchc_savepoint,`
  `room_dw_churchc_slidingpiano, room_dw_churchc_superprophecies,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_post, room_dw_churchc_titanclimb1_tiled,`
  `room_dw_churchc_titanclimb2, room_dw_churchc_titanclimb2_old,`
  `room_dw_churchc_titanclimb2_old2, room_dw_churchc_titanclimb2_post,`
  `room_dw_churchc_titanclimb2_tiled, room_dw_churchc_titandefeated,`
  `room_dw_churchc_treasurechest, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_front, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rotating_tower,`
  `room_dw_titan_tower_test, room_gersonbattleroomtest, room_GMS2_test,`
  `room_overworld_darkmaku_blocks, room_overworld_darkmaku_ring,`
  `room_overworld_darkmakumaze, room_overworldBulletEnemyTest,`
  `room_overworldDarknessBulletTest, room_ripple_test,`
  `room_rotating_tower_new_example, room_rotating_tower_new_test,`
  `room_shapetest, room_test_climb_0001, room_test_climb_cameratest,`
  `room_test_climb_enterexit, room_test_climb_new, room_test_climb_new2,`
  `room_test_pianoGimmick, room_test_remotePiano`

### Party record 1730

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3 || global.char[1] == 3)                 {`
  `global.interact = 1`
- condition: `line 143; if (throwitem == 4) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_dark_twostoryTest,`
  `room_DARKbase_GMS2, room_DARKempty, room_darkness_example,`
  `room_darkness_example_2, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_layeredLevelTest,`
  `room_debug_pianotest, room_debug_smallface_dark,`
  `room_debug_windowEffect, room_dw_3d_tower_test,`
  `room_dw_castle_area_1, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_dungeon, room_dw_castle_east_door,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_kris_susie, room_dw_castle_rooms_queen,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_rooms_tenna, room_dw_castle_town, room_dw_castle_tv,`
  `room_dw_castle_tv_rhythm, room_dw_castle_tv_zone_1,`
  `room_dw_castle_tv_zone_2, room_dw_castle_tv_zone_3,`
  `room_dw_castle_tv_zone_battle, room_dw_castle_tv_zone_minigame,`
  `room_dw_castle_west_cliff, room_dw_church_arena,`
  `room_dw_church_b_intro, room_dw_church_bellclimb,`
  `room_dw_church_bellhall_bookroom, room_dw_church_bellhall_central,`
  `room_dw_church_bellhall_curtain, room_dw_church_bellhall_east,`
  `room_dw_church_bellhall_west, room_dw_church_bellplay,`
  `room_dw_church_bellsareawest, room_dw_church_biblioxencounter,`
  `room_dw_church_bookcase, room_dw_church_bookenemywest,`
  `room_dw_church_bookshelfpuzzle, room_dw_church_bookshelfpuzzle_rev,`
  `room_dw_church_bookshelfpuzzle1, room_dw_church_bookshelfpuzzle2,`
  `room_dw_church_candlelighting, room_dw_church_candlesroom1,`
  `room_dw_church_chase_old, room_dw_church_claw,`
  `room_dw_church_climbtut, room_dw_church_crumbletower,`
  `room_dw_church_dark_fire_puzzle, room_dw_church_darkbell_old,`
  `room_dw_church_darkclimb, room_dw_church_darkmaze,`
  `room_dw_church_darkroom_old, room_dw_church_darkroom1_old,`
  `room_dw_church_dogclimb, room_dw_church_fastwater,`
  `room_dw_church_fountainconnection, room_dw_church_gersonstudy,`
  `room_dw_church_glass, room_dw_church_guei, room_dw_church_gueitest,`
  `room_dw_church_holywatercooler, room_dw_church_intro_gerson,`
  `room_dw_church_intro_guei, room_dw_church_intro1,`
  `room_dw_church_intro3, room_dw_church_intropiano,`
  `room_dw_church_jackenstein, room_dw_church_knightclimb,`
  `room_dw_church_knightclimb_post, room_dw_church_lantern_hallway,`
  `room_dw_church_lantern_hallway_old, room_dw_church_lantern1_old,`
  `room_dw_church_lantern1_old_old, room_dw_church_lantern2,`
  `room_dw_church_librarybookenemy, room_dw_church_minorlegend,`
  `room_dw_church_mizzleencounter, room_dw_church_moneyfountain,`
  `room_dw_church_northprophecies, room_dw_church_npcroom_pools1,`
  `room_dw_church_npcroom_shelfclimb, room_dw_church_nwconnect,`
  `room_dw_church_offering, room_dw_church_organpuzzle,`
  `room_dw_church_pianopiece_left, room_dw_church_pianopiece_left_b,`
  `room_dw_church_pianopiece_right,`
  `room_dw_church_pianopiece_rightprophecy, room_dw_church_pianopuzzle,`
  `room_dw_church_poolsroom1, room_dw_church_poolsroom1_east,`
  `room_dw_church_poolsroom2, room_dw_church_poolsroom2south,`
  `room_dw_church_quicktest, room_dw_church_rightconnect,`
  `room_dw_church_ripplepuzzle, room_dw_church_ripplepuzzle_postgers,`
  `room_dw_church_rippletest, room_dw_church_rippleworship,`
  `room_dw_church_ripseq1, room_dw_church_ripseq2,`
  `room_dw_church_savepoint, room_dw_church_secretpiano,`
  `room_dw_church_shadowgerson, room_dw_church_shelfclimb1,`
  `room_dw_church_shelfclimb2, room_dw_church_shiftclimb,`
  `room_dw_church_sideclimb, room_dw_church_slidingbookshelf,`
  `room_dw_church_smallbells, room_dw_church_solowaterfall,`
  `room_dw_church_stainedglasspreview, room_dw_church_staircase,`
  `room_dw_church_stairs_stainedglass, room_dw_church_stairs_topleft,`
  `room_dw_church_stairs_topright, room_dw_church_stairs_west_bell,`
  `room_dw_church_stairspreview, room_dw_church_statueclimb,`
  `room_dw_church_statueclimb_npcroom, room_dw_church_statueroom,`
  `room_dw_church_statueroom_old, room_dw_church_swingingbell,`
  `room_dw_church_tallbookcases, room_dw_church_tallbookcases_backup,`
  `room_dw_church_tower1, room_dw_church_trueclimbadventure,`
  `room_dw_church_turtles, room_dw_church_waterfallroom,`
  `room_dw_church_waterfalltearoom, room_dw_church_worshiproom,`
  `room_dw_churchb_bellroom, room_dw_churchb_bookshelf,`
  `room_dw_churchb_darkclimb, room_dw_churchb_darkclimb_scene,`
  `room_dw_churchb_escherstaircase, room_dw_churchb_extinguisher,`
  `room_dw_churchb_fireplace, room_dw_churchb_fountain,`
  `room_dw_churchb_gallery, room_dw_churchb_gersonchase,`
  `room_dw_churchb_gersonstudy, room_dw_churchb_library,`
  `room_dw_churchb_library_alternate, room_dw_churchb_libraryconnector,`
  `room_dw_churchb_man, room_dw_churchb_moneyfountain,`
  `room_dw_churchb_nongerson, room_dw_churchb_nongerson_post,`
  `room_dw_churchb_prophecyencounter, room_dw_churchb_prophecymaze,`
  `room_dw_churchb_prophecymaze_old, room_dw_churchb_ripple1,`
  `room_dw_churchb_ripplepost, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchb_savepoint, room_dw_churchb_staircaseintro,`
  `room_dw_churchb_windows, room_dw_churchb_worshiproom,`
  `room_dw_churchc_angelprophecy,`
  `room_dw_churchc_angelprophecy_encounter, room_dw_churchc_darkswords,`
  `room_dw_churchc_dodge, room_dw_churchc_encounter1,`
  `room_dw_churchc_encounter2, room_dw_churchc_final_prophecy,`
  `room_dw_churchc_finalclimb, room_dw_churchc_insidetitan,`
  `room_dw_churchc_prepretitan, room_dw_churchc_pretitan,`
  `room_dw_churchc_prophecies, room_dw_churchc_prophecies_backup,`
  `room_dw_churchc_ripplesneak_poc, room_dw_churchc_savepoint,`
  `room_dw_churchc_slidingpiano, room_dw_churchc_superprophecies,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_post, room_dw_churchc_titanclimb1_tiled,`
  `room_dw_churchc_titanclimb2, room_dw_churchc_titanclimb2_old,`
  `room_dw_churchc_titanclimb2_old2, room_dw_churchc_titanclimb2_post,`
  `room_dw_churchc_titanclimb2_tiled, room_dw_churchc_titandefeated,`
  `room_dw_churchc_treasurechest, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_front, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rotating_tower,`
  `room_dw_titan_tower_test, room_gersonbattleroomtest, room_GMS2_test,`
  `room_overworld_darkmaku_blocks, room_overworld_darkmaku_ring,`
  `room_overworld_darkmakumaze, room_overworldBulletEnemyTest,`
  `room_overworldDarknessBulletTest, room_ripple_test,`
  `room_rotating_tower_new_example, room_rotating_tower_new_test,`
  `room_shapetest, room_test_climb_0001, room_test_climb_cameratest,`
  `room_test_climb_enterexit, room_test_climb_new, room_test_climb_new2,`
  `room_test_pianoGimmick, room_test_remotePiano`

### Party record 1731

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         myx[i] += 15`
- condition: `line 23; if (i_ex(global.charinstance[i])) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1732

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         myx[i] += 15`
- condition: `line 27; if (global.char[i] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1733

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 || global.char[1] == 2 || global.char[2] == 2)     {`
  `sus = 0`
- condition: `line 245; if (global.charauto[2] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1734

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)         {             sus = 1`
- condition: `line 248; if (global.char[0] == 2 || global.char[1] == 2 ||`
  `global.char[2] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1735

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)         {             sus = 2`
- condition: `line 252; if (global.char[1] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1736

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `2`
- condition: `line 66; if (global.chapter == 4 && (global.encounterno == 160 ||`
  `global.encounterno == 176))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1737

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 67; if (global.chapter == 4 && (global.encounterno == 160 ||`
  `global.encounterno == 176))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1738

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 68; if (global.chapter == 4 && (global.encounterno == 160 ||`
  `global.encounterno == 176))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1739

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 73; if (global.chapter == 4 && global.encounterno == 186)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1740

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `2`
- condition: `line 74; if (global.chapter == 4 && global.encounterno == 186)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1741

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 75; if (global.chapter == 4 && global.encounterno == 186)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1742

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 221; if (global.char[i] != 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1743

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 230; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1744

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 239; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1745

- chapter: `4`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 248; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1746

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             if`
  `(global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoor...`
  `== 2 ||`
  `global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoord...`
  `== 4)             {                 if (havechar[1] == 0 ||`
  `global.hp[2] <= 0)                 {`
  `canpress = 0`
- condition: `line 889; if (cango == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1747

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)                     {                         for (var i =`
  `0`
- condition: `line 1152; if (global.bmenuno == 11) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1748

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         for (var i =`
  `0`
- condition: `line 1165; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1749

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         for (var i =`
  `0`
- condition: `line 1178; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1750

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         for (var i =`
  `0`
- condition: `line 1191; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1751

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         __actname =`
  `global.actnamesus[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 216; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1752

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         __actname =`
  `global.actnameral[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 220; if (global.char[global.charturn] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1753

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         __actname =`
  `global.actnamenoe[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 224; if (global.char[global.charturn] == 3) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1754

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[thisenemy][__acti]`
- condition: `line 483; if (global.bmenuno == 9 && global.myfight == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1755

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[thisenemy][__acti]`
- condition: `line 491; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1756

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[thisenemy][__acti]`
- condition: `line 499; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1757

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[thisenemy][__acti]`
- condition: `line 507; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1758

- chapter: `4`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             chartime =`
  `global.actactor[global.bmenucoord[11][global.charturn]][i]`
- condition: `line 537; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1759

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; ﻿if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_savepoint`

### Party record 1760

- chapter: `4`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1761

- chapter: `4`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `2`
- condition: `line 5; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1762

- chapter: `4`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1763

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 928; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1764

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 929; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1765

- chapter: `4`
- phase: `global.char[dx]`
- field: `global.char[dx]`
- expression: `= 2)                 {                     if`
  `(global.charcond[dx] != 5)                     {`
  `global.charcond[dx] = 5`
- condition: `line 245; if (scr_monsterpop() > 1 && scr_havechar(2)) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1766

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 8; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_savepoint`

### Party record 1767

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_church_moneyfountain`

### Party record 1768

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 51; if (scr_debug())`
- status: `production`
- rooms: `room_dw_church_ripplepuzzle_postgers`

### Party record 1769

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 56; if (scr_debug()) > if (global.entrance == 5 ||`
  `(scr_debug() && keyboard_check(ord("W"))))`
- status: `production`
- rooms: `room_dw_church_ripplepuzzle_postgers`

### Party record 1770

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 91; else if (global.plot <= 145) > if (global.plot == 141)`
- status: `production`
- rooms: `room_dw_church_ripplepuzzle_postgers`

### Party record 1771

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 95; if (global.plot == 141) > if (global.flag[1604] == 1)`
- status: `production`
- rooms: `room_dw_church_ripplepuzzle_postgers`

### Party record 1772

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 734; if (sucon == 6)`
- status: `production`
- rooms: `room_dw_church_ripplepuzzle_postgers`

### Party record 1773

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 33; if (global.fighting == 0) > if`
  `(sunkus_kb_check_pressed(ord("6")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1774

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 34; if (global.fighting == 0) > if`
  `(sunkus_kb_check_pressed(ord("6")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1775

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 35; if (global.fighting == 0) > if`
  `(sunkus_kb_check_pressed(ord("6")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1776

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 39; if (sunkus_kb_check_pressed(ord("7")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1777

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 43; if (sunkus_kb_check_pressed(ord("7"))) > if`
  `(sunkus_kb_check_pressed(ord("8")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1778

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 44; if (sunkus_kb_check_pressed(ord("7"))) > if`
  `(sunkus_kb_check_pressed(ord("8")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1779

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 48; if (sunkus_kb_check_pressed(ord("8"))) > if`
  `(sunkus_kb_check_pressed(ord("9")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1780

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 49; if (sunkus_kb_check_pressed(ord("9")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1781

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 53; if (sunkus_kb_check_pressed(ord("9"))) > if`
  `(sunkus_kb_check_pressed(ord("0")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1782

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 54; if (sunkus_kb_check_pressed(ord("0")))`
- status: `debug`
- rooms: `room_battletest`

### Party record 1783

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1784

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 5; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1785

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 6; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 1786

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 12; if (global.chapter != 2 || global.flag[316] == 1)`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1787

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 17; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1788

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 18; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 1789

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 15; if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_gallery`

### Party record 1790

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 12; if (scr_debug()) > if (keyboard_check(ord("P")))`
- status: `production`
- rooms: `room_dw_churchb_bookshelf`

### Party record 1791

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 15; if (keyboard_check(ord("P"))) > if (global.plot >= 242)`
- status: `production`
- rooms: `room_dw_churchb_bookshelf`

### Party record 1792

- chapter: `4`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 27; else if (!scr_havechar(3))`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 1793

- chapter: `4`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 25; if (global.chapter == 4) > if (global.plot >= 240 &&`
  `global.flag[1661] > 0)`
- status: `production`
- rooms: `room_dw_castle_town`

### Party record 1794

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 5; if (global.flag[1661] == 0)`
- status: `production`
- rooms: `room_dw_castle_town`

### Party record 1795

- chapter: `4`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 20; if (global.flag[encounterflag] == 1) > if (scr_debug())`
- status: `production`
- rooms: `room_dw_churchb_prophecyencounter`

### Party record 1796

- chapter: `5`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         scr_debug_print("No party member in slot " +`
  `string(arg0))`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1797

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `arg0 = false, arg1 = false, arg2 = false`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1798

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 10; if (!i_ex(kris))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1799

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 14; if (arg0 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1800

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 29; if (arg1 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1801

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 44; if (arg2 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1802

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 68; if (!i_ex(kris))`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1803

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 72; if (arg0 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1804

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 87; if (arg1 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1805

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 102; if (arg2 == true)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1806

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1807

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1808

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1809

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1810

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 6; if (arg0)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1811

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 10; if (arg0) > if (arg1)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1812

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 14; if (arg1) > if (arg2)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1813

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1814

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1815

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1816

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)             {                 continue`
- condition: `line 35; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1817

- chapter: `5`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 if (global.cinstance[i].x !=`
  `s.x || global.cinstance[i].y != s.x)                 {`
  `global.cinstance[i].x = s.x`
- condition: `line 7; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1818

- chapter: `5`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 if (global.cinstance[i].x !=`
  `r.x || global.cinstance[i].y != r.x)                 {`
  `global.cinstance[i].x = r.x`
- condition: `line 44; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1819

- chapter: `5`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 2)             {                 s =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 9; if (i_ex(global.cinstance[i])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1820

- chapter: `5`
- phase: `global.char[i + 1]`
- field: `global.char[i + 1]`
- expression: `= 3)             {                 r =`
  `scr_dark_marker(global.cinstance[i].x, global.cinstance[i].y,`
  `global.cinstance[i].sprite_index)`
- condition: `line 17; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1821

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `arg0`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1822

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 0)     {         global.char[0] = characterToGet`
- condition: `line 24; case "noelle": > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1823

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && getchar == 0)     {         global.char[1] =`
  `characterToGet`
- condition: `line 29; if (global.char[0] == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1824

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0 && getchar == 0)     {         global.char[2] =`
  `characterToGet`
- condition: `line 34; if (global.char[1] == 0 && getchar == 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1825

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 53; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1826

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 58; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1827

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 63; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1828

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 68; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1829

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 1; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1830

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 3; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1831

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1832

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)             {                 havechar[0] = 1`
- condition: `line 19; if (global.char[i] != 0) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1833

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)             {                 havechar[1] = 1`
- condition: `line 24; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1834

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)             {                 havechar[2] = 1`
- condition: `line 29; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1835

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)             {                 havechar[3] = 1`
- condition: `line 34; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1836

- chapter: `5`
- phase: `global.char[arg0]`
- field: `global.char[arg0]`
- expression: `= 0)     {         charcan = 0`
- condition: `line 12; if (global.acting[arg0] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1837

- chapter: `5`
- phase: `global.char[caster]`
- field: `global.char[caster]`
- expression: `= 4)         {             dm.type = 6`
- condition: `line 7; if (caster < 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1838

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2)     {         sus = 0`
- condition: `line 3; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1839

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)     {         sus = 1`
- condition: `line 7; if (global.char[0] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1840

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)     {         sus = 2`
- condition: `line 11; if (global.char[1] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1841

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 && global.charauto[2] == 1)             {`
  `global.acting[0] = 1`
- condition: `line 118; if (skip == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1842

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             with (obj_monsterparent)`
  `{                 actingnoe = 0`
- condition: `line 28; if (moveswapped == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1843

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             with (obj_monsterparent)`
  `{                 actingral = 0`
- condition: `line 35; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1844

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             with (obj_monsterparent)`
  `{                 actingsus = 0`
- condition: `line 42; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1845

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1846

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1847

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1848

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         partyconfig = 1`
- condition: `line 10; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1849

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         partyconfig = 2`
- condition: `line 14; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1850

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 0 && global.char[2] == 0)     {         global.heromakey[0] =`
  `yy + 140`
- condition: `line 29; if (global.char[0] != 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1851

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 0)     {         global.heromakey[0] = yy + 100`
- condition: `line 33; if (global.char[0] != 0 && global.char[1] == 0 &&`
  `global.char[2] == 0) > if (global.char[0] != 0 && global.char[1]`
  `!= 0 &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1852

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(20))`
- condition: `line 466; case 212: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1853

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(80))`
- condition: `line 470; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1854

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(50))`
- condition: `line 474; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1855

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(30))`
- condition: `line 478; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1856

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(80))`
- condition: `line 484; case 213: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1857

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(20))`
- condition: `line 488; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1858

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(50))`
- condition: `line 492; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1859

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(70))`
- condition: `line 496; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1860

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1) ? 100 : 90`
- condition: `line 537; case 225: > case 226:`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1861

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(400))`
- condition: `line 619; case 260: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1862

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(40))`
- condition: `line 623; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1863

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(40))`
- condition: `line 627; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1864

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(40))`
- condition: `line 631; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1865

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(160))`
- condition: `line 640; case 262: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1866

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(160))`
- condition: `line 644; if (global.char[star] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1867

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(160))`
- condition: `line 648; if (global.char[star] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1868

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 4)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(155))`
- condition: `line 652; if (global.char[star] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1869

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 1)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(200))`
- condition: `line 692; case 267: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1870

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 2)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(200))`
- condition: `line 702; case 268: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1871

- chapter: `5`
- phase: `global.char[star]`
- field: `global.char[star]`
- expression: `= 3)             {`
  `scr_healitemspell(scr_heal_amount_modify_by_equipment(200))`
- condition: `line 712; case 269: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1872

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)         {             suspos = i`
- condition: `line 16; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1873

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)         {             ralpos = i`
- condition: `line 20; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1874

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)         {             noepos = i`
- condition: `line 24; if (global.char[i] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1875

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cooked to`
  `perfection!", "scr_itemuse_slash_scr_itemuse_gml_123_0"))`
- condition: `line 166; case 8: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1876

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("A bit`
  `burnt...?", "scr_itemuse_slash_scr_itemuse_gml_127_0"))`
- condition: `line 170; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1877

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 174; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1878

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Mmm... face",`
  `"scr_itemuse_slash_scr_itemuse_gml_143_0"))`
- condition: `line 184; case 9: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1879

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect,`
  `stringsetloc("(uncomfortable)",`
  `"scr_itemuse_slash_scr_itemuse_gml_147_0"))`
- condition: `line 188; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1880

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Umm, what is`
  `this? It's cute...", "scr_itemuse_slash_scr_itemuse_gml_151_0"))`
- condition: `line 192; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1881

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Why this!?",`
  `"scr_itemuse_slash_scr_itemuse_gml_161_0"))`
- condition: `line 200; case 10: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1882

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Let's be`
  `healthy!", "scr_itemuse_slash_scr_itemuse_gml_165_0"))`
- condition: `line 204; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1883

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Something to`
  `graze on!", "scr_itemuse_slash_scr_itemuse_gml_169_0"))`
- condition: `line 208; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1884

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 233; case 12: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1885

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 237; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1886

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 242; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1887

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_healitem(global.charselect, 30)`
- condition: `line 247; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1888

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 80)`
- condition: `line 255; case 13: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1889

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 20)`
- condition: `line 259; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1890

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_healitem(global.charselect, 50)`
- condition: `line 264; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1891

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_healitem(0, 35)`
- condition: `line 269; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1892

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(It's SO`
  `good!)", "scr_itemuse_slash_scr_itemuse_gml_239_0"))`
- condition: `line 279; case 14: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1893

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("K-Kris!? I...",`
  `"scr_itemuse_slash_scr_itemuse_gml_243_0"))`
- condition: `line 283; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1894

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Huh? I didn't`
  `know Kris liked this flavor.)",`
  `"scr_itemuse_slash_scr_itemuse_gml_247_0"))`
- condition: `line 287; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1895

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Cool, it's`
  `wriggling.", "scr_itemuse_slash_scr_itemuse_gml_257_0"))`
- condition: `line 295; case 15: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1896

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Yum, is this`
  `spaghetti?", "scr_itemuse_slash_scr_itemuse_gml_261_0"))`
- condition: `line 299; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1897

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Tastes like...`
  `jumprope?", "scr_itemuse_slash_scr_itemuse_gml_265_0"))`
- condition: `line 303; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1898

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 343; case 18: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1899

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 347; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1900

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 351; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1901

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 360; case 19: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1902

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 364; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1903

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 368; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1904

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 377; case 20: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1905

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 381; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1906

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 385; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1907

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, scr_text(1460))`
- condition: `line 394; case 21: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1908

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, scr_text(1461))`
- condition: `line 398; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1909

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, scr_text(1462))`
- condition: `line 402; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1910

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("C'mon, gimme`
  `the rest!", "scr_itemuse_slash_scr_itemuse_gml_418_0"))`
- condition: `line 412; case 22: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1911

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("M-maybe give`
  `Susie the rest?", "scr_itemuse_slash_scr_itemuse_gml_422_0"))`
- condition: `line 416; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1912

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healchoice = 20`
- condition: `line 420; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1913

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hey, this`
  `rules!", "scr_itemuse_slash_scr_itemuse_gml_438_0"))`
- condition: `line 430; case 23: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1914

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Nice and`
  `chalky.", "scr_itemuse_slash_scr_itemuse_gml_442_0"))`
- condition: `line 434; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1915

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(I-isn't this`
  `the chalk I gave her?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_446_0"))`
- condition: `line 438; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1916

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell'd you call`
  `this!?", "scr_itemuse_slash_scr_itemuse_gml_456_0"))`
- condition: `line 446; case 24: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1917

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I made this.",`
  `"scr_itemuse_slash_scr_itemuse_gml_460_0"))`
- condition: `line 450; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1918

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("B-Brainfreeze!`
  `... kidding!", "scr_itemuse_slash_scr_itemuse_gml_464_0"))`
- condition: `line 454; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1919

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 heal_amount = 100`
- condition: `line 485; case 26: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1920

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says GUTS!",`
  `"scr_itemuse_slash_scr_itemuse_gml_487_0"))`
- condition: `line 489; if (global.char[global.charselect] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1921

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It says`
  `Fluffy...", "scr_itemuse_slash_scr_itemuse_gml_491_0"))`
- condition: `line 493; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1922

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I... I can't`
  `read these symbols...",`
  `"scr_itemuse_slash_scr_itemuse_gml_495_0"))`
- condition: `line 497; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1923

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 usable = 1`
- condition: `line 557; case 32: > if (haveflowery &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1924

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Ugh! ...tastes`
  `good?", "scr_itemuse_slash_scr_itemuse_gml_553_0"))`
- condition: `line 570; if (global.char[global.charselect] != 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1925

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Ow... er,`
  `thanks, Kris!", "scr_itemuse_slash_scr_itemuse_gml_557_0"))`
- condition: `line 574; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1926

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("(I'll... just`
  `pretend to drink it...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_561_0"))`
- condition: `line 578; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1927

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 if (global.filechoice == 1 &&`
  `scr_havechar("noelle"))                 {`
  `scr_itemcomment(noepos, stringsetloc("What are you, a unicorn?`
  `Faha.", "scr_itemuse_slash_scr_itemuse_gml_580_0"))`
- condition: `line 592; case 34: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1928

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {                     item_comment =`
  `stringsetloc("Butterscotch, nice!",`
  `"scr_itemuse_slash_scr_itemuse_gml_588_0")`
- condition: `line 602; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1929

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {                     item_comment =`
  `stringsetloc("Wow, what a nice flavor!",`
  `"scr_itemuse_slash_scr_itemuse_gml_600_0")`
- condition: `line 614; else if (global.filechoice == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1930

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {                     item_comment =`
  `stringsetloc("Mmm, butterscotch!",`
  `"scr_itemuse_slash_scr_itemuse_gml_612_0")`
- condition: `line 626; else if (global.filechoice == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1931

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {                 usable = 1`
- condition: `line 643; case 35: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1932

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 usable = 1`
- condition: `line 660; if (scr_havechar("noelle")) > else if (haveflowery &&`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1933

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell no.",`
  `"scr_itemuse_slash_scr_itemuse_gml_654_0"))`
- condition: `line 668; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1934

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("Is... that, um,`
  `nutritious?", "scr_itemuse_slash_scr_itemuse_gml_658_0"))`
- condition: `line 672; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1935

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)                 {`
  `scr_itemcomment(global.charselect, stringsetloc("C... can we`
  `keep it?", "scr_itemuse_slash_scr_itemuse_gml_662_0"))`
- condition: `line 676; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1936

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Fine, I'll`
  `finish it.", "scr_itemuse_slash_scr_itemuse_gml_674_0"))`
- condition: `line 685; case 36: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1937

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Aw, you saved`
  `me half?", "scr_itemuse_slash_scr_itemuse_gml_678_0"))`
- condition: `line 689; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1938

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Whatever, it's`
  `just Kris's...)", "scr_itemuse_slash_scr_itemuse_gml_682_0"))`
- condition: `line 693; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1939

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Like my old`
  `school.", "scr_itemuse_slash_scr_itemuse_gml_693_0"))`
- condition: `line 701; case 37: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1940

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Is this`
  `legal?", "scr_itemuse_slash_scr_itemuse_gml_697_0"))`
- condition: `line 705; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1941

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Here, I`
  `refreezed it!", "scr_itemuse_slash_scr_itemuse_gml_701_0"))`
- condition: `line 709; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1942

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Look, I'm a`
  `roach.", "scr_itemuse_slash_scr_itemuse_gml_722_0"))`
- condition: `line 733; case 39: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1943

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'm a comfy`
  `caterpillar!", "scr_itemuse_slash_scr_itemuse_gml_726_0"))`
- condition: `line 737; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1944

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'm, um, an`
  `alien?", "scr_itemuse_slash_scr_itemuse_gml_730_0"))`
- condition: `line 741; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1945

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Why don't we`
  `eat bullets more?", "scr_itemuse_slash_scr_itemuse_gml_729_0"))`
- condition: `line 772; case 41: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1946

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Mmm, friendly`
  `pellets.", "scr_itemuse_slash_scr_itemuse_gml_733_0"))`
- condition: `line 776; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1947

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(Stop`
  `pretending it's an attack...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_737_0"))`
- condition: `line 780; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1948

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Man, Green did`
  `awesome.", "scr_itemuse_slash_scr_itemuse_gml_748_0"))`
- condition: `line 788; case 42: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1949

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Wow, Green did`
  `wonderfully!", "scr_itemuse_slash_scr_itemuse_gml_752_0"))`
- condition: `line 792; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1950

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("You mean`
  `cardamom?", "scr_itemuse_slash_scr_itemuse_gml_756_0"))`
- condition: `line 796; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1951

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Dude, this`
  `isn't orange.", "scr_itemuse_slash_scr_itemuse_gml_767_0"))`
- condition: `line 804; case 43: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1952

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("The name and`
  `color don't match.", "scr_itemuse_slash_scr_itemuse_gml_771_0"))`
- condition: `line 808; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1953

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("You mean`
  `CITRUS? CITRUS, right? CITRUS?",`
  `"scr_itemuse_slash_scr_itemuse_gml_775_0"))`
- condition: `line 812; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1954

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1) ? 400 : 40`
- condition: `line 819; if (global.char[global.charselect] == 4) > case 60:`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1955

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Ugh! How old is`
  `this?!", "scr_itemuse_slash_scr_itemuse_gml_741_0"))`
- condition: `line 820; case 60: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1956

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Aww Kris,`
  `y-your favorite...", "scr_itemuse_slash_scr_itemuse_gml_745_0"))`
- condition: `line 824; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1957

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("I'd... I'd`
  `rather eat meat...", "scr_itemuse_slash_scr_itemuse_gml_749_0"))`
- condition: `line 828; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1958

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Sounds kinda`
  `like Noelle.", "scr_itemuse_slash_scr_itemuse_gml_760_0"))`
- condition: `line 837; case 61: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1959

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("... the hymn of`
  `the prophecy.", "scr_itemuse_slash_scr_itemuse_gml_764_0"))`
- condition: `line 841; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1960

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("(... Kris would`
  `never join choir...)",`
  `"scr_itemuse_slash_scr_itemuse_gml_768_0"))`
- condition: `line 845; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1961

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Hell yeah!`
  `Cheers!", "scr_itemuse_slash_scr_itemuse_gml_780_0"))`
- condition: `line 854; case 62: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1962

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {`
  `scr_itemcomment(global.charselect, stringsetloc("Y-yuck! Er,`
  `mmm, medicine?", "scr_itemuse_slash_scr_itemuse_gml_784_0"))`
- condition: `line 858; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1963

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 _healamount = 155`
- condition: `line 862; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1964

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_itemcomment(global.charselect, stringsetloc("... isn't that`
  `rain?", "scr_itemuse_slash_scr_itemuse_gml_809_0"))`
- condition: `line 878; if (haveflowery && global.charselect == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1965

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {`
  `scr_itemcomment(global.charselect, stringsetloc("It's like when`
  `we ate snow.", "scr_itemuse_slash_scr_itemuse_gml_813_0"))`
- condition: `line 882; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1966

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {                 scr_itemcomment(suspos,`
  `stringsetloc("Still kinda burns.",`
  `"scr_itemuse_slash_scr_itemuse_gml_886_0"))`
- condition: `line 927; case 66: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1967

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 scr_itemcomment(ralpos,`
  `stringsetloc("Um, is it caffeinated?",`
  `"scr_itemuse_slash_scr_itemuse_gml_887_0"))`
- condition: `line 931; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1968

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_itemcomment(noepos,`
  `stringsetloc("This... is expired!",`
  `"scr_itemuse_slash_scr_itemuse_gml_888_0"))`
- condition: `line 935; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1969

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 1)             {`
  `scr_healitem(global.charselect, 200)`
- condition: `line 942; case 67: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1970

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {                 scr_itemcomment(suspos,`
  `stringsetloc("Can't get the marble.",`
  `"scr_itemuse_slash_scr_itemuse_gml_902_0"))`
- condition: `line 950; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1971

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 scr_itemcomment(ralpos,`
  `stringsetloc("How do I recycle this?",`
  `"scr_itemuse_slash_scr_itemuse_gml_903_0"))`
- condition: `line 954; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1972

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_itemcomment(noepos,`
  `stringsetloc("(Are they, pronouncing it wrong on purpose?)",`
  `"scr_itemuse_slash_scr_itemuse_gml_904_0"))`
- condition: `line 958; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1973

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {`
  `scr_healitem(global.charselect, 200)`
- condition: `line 965; case 68: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1974

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {                 scr_itemcomment(suspos,`
  `stringsetloc("Bought. With money. Hell yeah.",`
  `"scr_itemuse_slash_scr_itemuse_gml_918_0"))`
- condition: `line 973; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1975

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 scr_itemcomment(ralpos,`
  `stringsetloc("But, it's Susie's favorite...",`
  `"scr_itemuse_slash_scr_itemuse_gml_919_0"))`
- condition: `line 977; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1976

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_itemcomment(noepos,`
  `stringsetloc("Look, Kris! Susie's venom! (drinks it) (drinks`
  `it)", "scr_itemuse_slash_scr_itemuse_gml_920_0"))`
- condition: `line 981; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1977

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 usable = 0`
- condition: `line 987; case 69: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1978

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 2)             {                 scr_itemcomment(suspos,`
  `stringsetloc("Eww, Ralsei likes lactose?",`
  `"scr_itemuse_slash_scr_itemuse_gml_934_0"))`
- condition: `line 996; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1979

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 3)             {                 scr_itemcomment(ralpos,`
  `stringsetloc("I... I'm not thirsty.",`
  `"scr_itemuse_slash_scr_itemuse_gml_935_0"))`
- condition: `line 1000; if (global.char[global.charselect] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1980

- chapter: `5`
- phase: `global.char[global.charselect]`
- field: `global.char[global.charselect]`
- expression: `= 4)             {                 scr_itemcomment(noepos,`
  `stringsetloc("........ who the heck is Flowery?",`
  `"scr_itemuse_slash_scr_itemuse_gml_936_0"))`
- condition: `line 1004; if (global.char[global.charselect] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1981

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)                 {                     continue`
- condition: `line 1013; case 70: > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1982

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4) ? 5 : 80`
- condition: `line 1017; if (global.char[i] == 0)`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1983

- chapter: `5`
- phase: `global.char[3]`
- field: `global.char[3]`
- expression: `0`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1984

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1985

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1986

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1987

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 29; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1988

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 31; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1989

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `ossafe_file_text_read_real(myfileid)`
- condition: `line 33; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1990

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)                     {                         facetype =`
  `spr_headkris`
- condition: `line 37; if (itemtype[menuc[1]] == "weapon" || itemtype[menuc[1]]`
  `== "armor") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1991

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         facetype =`
  `spr_headsusie`
- condition: `line 41; if (global.char[i] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1992

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         facetype =`
  `spr_headralsei`
- condition: `line 45; if (global.char[i] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1993

- chapter: `5`
- phase: `global.char[__findchar]`
- field: `global.char[__findchar]`
- expression: `= arg0)         {             __charslot = __findchar`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1994

- chapter: `5`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 2)                 {                     with (__minstance)`
  `{                         actconsus = 1`
- condition: `line 25; if (global.actingsingle[global.currentactingchar] == 1)`
  `> if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1995

- chapter: `5`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 3)                 {                     with (__minstance)`
  `{                         actconral = 1`
- condition: `line 37; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1996

- chapter: `5`
- phase: `global.char[global.currentactingchar]`
- field: `global.char[global.currentactingchar]`
- expression: `= 4)                 {                     with (__minstance)`
  `{                         actconnoe = 1`
- condition: `line 49; if (global.actingsimul[global.currentactingchar] == 0) >`
  `if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1997

- chapter: `5`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 1 &&`
  `global.actsimul[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderkri = __simulcount`
- condition: `line 9; if (global.actingsingle[__ii] == 1 &&`
  `instance_exists(obj_monsterparent)) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1998

- chapter: `5`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 2 &&`
  `global.actsimulsus[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordersus = __simulcount`
- condition: `line 18; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 1999

- chapter: `5`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 3 &&`
  `global.actsimulral[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulorderral = __simulcount`
- condition: `line 27; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2000

- chapter: `5`
- phase: `global.char[__ii]`
- field: `global.char[__ii]`
- expression: `= 4 &&`
  `global.actsimulnoe[global.actingtarget[__ii]][global.actingchoice[__ii]]`
  `== 1)             {`
  `obj_monsterparent.simulordernoe = __simulcount`
- condition: `line 36; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2001

- chapter: `5`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 1)             {                 if (global.canact[0][__fj] ==`
  `1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 20; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2002

- chapter: `5`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 2)             {                 if (global.canactsus[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 36; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2003

- chapter: `5`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 3)             {                 if (global.canactral[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 56; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2004

- chapter: `5`
- phase: `global.char[__i]`
- field: `global.char[__i]`
- expression: `= 4)             {                 if (global.canactnoe[0][__fj]`
  `== 1)                 {`
  `global.battlespell[__i][__fj] = -1`
- condition: `line 76; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2005

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             global.monsterinstance[arg0].acting =`
  `arg1 + 1`
- condition: `line 5; if (i_ex(global.monsterinstance[arg0])) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2006

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {`
  `global.monsterinstance[arg0].actingsus = arg1 + 1`
- condition: `line 9; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2007

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {`
  `global.monsterinstance[arg0].actingral = arg1 + 1`
- condition: `line 13; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2008

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {`
  `global.monsterinstance[arg0].actingnoe = arg1 + 1`
- condition: `line 17; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2009

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)     {         global.actingsimul[0] = actsimul[arg1]`
- condition: `line 22; if (global.char[global.charturn] == 4) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2010

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[arg0][__acti]`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2011

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[arg0][__acti]`
- condition: `line 12; if (global.char[global.charturn] == 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2012

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[arg0][__acti]`
- condition: `line 18; if (global.char[global.charturn] == 2) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2013

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[arg0][__acti]`
- condition: `line 24; if (global.char[global.charturn] == 3) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2014

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 18; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2015

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 19; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2016

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 20; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2017

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 17; if (checker == "noelle" || checker == "no" || checker ==`
  `"n") > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2018

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 21; if (global.char[0] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2019

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= checker)     {         _rreturn = 1`
- condition: `line 25; if (global.char[1] == checker) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2020

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)         {             ralpos = i`
- condition: `line 6; if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2021

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 32; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2022

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)         {             continue`
- condition: `line 12; if (delaytimer >= 1) > if (`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2023

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2024

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `0`
- condition: `line 5; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2025

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `production-uncertain`
- rooms: `not room-owned`

### Party record 2026

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 7; unconditional in entry`
- status: `production`
- rooms: `room_dw_dogballoon`

### Party record 2027

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 10; if (global.plot >= 190 && global.plot < 200)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2028

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_onsen`

### Party record 2029

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_garden_hospital`

### Party record 2030

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 0)     {         continue`
- condition: `line 11; if (`
- status: `production`
- rooms: `room_dw_garden_hospital`

### Party record 2031

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `true, true`
- condition: `line 18; if (scr_debug())`
- status: `production`
- rooms: `room_dw_pink_encounter`

### Party record 2032

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_garden_aquadash, room_dw_garden_aquadash_plat`

### Party record 2033

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 3; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2034

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 25; unconditional in entry`
- status: `production`
- rooms: `room_dw_fcastle_flowerclimb`

### Party record 2035

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 5; if (scr_debug())`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2036

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 165; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2037

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2 || global.char[2] == 2`
- condition: `line 117; unconditional in entry`
- status: `unplaced-or-presentation`
- rooms: `room_dw_rhythm`

### Party record 2038

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 3 || global.char[2] == 3`
- condition: `line 132; unconditional in entry`
- status: `unplaced-or-presentation`
- rooms: `room_dw_rhythm`

### Party record 2039

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 14; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2040

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 7; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_second_diner`

### Party record 2041

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 6; if (scr_debug())`
- status: `production`
- rooms: `room_dw_flowery_tree`

### Party record 2042

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 15; if (!plot_check_on || global.plot < plot_post)`
- status: `production`
- rooms: `room_dw_flowery_tree`

### Party record 2043

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 28; if (con == 2)`
- status: `production`
- rooms: `room_dw_flowery_tree`

### Party record 2044

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"su"`
- condition: `line 285; unconditional in entry`
- status: `production`
- rooms: `room_dw_flowery_tree`

### Party record 2045

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 7; if (scr_debug())`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2046

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 231; if (global.plot < 5)`
- status: `production`
- rooms: `room_krisroom`

### Party record 2047

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"susie"`
- condition: `line 106; if (!scr_havechar("susie"))`
- status: `production`
- rooms: `room_krisroom`

### Party record 2048

- chapter: `5`
- phase: `global.char[ti]`
- field: `global.char[ti]`
- expression: `= 0)                 {                     ti++`
- condition: `line 46; if (abs(obj_heart.y - y) < 12 && global.inv < 0) > if`
  `(global.hp[global.char[ti]] < 0 ||`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2049

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug() && global.plot < 264)`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2050

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 1`
- condition: `line 9; if (scr_debug() && global.plot < 264) > if (global.plot`
  `== 264)`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2051

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 1`
- condition: `line 13; if (global.plot == 264) > if (global.plot == 265)`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2052

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 6; if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_post_fountain_close`

### Party record 2053

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 33; if (con == 2)`
- status: `production-subsystem`
- rooms: `room_dw_post_fountain_close`

### Party record 2054

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 2; unconditional in entry`
- status: `production`
- rooms: `room_dw_cliff_seth_miniboss`

### Party record 2055

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 26; if (global.plot < 200)`
- status: `production`
- rooms: `room_dw_garden_intro`

### Party record 2056

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 19; if (con == 2)`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2057

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 371; if (con == 7)`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2058

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"susie"`
- condition: `line 376; if (con == 7)`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2059

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"ralsei"`
- condition: `line 377; unconditional in entry`
- status: `production`
- rooms: `room_dw_garden_hardpressureplates`

### Party record 2060

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 10; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2061

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 2355; if (hero == 3)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2062

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_cliff_sethaqua_battle`

### Party record 2063

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_entrance`

### Party record 2064

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 3; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2065

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 28; if (global.plot == minplot)`
- status: `production`
- rooms: `room_dw_garden_susiechase`

### Party record 2066

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 1, 0`
- condition: `line 6; if (global.plot < 50)`
- status: `production`
- rooms: `room_dw_castle_town`

### Party record 2067

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 139; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2068

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 56; if (appearance == 1) > if (appearance == 1)`
- status: `production`
- rooms: `room_dw_fcastle_flowerclimb`

### Party record 2069

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 54; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2070

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 15; if (plot_check_on == false || global.plot <`
  `plot_on_completion) > if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_post_party_jail`

### Party record 2071

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `"ralsei"`
- condition: `line 103; if (extflag == "cutscene" && place_meeting(x, y,`
  `obj_mainchara))`
- status: `production`
- rooms: `room_dw_fcastle_post_party_jail`

### Party record 2072

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0, 0, 0`
- condition: `line 3; unconditional in entry`
- status: `production`
- rooms: `room_man`

### Party record 2073

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 14; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_right_endingscene`

### Party record 2074

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 1378; if (hero == 3)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2075

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_yellowjail`

### Party record 2076

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 78; if (collided == 0 && x > (camerax() + 320))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2077

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 113; if (global.plot < 60)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2078

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 4; if (scr_debug())`
- status: `production`
- rooms: `room_dw_cliff_gardentransition_new`

### Party record 2079

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 9; if (scr_debug())`
- status: `production-subsystem`
- rooms: `room_dw_fcastle_green_orange_battle`

### Party record 2080

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 0, 0`
- condition: `line 21; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2081

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 21; if (scr_havechar("noelle"))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2082

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 22; if (scr_havechar("noelle"))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2083

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 44; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2084

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 52; if (i_ex(obj_caterpillarchara))`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2085

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `4`
- condition: `line 53; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2086

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 10; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_left_wing_floweryscene`

### Party record 2087

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `true, true`
- condition: `line 5; if (scr_debug())`
- status: `production`
- rooms: `room_dw_garden_cliffexit`

### Party record 2088

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `0`
- condition: `line 556; unconditional in entry`
- status: `production`
- rooms: `room_dw_garden_aqua`

### Party record 2089

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 628; if (con == 6.1) > if (!global.fighting)`
- status: `production`
- rooms: `room_dw_garden_aqua`

### Party record 2090

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1, 0`
- condition: `line 5; ﻿if (instance_number(obj_dw_transition) > 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2091

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 47; if (cutscene == 0) > if (scr_trigcheck("cut1") ||`
  `cupboard.myinteract == 3)`
- status: `production`
- rooms: `room_dw_garden_ralseicupboard`

### Party record 2092

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)                 {                     c[i].sprite_index =`
  `spr_krisb_attack`
- condition: `line 37; if (global.char[i] != 4) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2093

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                 {                     c[i].sprite_index =`
  `spr_susieb_attack`
- condition: `line 41; if (global.char[i] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2094

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                 {                     c[i].sprite_index =`
  `spr_ralsei_battleintro`
- condition: `line 49; if (global.charweapon[global.char[i]] == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2095

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 55; if (global.char[i] != 0) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer, room_climbtest,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_darkbulbTest, room_DARKempty, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_smallface_dark,`
  `room_dogplatforming, room_dw_castle_area_1, room_dw_castle_cafe,`
  `room_dw_castle_church_climb, room_dw_castle_church_entrance,`
  `room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_music,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_tv, room_dw_castle_tv_kikky,`
  `room_dw_castle_tv_mike, room_dw_castle_tv_rhythm,`
  `room_dw_castle_west_cliff, room_dw_cliff_bonuscombat,`
  `room_dw_cliff_bunnyfarm, room_dw_cliff_climbrefresher,`
  `room_dw_cliff_cutdown_tutorial, room_dw_cliff_dash_runner,`
  `room_dw_cliff_eastcliff, room_dw_cliff_finaldash,`
  `room_dw_cliff_gardentransition_new, room_dw_cliff_kawkawdash,`
  `room_dw_cliff_netskieclimb, room_dw_cliff_netskieclimb_behind,`
  `room_dw_cliff_precipice, room_dw_cliff_seth_miniboss,`
  `room_dw_cliff_sethaqua_battle, room_dw_cliff_shicave,`
  `room_dw_cliff_shop, room_dw_cliff_silver_hammer,`
  `room_dw_cliff_twirlflowerplatforming, room_dw_cliff_twirlflowerwind,`
  `room_dw_cliff_verticalwind, room_dw_cliff_verticalwind_post,`
  `room_dw_cliff_yellowcave, room_dw_dogballoon, room_dw_fcastle_asgore,`
  `room_dw_fcastle_blueroom, room_dw_fcastle_bounce_1,`
  `room_dw_fcastle_bounce_3, room_dw_fcastle_bromides,`
  `room_dw_fcastle_cafe, room_dw_fcastle_dangerous_platforming,`
  `room_dw_fcastle_entrance, room_dw_fcastle_final_save,`
  `room_dw_fcastle_flowerclimb, room_dw_fcastle_flowerclimb_for_tiling,`
  `room_dw_fcastle_flowery, room_dw_fcastle_flowerydash,`
  `room_dw_fcastle_foxhunt, room_dw_fcastle_foxhunt_chaos,`
  `room_dw_fcastle_foxhunt_secret, room_dw_fcastle_foxhunt_socks,`
  `room_dw_fcastle_foxhunt_terakota, room_dw_fcastle_foyer,`
  `room_dw_fcastle_fusumadodge, room_dw_fcastle_gloves_tower,`
  `room_dw_fcastle_green_checkpoint,`
  `room_dw_fcastle_green_orange_battle, room_dw_fcastle_heldmushrooms,`
  `room_dw_fcastle_left_penultimate, room_dw_fcastle_left_twodoors,`
  `room_dw_fcastle_left_wing_floweryscene,`
  `room_dw_fcastle_obscured_bullets, room_dw_fcastle_onsen,`
  `room_dw_fcastle_orange_gauntlet,`
  `room_dw_fcastle_orange_puppet_introduction,`
  `room_dw_fcastle_partyjail, room_dw_fcastle_pinkroom,`
  `room_dw_fcastle_pinkshop, room_dw_fcastle_post_party_jail,`
  `room_dw_fcastle_right_endingscene, room_dw_fcastle_right_penultimate,`
  `room_dw_fcastle_right_puzzle,`
  `room_dw_fcastle_right_wing_floweryscene, room_dw_fcastle_sandtrap,`
  `room_dw_fcastle_second_diner, room_dw_fcastle_seth_encounter,`
  `room_dw_fcastle_shadowplatformTest, room_dw_fcastle_shinobeetle_3d,`
  `room_dw_fcastle_shinobeetle_encounter, room_dw_fcastle_sidepuzzle,`
  `room_dw_fcastle_terracotta_bonus,`
  `room_dw_fcastle_terracotta_encounter,`
  `room_dw_fcastle_terracotta_puzzle, room_dw_fcastle_top_ascent,`
  `room_dw_fcastle_top_challenge, room_dw_fcastle_top_descent,`
  `room_dw_fcastle_top_entrance, room_dw_fcastle_top_fountain,`
  `room_dw_fcastle_top_intro, room_dw_fcastle_top_pinkdoor,`
  `room_dw_fcastle_top_staircase_1, room_dw_fcastle_top_staircase_2,`
  `room_dw_fcastle_trainroom, room_dw_fcastle_ultradash,`
  `room_dw_fcastle_yellow_miniboss, room_dw_fcastle_yellowblue,`
  `room_dw_fcastle_yellowjail, room_dw_fcastle_zenlooker,`
  `room_dw_flowery_tree, room_dw_garden_aqua,`
  `room_dw_garden_aquadarkness, room_dw_garden_aquadash,`
  `room_dw_garden_aquadash_plat, room_dw_garden_aquahole,`
  `room_dw_garden_aquahole_left, room_dw_garden_aquaplatforming,`
  `room_dw_garden_aquashrine, room_dw_garden_aquatransition,`
  `room_dw_garden_cliffexit, room_dw_garden_diner,`
  `room_dw_garden_enemyrush, room_dw_garden_finalplatforming,`
  `room_dw_garden_finalplatforming_right, room_dw_garden_firstdash,`
  `room_dw_garden_fishingspot, room_dw_garden_floradinnencounter,`
  `room_dw_garden_flowerygardening, room_dw_garden_hardpressureplates,`
  `room_dw_garden_hopschef, room_dw_garden_hospital,`
  `room_dw_garden_intro, room_dw_garden_meetflowery,`
  `room_dw_garden_mushrooms, room_dw_garden_newdash,`
  `room_dw_garden_pedestal, room_dw_garden_platshortcut,`
  `room_dw_garden_ralseicupboard, room_dw_garden_riverchest,`
  `room_dw_garden_shearydodge, room_dw_garden_shearyguide,`
  `room_dw_garden_starwalkerdash, room_dw_garden_susiechase,`
  `room_dw_garden_wateringcan_aqua, room_dw_petaltest,`
  `room_dw_pink_encounter, room_dw_post_flowery_battle,`
  `room_dw_post_fountain_close, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_basketball, room_dw_ralsei_castle_front,`
  `room_dw_rhythm, room_dw_rhythm_countdown, room_floortex_test,`
  `room_GMS2_test, room_man, room_overworldBulletEnemyTest,`
  `room_plat_lab`

### Party record 2096

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 60; if (global.char[i] == 1) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer, room_climbtest,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_darkbulbTest, room_DARKempty, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_smallface_dark,`
  `room_dogplatforming, room_dw_castle_area_1, room_dw_castle_cafe,`
  `room_dw_castle_church_climb, room_dw_castle_church_entrance,`
  `room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_music,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_tv, room_dw_castle_tv_kikky,`
  `room_dw_castle_tv_mike, room_dw_castle_tv_rhythm,`
  `room_dw_castle_west_cliff, room_dw_cliff_bonuscombat,`
  `room_dw_cliff_bunnyfarm, room_dw_cliff_climbrefresher,`
  `room_dw_cliff_cutdown_tutorial, room_dw_cliff_dash_runner,`
  `room_dw_cliff_eastcliff, room_dw_cliff_finaldash,`
  `room_dw_cliff_gardentransition_new, room_dw_cliff_kawkawdash,`
  `room_dw_cliff_netskieclimb, room_dw_cliff_netskieclimb_behind,`
  `room_dw_cliff_precipice, room_dw_cliff_seth_miniboss,`
  `room_dw_cliff_sethaqua_battle, room_dw_cliff_shicave,`
  `room_dw_cliff_shop, room_dw_cliff_silver_hammer,`
  `room_dw_cliff_twirlflowerplatforming, room_dw_cliff_twirlflowerwind,`
  `room_dw_cliff_verticalwind, room_dw_cliff_verticalwind_post,`
  `room_dw_cliff_yellowcave, room_dw_dogballoon, room_dw_fcastle_asgore,`
  `room_dw_fcastle_blueroom, room_dw_fcastle_bounce_1,`
  `room_dw_fcastle_bounce_3, room_dw_fcastle_bromides,`
  `room_dw_fcastle_cafe, room_dw_fcastle_dangerous_platforming,`
  `room_dw_fcastle_entrance, room_dw_fcastle_final_save,`
  `room_dw_fcastle_flowerclimb, room_dw_fcastle_flowerclimb_for_tiling,`
  `room_dw_fcastle_flowery, room_dw_fcastle_flowerydash,`
  `room_dw_fcastle_foxhunt, room_dw_fcastle_foxhunt_chaos,`
  `room_dw_fcastle_foxhunt_secret, room_dw_fcastle_foxhunt_socks,`
  `room_dw_fcastle_foxhunt_terakota, room_dw_fcastle_foyer,`
  `room_dw_fcastle_fusumadodge, room_dw_fcastle_gloves_tower,`
  `room_dw_fcastle_green_checkpoint,`
  `room_dw_fcastle_green_orange_battle, room_dw_fcastle_heldmushrooms,`
  `room_dw_fcastle_left_penultimate, room_dw_fcastle_left_twodoors,`
  `room_dw_fcastle_left_wing_floweryscene,`
  `room_dw_fcastle_obscured_bullets, room_dw_fcastle_onsen,`
  `room_dw_fcastle_orange_gauntlet,`
  `room_dw_fcastle_orange_puppet_introduction,`
  `room_dw_fcastle_partyjail, room_dw_fcastle_pinkroom,`
  `room_dw_fcastle_pinkshop, room_dw_fcastle_post_party_jail,`
  `room_dw_fcastle_right_endingscene, room_dw_fcastle_right_penultimate,`
  `room_dw_fcastle_right_puzzle,`
  `room_dw_fcastle_right_wing_floweryscene, room_dw_fcastle_sandtrap,`
  `room_dw_fcastle_second_diner, room_dw_fcastle_seth_encounter,`
  `room_dw_fcastle_shadowplatformTest, room_dw_fcastle_shinobeetle_3d,`
  `room_dw_fcastle_shinobeetle_encounter, room_dw_fcastle_sidepuzzle,`
  `room_dw_fcastle_terracotta_bonus,`
  `room_dw_fcastle_terracotta_encounter,`
  `room_dw_fcastle_terracotta_puzzle, room_dw_fcastle_top_ascent,`
  `room_dw_fcastle_top_challenge, room_dw_fcastle_top_descent,`
  `room_dw_fcastle_top_entrance, room_dw_fcastle_top_fountain,`
  `room_dw_fcastle_top_intro, room_dw_fcastle_top_pinkdoor,`
  `room_dw_fcastle_top_staircase_1, room_dw_fcastle_top_staircase_2,`
  `room_dw_fcastle_trainroom, room_dw_fcastle_ultradash,`
  `room_dw_fcastle_yellow_miniboss, room_dw_fcastle_yellowblue,`
  `room_dw_fcastle_yellowjail, room_dw_fcastle_zenlooker,`
  `room_dw_flowery_tree, room_dw_garden_aqua,`
  `room_dw_garden_aquadarkness, room_dw_garden_aquadash,`
  `room_dw_garden_aquadash_plat, room_dw_garden_aquahole,`
  `room_dw_garden_aquahole_left, room_dw_garden_aquaplatforming,`
  `room_dw_garden_aquashrine, room_dw_garden_aquatransition,`
  `room_dw_garden_cliffexit, room_dw_garden_diner,`
  `room_dw_garden_enemyrush, room_dw_garden_finalplatforming,`
  `room_dw_garden_finalplatforming_right, room_dw_garden_firstdash,`
  `room_dw_garden_fishingspot, room_dw_garden_floradinnencounter,`
  `room_dw_garden_flowerygardening, room_dw_garden_hardpressureplates,`
  `room_dw_garden_hopschef, room_dw_garden_hospital,`
  `room_dw_garden_intro, room_dw_garden_meetflowery,`
  `room_dw_garden_mushrooms, room_dw_garden_newdash,`
  `room_dw_garden_pedestal, room_dw_garden_platshortcut,`
  `room_dw_garden_ralseicupboard, room_dw_garden_riverchest,`
  `room_dw_garden_shearydodge, room_dw_garden_shearyguide,`
  `room_dw_garden_starwalkerdash, room_dw_garden_susiechase,`
  `room_dw_garden_wateringcan_aqua, room_dw_petaltest,`
  `room_dw_pink_encounter, room_dw_post_flowery_battle,`
  `room_dw_post_fountain_close, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_basketball, room_dw_ralsei_castle_front,`
  `room_dw_rhythm, room_dw_rhythm_countdown, room_floortex_test,`
  `room_GMS2_test, room_man, room_overworldBulletEnemyTest,`
  `room_plat_lab`

### Party record 2097

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 70; if (i > 0) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer, room_climbtest,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_darkbulbTest, room_DARKempty, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_smallface_dark,`
  `room_dogplatforming, room_dw_castle_area_1, room_dw_castle_cafe,`
  `room_dw_castle_church_climb, room_dw_castle_church_entrance,`
  `room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_music,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_tv, room_dw_castle_tv_kikky,`
  `room_dw_castle_tv_mike, room_dw_castle_tv_rhythm,`
  `room_dw_castle_west_cliff, room_dw_cliff_bonuscombat,`
  `room_dw_cliff_bunnyfarm, room_dw_cliff_climbrefresher,`
  `room_dw_cliff_cutdown_tutorial, room_dw_cliff_dash_runner,`
  `room_dw_cliff_eastcliff, room_dw_cliff_finaldash,`
  `room_dw_cliff_gardentransition_new, room_dw_cliff_kawkawdash,`
  `room_dw_cliff_netskieclimb, room_dw_cliff_netskieclimb_behind,`
  `room_dw_cliff_precipice, room_dw_cliff_seth_miniboss,`
  `room_dw_cliff_sethaqua_battle, room_dw_cliff_shicave,`
  `room_dw_cliff_shop, room_dw_cliff_silver_hammer,`
  `room_dw_cliff_twirlflowerplatforming, room_dw_cliff_twirlflowerwind,`
  `room_dw_cliff_verticalwind, room_dw_cliff_verticalwind_post,`
  `room_dw_cliff_yellowcave, room_dw_dogballoon, room_dw_fcastle_asgore,`
  `room_dw_fcastle_blueroom, room_dw_fcastle_bounce_1,`
  `room_dw_fcastle_bounce_3, room_dw_fcastle_bromides,`
  `room_dw_fcastle_cafe, room_dw_fcastle_dangerous_platforming,`
  `room_dw_fcastle_entrance, room_dw_fcastle_final_save,`
  `room_dw_fcastle_flowerclimb, room_dw_fcastle_flowerclimb_for_tiling,`
  `room_dw_fcastle_flowery, room_dw_fcastle_flowerydash,`
  `room_dw_fcastle_foxhunt, room_dw_fcastle_foxhunt_chaos,`
  `room_dw_fcastle_foxhunt_secret, room_dw_fcastle_foxhunt_socks,`
  `room_dw_fcastle_foxhunt_terakota, room_dw_fcastle_foyer,`
  `room_dw_fcastle_fusumadodge, room_dw_fcastle_gloves_tower,`
  `room_dw_fcastle_green_checkpoint,`
  `room_dw_fcastle_green_orange_battle, room_dw_fcastle_heldmushrooms,`
  `room_dw_fcastle_left_penultimate, room_dw_fcastle_left_twodoors,`
  `room_dw_fcastle_left_wing_floweryscene,`
  `room_dw_fcastle_obscured_bullets, room_dw_fcastle_onsen,`
  `room_dw_fcastle_orange_gauntlet,`
  `room_dw_fcastle_orange_puppet_introduction,`
  `room_dw_fcastle_partyjail, room_dw_fcastle_pinkroom,`
  `room_dw_fcastle_pinkshop, room_dw_fcastle_post_party_jail,`
  `room_dw_fcastle_right_endingscene, room_dw_fcastle_right_penultimate,`
  `room_dw_fcastle_right_puzzle,`
  `room_dw_fcastle_right_wing_floweryscene, room_dw_fcastle_sandtrap,`
  `room_dw_fcastle_second_diner, room_dw_fcastle_seth_encounter,`
  `room_dw_fcastle_shadowplatformTest, room_dw_fcastle_shinobeetle_3d,`
  `room_dw_fcastle_shinobeetle_encounter, room_dw_fcastle_sidepuzzle,`
  `room_dw_fcastle_terracotta_bonus,`
  `room_dw_fcastle_terracotta_encounter,`
  `room_dw_fcastle_terracotta_puzzle, room_dw_fcastle_top_ascent,`
  `room_dw_fcastle_top_challenge, room_dw_fcastle_top_descent,`
  `room_dw_fcastle_top_entrance, room_dw_fcastle_top_fountain,`
  `room_dw_fcastle_top_intro, room_dw_fcastle_top_pinkdoor,`
  `room_dw_fcastle_top_staircase_1, room_dw_fcastle_top_staircase_2,`
  `room_dw_fcastle_trainroom, room_dw_fcastle_ultradash,`
  `room_dw_fcastle_yellow_miniboss, room_dw_fcastle_yellowblue,`
  `room_dw_fcastle_yellowjail, room_dw_fcastle_zenlooker,`
  `room_dw_flowery_tree, room_dw_garden_aqua,`
  `room_dw_garden_aquadarkness, room_dw_garden_aquadash,`
  `room_dw_garden_aquadash_plat, room_dw_garden_aquahole,`
  `room_dw_garden_aquahole_left, room_dw_garden_aquaplatforming,`
  `room_dw_garden_aquashrine, room_dw_garden_aquatransition,`
  `room_dw_garden_cliffexit, room_dw_garden_diner,`
  `room_dw_garden_enemyrush, room_dw_garden_finalplatforming,`
  `room_dw_garden_finalplatforming_right, room_dw_garden_firstdash,`
  `room_dw_garden_fishingspot, room_dw_garden_floradinnencounter,`
  `room_dw_garden_flowerygardening, room_dw_garden_hardpressureplates,`
  `room_dw_garden_hopschef, room_dw_garden_hospital,`
  `room_dw_garden_intro, room_dw_garden_meetflowery,`
  `room_dw_garden_mushrooms, room_dw_garden_newdash,`
  `room_dw_garden_pedestal, room_dw_garden_platshortcut,`
  `room_dw_garden_ralseicupboard, room_dw_garden_riverchest,`
  `room_dw_garden_shearydodge, room_dw_garden_shearyguide,`
  `room_dw_garden_starwalkerdash, room_dw_garden_susiechase,`
  `room_dw_garden_wateringcan_aqua, room_dw_petaltest,`
  `room_dw_pink_encounter, room_dw_post_flowery_battle,`
  `room_dw_post_fountain_close, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_basketball, room_dw_ralsei_castle_front,`
  `room_dw_rhythm, room_dw_rhythm_countdown, room_floortex_test,`
  `room_GMS2_test, room_man, room_overworldBulletEnemyTest,`
  `room_plat_lab`

### Party record 2098

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 109; if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer, room_climbtest,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_darkbulbTest, room_DARKempty, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_smallface_dark,`
  `room_dogplatforming, room_dw_castle_area_1, room_dw_castle_cafe,`
  `room_dw_castle_church_climb, room_dw_castle_church_entrance,`
  `room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_music,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_tv, room_dw_castle_tv_kikky,`
  `room_dw_castle_tv_mike, room_dw_castle_tv_rhythm,`
  `room_dw_castle_west_cliff, room_dw_cliff_bonuscombat,`
  `room_dw_cliff_bunnyfarm, room_dw_cliff_climbrefresher,`
  `room_dw_cliff_cutdown_tutorial, room_dw_cliff_dash_runner,`
  `room_dw_cliff_eastcliff, room_dw_cliff_finaldash,`
  `room_dw_cliff_gardentransition_new, room_dw_cliff_kawkawdash,`
  `room_dw_cliff_netskieclimb, room_dw_cliff_netskieclimb_behind,`
  `room_dw_cliff_precipice, room_dw_cliff_seth_miniboss,`
  `room_dw_cliff_sethaqua_battle, room_dw_cliff_shicave,`
  `room_dw_cliff_shop, room_dw_cliff_silver_hammer,`
  `room_dw_cliff_twirlflowerplatforming, room_dw_cliff_twirlflowerwind,`
  `room_dw_cliff_verticalwind, room_dw_cliff_verticalwind_post,`
  `room_dw_cliff_yellowcave, room_dw_dogballoon, room_dw_fcastle_asgore,`
  `room_dw_fcastle_blueroom, room_dw_fcastle_bounce_1,`
  `room_dw_fcastle_bounce_3, room_dw_fcastle_bromides,`
  `room_dw_fcastle_cafe, room_dw_fcastle_dangerous_platforming,`
  `room_dw_fcastle_entrance, room_dw_fcastle_final_save,`
  `room_dw_fcastle_flowerclimb, room_dw_fcastle_flowerclimb_for_tiling,`
  `room_dw_fcastle_flowery, room_dw_fcastle_flowerydash,`
  `room_dw_fcastle_foxhunt, room_dw_fcastle_foxhunt_chaos,`
  `room_dw_fcastle_foxhunt_secret, room_dw_fcastle_foxhunt_socks,`
  `room_dw_fcastle_foxhunt_terakota, room_dw_fcastle_foyer,`
  `room_dw_fcastle_fusumadodge, room_dw_fcastle_gloves_tower,`
  `room_dw_fcastle_green_checkpoint,`
  `room_dw_fcastle_green_orange_battle, room_dw_fcastle_heldmushrooms,`
  `room_dw_fcastle_left_penultimate, room_dw_fcastle_left_twodoors,`
  `room_dw_fcastle_left_wing_floweryscene,`
  `room_dw_fcastle_obscured_bullets, room_dw_fcastle_onsen,`
  `room_dw_fcastle_orange_gauntlet,`
  `room_dw_fcastle_orange_puppet_introduction,`
  `room_dw_fcastle_partyjail, room_dw_fcastle_pinkroom,`
  `room_dw_fcastle_pinkshop, room_dw_fcastle_post_party_jail,`
  `room_dw_fcastle_right_endingscene, room_dw_fcastle_right_penultimate,`
  `room_dw_fcastle_right_puzzle,`
  `room_dw_fcastle_right_wing_floweryscene, room_dw_fcastle_sandtrap,`
  `room_dw_fcastle_second_diner, room_dw_fcastle_seth_encounter,`
  `room_dw_fcastle_shadowplatformTest, room_dw_fcastle_shinobeetle_3d,`
  `room_dw_fcastle_shinobeetle_encounter, room_dw_fcastle_sidepuzzle,`
  `room_dw_fcastle_terracotta_bonus,`
  `room_dw_fcastle_terracotta_encounter,`
  `room_dw_fcastle_terracotta_puzzle, room_dw_fcastle_top_ascent,`
  `room_dw_fcastle_top_challenge, room_dw_fcastle_top_descent,`
  `room_dw_fcastle_top_entrance, room_dw_fcastle_top_fountain,`
  `room_dw_fcastle_top_intro, room_dw_fcastle_top_pinkdoor,`
  `room_dw_fcastle_top_staircase_1, room_dw_fcastle_top_staircase_2,`
  `room_dw_fcastle_trainroom, room_dw_fcastle_ultradash,`
  `room_dw_fcastle_yellow_miniboss, room_dw_fcastle_yellowblue,`
  `room_dw_fcastle_yellowjail, room_dw_fcastle_zenlooker,`
  `room_dw_flowery_tree, room_dw_garden_aqua,`
  `room_dw_garden_aquadarkness, room_dw_garden_aquadash,`
  `room_dw_garden_aquadash_plat, room_dw_garden_aquahole,`
  `room_dw_garden_aquahole_left, room_dw_garden_aquaplatforming,`
  `room_dw_garden_aquashrine, room_dw_garden_aquatransition,`
  `room_dw_garden_cliffexit, room_dw_garden_diner,`
  `room_dw_garden_enemyrush, room_dw_garden_finalplatforming,`
  `room_dw_garden_finalplatforming_right, room_dw_garden_firstdash,`
  `room_dw_garden_fishingspot, room_dw_garden_floradinnencounter,`
  `room_dw_garden_flowerygardening, room_dw_garden_hardpressureplates,`
  `room_dw_garden_hopschef, room_dw_garden_hospital,`
  `room_dw_garden_intro, room_dw_garden_meetflowery,`
  `room_dw_garden_mushrooms, room_dw_garden_newdash,`
  `room_dw_garden_pedestal, room_dw_garden_platshortcut,`
  `room_dw_garden_ralseicupboard, room_dw_garden_riverchest,`
  `room_dw_garden_shearydodge, room_dw_garden_shearyguide,`
  `room_dw_garden_starwalkerdash, room_dw_garden_susiechase,`
  `room_dw_garden_wateringcan_aqua, room_dw_petaltest,`
  `room_dw_pink_encounter, room_dw_post_flowery_battle,`
  `room_dw_post_fountain_close, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_basketball, room_dw_ralsei_castle_front,`
  `room_dw_rhythm, room_dw_rhythm_countdown, room_floortex_test,`
  `room_GMS2_test, room_man, room_overworldBulletEnemyTest,`
  `room_plat_lab`

### Party record 2099

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 3 || global.char[1] == 3)                 {`
  `global.interact = 1`
- condition: `line 140; if (throwitem == 4) > if (`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer, room_climbtest,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_darkbulbTest, room_DARKempty, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_smallface_dark,`
  `room_dogplatforming, room_dw_castle_area_1, room_dw_castle_cafe,`
  `room_dw_castle_church_climb, room_dw_castle_church_entrance,`
  `room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_music,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_tv, room_dw_castle_tv_kikky,`
  `room_dw_castle_tv_mike, room_dw_castle_tv_rhythm,`
  `room_dw_castle_west_cliff, room_dw_cliff_bonuscombat,`
  `room_dw_cliff_bunnyfarm, room_dw_cliff_climbrefresher,`
  `room_dw_cliff_cutdown_tutorial, room_dw_cliff_dash_runner,`
  `room_dw_cliff_eastcliff, room_dw_cliff_finaldash,`
  `room_dw_cliff_gardentransition_new, room_dw_cliff_kawkawdash,`
  `room_dw_cliff_netskieclimb, room_dw_cliff_netskieclimb_behind,`
  `room_dw_cliff_precipice, room_dw_cliff_seth_miniboss,`
  `room_dw_cliff_sethaqua_battle, room_dw_cliff_shicave,`
  `room_dw_cliff_shop, room_dw_cliff_silver_hammer,`
  `room_dw_cliff_twirlflowerplatforming, room_dw_cliff_twirlflowerwind,`
  `room_dw_cliff_verticalwind, room_dw_cliff_verticalwind_post,`
  `room_dw_cliff_yellowcave, room_dw_dogballoon, room_dw_fcastle_asgore,`
  `room_dw_fcastle_blueroom, room_dw_fcastle_bounce_1,`
  `room_dw_fcastle_bounce_3, room_dw_fcastle_bromides,`
  `room_dw_fcastle_cafe, room_dw_fcastle_dangerous_platforming,`
  `room_dw_fcastle_entrance, room_dw_fcastle_final_save,`
  `room_dw_fcastle_flowerclimb, room_dw_fcastle_flowerclimb_for_tiling,`
  `room_dw_fcastle_flowery, room_dw_fcastle_flowerydash,`
  `room_dw_fcastle_foxhunt, room_dw_fcastle_foxhunt_chaos,`
  `room_dw_fcastle_foxhunt_secret, room_dw_fcastle_foxhunt_socks,`
  `room_dw_fcastle_foxhunt_terakota, room_dw_fcastle_foyer,`
  `room_dw_fcastle_fusumadodge, room_dw_fcastle_gloves_tower,`
  `room_dw_fcastle_green_checkpoint,`
  `room_dw_fcastle_green_orange_battle, room_dw_fcastle_heldmushrooms,`
  `room_dw_fcastle_left_penultimate, room_dw_fcastle_left_twodoors,`
  `room_dw_fcastle_left_wing_floweryscene,`
  `room_dw_fcastle_obscured_bullets, room_dw_fcastle_onsen,`
  `room_dw_fcastle_orange_gauntlet,`
  `room_dw_fcastle_orange_puppet_introduction,`
  `room_dw_fcastle_partyjail, room_dw_fcastle_pinkroom,`
  `room_dw_fcastle_pinkshop, room_dw_fcastle_post_party_jail,`
  `room_dw_fcastle_right_endingscene, room_dw_fcastle_right_penultimate,`
  `room_dw_fcastle_right_puzzle,`
  `room_dw_fcastle_right_wing_floweryscene, room_dw_fcastle_sandtrap,`
  `room_dw_fcastle_second_diner, room_dw_fcastle_seth_encounter,`
  `room_dw_fcastle_shadowplatformTest, room_dw_fcastle_shinobeetle_3d,`
  `room_dw_fcastle_shinobeetle_encounter, room_dw_fcastle_sidepuzzle,`
  `room_dw_fcastle_terracotta_bonus,`
  `room_dw_fcastle_terracotta_encounter,`
  `room_dw_fcastle_terracotta_puzzle, room_dw_fcastle_top_ascent,`
  `room_dw_fcastle_top_challenge, room_dw_fcastle_top_descent,`
  `room_dw_fcastle_top_entrance, room_dw_fcastle_top_fountain,`
  `room_dw_fcastle_top_intro, room_dw_fcastle_top_pinkdoor,`
  `room_dw_fcastle_top_staircase_1, room_dw_fcastle_top_staircase_2,`
  `room_dw_fcastle_trainroom, room_dw_fcastle_ultradash,`
  `room_dw_fcastle_yellow_miniboss, room_dw_fcastle_yellowblue,`
  `room_dw_fcastle_yellowjail, room_dw_fcastle_zenlooker,`
  `room_dw_flowery_tree, room_dw_garden_aqua,`
  `room_dw_garden_aquadarkness, room_dw_garden_aquadash,`
  `room_dw_garden_aquadash_plat, room_dw_garden_aquahole,`
  `room_dw_garden_aquahole_left, room_dw_garden_aquaplatforming,`
  `room_dw_garden_aquashrine, room_dw_garden_aquatransition,`
  `room_dw_garden_cliffexit, room_dw_garden_diner,`
  `room_dw_garden_enemyrush, room_dw_garden_finalplatforming,`
  `room_dw_garden_finalplatforming_right, room_dw_garden_firstdash,`
  `room_dw_garden_fishingspot, room_dw_garden_floradinnencounter,`
  `room_dw_garden_flowerygardening, room_dw_garden_hardpressureplates,`
  `room_dw_garden_hopschef, room_dw_garden_hospital,`
  `room_dw_garden_intro, room_dw_garden_meetflowery,`
  `room_dw_garden_mushrooms, room_dw_garden_newdash,`
  `room_dw_garden_pedestal, room_dw_garden_platshortcut,`
  `room_dw_garden_ralseicupboard, room_dw_garden_riverchest,`
  `room_dw_garden_shearydodge, room_dw_garden_shearyguide,`
  `room_dw_garden_starwalkerdash, room_dw_garden_susiechase,`
  `room_dw_garden_wateringcan_aqua, room_dw_petaltest,`
  `room_dw_pink_encounter, room_dw_post_flowery_battle,`
  `room_dw_post_fountain_close, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_basketball, room_dw_ralsei_castle_front,`
  `room_dw_rhythm, room_dw_rhythm_countdown, room_floortex_test,`
  `room_GMS2_test, room_man, room_overworldBulletEnemyTest,`
  `room_plat_lab`

### Party record 2100

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)                     {                         myx[i] += 15`
- condition: `line 23; if (i_ex(global.charinstance[i])) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2101

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)                     {                         myx[i] += 15`
- condition: `line 27; if (global.char[i] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2102

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `= 2 || global.char[1] == 2 || global.char[2] == 2)     {`
  `sus = 0`
- condition: `line 245; if (global.charauto[2] == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2103

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `= 2)         {             sus = 1`
- condition: `line 248; if (global.char[0] == 2 || global.char[1] == 2 ||`
  `global.char[2] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2104

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `= 2)         {             sus = 2`
- condition: `line 252; if (global.char[1] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2105

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 1)     {         havechar[0] = 1`
- condition: `line 199; if (global.char[i] != 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2106

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 2)     {         havechar[1] = 1`
- condition: `line 208; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2107

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 3)     {         havechar[2] = 1`
- condition: `line 217; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2108

- chapter: `5`
- phase: `global.char[i]`
- field: `global.char[i]`
- expression: `= 4)     {         havechar[3] = 1`
- condition: `line 226; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2109

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             if`
  `(global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoor...`
  `== 2 ||`
  `global.actactor[global.bmenucoord[11][global.charturn]][global.bmenucoord...`
  `== 4)             {                 if (havechar[1] == 0 ||`
  `global.hp[2] <= 0)                 {`
  `canpress = 0`
- condition: `line 888; if (cango == 1) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2110

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)                     {                         for (i = 0`
- condition: `line 1154; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2111

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         for (i = 0`
- condition: `line 1167; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2112

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         for (i = 0`
- condition: `line 1180; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2113

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         for (i = 0`
- condition: `line 1193; if (actcoord > 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2114

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)                     {                         __actname =`
  `global.actnamesus[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 185; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2115

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)                     {                         __actname =`
  `global.actnameral[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 189; if (global.char[global.charturn] == 2) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2116

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)                     {                         __actname =`
  `global.actnamenoe[i][global.bmenucoord[2][global.charturn]]`
- condition: `line 193; if (global.char[global.charturn] == 3) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2117

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             canact[__acti] =`
  `global.canact[thisenemy][__acti]`
- condition: `line 469; if (global.bmenuno == 9 && global.myfight == 0) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2118

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 2)         {             canact[__acti] =`
  `global.canactsus[thisenemy][__acti]`
- condition: `line 477; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2119

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 3)         {             canact[__acti] =`
  `global.canactral[thisenemy][__acti]`
- condition: `line 485; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2120

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 4)         {             canact[__acti] =`
  `global.canactnoe[thisenemy][__acti]`
- condition: `line 493; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2121

- chapter: `5`
- phase: `global.char[global.charturn]`
- field: `global.char[global.charturn]`
- expression: `= 1)         {             chartime =`
  `global.actactor[global.bmenucoord[11][global.charturn]][i]`
- condition: `line 523; if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2122

- chapter: `5`
- phase: `global.char[0]`
- field: `global.char[0]`
- expression: `1`
- condition: `line 4; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2123

- chapter: `5`
- phase: `global.char[1]`
- field: `global.char[1]`
- expression: `2`
- condition: `line 5; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2124

- chapter: `5`
- phase: `global.char[2]`
- field: `global.char[2]`
- expression: `0`
- condition: `line 6; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2125

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 928; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2126

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 929; if (global.flag[215] == 1)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2127

- chapter: `5`
- phase: `global.char[dx]`
- field: `global.char[dx]`
- expression: `= 2)                 {                     if`
  `(global.charcond[dx] != 5)                     {`
  `global.charcond[dx] = 5`
- condition: `line 245; if (scr_monsterpop() > 1 && scr_havechar(2)) > if (`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2128

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 517; if (subcontimer == 160)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2129

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 659; if (subcontimer == 200)`
- status: `unplaced-or-uncertain`
- rooms: `not room-owned`

### Party record 2130

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 12; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_right_wing_floweryscene`

### Party record 2131

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 91; if (global.plot == 16 && global.chapter == 2)`
- status: `production`
- rooms: `room_dw_garden_aquadash, room_dw_garden_aquadash_plat`

### Party record 2132

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1, 1`
- condition: `line 10; if (scr_debug())`
- status: `production`
- rooms: `room_dw_fcastle_partyjail`

### Party record 2133

- chapter: `5`
- phase: `setparty-call`
- field: `setparty-call`
- expression: `1`
- condition: `line 16; if (plot_check_on == false || global.plot < plot_post)`
- status: `production`
- rooms: `room_dw_fcastle_partyjail`

### Party record 2134

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 80; if (global.plot == 16 && global.chapter == 2)`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Party record 2135

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 12; if (global.chapter != 2 || global.flag[316] == 1)`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 2136

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `2`
- condition: `line 17; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 2137

- chapter: `5`
- phase: `getchar-call`
- field: `getchar-call`
- expression: `3`
- condition: `line 18; if (instance_exists(obj_caterpillarchara))`
- status: `production`
- rooms: `room_hospital_rudy`

### Party record 2138

- chapter: `5`
- phase: `losechar-call`
- field: `losechar-call`
- expression: `—`
- condition: `line 292; unconditional in entry`
- status: `production`
- rooms: `room_town_north`
