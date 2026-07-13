# Troubleshooting

When something breaks, the fastest path is usually:

1. decide whether the problem is startup, import, launch, or networking
2. check the log
3. retry with the smallest clean setup you can

This page is about shortening that loop.

---

## The First Questions

Before digging deeper, ask:

- does G3M itself open
- is the game path correct
- is the right profile selected
- does the issue still happen with no mods selected
- does it still happen with one simple mod instead of the full stack

That quick check often tells you whether the issue is launcher setup, mod order,
a bad import, or something game-specific.

---

## Most Common Real Causes

The issues people hit most often are:

- another G3M instance is already running
- the game is already running
- the game path points to the wrong folder
- the wrong profile is active
- the imported mod format is incomplete or unsupported
- the game folder is not writable

These are worth ruling out before assuming a deeper patching bug.

---

## Logs

The main logs to check are:

- `%LOCALAPPDATA%\G3M\logs\g3m.log`
- `%LOCALAPPDATA%\G3M\logs\shortcut.log`
- archived logs under `%LOCALAPPDATA%\G3M\logs\g3m\`

If you need to report a real bug, include the relevant log section. It is
usually the fastest way to move from "it failed" to "this exact step failed".

---

## Hard Reset Option

If you truly want a clean restart of the whole launcher state, the destructive
option is still:

1. close G3M
2. remove the user data folder
3. reopen G3M and rebuild the setup

Use that only when you already accepted losing local settings, profiles,
plugins, and installed mods.
