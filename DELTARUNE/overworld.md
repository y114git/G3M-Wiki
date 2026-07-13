# Overworld Runtime

The numbered chapters build their navigable world from rooms, placed objects,
and per-room controller objects. `obj_mainchara` is the shared player root;
`obj_overworldc` supplies room-level overworld state. The complete route catalog
is on [Rooms, Events, and Progression](rooms-events-and-progression.md).

## Player Movement

`obj_mainchara` reads directional button helpers into `press_l`, `press_r`,
`press_u`, and `press_d`, resolves movement against solids, updates facing and
walk animation, and owns the interaction buffers. Its conventional speeds are
`3` in the Light World and `4` in the Dark World. Later payloads extend the same
controller rather than replacing it:

### Chapter 1

**Important additions:** `autorun`, `battlemode`, sub-pixel movement, facing
sprites

### Chapter 2

**Important additions:** `sliding`, `swordmode`, `stop_movement`, safer entrance
fallback

### Chapter 3

**Important additions:** `climbing`, `floorheight`, `canrun`, `freeze`

### Chapter 4

**Important additions:** church clothing, tower shake, climbing and darkness
states

### Chapter 5

**Important additions:** platforming, dash, wind, climb, cut-down and special
follower states

Movement is state-driven. A room gimmick normally sets a player field or
temporarily delegates movement to a controller; it does not create another
general-purpose player class. Chapter 5's garden, cliff, and flower-castle rooms
are the clearest examples.

## Collision, Depth, and Layers

Placed `obj_solidblock` instances provide much of the rectangular collision.
Specialized parents and room objects add slopes, moving platforms, water,
climbable geometry, darkness hazards, bullets, and scripted blockers. Visual
depth is a mixture of instance `depth`, automatic Y-based depth, foreground
layers, and explicit cutscene commands such as `c_depth` and `c_autodepth`.
Consequently, moving only a background or tile layer does not move collision.

Room JSON also records view dimensions, follow borders, layer depth, tile
assets, and instance placement. Treat those values as part of the room, not as
properties of its background sprite.

## Doors and Room Entry

Placed door controllers use `doorRoom` and numeric `doorEntrance` fields,
perform their freeze/fade flow, and let the destination controller place Kris at
the matching marker. Some inherited Light World doors still use letter-like
marker values, but Chapter 5 platforming routes use numeric entrances. Chapter 2
and later can fall back to `obj_markerAny`, then to the room center.
`global.currentroom` and room history support save repair and return
transitions.

A complete Chapter 5 pattern configures the placed `obj_doorAny` or
`obj_doorAnyHorz` in its room pre-create code:

```gml
doorRoom = room_dogplatforming;
doorEntrance = 3;
doorFadeMusic = 1;
doorAllowPlatmode = false;
```

The door object performs collision/interact, input freeze, fade, room change,
and release. The destination must contain entrance 3 or an accepted fallback. Do
not replace this with a naked `room_goto()`: it bypasses the controller's
freeze/fade and platform-mode cleanup.

## Interaction

The confirm buffer in `obj_mainchara` finds eligible nearby interactables; room
and NPC objects then dispatch their own branch. `global.interact` is often the
selected instance. Typical interactables include doors, save points, chests,
switches, signs, NPCs, shops, and chapter-specific puzzle controls. An NPC
branch should gate on a durable flag and populate localized text:

```gml
if (scr_flag_get(1200) == 0) {
    scr_flag_set(1200, 1);
    global.msg[0] = stringsetloc("* First visit.%%", "mod_slash_npc_first_0");
} else {
    global.msg[0] = stringsetloc("* Welcome back.%%", "mod_slash_npc_repeat_0");
}
scr_writetext();
```

Use a free flag only after checking the chapter's flag consumers. See
[Dialogue System](dialogue-system.md) for message ownership.

## Camera

Rooms enable a view and establish its dimensions, port, follow borders, and
optional follow target. The normal camera follows the player; cutscenes can pan
to coordinates or objects and change pan speed. Cleanup must restore the player
target and automatic follow. Special modes use dedicated controllers for board,
climb, platforming, chase, tower, and battle framing.

## Followers

The caterpillar party is created and reordered by party helpers, while follower
objects replay stored player positions with per-member spacing. Cutscenes can
convert actors to party members and back. Chapter 5 sometimes suppresses or
restages followers around vertical platforming. A room transition must preserve
the party state or deliberately rebuild it; merely placing Kris is insufficient.

## Encounters and Hazards

Touch encounters generally freeze overworld motion, stage enemies, transfer the
current party and encounter data into battle, then restore or remove the
overworld encounter according to the result. Overworld bullet zones instead keep
Kris in the room and use `obj_overworldheart` plus bullet parents. Chapters 4
and 5 add darkness, climb, platform, wind, dash, and obstacle controllers whose
failure path may reposition the player without changing rooms.

## Related Pages

- [Rooms, Events, and Progression](rooms-events-and-progression.md)
- [Cutscene System](cutscene-system.md)
- [Party Management](party-management.md)
- [Battle System](battle-system.md)
- [Global Variables](global-variables.md)
