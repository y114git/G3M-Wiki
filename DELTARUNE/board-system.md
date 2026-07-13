# Board System

The board game is a Chapter 3 runtime, not a shared Chapter 3–5 mode. Chapter 4
retains only `obj_board_writer` and `obj_board_writer_stay`; Chapter 5 has no
board controller or board room.

## Runtime and reachability

Chapter 3 has 17 board rooms classified as production reachable, one conditional
sword-introduction room, and eight debug or test rooms. The runtime root is
`obj_board_controller`. It creates a 32-pixel `mp_grid`, initializes turn and
board state, and chooses the room-specific violence rule. Movement uses
`obj_mainchara_board`; `obj_board_playercamera`, the two board writers, and the
board transition objects replace or wrap their ordinary-overworld equivalents.

Chapter 4's two writers are retained code. No board room or board controller is
present, so their presence is not runtime basis that Chapter 4 runs the game. No
Chapter 5 board extension was found.

## State and combat

`scr_board_enemy_init` gives the dedicated enemy family its local HP, damage,
aggression, contact hitbox, path, hurt sprite, and sword-immunity state. This is
separate from `scr_monstersetup`. `scr_board_enemy_sword_collision` ends paths,
applies the hurt window, and either damages, detects, or clangs according to the
sword level and target state. Ice creates `obj_pushableblock_board` for ordinary
targets while selected fish and flower variants use direct destruction.

The controller owns `global.turnnumber`, `global.grid`, `global.cell_size`, and
`global.flag[1116]`. `scr_board_score` creates `obj_board_scoreAdder`;
`scr_board_score_set(value)` writes `global.flag[1044]`. Board defeat, health,
checkpoint, warp, camera, and game-over objects complete a parallel overworld
lifecycle.

## Presentation

Board presentation is object-led: afterimages, flashes, markers and marker
glows, smoke and break poofs, ice-spell snowflakes, square/star transitions,
screen-color changes, shadow spotlights, water and waterfall layers, camera
glows, score popups, and board-specific writers. Sprite animation state remains
on each object through `sprite_index`, `image_index`, `image_speed`, blend,
alpha, scale, and depth. The controller does not provide a universal animation
graph.

## Practical extension

To add a production enemy, duplicate a placed `obj_board_enemy_*` from the
target board room, call `scr_board_enemy_init` in Create, then override `hp`,
`damage`, `sword_immunity_lv`, `hurt_sprite`, and movement state. Add its solids
to the controller grid, handle sword and ice conversion explicitly, and test
normal, sword-route, checkpoint, room-reentry, and game-over paths. Do not copy
the retained Chapter 4 writers as though they bootstrap the board runtime.

## Related pages

- [Overworld Movement](overworld.md)
- [Rooms, Events, and Progression](rooms-events-and-progression.md)
- [Rendering, Animation, and Audio](rendering-animation-audio.md)
