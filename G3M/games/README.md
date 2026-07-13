# Games

G3M currently ships with seven built-in games and also supports runtime-defined
custom single-tab games.

---

## Built-In Games

- **Game:** DELTARUNE
  - **ID:** `deltarune`
  - **Steam App ID:** `1671210`
  - **GameBanana ID:** `6755`
  - **Tabs:** Main menu, Chapters 1-5
  - **Full Install:** No
  - **Direct Launch:** Yes

- **Game:** DELTARUNEdemo
  - **ID:** `deltarunedemo`
  - **Steam App ID:** `1690940`
  - **GameBanana ID:** —
  - **Tabs:** Demo
  - **Full Install:** Yes
  - **Direct Launch:** No

- **Game:** UNDERTALE
  - **ID:** `undertale`
  - **Steam App ID:** `391540`
  - **GameBanana ID:** `5506`
  - **Tabs:** Single tab
  - **Full Install:** No
  - **Direct Launch:** Yes

- **Game:** UNDERTALE Yellow
  - **ID:** `undertaleyellow`
  - **Steam App ID:** —
  - **GameBanana ID:** `19606`
  - **Tabs:** Single tab
  - **Full Install:** Yes
  - **Direct Launch:** Yes

- **Game:** Pizza Tower
  - **ID:** `pizzatower`
  - **Steam App ID:** `2231450`
  - **GameBanana ID:** `7692`
  - **Tabs:** Single tab
  - **Full Install:** No
  - **Direct Launch:** Yes

- **Game:** Sugary Spire
  - **ID:** `sugaryspire`
  - **Steam App ID:** —
  - **GameBanana ID:** `18218`
  - **Tabs:** Single tab
  - **Full Install:** Yes
  - **Direct Launch:** Yes

- **Game:** FRICKBEARS3
  - **ID:** `frickbears3`
  - **Steam App ID:** —
  - **GameBanana ID:** `24426`
  - **Tabs:** Single tab
  - **Full Install:** Yes
  - **Direct Launch:** Yes

Only games with a nonzero GameBanana ID are included in search and
browser-backed download flows.

---

## Custom Games

Custom games are stored on Windows in
`%LOCALAPPDATA%\G3M\settings\custom_games.json` and published through the same
runtime registry as built-in games.

Each custom game defines:

- display name
- primary executable file name
- data file name
- optional Steam App ID
- optional GameBanana ID

Custom games are always single-tab and do not support full install.

---

## Registry and Visibility

G3M keeps a runtime game registry with:

- order
- visibility
- built-in entries
- custom entries

The game manager can reorder entries, hide games, and add or remove custom
games. At least one game must stay visible.

---

## Launch Behavior

At launch time G3M resolves the selected game definition, current profile state,
and selected mods, then:

1. validates the game path
2. resolves the executable
3. applies patches or full replacements
4. copies extra files
5. runs plugin hooks
6. launches directly or through Steam
7. monitors the target process
8. restores original files after exit

DELTARUNE is the only built-in multi-tab game. It also supports per-chapter
direct launch state and can block Steam when direct launch is used.
