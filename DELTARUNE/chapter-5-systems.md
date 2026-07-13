# Chapter 5 Systems

Chapter 5 keeps the ordinary overworld, cutscene, battle, save and rhythm
contracts, then adds a room-backed platform-action layer across the cliffs,
garden and flower castle. These player-facing systems are distinct from retained
shared code, debug tools, legacy objects, and unresolved definitions.

## Platform-action lifecycle

`obj_plat_game`, `obj_plat_player`, `obj_plat_camera` and
`obj_plat_actors_renderer` form the mode root. Floors, slopes, moving and
rotating platforms, loops, ziplines, hooks, vine hooks, umbrellas, wind and
petal platforms extend movement. Camera clamp, nudge, steady and target zones
stage rooms independently of the normal overworld camera. Checkpoints,
anti-softlock zones, pause helpers, room swap helpers and action blockers cover
failure, pause and handoff.

`obj_platswap` and `scr_platswap_transition` bridge ordinary rooms and the
platform representation. Swap helpers, shipped props, wall textures and fall
cues rebuild the visible scene. Retained exporter/debug objects are tooling, not
player-facing systems.

## Combat and route interaction

Platform combat uses `obj_plat_bullet` plus red, blue and yellow variants,
emitters, zones and path previews. `scr_pause_plat_bullet` and its inverse keep
hazards synchronized with pauses. Attack queues, attack triggers, combat
starters, hitboxes, cooldown UI and friendly bullets extend the encounter
lifecycle without replacing ordinary battle rooms.

Enemy families include Aqua bouncers, swords and miniboss variants; green-food,
orange, yellow, gun, glove, wallet, book and Seth variants. Cliff rooms
explicitly include Seth miniboss and Seth/Aqua battle routes. The ordinary
Chapter 5 battle controller separately adds forced actions, sprite
reset/scale/ACT flash, bullet inheritance and healing, and platform-miniboss
cases. A platform enemy object is not automatically an ordinary
`scr_monstersetup` case.

Garden and flower systems track recruit state, flower spawn/despawn, death,
respawn and cutscene-watched flags. Flowery adds a dedicated ACT menu, battle
transition, bullets, shooter/runner/tower attacks, thrown-Kris sequence, voice
clips and item-use handler. Route-dependent inventory and save behavior remains
owned by the shared save and progression systems.

## Pink secret encounter

The Flower Castle pink-room door enters `room_dw_pink_encounter`, which places
`obj_dw_pink_encounter` and starts encounter `224`. The encounter creates
`obj_pink_enemy`; Chapter 5 maps secret result flag `1908` to this completion
chain. The controller sets result `1908` to `2`, sets progression flag `1815`,
calls the Chapter 5 Shadow Crystal helper, and grants key item `13`.

Pink uses `obj_purplecontrols` for buffered lane, grid, rotating-grid, maze,
tunnel, and node movement. The controller synchronizes the hidden battle heart
with its discrete position. Pink has separate Kris, Susie, and Ralsei ACT
handlers. One transition resets `phaseturns` and adds `25` mercy.

After battle startup, the room controller checks `global.console`. When it is
true, the controller calls `obj_border_controller.show_border()`.

Flowery's `obj_ch5_DW29` controller starts encounter `225`, and the encounter
creates `obj_flowery_enemy`. This confirms an implemented battle and its local
orange-heart simulation. The dispatch does not establish whether players can
bypass the route or whether Flowery has a separate secret-result identity.

## Event families and rooms

Player-facing families with room runtime basis include:

- cliff climb, dash, cut-down, wind, petal, cave, shop and miniboss sequences;
- garden dash, Aqua shrine/hole/platforming, diner, hospital, fishing, pressure
  plates, enemy rush, Flowery meeting/gardening and final platforming;
- flower-castle danger and shadow-platforming sequences;
- castle-town, church-climb, dungeon, music and castle-TV/rhythm continuations;
- returning Light World church rooms and the Chapter 5 video room.

`room_dogplatforming` is a production-referenced optional Flower Castle
challenge. Shadow-platform tests and floor-texture debuggers remain debug-only;
unrouted definitions remain uncertain rather than player-facing.

## Presentation extensions

Cliff parallax and color helpers, self-shadow and sun-shadow lists, live shader
replacement, garden lights, wind particles, dash lines, platform VFX, castle
reflections, floor-texture layers and actor render surfaces form the distinctive
visual stack. Music beat events can cue instances and user events; Flowery voice
routing and platform hit/UI sounds remain separate from room music.

## Practical extension

To add a cliff challenge, start from a production cliff room. Place
`obj_plat_game`, player/camera roots, floor or slope assets, one checkpoint and
the appropriate camera zones. Add hazards through a bullet emitter and zone,
register pause behavior, then connect completion to an existing room transition
and explicit plot/flag write. Add renderer layers and shader hooks only after
testing surface recreation, pause, death, checkpoint reload, room return and
both relevant route states.

## Related pages

- [Rendering, Animation, and Audio](rendering-animation-audio.md)
- [Rhythm System](rhythm-system.md)
- [Platform Differences](platform-differences.md)
