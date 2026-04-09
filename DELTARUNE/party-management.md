# Party Management

Party composition is managed through `scr_setparty`, `scr_getchar`, `scr_losechar`, and the caterpillar follower system.

---

## Core Scripts

| Script | Purpose |
|---|---|
| `scr_setparty` | Sets the active party and creates follower chain |
| `scr_getchar` | Adds a character to the party array |
| `scr_losechar` | Removes all non-Kris party members |
| `scr_havechar` | Checks if a character is in the party |
| `scr_makecaterpillar` | Creates a follower instance behind the leader |
| `scr_makecaterpillar` | Creates follower with alignment offsets |
| `scr_caterpillar_facing` | Updates all follower facing directions |
| `scr_caterpillar_interpolate` | Smooths follower positions |

---

## `scr_setparty`

Present in Chapters 1, 3, and 4. Chapter 2 does not have this script (party is set through other means).

| Chapter | Signature |
|---|---|
| 1 | `scr_setparty(arg0 = false, arg1 = false)` — Susie, Ralsei only |
| 3 | `scr_setparty(arg0 = undefined, arg1 = undefined, arg2 = undefined)` — adds Noelle slot |
| 4 | `scr_setparty(arg0 = false, arg1 = false, arg2 = false)` — same 3 args |

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

| Character | Light World (h, v) | Dark World (h, v) |
|---|---|---|
| Susie | 3, 6 | 6, 16 |
| Ralsei | 2, 12 | 2, 12 |
| Noelle | 2, 9 | 4, 18 |

The offset positions the follower behind Kris. Larger offsets in Dark World account for the doubled sprite scale.

---

## Character IDs

| ID | Character |
|---:|---|
| 0 | *(empty)* |
| 1 | Kris |
| 2 | Susie |
| 3 | Ralsei |
| 4 | Noelle |

---

## `global.char[]` Array

The party array maps battle slots to character ids:

| Index | Slot |
|---:|---|
| 0 | Slot 0 (always Kris: `global.char[0] = 1`) |
| 1 | Slot 1 (first follower) |
| 2 | Slot 2 (second follower) |

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

| Variable | Purpose |
|---|---|
| `global.char[i]` | Character id in party slot |
| `global.charinstance[i]` | Instance reference to the character's battle hero object |
| `global.charaction[i]` | Current battle action for the party slot |
| `global.charweapon[char_id]` | Equipped weapon |
| `global.chararmor1[char_id]` | Equipped armor slot 1 |
| `global.chararmor2[char_id]` | Equipped armor slot 2 |

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Change party composition | Call `scr_setparty(susie, ralsei, noelle)` |
| Add a 4th follower | Extend `scr_setparty` with a new argument and `scr_getchar` call |
| Change follower spacing | Edit alignment offsets in `scr_setparty` |
| Change following behavior | Edit `scr_caterpillar_interpolate` |
| Check party membership | `scr_havechar(char_id)` returns true/false |