# Games

G3M currently ships with seven built-in games and also supports runtime-defined custom single-tab games.

---

## Built-In Games

| Game | ID | Steam App ID | GameBanana ID | Tabs | Full Install | Direct Launch |
| --- | --- | --- | --- | --- | --- | --- |
| DELTARUNE | `deltarune` | `1671210` | `6755` | Main menu, Chapters 1-4 | No | Yes |
| DELTARUNEdemo | `deltarunedemo` | `1690940` | — | Demo | Yes | No |
| UNDERTALE | `undertale` | `391540` | `5506` | Single tab | No | Yes |
| UNDERTALE Yellow | `undertaleyellow` | — | `19606` | Single tab | Yes | Yes |
| Pizza Tower | `pizzatower` | `2231450` | `7692` | Single tab | No | Yes |
| Sugary Spire | `sugaryspire` | — | `18218` | Single tab | Yes | Yes |
| FRICKBEARS3 | `frickbears3` | — | `24426` | Single tab | Yes | Yes |

Only games with a nonzero GameBanana ID are included in search and browser-backed download flows.

---

## Custom Games

Custom games are stored in `settings/custom_games.json` and published through the same runtime registry as built-in games.

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

The game manager can reorder entries, hide games, and add or remove custom games. At least one game must stay visible.

---

## Launch Behavior

At launch time G3M resolves the selected game definition, current profile state, and selected mods, then:

1. validates the game path
2. resolves the executable
3. applies patches or full replacements
4. copies extra files
5. runs plugin hooks
6. launches directly or through Steam
7. monitors the target process
8. restores original files after exit

DELTARUNE is the only built-in multi-tab game. It also supports per-chapter direct launch state and can block Steam when direct launch is used.
