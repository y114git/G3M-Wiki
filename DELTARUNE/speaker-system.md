# Speaker System

`scr_speaker` is the centralized text-voice routing function. It maps character name strings to `global.typer` (voice/font style) and `global.fc` (portrait character id).

---

## Core Script

```gml
function scr_speaker(arg0)
```

Sets `global.typer` and `global.fc` based on the input string. The function first applies a base typer depending on world state:

| Condition | Base `global.typer` |
|---|---:|
| Light World | 5 |
| Dark World (`global.darkzone == 1`) | 6 |
| In battle (`global.fighting == 1`) | 4 |

Then `global.fc` is reset to `0` (no portrait).

---

## Speaker Mapping

`scr_speaker` exists in Chapters 2, 3, and 4. Each chapter extends the mapping with new characters. The table below shows the Chapter 4 version (the most entries):

| Speaker String | Aliases | `global.fc` | `global.typer` | Notes |
|---|---|---:|---:|---|
| `"silent"` | — | 0 | 2 (light) / 36 (dark) | No voice, narrator style |
| `"balloon"` / `"enemy"` | — | 0 | 50 | Black-text dotumche font |
| `"sans"` | — | 6 | 14 | — |
| `"undyne"` | `"und"` | 9 | 17 | — |
| `"temmie"` | `"tem"` | 0 | 21 | No portrait |
| `"jevil"` | — | 0 | 35 | No portrait |
| `"catti"` | — | 13 | *(base)* | Portrait only, default typer |
| `"jockington"` | `"joc"` | 14 | *(base)* | Portrait only |
| `"catty"` | `"caddy"` | 16 | *(base)* | Portrait only |
| `"bratty"` | `"bra"` | 17 | *(base)* | Portrait only |
| `"rouxls"` | `"rou"` | 18 | *(base)* | Portrait only |
| `"burgerpants"` | `"bur"` | 19 | *(base)* | Portrait only |
| `"spamton"` | — | 0 | 66 (overworld) / 68 (battle) | Context-dependent |
| `"sneo"` | — | 0 | 67 | — |
| `"gerson"` | `"ger"`, `"gers"` | 0 | 85 | — |
| `"susie"` | `"sus"` | 1 | 10 (light) / 30 (dark) / 47 (battle) | Full context logic |
| `"ralsei"` | `"ral"` | 2 | 31 / 45 (battle) / 6 (flag 30) | `global.flag[30] == 1` → disguised typer |
| `"noelle"` | `"noe"` | 3 | 12 (light) / 56 (dark) / 59 (battle) | Full context logic |
| `"toriel"` | `"tor"` | 4 | 7 | — |
| `"asgore"` | `"asg"` | 10 | 18 | — |
| `"king"` | `"kin"` | 20 | 33 / 36 (Ch1 pre-plot 235) / 48 (battle) | Chapter-sensitive |
| `"rudy"` | `"rud"` | 15 | 55 | — |
| `"lancer"` | `"lan"` | 5 | 32 / 46 (battle) | — |
| `"berdly"` | `"ber"` | 12 | 13 (light) / 57 (dark) / 77 (battle) | Full context logic |
| `"alphys"` | `"alp"` | 11 | 20 | — |
| `"queen"` | `"que"` | 21 | 58 | — |
| `"queen_2"` | `"que_2"` | 21 | 62 | Alternate Queen voice |
| `"carol"` | — | 22 | 87 | — |
| `"jackenstein_cute"` | — | 0 | 82 | — |
| `"jackenstein"` | — | 0 | 83 | — |
| `"tenna"` | — | 0 | 84 | — |

---

## Context Logic for Main Characters

### Susie

```
Light World:       typer = 10
Dark World:        typer = 30
Battle:            typer = 47
```

### Ralsei

```
Standard:          typer = 31
Battle:            typer = 45
global.flag[30]:   typer = 6 (disguised/default dark voice)
```

### Noelle

```
Light World:       typer = 12
Dark World:        typer = 56
Battle:            typer = 59
```

### Berdly

```
Light World:       typer = 13
Dark World:        typer = 57
Battle:            typer = 77
```

### King

```
Standard:          typer = 33
Ch1 (plot<235):    typer = 36 (no-face dark voice)
Battle:            typer = 48
```

---

## Usage

`scr_speaker` is called by:

- Cutscene commands (`c_speaker`)
- Room event scripts before `scr_writetext`
- Battle controller for speaker-specific text

The `\\T?` inline writer tag provides a similar per-character typer change mid-line. See [Dialogue System](dialogue-system.md) for the `\\T` tag reference.

---

## Portrait Character IDs (`global.fc`)

| `global.fc` | Character |
|---:|---|
| 0 | No portrait |
| 1 | Susie |
| 2 | Ralsei |
| 3 | Noelle |
| 4 | Toriel |
| 5 | Lancer |
| 6 | Sans |
| 9 | Undyne |
| 10 | Asgore |
| 11 | Alphys |
| 12 | Berdly |
| 13 | Catti |
| 14 | Jockington |
| 15 | Rudy |
| 16 | Catty |
| 17 | Bratty |
| 18 | Rouxls |
| 19 | Burgerpants |
| 20 | King |
| 21 | Queen |
| 22 | Carol |

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a new speaker | Add an `if` block in `scr_speaker`, assign fc + typer |
| Change voice/font for a speaker | Edit the typer assignment in `scr_speaker` |
| Add a new portrait | Add a sprite sheet and assign a new `global.fc` value |
| Change context-dependent voice | Edit the darkzone/fighting branches for the speaker |