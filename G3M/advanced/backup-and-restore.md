# Backup & Restore

Backup and restore is the reason G3M can behave like a launcher session instead
of a one-way patcher.

---

## The Core Promise

When you launch with mods, G3M is supposed to:

1. remember the original state
2. apply the modded state
3. let you play
4. put things back afterward

That is the safety model behind normal modded launching.

---

## What This Protects

The important targets are the files G3M changes during patching, including main
game data and other files a mod may overwrite or add.

So if you are worried that "launching with mods" permanently rewrites your
install, this is the system that exists to prevent that.

---

## Crash Recovery

G3M also keeps session state for interrupted modded runs.

That means if the launcher or machine goes down at the wrong time, the next
startup can still try to restore the previous session instead of leaving the
game in a half-modded state.

---

## Not the Same as Game Versions

Do not mix up these two features:

- **Backup & Restore**: temporary protection around a modded launch session
- **Game Versions**: user-managed saved snapshots you keep on purpose

They solve different problems.
