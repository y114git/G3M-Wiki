# Game Manager

The Game Manager controls the launcher's game list: what appears, in what order,
and which extra custom games exist.

---

## Where to find it

1. Open G3M.
2. Open **Settings**.
3. Go to the game settings area.
4. Click **Game Manager**.

The dialog affects which games appear in selectors across G3M. It does not edit
game files on disk.

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

Built-in games are part of G3M itself. You can reorder or hide them, but not
delete them.

Custom games are user-defined registry entries. You can:

- create them
- edit them
- reorder them
- hide them
- delete them

---

## Add a custom game

1. Open **Settings -> Game Manager**.
2. Click **Add** or **Create custom game**.
3. Enter the display name.
4. Enter the executable file name, for example `MyGame.exe` on Windows or
   `runner` for a native Linux GameMaker build.
5. Enter the DATA file name, for example `data.win`, `game.unx`, `game.ios`, or
   `game.win`.
6. Optionally enter Steam or GameBanana IDs if the game uses them.
7. Save.

After saving, the game appears in G3M's game selector if it is visible. Then
configure its game folder in **Settings -> Game Settings**.

For native Linux GameMaker games, the DATA file is commonly `game.unx`. For
Windows builds, it is commonly `data.win`.

---

## Hide or reorder games

Use hide when you do not want a game to appear in normal selectors. Use reorder
to put the games you use most at the top.

Hidden games keep their saved settings. Hiding a game does not delete installed
mods, profiles, saved game versions, or custom game records.

---

## Visibility Rules

Hidden games stop showing up in normal selectors, but their related data is not
erased just because you hid them.

One safety rule is enforced: at least one game must stay visible.

---

## Persistence

The manager stores its state on Windows in:

`%LOCALAPPDATA%\G3M\settings\custom_games.json`

That file includes:

- order
- visibility
- custom game definitions

Changes are meant to take effect across the app, not just inside the dialog.
