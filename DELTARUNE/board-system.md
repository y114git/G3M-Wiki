# Board System

The board-game layer is Chapter 3's largest runtime addition. It replaces the standard overworld with a grid-based movement system that has its own controller, enemy family, combat, camera, scoring, and writer variants.

---

## Core Scripts

| Script | Purpose |
|---|---|
| `scr_board_enemy_init` | Initializes board enemy instance variables |
| `scr_board_enemy_sword_collision` | Sword-hit detection and response |
| `scr_board_enemy_hurt_state` | Enemy hurt state machine |
| `scr_board_enemy_step_init` | Enemy step initialization |
| `scr_board_enemy_reset` | Enemy reset to initial state |
| `scr_board_score` | Score popup creation |
| `scr_board_score_set` | Directly sets score flag |
| `scr_board_populatevars` | Resolves character references |
| `scr_board_gridreset` | Resets the navigation grid |
| `scr_board_checklocation` | Location-based event checks |
| `scr_board_battlehealth` | Battle health display |
| `scr_board_caterpillar_interpolate` | Board-specific follower smoothing |
| `scr_board_instawarp` | Instant character teleport |
| `scr_board_flash` | Screen flash effect |
| `scr_board_marker` | Visual marker/particle creation |
| `scr_board_sword_repeat` | Sword attack repeat logic |
| `scr_board_forcethrow` | Forced throw mechanics |
| `board_tilex` | Tile-to-pixel coordinate conversion |

---

## Controller Bootstrap

`obj_board_controller` Create establishes runtime state:

```gml
global.darkzone = 1;
global.turnnumber = 1;
violence = true;
if (room == room_board_1_sword)
    violence = false;
global.cell_size = 32;
global.grid_width = room_width / global.cell_size;
global.grid_height = room_height / global.cell_size;
global.grid = mp_grid_create(0, 0, global.grid_width, global.grid_height,
    global.cell_size, global.cell_size);
global.flag[1116] = 0;
global.battlegrade[30] = "";
```

Key properties:

| Variable | Purpose |
|---|---|
| `global.darkzone` | Always `1` — board is Dark World |
| `global.turnnumber` | Current board turn |
| `violence` | Controls enemy aggression (room-specific) |
| `global.cell_size` | Grid cell size (32px) |
| `global.grid` | GameMaker `mp_grid` for pathfinding |
| `global.flag[1116]` | Board state flag |
| `global.battlegrade[30]` | Battle grade string |

---

## Board Enemy System

### `scr_board_enemy_init`

All board enemies are initialized with:

```gml
function scr_board_enemy_init()
{
    damage = 1;
    hp = 1;
    maxhp = hp;
    xp_given = 1;
    state = "init";
    drop_candy = true;
    show_outline = false;
    sword_immunity_lv = 1;
    aggressive = obj_board_controller.violence;
    active = true;
    active_hitbox = aggressive;
    distance_to_become_aggressive = 90;
    spd = 3;
    damage_hitbox = instance_create(x + 16, y + 16, obj_board_enemy_contact_hitbox);
    damage_hitbox.parentid = id;
    path = path_add();
    hurt_sprite = spr_board_monster_hurt;
}
```

Board enemies are **not** traditional battle monsters. They have their own HP/damage/state model separate from `scr_monstersetup`.

### Enemy Instance Variables

| Variable | Default | Purpose |
|---|---|---|
| `hp` | 1 | Hit points (some enemies use `999` for invulnerability) |
| `damage` | 1 | Contact damage to player |
| `xp_given` | 1 | Score/XP on defeat |
| `state` | `"init"` | Current AI state |
| `aggressive` | from `violence` | Whether the enemy attacks |
| `active_hitbox` | from `aggressive` | Whether the contact hitbox deals damage |
| `sword_immunity_lv` | 1 | Minimum sword level needed to damage |
| `drop_candy` | true | Whether the enemy drops candy on defeat |
| `spd` | 3 | Movement speed |
| `distance_to_become_aggressive` | 90 | Proximity trigger distance |
| `hurttimer` | 0 | Invulnerability frames after hit |
| `hitdir` | -1 | Direction of the last hit |
| `dontmoveduringhurt` | false | Freeze position during hurt state |

### Enemy Types

Board rooms spawn specific enemy objects:

| Object | Description |
|---|---|
| `obj_board_enemy_monster` | Standard board monster |
| `obj_board_enemy_deer` | Deer (following behavior, ice-spell interaction) |
| `obj_board_enemy_bluebird` | Blue bird (room-specific sword immunity) |
| `obj_board_enemy_bluefish` | Blue fish (ice interaction variant) |
| `obj_board_enemy_yellowflower` | Yellow flower (ice interaction variant) |
| `obj_board_enemy_bluebird_board1` | Board 1-specific blue bird variant |

---

## Sword Combat

### `scr_board_enemy_sword_collision`

The sword collision system checks three conditions:

1. **Standard hit** — sword level ≥ enemy `sword_immunity_lv`:
   - Ends enemy path
   - Sets `hurttimer = 10`
   - Decrements HP (unless `hp == 999`)
   - Disables contact hitbox during hurt

2. **Detection-only hit** — hitbox has `detectiononly == true`:
   - Plays sword sound effect
   - Sets `swordbuffer = 8` on Kris
   - No damage dealt

3. **Immune hit** — sword level < `sword_immunity_lv`:
   - Plays metal clang sound
   - Sets hurt timer but no damage

### Gray Enemies

Enemies with `image_blend == c_gray` are invulnerable to swords — hits produce a metal sound and knockback with no damage.

### Ice Spell Interaction

Board enemies can be frozen by `obj_board_enemy_deer_ice_spell`:

- Standard enemies become pushable ice blocks (`obj_pushableblock_board`)
- Blue fish and yellow flowers are destroyed directly
- Snowflake particle effects spawn on freeze

---

## Score System

### `scr_board_score`

```gml
function scr_board_score(arg0)
{
    var scoreadder = instance_create(x, y, obj_board_scoreAdder);
    scoreadder.scoreamount = arg0;
}
```

Creates a floating score popup at the event position.

### `scr_board_score_set`

```gml
function scr_board_score_set(arg0)
{
    global.flag[1044] = arg0;
}
```

Board score is stored in `global.flag[1044]`.

### Battle Grade

`global.battlegrade[30]` stores the final battle grade string (set by the controller after board segments).

---

## Violence Rules

Enemy aggression is room-driven:

```gml
Violence = true;
if (room == room_board_1_sword)
    violence = false;
```

When `violence = false`:
- `aggressive = false` — enemies don't chase
- `active_hitbox = false` — contact doesn't deal damage
- Enemies use passive AI behaviors

---

## Grid Pathfinding

The controller creates a `mp_grid` at startup covering the entire room at 32px cell resolution. Enemies create individual `path = path_add()` instances and compute routes through `mp_grid_path`.

| Variable | Purpose |
|---|---|
| `global.grid` | Shared GameMaker motion planning grid |
| `global.cell_size` | 32px cell size |
| `global.grid_width` | Room width ÷ cell size |
| `global.grid_height` | Room height ÷ cell size |

Board-specific collision uses grid cells rather than pixel-level collision.

---

## Character References

`scr_board_populatevars` resolves named character references:

```gml
function scr_board_populatevars()
{
    // Finds obj_mainchara_board instances by name
    // Sets kris, susie, ralsei instance references
}
```

Board movement uses `obj_mainchara_board` instead of the standard `obj_mainchara`. Each party member has a named instance.

---

## Camera System

`obj_board_playercamera` handles follow-camera and scripted staging:

| Property | Purpose |
|---|---|
| `createphoto` | Photo mode trigger |
| `addgreenblocks` | Environment modification flag |
| `flagtoset` | Flag to set on camera event |
| `controllable` | Whether the player can move the camera |
| `notalk` | Disable dialogue during camera sequence |

---

## Board Writer

`obj_board_writer` is a board-specific text display object. It integrates with the show/TV-style presentation used in Chapter 3's board segments without disrupting the standard `obj_writer` lifecycle.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a board enemy type | Create a new `obj_board_enemy_*` object, call `scr_board_enemy_init` in Create |
| Change enemy HP/damage | Edit defaults in `scr_board_enemy_init` or per-object Create overrides |
| Change sword requirements | Edit `sword_immunity_lv` per enemy |
| Change pathfinding grid | Edit `global.cell_size` in `obj_board_controller` Create |
| Change scoring | Edit `scr_board_score` and `global.flag[1044]` |
| Change violence rules | Edit the room-based `violence` branches in controller Create |
| Add ice interactions | Edit `scr_board_enemy_sword_collision` ice spell section |

---

## Relationship To Other Pages

- [Overworld Movement](overworld.md) explains the standard non-board player controller
- [Dialogue System](dialogue-system.md) explains the shared text runtime that board writers build on
- [Global Variables](global-variables.md) for `global.flag[1044]` (board score) and `global.flag[1116]` (board state)