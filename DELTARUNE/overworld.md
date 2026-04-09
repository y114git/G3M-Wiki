# Overworld Movement

The main overworld controller in the numbered chapters is `obj_mainchara`. It owns:

- Kris movement
- room entry positioning
- overworld interaction checks
- menu opening
- overworld battle collision support
- later chapter movement extensions such as sword state or climbing

This page documents `obj_mainchara` as seen through UndertaleModTool.

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

Chapter 2 adds `i_ex()` existence checks and `obj_markerAny` fallback for missing markers.

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

Chapter 4 Create-time state is denser than earlier chapters before Step logic even begins.

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

Dark World mode changes movement speed and sprite sets inside `obj_mainchara`, not only room art.

---

## Entrance / Room Transition Placement

This transition path is one of the main chapter-flow entrypoints.

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

Overworld combat is attached to the main player controller from Chapter 1 onward and grows with each chapter.

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

`obj_mainchara` handles movement, interaction routing, door checks, and menu opening.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Change base player speed | `bwspeed` in `obj_mainchara` Create |
| Change room-entry placement | `global.entrance` switch in `obj_mainchara`, marker objects |
| Change overworld battle | `obj_overworldheart`, `obj_overworldbulletparent` |
| Change follower behavior | `scr_makecaterpillar`, caterpillar alignment offsets |
| Add sword/climbing state | Extend `swordmode`/`climbmode` branches in `obj_mainchara` Step |
| Change menu opening | `global.menuno` and interaction buffer state |
| Change NPC interaction | `scr_interact`, NPC objects in room |

---

## Relationship To Other Pages

- [Party Management](party-management.md) explains the caterpillar follower system
- [Cutscene System](cutscene-system.md) explains how cutscenes drive overworld actors
- [Board System](board-system.md) explains the grid-based overworld replacement in Ch3
- [Battle System](battle-system.md) explains how overworld encounters transition to battle
- [Global Variables](global-variables.md) explains `global.entrance`, `global.darkzone`, `global.interact`