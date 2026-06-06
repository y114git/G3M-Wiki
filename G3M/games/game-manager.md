# Game Manager

The Game Manager controls the launcher's game list: what appears, in what order, and which extra custom games exist.

---

## What It Is For

Use the Game Manager when you want to:

- hide games you never use
- put your main game at the top
- add a custom GameMaker game
- remove a custom game you no longer want in the launcher

It changes the launcher view, not your actual game files.

---

## Built-In vs Custom Games

Built-in games are part of G3M itself. You can reorder or hide them, but not delete them.

Custom games are user-defined registry entries. You can:

- create them
- edit them
- reorder them
- hide them
- delete them

---

## Visibility Rules

Hidden games stop showing up in normal selectors, but their related data is not erased just because you hid them.

One safety rule is enforced: at least one game must stay visible.

---

## Persistence

The manager stores its state in `settings/custom_games.json`, including:

- order
- visibility
- custom game definitions

Changes are meant to take effect across the app, not just inside the dialog.
