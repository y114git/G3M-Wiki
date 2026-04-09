# Board System

The board-game layer is one of Chapter 3's biggest runtime additions. It is not a minor minigame glued on top of the existing overworld. It has its own controller objects, enemy runtime, camera helpers, pickup logic, writer variants, and progression state.

The main roots are:

- `scripts/scr_board_*`
- `objects/obj_board_controller`
- `objects/obj_board_enemy_*`
- `objects/obj_board_playercamera`
- `objects/obj_board_writer`

This system is primarily Chapter 3-specific.

---

## Controller Bootstrap

`obj_board_controller/Create_0.gml` establishes core runtime state:

```gml
global.darkzone = 1;
global.turnnumber = 1;
violence = true;
if (room == room_board_1_sword)
    violence = false;
global.cell_size = 32;
global.grid_width = room_width / global.cell_size;
global.grid_height = room_height / global.cell_size;
global.grid = mp_grid_create(0, 0, global.grid_width, global.grid_height, global.cell_size, global.cell_size);
global.flag[1116] = 0;
global.battlegrade[30] = "";
```

Important consequences:

- the board layer still identifies itself as Dark World runtime through `global.darkzone`
- it introduces a grid-based movement model
- it uses normal save-state families like `global.flag[]`
- it supports room-level rules through `violence`

For the underlying GameMaker grid API, see:

- https://manual.gamemaker.io/monthly/en/GameMaker_Language/GML_Reference/Movement_And_Collisions/Motion_Planning/mp_grid_create.htm

---

## Board Enemy Initialization

`scr_board_enemy_init` sets up board enemies as their own runtime family:

```gml
damage = 10;
hp = 1;
xp_given = 0;
state = "init";
drop_candy = false;
show_outline = false;
sword_immunity_lv = 0;
spawnerid = noone;
aggressive = obj_board_controller.violence;
active = true;
active_hitbox = true;
distance_to_become_aggressive = 90;
spd = 3;
path = path_add();
instance_create(x, y, obj_board_enemy_contact_hitbox);
```

These are not normal battle monsters. They have their own HP/damage/state machine/pathing/contact-hitbox model.

---

## Grid, Paths, and Chase Logic

The board controller owns `global.grid`, while enemies create their own `path`. The implied runtime model is:

1. controller defines navigable space
2. enemies compute or rebuild movement routes on that grid
3. enemies follow local path state according to board AI

---

## Violence Rules

The line:

```gml
aggressive = obj_board_controller.violence;
```

combined with the room-specific `violence = false` branch shows that enemy temperament is rule-driven by board-room setup, not only by enemy type.

---

## Camera / Photo Runtime

`obj_board_playercamera/Create_0.gml` carries more than simple follow-camera state. It also includes fields such as:

- `createphoto`
- `addgreenblocks`
- `flagtoset`
- `controllable`
- `notalk`

So the board camera layer also handles scripted staging, environment changes, and temporary control restrictions.

---

## Writer and UI Variants

Chapter 3 introduces board-specific writer objects such as `obj_board_writer`. This keeps the system visually integrated with show-style scenes without abandoning the broader text runtime completely.

---

## Chapter Differences

## Chapter 3

- primary home of the board runtime
- full controller/enemy/camera/writer stack

## Chapter 4

- does not replace the normal overworld with the board layer
- board logic is no longer a dominant world framework

---

## Modding Implications

- If board enemy collisions fail, inspect the spawned contact hitbox.
- If pathing breaks, inspect both `global.grid` and enemy `path` state.
- If aggression looks wrong, inspect `obj_board_controller.violence` before rewriting AI.

---

## Relationship To Other Pages

- [Overworld Movement](overworld.md) explains the standard non-board player controller.
- [Dialogue System](dialogue-system.md) explains the shared text runtime that board writers build on.
