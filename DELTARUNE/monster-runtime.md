# Monster Runtime

Monster data is split between encounter recipes, object instances, and global
slot arrays. A resource name is not a playable enemy until those layers connect.

## Setup Pipeline

1. `scr_encountersetup(encounter_id)` assigns type, object, and spawn data.
2. The controller resets each monster slot.
3. `scr_monster_makeinstance(slot)` creates the assigned object.
4. `scr_monstersetup()` fills HP, AT, DF, reward, mercy, and ACT arrays from
   current slot/type state.
5. The object user-event protocol supplies ACT and attack behavior.
6. `scr_monsterdefeat()` aggregates outcome and reward state from the current
   slot/context.

Core arrays include `global.monsterinstance`, `global.monstertype`,
`global.monsterhp`, `global.monstermaxhp`, `global.monsterat`,
`global.monsterdf`, `global.monstergold`, `global.monsterexp`,
`global.sparepoint`, `global.mercymod`, `global.mercymax`, and
`global.monstertired`.

## ACT And Mercy

`global.canact`, `global.actname`, `global.actdesc`, `global.actcost`,
`global.actactor`, and `global.actsimul` describe Kris's menu and multi-actor
requirements. Later chapters add corresponding Susie, Ralsei, and Noelle ACT
arrays. Menu synthesis copies enabled entries into battle spell/ACT tables.

Ordinary spare eligibility is current mercy at or above `global.mercymax`.
Standard enemies normally use 100; bosses often use an unreachable sentinel and
end through scripted phases. Tired targets can leave through Pacify. Mercy, HP,
and status are independent state dimensions.

An ACT applies its enemy-defined mercy increment to the current slot and tests
that slot against `mercymax`; there is no universal ACT increment. Tired,
spareable, defeated, downed, and scripted-phase states remain independent.

## Chapter Sets

- Chapter 1 establishes types 1–25, including Lancer, Rudinn, Hathy, Clover, the
  Round enemies, Ponman, Rabbick, Bloxer, Jigsawry, Jevil, and King.
- Chapter 2 adds types 30–44, including Cyber World regulars and advanced forms.
  Boss objects cover Berdly, Queen, Spamton, and Spamton NEO.
- Chapter 3's ordinary set includes Shadowguy, Shuttah, Zapper, Ribbick,
  Watercooler, Pippins, Elnina, and Lanino, plus scripted show/board fights.
- Chapter 4 uses types 62–69 for its regular/recruit set and types 105–111 for
  Hammer, Jackenstein, Titan, Titan Spawn, and paired boss forms.
- Chapter 5 keeps the same setup scripts and adds room-rooted platform and
  fountain-castle miniboss machinery. These are not ordinary menu enemies until
  an encounter/type chain demonstrates that contract.

The exact per-type records in [Battle Catalog Data](battle-catalog-data.md)
retain each numeric type, HP/AT/DF/EXP/gold/mercy fields, ACT strings, and
case-local object references. Chapter 1 stores display and ACT text behind
localization-key calls, so null text fields there mean "not present in this code
inventory," not "unnamed." The prose index is
[Enemies, Encounters, and Attacks](enemies-encounters-and-attacks.md).

## Reachability

The semantic review contains 24, 48, 61, 67, and 26 MS branches and 32, 86, 74,
86, and 76 ES branches for Chapters 1–5. ES rows preserve final indexed slots,
including explicit zero-valued empty/sentinel slots. MS rows preserve text
resolution status so localization keys and source expressions cannot be mistaken
for player-facing labels. The companion publishes only the smaller attack,
outcome, and room subsets that meet its typed semantic gates; omitted joins
remain unresolved.

## Runnable Enemy And ACT

```gml
// Inside scr_monstersetup(), after ACT reset.
case 900:
    global.monstername[myself] = "Example";
    global.monstermaxhp[myself] = 300;
    global.monsterhp[myself] = 300;
    global.monsterat[myself] = 10;
    global.monsterdf[myself] = 1;
    global.monstergold[myself] = 75;
    global.mercymax[myself] = 100;
    global.canact[myself][0] = 1;
    global.actname[myself][0] = "Check";
    global.actdesc[myself][0] = "EXAMPLE - A modded enemy.";
    break;
```

Provide an enemy object, encounter mapping, and user-event ACT/attack handlers.

## Related Pages

- [Battle System](battle-system.md)
- [Recruit System](recruit-system.md)
- [Damage System](damage-system.md)
