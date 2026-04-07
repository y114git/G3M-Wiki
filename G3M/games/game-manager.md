# Game Manager

The Game Manager is a dialog that lets you control which games appear in G3M and in what order.

---

## Opening the Game Manager

Settings → Game section → click the **Game Manager** button.

---

## Game List

The dialog shows all games — both built-in and custom — in their current display order. Each row shows:

- **Game icon / name** — The display name of the game.
- **Visibility toggle** — A checkbox or eye icon to show/hide the game across the app. Hidden games do not appear in the Library game dropdown, the Mods Browser game selector, or the title bar game switcher.
- **Reorder controls** — Up/Down arrow buttons to change the game's position in the list. The order determines the display order everywhere in G3M.

---

## Reordering

Click the up or down arrows (or drag, if supported) to move a game higher or lower in the list. The first visible game in the list becomes the default game selected on launch.

---

## Visibility

Toggle the visibility checkbox to hide or show a game. A hidden game:

- Is removed from game selector dropdowns.
- Its mods are still stored on disk and in profiles — they are just not displayed.
- It can be made visible again at any time.

You cannot hide all games. At least one must remain visible.

---

## Adding a Custom Game

At the bottom of the Game Manager dialog, there is an **Add Game** button. Clicking it opens the custom game creation form. See [Custom Games](custom-games.md) for details on the fields.

---

## Deleting a Custom Game

Select a custom game in the list and click **Delete**. Built-in games cannot be deleted. A confirmation dialog prevents accidental deletion.

---

## Persistence

All changes (order, visibility, custom games) are saved immediately to `custom_games.json` in the user data folder. The changes take effect across the entire application.
