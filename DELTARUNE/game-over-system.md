# Game Over System

Party damage calls `scr_dead` for an individual downed character. When no
eligible living party member remains, the damage transaction calls
`scr_gameover()`.

## Modes

- Mode 0 enters the standard game-over presentation and reload/continue flow.
- Mode 1 is a scripted no-death continuation used by controlled encounters.
- Mode 2 restarts the room or encounter from prepared state.

The selected mode is stored in battle/route state, principally flag 35 in the
reviewed branches. `cantdie` encounters clamp HP and deliberately avoid this
transition. Chapter 5 platform damage has separate callers but converges on the
same game-over script.

## Ordering

The current damage transaction finishes first. Battle writers, faces, arena,
bullets, overlays, and music are then destroyed or transferred. Restart state is
preserved before room control changes. Victory rewards, recruitment, and
ordinary victory cleanup must not execute afterward.

The compiled Chapter 5 wrapper has one argument slot, but ordinary runtime
callers invoke `scr_gameover()` with no explicit argument.

## Runnable Restart

```gml
if (global.hp[0] <= 0 && global.hp[1] <= 0 && global.hp[2] <= 0) {
    global.flag[35] = 2;
    scr_gameover();
    exit;
}
```

Use the stock damage routine for normal battles because it understands absent
and already-downed party slots.

## Related Pages

- [Damage System](damage-system.md)
- [Battle System](battle-system.md)
- [Save and Load System](save-load-system.md)
