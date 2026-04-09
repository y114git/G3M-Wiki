# Overworld Movement

The main overworld controller in the numbered chapters is `obj_mainchara`. It owns:

- Kris movement
- room entry positioning
- overworld interaction checks
- menu opening
- overworld battle collision support
- later chapter movement extensions such as sword state or climbing

This page focuses on the shipped runtime implementation visible in the extracted chapter payloads.

---

## Shared Core Responsibilities

Across the numbered chapters, `obj_mainchara` Create event usually does the following:

1. set room/depth state
2. initialize battle-heart support for overworld battle zones
3. initialize movement variables
4. choose the correct sprite set for light or dark world
5. restore facing
6. position Kris at the correct entrance marker if entering from a door
7. reset menu state
8. prepare effective defensive stats or related runtime values

---

## Chapter 1 Baseline

Important Create-time features in Chapter 1:

- `global.currentroom = scr_get_id_by_room_index(room)`
- `alarm[2] = 2`
- `autorun = 0`
- `battlemode = 0`
- `battleheart = instance_create(x, y, obj_overworldheart)`
- `darkmode = global.darkzone`
- `bwspeed = 3` in Light World, `4` in Dark World
- direction sprite fields:
  - `dsprite`
  - `rsprite`
  - `usprite`
  - `lsprite`
- entrance placement through hardcoded marker checks

Chapter 1 is the cleanest version of the classic Kris-overworld controller.

---

## Chapter 2 Expansion

Chapter 2 keeps the same movement core and adds more overworld state:

- `drawbattlemode`
- `sliding`
- `becamesword`
- `swordmode`
- `swordcon`
- `swordtimer`
- `stop_movement`
- `roomenterfreezeend`
- `runcounter`

It also upgrades room-entry logic:

- stores `cameFromEntrance`
- uses `switch (global.entrance)` instead of only chained `if`
- checks marker existence with `i_ex(...)`
- falls back to `obj_markerAny` or room center if a specific marker is missing

This is a substantial robustness improvement over Chapter 1.

---

## Chapter 3 Expansion

Chapter 3 adds more movement-state extensions:

- `climbing`
- `climbbuffer`
- `floorheight`
- `canrun`
- `drawdebug`
- `ignoredepth`
- `freeze`

It also introduces Chapter 3-specific sprite overrides inside the Dark World:

```gml
if (global.chapter == 3)
{
    if (scr_flag_get(1076) == 1 || scr_flag_get(1077) == 1)
    {
        usprite = spr_krisu_dark_cool;
    }
}
```

That is a good example of chapter-specific overworld presentation living directly in the main player controller.

---

## Chapter 4 Expansion

Chapter 4 keeps most of the Chapter 3 movement runtime and adds chapter-specific presentation branches again.

Notable changes visible in Create:

- `global.currentroom = room` instead of the earlier `scr_get_id_by_room_index(room)` form at this point in Create
- `climbsprite` changes again
- special Chapter 4 clothing/presentation branch:

```gml
if (global.chapter == 4)
{
    if (global.darkzone == 0 && global.plot >= 11 && global.plot < 35)
    {
        init_clothes = true;
        dsprite = spr_kris_walk_down_church;
        rsprite = spr_kris_walk_right_church;
        lsprite = spr_kris_walk_left_church;
    }
    tower_shake_xoffset = 0;
}
```

This means Chapter 4 overworld presentation is materially more stateful than earlier chapters even before Step-event logic starts.

---

## Base Movement Model

The classic Kris overworld movement model is still recognizable in all chapters:

- `press_l`, `press_r`, `press_u`, `press_d`
- `px`, `py`
- `wspeed`, `bwspeed`
- `run`, `runtimer`
- `subx`, `suby`, `subxspeed`, `subyspeed`
- `walktimer`, `walkbuffer`

This controller is still heavily state-driven rather than physics-driven.

---

## Light World vs Dark World

The basic split remains:

- Light World base speed: `3`
- Dark World base speed: `4`

and the dark world usually enables:

- `stepping = 1`
- doubled sprite scale
- dark sprite set

So “dark world feel” is partly a movement-state and sprite-state change in `obj_mainchara`, not only a room-art difference.

---

## Entrance / Room Transition Placement

This is one of the most important practical systems for recreating chapter flow.

### Chapter 1

Hardcoded marker checks:

- `obj_markerA`
- `obj_markerB`
- `obj_markerC`
- `obj_markerD`
- `obj_markerE`
- `obj_markerF`
- `obj_markerr`
- `obj_markers`
- `obj_markert`
- `obj_markeru`
- `obj_markerv`
- `obj_markerw`
- `obj_markerX`

### Chapter 2+

The same marker family remains, but the logic becomes safer:

- explicit `switch` on `global.entrance`
- `i_ex(...)` marker existence checks
- fallback to `obj_markerAny`
- final fallback to room center

This is exactly the kind of chapter-to-chapter implementation difference modders need documented.

---

## Overworld Battle Support

Even outside formal battle scenes, `obj_mainchara` is connected to overworld combat support through:

- `battleheart`
- `battlemode`
- `drawbattlemode`
- overworld bullet-area objects

Related object families grow across chapters:

- Chapter 1: `obj_overworldbulletparent`, `obj_overworldheart`
- Chapter 2: adds more overworld enemy / bullet-area support
- Chapter 4: adds darkness, knight-sword, lantern-flame, and more specialized overworld danger objects

So overworld combat is not a side system. It is attached to the main player controller from the start and expands significantly later.

---

## Interaction / Menu Layer

`obj_mainchara` also anchors:

- interaction button buffering
- menu opening state
- door-entry flow

Common state includes:

- `onebuffer`
- `twobuffer`
- `threebuffer`
- `global.menuno`

This means the player controller is not only locomotion. It is also the top-level input router for most ordinary overworld play.

---

## Why Chapters 3 And 4 Matter

If you only study Chapter 1 or Chapter 2, you miss large runtime shifts:

- Chapter 3 adds climbing and more special movement state
- Chapter 3 has more cutscene-friendly player control flags
- Chapter 4 adds church-specific sprite/state handling and more specialized overworld hazard families

The later chapters do not just reuse the same Kris controller unchanged.

---

## What To Patch For Mods

### To change base player movement

Inspect:

- `obj_mainchara`

### To change room-entry placement

Inspect:

- `obj_mainchara`
- marker objects in the relevant room
- door objects that set `global.entrance`

### To change overworld battle behavior

Inspect:

- `obj_mainchara`
- `obj_overworldheart`
- `obj_overworldbulletparent`
- chapter-specific overworld hazard objects

### To change chapter-specific traversal mechanics

Inspect:

- Chapter 2 sword-related state in `obj_mainchara`
- Chapter 3 climbing-related state in `obj_mainchara`
- Chapter 4 church/darkness presentation branches in `obj_mainchara`
