# Desktop Shortcuts

Desktop shortcuts launch a saved setup without reopening the full launcher.

---

## What a Shortcut Is

A shortcut is a small launcher file that remembers:

- which game to run
- which profile to use
- which launch options matter for that run
- which mod setup should be applied

They avoid recreating the same setup in the UI.

---

## Why People Use Them

Shortcuts are most useful for:

- a stable personal modded playthrough
- a dedicated testing setup
- keeping separate launch icons for separate profiles or games

They avoid rebuilding the same loadout for every session.

---

## Limitation

Shortcuts depend on the referenced setup still existing.

A shortcut can store several priority steps, but each step can contain only one
mod. Use the main window when one step must merge several mods.

If you later:

- remove the mod
- change the profile in a way that breaks the saved setup
- move the launcher install in a way the shortcut no longer expects

then the shortcut may stop working correctly and should be recreated.

---

## Troubleshooting Tip

If a shortcut launch fails, check the shortcut-specific log in the G3M logs
area first.
