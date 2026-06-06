# Creating Mods

If you are making a mod for G3M, the most important choice is not "which button do I press", but "what kind of payload am I shipping".

---

## The Two Main Approaches

For most creators, there are two practical options:

- ship a full modified data file
- ship a patch built from the difference between clean and modified data

Both work. Patch-based mods are usually the better default for sharing.

---

## Why Patches Are Usually Better

Patch-based mods are usually easier to live with because they are:

- smaller
- cleaner to distribute
- less blunt than shipping a whole replacement file

A full replacement file is still valid, but it is the heavy-handed option and is more likely to fight with other mods.

---

## Practical Creator Flow

The normal workflow is:

1. keep a clean original data file
2. create your modified result with your external tool of choice
3. decide whether to ship the whole file or generate a patch
4. create the mod entry in G3M
5. assign the file or patch to the right game or chapter
6. test the mod in a real launch

That is the heart of mod creation even if your external editing tool changes.

---

## Multi-Chapter Mods

For chapter-aware games, think in assignments:

- which chapter does this change belong to
- does the mod affect one chapter or several
- do some chapters stay vanilla

You do not need to force every mod into an all-chapters design.

---

## Before Sharing

At minimum, verify:

- the mod imports cleanly
- it launches cleanly
- the expected changes appear in game
- restore-after-exit still works
- the description, name, version, and tags make sense to someone else

The most useful mod is not just the one that works for you, but the one another person can understand and install without guessing.
