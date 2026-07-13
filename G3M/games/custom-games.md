# Custom Games

Custom games let you teach G3M about another GameMaker-based game without
changing G3M's source code.

---

## When a Custom Game Makes Sense

Use a custom game when:

- the game is not one of G3M's built-in entries
- you still know its main executable name
- you know which data file should be patched
- you want it to behave like a normal single-tab launcher target

This is the fastest path for getting an unsupported GameMaker game into the
launcher.

---

## What You Need to Provide

The creation form asks for:

- display name
- executable file name
- data file name
- optional Steam App ID
- optional GameBanana ID

The executable and data file fields are file names, not arbitrary folder paths.

---

## What You Get

A custom game becomes a normal launcher target with:

- its own game path setting
- its own custom executable override
- its own used-mod state
- optional Steam launch support
- optional Mods Browser presence if you gave it a GameBanana ID

---

## Limits

Custom games are intentionally simpler than some built-in ones.

Current limits:

- single-tab only
- no full install
- no built-in chapter splitting

So custom games fit best when the target game behaves like one main data file
plus one main executable.
