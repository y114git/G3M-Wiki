# Heart and SOUL Mechanics

`obj_heart` is the shared battle hitbox. Red is its live default in Chapters
1–5. Other SOUL behavior is chapter-scoped: some behavior extends
`obj_heart`, while green, purple, and Flowery's orange behavior depend on
encounter-local controllers.

## Chapter Availability

| Chapter | Red | Yellow | Other behavior |
| --- | --- | --- | --- |
| 1 | Live | Absent | None |
| 2 | Live | Live: Spamton NEO | None |
| 3 | Live | Retained | None |
| 4 | Live | Retained | Green: Hammer of Justice |
| 5 | Live | Retained | Purple: Pink; orange: Flowery and retained branch |

"Retained" means executable code remains in the chapter payload without a
player-facing entry contract. It does not mean that the player encounters that
mode.

## Red

Red uses held directional input for free two-axis movement. Holding `button2`
can slow movement. `obj_heart` handles battle-solid and damaging-bullet
collision, and the battle heart lifecycle owns the ordinary entry and exit.

Chapter 4 temporarily suppresses red translation while `obj_spearblocker`
controls the green shield. Chapter 5 likewise allows local controllers to take
over the heart's position or visibility.

## Yellow

Yellow retains free movement and adds `button1` rapid and charged shots through
the `color == 1` branch of `obj_heart`; shots are `obj_yheart_shot` instances.
In Chapter 2, `obj_spamton_neo_enemy` enters the mode with
`scr_heartcolor("yellow")`, and `scr_heartcolor("red")` restores red.

Chapters 3–5 still contain the yellow branches in `scr_heartcolor` and
`obj_heart`, but expose no player-facing yellow entry contract. Their yellow
implementation is retained-unused rather than a live chapter mode.

## Chapter 4 Green

Green is local to Hammer of Justice, not a branch of `scr_heartcolor`.
`scr_spearshot` command 36 creates `obj_spearblocker`, whose Create event
changes the heart state. While the blocker exists, ordinary directional
translation is suppressed and the heart may be pulled toward
`obj_growtangle`.

Directional presses and holds rotate a four-way shield; selected attacks also
permit diagonal guarding. `obj_spearshot` compares its approach direction with
the shield angle and supports timed blocks and parries. Command 55 fades the
shield, destroys remaining spears, and calls `scr_heartcolor("red")`; the
giant-hammer shield-break path also restores red.

## Chapter 5 Purple

Purple is a local controller used by Pink. Attack types 199–210 disable normal
heart movement, select `spr_purpleheart`, and create `obj_purplecontrols` in
several modes. The controller buffers directional input and implements lane
swaps, grids, rotating layouts, mazes, tunnels, and node traversal. It
synchronizes the real `obj_heart`, which remains the collision target even
when alternate rendering hides it.

`obj_purplecontrols` destruction restores visibility and removes Pink nodes
only. Purple has no documented general exit contract that also restores
movement, color, and sprite state, so it is not a general-purpose global mode.

## Chapter 5 Orange

Chapter 5 has two different orange implementations.

The real-heart implementation uses `obj_heart.color == 2`. Dispatch branches
for attack types 400, 401, 402, 403, and 410 select `spr_orangeheart`. Held and
released `button1` charges a horizontal dash, adds `dash_h` to movement, tests
`obj_growtangle`, and creates `obj_dashpath`. This branch has dispatcher-only
ownership and no documented reset contract, so it is retained-unused.

Flowery instead uses a live encounter-local simulation. Attack types 620–641
and 647 create `obj_orangeheart` and
`obj_debug_orangeheartcontroller`, then hide `obj_heart`; types 642–646 do not
enter this behavior. Up and down provide vertical movement, while holding and
releasing `button1` charges a forward dash. Type 647 adds rotational control.
The helper synchronizes the hidden real heart, while local walls and bullets
collide with `obj_orangeheart` and still route damage through the standard
damage scripts.

Despite its name, `obj_debug_orangeheartcontroller` is used by live Flowery
attack dispatch. Its cleanup is encounter-owned rather than a complete global
`obj_heart` reset contract, so the Flowery objects are not a global orange API.

## Modding Existing Behavior

For a Chapter 2 yellow wave, use the existing color API and restore red when
the wave ends. The yellow branch in `obj_heart` creates rapid and charged
`obj_yheart_shot` instances itself.

```gml
scr_heartcolor("yellow");

// Run the yellow wave, then restore ordinary movement.
scr_heartcolor("red");
```

For encounter-local mechanics, mirror a controller with a verified entry and
exit instead of adding an unsupported color name to `scr_heartcolor`. Chapter
4's shield path uses these existing objects and reset operations:

```gml
// Entry from an encounter controller.
if (!i_ex(obj_spearblocker))
{
    instance_create(x, y, obj_spearblocker);
}

// Exit after the shield wave.
with (obj_spearblocker)
{
    vanish = 1;
}
with (obj_spearshot)
{
    instance_destroy();
}
scr_heartcolor("red");
```

The Pink and Flowery helpers are useful implementation references, but they do
not expose complete generic cleanup contracts. A mod that reuses them must own
and test restoration of heart movement, sprite, visibility, position, and
collision state rather than assuming object destruction performs a full exit.

## Related Pages

- [Battle System](battle-system.md)
- [Tension System](tension-system.md)
- [Enemies, Encounters, and Attacks](enemies-encounters-and-attacks.md)
