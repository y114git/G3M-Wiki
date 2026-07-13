# Enemies, Encounters, and Attacks

Development and reachability status meanings are centralized in
[Debug, Legacy, and Unused Content](debug-legacy-and-unused-content.md).

For indexed ES slot mappings, MS names, stats, rewards, mercy fields, and ACT
assignments, see [Battle Catalog Data](battle-catalog-data.md).

## Coverage and Runtime Rules

An enemy or attack is **confirmed** when an encounter recipe and a reachable
room/script root lead to its battle object. **Conditional** means a route,
phase, optional boss, or minigame gate is required. **Candidate** means the
resource exists but the chain is incomplete. **Debug/prototype** requires
positive runtime basis such as a tester/debug/old name or a test-only room;
absence from room JSON alone is not enough because encounters create objects by
code.

| Chapter | ES cases | MS cases | Unresolved ES type IDs |
| ------: | -------: | -------: | ---------------------: |
|       1 |       32 |       24 |                      0 |
|       2 |       86 |       48 |                      0 |
|       3 |       74 |       61 |                      0 |
|       4 |       86 |       67 |                      0 |
|       5 |       76 |       26 |                     31 |

These counts cover executable branch populations, not player-facing enemy
totals. Unresolved IDs remain unresolved. Type-zero slots are empty or sentinel
slots, not enemies.

### Normalized Chapter 5 recruit definitions

`scr_recruit_info` defines the following Chapter 5 cases. `Defined/uncertain`
means complete metadata exists but encounter-to-spare reachability remains
uncertain.

| Case | Enemy       | Classification    | Route result         |
| ---: | ----------- | ----------------- | -------------------- |
|   70 | Floradinn   | Defined/uncertain | Recruit if reachable |
|   71 | Leafling    | Defined/uncertain | Recruit if reachable |
|   72 | Shi         | Defined/uncertain | Recruit if reachable |
|   73 | Shinobeetle | Defined/uncertain | Recruit if reachable |
|   74 | Kawkaw      | Defined/uncertain | Recruit if reachable |
|   75 | Sheary      | Defined/uncertain | Recruit if reachable |
|   76 | Netskie     | Defined/uncertain | Recruit if reachable |
|   77 | Terakota    | Defined/uncertain | Recruit if reachable |

## ACT, Reward, And Route Inventory

The type tables and ACT names live in [Monster Runtime](monster-runtime.md).
Every standard enemy supplies Check plus zero or more progress ACTs; later
chapters add party-member ACT menus and simultaneous ACTs. Outcomes fall into:

- HP defeat: defeat event, route/violence flags, gold/EXP aggregation, no
  ordinary recruit increment;
- mercy spare: spare event, gold/EXP aggregation, recruit increment when the
  type is eligible and route flags permit it;
- Pacify: tired target removal through the spare-like path;
- scripted phase/end: boss-specific flags and rewards, possibly neither normal
  defeat nor recruitment;
- flee, abort, room restart, or game over: no victory rewards.

Rewards are accumulated in monster slot 3 and then modified by remaining TP,
chapter, equipment, and route flags before flooring. The exact modifier set is
chapter-specific; see [Battle System](battle-system.md).

## Attack Families And SOUL Interaction

- Parent/arena: bullet parent, arena, and graze box; collision and graze.
- Directed projectile: dice, moon, sun, rain, note, and bubble; red movement.
- Beam/slash: zapper, knight, and knife families; warned lanes and timed gaps.
- Yellow shooter: reticle and reticle bullet; yellow firing and targets.
- Platform/minigame: aqua, orange, and yellow families; encounter movement.
- Recovery/hazard: healing, food, trash, and debris; custom hit callbacks.

Chapter 5 adds blue dancer/flower/revolver, green cooking, orange
dragon-punch/sine/superattack, yellow reticle, knife, fox, scarecrow, scissor,
shuriken, trash, and wheel-spring families. Color in these object names is not
proof of a new `scr_heartcolor` mode.

Tester objects (`obj_bullettester*`, `obj_battletester`) and names containing
`debug`, `test`, `prototype`, or `old` stay excluded from the player-facing list
unless a production route is independently demonstrated. Duplicate parent and
fancy-parent resources are implementation variants, not attacks by themselves.

Generic chase/solid enemies and bullet parents are infrastructure.
Tester/debug/old names remain uncertain until an exact development route is
known; other objects remain uncertain until ES/MS/AD references establish an
ordinary encounter chain.

## Secret Encounters

The five chapter payloads each connect one encounter to that chapter's secret
boss result slot. The controllers own their route checks, battle setup, result
flags, and rewards. Do not derive secret status from an enemy name or an
encounter-table entry alone.

### Chapter 1: Jevil

`room_cc_joker` places `obj_jokerbattleevent`. The event starts encounter `25`,
and `scr_encountersetup(25)` creates `obj_joker`.

Jevil advances `chaosdance` through a nine-position cycle. Hypnosis increments
`hypnosiscounter` and sets the `hypnosis` state. Pirouette copies the current
`chaosdance` value, so its effect follows the cycle instead of a separate
random table. The direct defeat branch calls `scr_monsterdefeat()`.

Jevil's room, enemy, ACT, and reward controllers do not call
`scr_heartcolor` or create yellow, green, orange, or purple mode controllers.
They contain no explicit SOUL color assignment.

The fight writes `global.flag[241]` as `6` or `7`. The reward controller grants
key item `13`; result `6` grants weapon `7`, while result `7` grants armor `7`.
`global.flag[242]` records deferred reward handling when the destination
inventory has no room.

For a Jevil-style extension, keep the attack-cycle counter on the enemy and let
the room event own battle startup and rewards. Add a new encounter case before
calling it from a room controller. Do not reuse flags `241` or `242` for an
unrelated fight.

### Chapter 2: Spamton NEO

`obj_ch2_sceneex2` and `obj_fountainkris_ch2_sideb` both call
`scr_battle(61, 1, sneo, 0, 0)`. Encounter `61` creates
`obj_spamton_neo_enemy`. The normal-scene controller points `global.flag[54]`
at `571`; the chapter save mapping also assigns Chapter 2's secret result to
flag `571`.

The side-B branch clamps HP at `1` and enters `weirdpathendcon` handling at the
10% threshold. Normal-route logic reserves its final attack below 10% HP. The
wire-snapping ACT branches add `2`, `4`, or `7` mercy according to the selected
party action.

Spamton NEO calls `scr_heartcolor("yellow")`. The shared `obj_heart` yellow
branch handles rapid shots and charged shots through the yellow-heart shot
objects. Code that adds another yellow-heart attack should use this existing
heart state and shot lifecycle instead of creating an encounter-local color
that the shared heart does not recognize.

The post-battle scene sets progression flag `309` to `9`. It grants key item
`13` plus weapon `21` for result `1`, or armor `21` for the other recorded
result. Flags `468` and `454` cover reward inventory state. The enemy and reward
controllers contain no encounter-local platform branch.

### Chapter 3: Plot-320 snow-zone Knight encounter

`room_dw_snow_zone` places `obj_ch3_PTB02`. The controller exits while
`global.plot < 320` and starts its sequence when the player reaches
`x >= 1840`. It assigns encounter flag `115`, copies that value to
`global.flag[54]`, and calls `scr_battle(115, 1, knight_marker, 0, 0)`.
Encounter `115` creates `obj_knight_enemy`.

The enemy selects attacks through phase `1`, `2`, `3`, and `4` branches.
Crossing the 80% HP threshold changes the phase to `4`. Kris, Susie, and Ralsei
have separate ACT handlers. The room controller resolves the outcome as result
`1` for defeat or `2` for the other completed outcome, writes flag `1047`, and
writes the same value to `UraBoss`.

The Knight enemy controller contains no explicit alternative SOUL-mode switch
or mode controller.

After battle, the shard readable grants key item `13` and weapon `26`. A mod
that follows this pattern should let the room controller preserve the
overworld marker, assign `global.flag[54]`, wait for the battle controller, and
write one result value. Keep the readable reward separate if the player must
collect it after combat.

### Chapter 4: Hammer of Justice

The church route checks `scr_flag_get(1547) > 0` and
`scr_flag_get(1629) == 0`. `room_dw_church_arena` places
`obj_dw_church_arena`, which assigns encounter `160`; the encounter creates
`obj_hammer_of_justice_enemy`.

The enemy advances a scripted spear list through `scr_spearshot`. Reaching its
end phase sets `have_used_final_attack`. Its status branches react to repeated
attacks, Susie's magic, and Rude Buster.

`scr_spearshot` creates `obj_spearblocker`. Directional input rotates the
four-way shield, selected attacks allow diagonal guarding, and approaching
spears compare their direction with the shield angle. Timed blocks feed the
encounter's block and parry events. The cleanup command destroys the shield and
calls `scr_heartcolor("red")`.

Flag `1547` gates the route, `1629` records the attempt, `852` records
completion, and `851`/`853` track arena progression. The reward sequence calls
the chapter Shadow Crystal helper and grants weapon `52`. The arena and enemy
controllers contain no encounter-local platform branch.

For another shield encounter, drive `scr_spearshot` from an enemy-owned attack
list and include its shield cleanup command. Do not treat
`obj_spearblocker` as a global green-mode toggle; the Hammer controller owns
its entry, timing, and exit.

### Chapter 5: Pink

The Flower Castle pink-room door points to `room_dw_pink_encounter`. That room
places `obj_dw_pink_encounter`, whose fight-count state uses temporary flag
`62`. The controller starts encounter `224`; the encounter creates
`obj_pink_enemy`. Chapter 5 maps its secret result to flag `1908`.

Pink tracks `datecount` and `phaseturns`, includes a `phase4introcon` sequence,
and selects among multiple attack choices. Its later transition checks `doki`
and the phase-turn count. Kris, Susie, and Ralsei each have ACT handlers; one
transition resets `phaseturns` and adds `25` mercy.

Pink creates `obj_purplecontrols` and selects `spr_purpleheart`. The controller
implements buffered directional input and discrete lane, grid, rotating-grid,
maze, tunnel, and node movement modes. It synchronizes the real `obj_heart`
with the controller position while encounter hazards continue to use the battle
heart for collision. Treat these as Pink-owned modes. The payload does not
provide one generalized purple-heart API for arbitrary encounters.

Completion sets flag `1908` to `2`, sets progression flag `1815`, calls the
Chapter 5 Shadow Crystal helper, and grants key item `13`. On console builds,
the post-start branch checks `global.console` and calls
`obj_border_controller.show_border()`.

When extending a Pink attack, select an existing `obj_purplecontrols.mode` and
create the controller once. Keep the hidden battle heart synchronized, then add
an explicit exit that restores visibility and movement state. New grid rules
belong in the purple controller; ordinary enemy code should not move the hidden
battle heart independently.

## Other Implemented Boss Battles

These dispatches create complete battle enemies. Their controllers do not
establish whether players can bypass the route, so this page does not call them
mandatory, optional, or secret.

- Chapter 1: `obj_kingcutscene` assigns encounter `40`, which creates
  `obj_king_boss`.
- Chapter 2: `obj_ch2_scene25` starts encounter `59`, which creates
  `obj_queen_enemy`.
- Chapter 3: `obj_ch3_BTB06` starts encounter `121`, which creates
  `obj_tenna_enemy`.
- Chapter 4: `obj_dw_churchc_titanclimb2_post` starts encounter `175`, which
  creates `obj_titan_enemy`.
- Chapter 5: `obj_ch5_DW29` starts encounter `225`, which creates
  `obj_flowery_enemy`.

Flowery's battle includes an encounter-local orange-heart simulation, but that
mechanic does not establish route or secret-boss status. See
[Heart Mechanics](heart-mechanics.md) for the distinction between the hidden
battle heart and `obj_orangeheart`.

## Runnable Bullet Pattern And Reward

```gml
// Wave controller Create event: battle arena and heart must already exist.
repeat (8) {
    var _b = instance_create(global.heartx + irandom_range(-120, 120),
        global.hearty - 100, obj_bullet_example);
    _b.direction = 270;
    _b.speed = 3;
    _b.damage = 8;
    _b.target = 4;
}
```

Make `obj_bullet_example` inherit the chapter's `obj_bulletparent` so graze,
damage, arena deletion, and cleanup conventions are preserved.

```gml
// Enemy defeat event, with `myself` already selecting the current slot.
global.monstergold[myself] = 75;
global.monsterexp[myself] = 0;
scr_monsterdefeat();
```

`scr_monsterdefeat()` takes zero arguments in Chapters 1–5 and reads current
slot/context state. Do not award currency directly; the controller still needs
to apply victory and route modifiers.

## Related Pages

- [Battle System](battle-system.md)
- [Damage System](damage-system.md)
- [Heart Mechanics](heart-mechanics.md)
- [Recruit System](recruit-system.md)
- [Game Over System](game-over-system.md)
- [Battle Catalog Data](battle-catalog-data.md)
