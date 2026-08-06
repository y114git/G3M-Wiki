# Multiple Mods

G3M can merge compatible mods and run dependent mods in separate steps.

## Priority inside a step

Mods in the same step use the same starting DATA file. G3MTool merges their
changes, and the mod with the higher priority wins when two changes cannot be
combined.

## Steps

Steps run from top to bottom. The result of one step becomes the starting DATA
for the next.

Use another step when:

- an addon expects the main mod to be applied first
- a version patch must run before the mod that needs that version
- two patches must run in sequence instead of being merged against the same
  original file

If a later patch does not accept the result of an earlier step, launch stops
with the patch error. G3M does not guess another order or skip the required
step.

## What affects compatibility

- overlapping edits
- raw replacement data versus patch-based mods
- the **Merge Properties** setting
- the **Merge Code** setting

Patch-based mods are usually the better fit when you want to combine several
changes.

## Shortcut limitation

Desktop shortcuts support multiple steps, but each shortcut step can contain
only one mod. Use the main G3M window when a step must merge several mods.
