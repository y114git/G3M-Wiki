# Damage System

Damage is an ordered transaction. Chapter 1 uses the legacy direct branch;
Chapters 2–5 route ordinary battle damage through `scr_damage_calculation` and
element resistance through `scr_element_damage_reduction`. Chapter 5 also has
`scr_damage_calculation_plat`, which belongs to platform combat.

## Incoming Pipeline

1. `scr_damage` receives raw damage and a target selector.
2. Encounter overrides adjust damage or force a target.
3. Selector 0–2 means a party slot, 3 means all, and 4 chooses a living slot.
4. Defense is applied. Chapter 1 subtracts the legacy DEF expression; Chapters
   2–5 call `scr_damage_calculation(raw, party_slot)`.
5. DEFEND changes single-target damage to `ceil(2d / 3)` and party-wide damage
   to `ceil(3d / 4)`.
6. Chapters 2–5 call `scr_element_damage_reduction(element, character_id)`.
7. The result is rounded/clamped, HP is removed, invulnerability starts, and
   `scr_dead` or `scr_gameover` runs when required.

Do not reorder defense, element, DEFEND, and rounding: integer results change.
`cantdie` is an encounter exception that clamps relevant HP instead of entering
the ordinary defeat branch.

## Outgoing Pipeline

`scr_damage_enemy` reads the acting character's derived battle AT/MAG, the
attack timing result or spell strength, target DEF, element modifiers, and boss
exceptions. It writes HP and damage presentation, then invokes the monster's
defeat protocol at zero HP. ACT and mercy progress are separate from HP damage.

## Chapter Ranges

- Chapter 1 computes `ceil(raw - 3 * DEF)`, applies DEFEND, and delivers at
  least 1. It has no general element helper.
- Chapters 2–5 iterate once per DEF point. While remaining damage is above 20%
  of target maximum HP they subtract 3; above 12.5% they subtract 2; otherwise
  they subtract 1. The helper returns at least 1.
- Chapters 2–5 multiply by element resistance and round upward. Each matching
  equipped resistance subtracts its configured fraction from 1. Element 9 covers
  elements 2 and 8; element 10 covers every nonzero element. The multiplier
  floors at 0.25 and delivered damage floors at 1.
- Chapter 5: the same ordinary helpers plus a separate platform helper.

Physical attack objects form damage from acting AT, target DEF, and timing, then
call `scr_damage_enemy(amount, monster_slot)`. Spells form their own base from
MAG and spell power. `scr_damage_enemy` is the applier, not the formula: it
subtracts the supplied amount and starts hurt, presentation, and defeat work.

## Runnable Modifier

```gml
/// scr_mod_damage_incoming(_raw, _target, _element)
var _raw = argument0;
var _target = argument1;
var _element = argument2;
var _scaled = scr_damage_calculation(_raw, _target);
var _char = global.char[_target];
return max(1, ceil(_scaled
    * scr_element_damage_reduction(_element, _char)));
```

Battle stats and equipment-element arrays must already exist. Preserve the stock
caller's minimum-damage and final-rounding rules.

## Related Pages

- [Battle System](battle-system.md)
- [Heart Mechanics](heart-mechanics.md)
- [Game Over System](game-over-system.md)
