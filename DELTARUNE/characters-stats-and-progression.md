# Characters, Stats, and Progression

This page is the canonical map of player-facing character state in the five
Windows chapter payloads. [Party Management](party-management.md) covers party
mutation, while [Level-Up System](level-up-system.md) covers encounter growth.

## Character records

`scr_gamestart` allocates character-indexed arrays for 20 IDs, but only four IDs
have complete playable records and are passed to battle-party code.

The former wrapped summary table was removed. The records below list runtime
values.

Chapter 5 includes runtime progression definitions. Its startup and party calls
must still be used to distinguish initialized records from playable states;
names alone are never roster runtime basis.

## Runtime stat model

The durable arrays are keyed by character ID, not battle position: `global.hp`,
`global.maxhp`, `global.at`, `global.df`, `global.mag`, `global.charweapon`,
`global.chararmor1`, `global.chararmor2`, and `global.spell[character][slot]`.
`global.char[0..2]` maps the current three battle positions to those records.
Noelle is character ID 4, but occupies an ordinary party position when present.

Equipment contributes temporary combat totals; changing an equipment info case
does not rewrite the saved base arrays. Conversely, directly changing
`global.at[1]` changes Kris's saved base AT and stacks with the equipped weapon.

## Chapter states

The former wrapped summary table was removed. The records below list runtime
values.

Thus “Noelle support exists” in Chapters 3–4 means the ID, stats, spell arrays,
equipment eligibility, and helper argument exist. It does not prove a normal
Noelle party segment in those chapters.

## Spell ownership

The startup assignment, rather than the spell definition case, determines
ownership. Chapter 1 assigns ACT (7) to Kris, Rude Buster (4) to Susie, and
Pacify (3) plus Heal Prayer (2) to Ralsei. Chapter 2 additionally assigns Noelle
Heal Prayer (2), Sleep Mist (8), and IceShock (9); SnowGrave (10) is
route-controlled. Chapters 3–4 initialize Susie's progressive heal (11) while
retaining the earlier character records. See
[Spells and Abilities](spells-abilities.md) for definition reachability.

## Save-compatible stat changes

Existing saves serialize the numeric arrays, so changing startup defaults alone
affects new files. A compatible migration should reserve a flag and be
idempotent:

```gml
// Run after load, once. Keep the existing character IDs and array widths.
if (global.flag[1998] == 0)
{
    global.maxhp[1] = max(global.maxhp[1], 180);
    global.hp[1] = min(global.hp[1], global.maxhp[1]);
    global.flag[1998] = 1;
}
```

Do not renumber character, item, weapon, armor, or spell IDs in a released mod:
old saves contain those integers. Add new cases in unused IDs, initialize new
slots after load, and preserve the existing 12-slot inventory/spell loops unless
all readers, writers, menus, and save fields are migrated together.

## Extension checklist

For a party-member mod, update `scr_gamestart`, party mutation, follower
creation, battle actor creation, equipment eligibility, spell ownership, save
load, and all character-indexed UI loops. Test a new file, a pre-mod save, a
chapter transition, equipment swap, battle entry/exit, save, reload, and removal
from the party. Merely extending `scr_setparty` creates no fourth battle slot.

## Value-inventory reconciliation

The complete 2138-row initialization/import inventory is published in
[Party Management](party-management.md#generated-party-stat-equipment-spell-and-import-assignments).
It covers HP, AT, DF, MAG, Guts, equipment, spells, active party, and Chapters
1–4 import into Chapter 5.
