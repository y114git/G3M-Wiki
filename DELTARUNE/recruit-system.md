# Recruit System

Recruitment is a post-spare progression layer introduced in the later runtime.
It is not synonymous with mercy or victory.

## Runtime Contract

`scr_recruit()` processes an eligible spared monster. `scr_recruit_info(type)`
supplies display metadata, required spare count, and placement policy. Bulk and
serialization helpers build Castle Town views and chapter-completion checks.

The persistent counter convention is `global.flag[type + 600]`. The flag is a
normalized progress value in the closed range 0–1, not a raw spare count. Route
flag 61 can block ordinary recruitment. Violence, flee, abort, game over,
scripted boss exits, and non-recruitable types do not increment the ordinary
counter.

For Chapters 2–5 the executable update is identical. When `recruitable == 1`,
flag 61 is zero, the stored progress is at least zero but below one, and the
instance `recruitcount` is positive, it adds `1 / recruitcount`, then clamps a
value above one back to one. The animation's completed count is
`round(flag[type + 600] / (1 / recruitcount))`; its required count is
`recruitcount`. Thus a requirement of 4 stores 0.25, 0.5, 0.75, then 1.0 and
displays 1, 2, 3, then 4. Chapter 1 has no `scr_recruit_info` implementation and
no later normalized recruitment contract.

The function contains a `recruitcount == -1` metadata fallback inside the outer
`recruitcount > 0` guard. That branch is unreachable as written in all four
chapter builds; it must not be described as an active fallback.

Placement value 0 means no Castle Town placement, 1 means ordinary placement,
and 2 means paired placement. Placement needs corresponding room and dialogue
handling; metadata alone is insufficient.

## Recruit Sets

- Chapter 1 metadata: Rudinn, Hathy, Ponman, Rabbick, Bloxer, Jigsawry, Jevil,
  Rudinn Ranger, and Head Hathy.
- Chapter 2 metadata: Ambyu-Lance, Poppup, Tasque, Werewire, Maus, Virovirokun,
  Swatchling, Werewerewire, Tasque Manager, and Mauswheel.
- Chapter 3 metadata: Shadowguy, Shuttah, Zapper, Ribbick, Watercooler, Pippins,
  Elnina, and Lanino.
- Chapter 4 metadata: Guei, Balthizard, Bibliox, Mizzle, Wicabel, Winglade,
  Organikk, and Miss Mizzle.

Chapter 5 retains `scr_recruit`, `scr_recruit_info`, bulk loading,
serialization, and the same flag convention. Presence of these scripts does not
prove that every Chapter 5 miniboss or platform enemy is recruitable.

### Chapter 5 source cases

Cases 70–77 are Floradinn, Leafling, Shi, Shinobeetle, Kawkaw, Sheary, Netskie,
and Terakota respectively. They contain Chapter 5 metadata and TODO dialogue.
These definitions do not establish that an ordinary spare path reaches them.

## Runnable Recruit Definition

```gml
// Inside scr_recruit_info(argument0).
case 900:
    _name = "Example";
    _chapter = 5;
    _recruitcount = 2;
    _placeable = 1;
    break;
```

The enemy must set its runtime `recruitable` state, its spare path must call
`scr_recruit()`, save initialization must reserve flag 1500, and placement plus
dialogue must exist before `_placeable` is set to 1.

## Related Pages

- [Monster Runtime](monster-runtime.md)
- [Battle System](battle-system.md)
- [Enemies, Encounters, and Attacks](enemies-encounters-and-attacks.md)
