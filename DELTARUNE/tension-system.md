# Tension and TP System

TP is stored in `global.tension`; the normal ceiling is `global.maxtension` (250
internal units). Player UI divides this scale into the displayed percentage.

## Sources And Spending

- A one-time or tick-limited bullet graze calls `scr_tensionheal` with the
  configured graze amount and equipment bonuses.
- DEFEND grants TP and marks action 10. Most battles grant 40 internal units;
  encounter overrides can replace that value.
- ACTs, attacks, and scripted events may grant TP explicitly.
- Spells and TP-cost ACTs subtract their listed menu cost when committed.

`scr_tensionheal(argument0)` adds its one argument and clamps to
`global.maxtension`. Chapter 3 also records game-show/mercy totals. Chapter 4
contains encounter-specific amplification. Chapter 5 performs a second clamp
when the live limiter object exposes `maxtensionlimit`.

Chapters 1–2 compute `min(oldTP + amount, maxTP)`. Chapter 3 computes the same
result and separately records the accepted amount for active show/mercy
trackers. Chapter 4 substitutes `ceil(1.5 * amount)` in the Jackenstein retry
branch, then clamps. Chapter 5 performs the ordinary add, clamps to max TP, and
then clamps to the live encounter limiter.

Direct writes to `global.tension` bypass these rules.

## Graze Dependencies

Graze uses the live heart position, the bullet's graze state,
`global.grazesize`, and `global.grazeamt`. Equipment arrays can change size,
amount, and bolt speed. A damaging collision and a graze must not both award
repeated TP after the bullet has been consumed.

The graze increment is base graze amount plus active equipment bonuses; the
radius is base graze size plus equipment size bonuses. The increment then uses
the chapter-specific `scr_tensionheal` formula above.

```gml
if (!grazed && distance_to_object(obj_heart) < global.grazesize) {
    grazed = true;
    scr_tensionheal(global.grazeamt);
}
```

Use the inherited collision convention when the bullet descends from
`obj_bulletparent`.

## Related Pages

- [Battle System](battle-system.md)
- [Heart Mechanics](heart-mechanics.md)
- [Spells and Abilities](spells-abilities.md)
