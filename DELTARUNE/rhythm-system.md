# Rhythm System

The rhythm-game runtime is a major Chapter 3 addition that continues into Chapter 4. It has its own controller, note chart format, performer objects, scoring, and persistence.

---

## Core Scripts

| Script | Purpose |
|---|---|
| `scr_rhythmgame_init` | Initializes instrument, note colors, chart, and performer |
| `scr_rhythmgame_notechart` | Dispatcher — calls `scr_rhythmgame_notechart_<instrument>(song_id)` |
| `scr_rhythmgame_addnote` | Adds a single note to the chart |
| `scr_rhythmgame_addnote_range` | Adds a note within a chart subsection |
| `scr_rhythmgame_addnote_bpm` | Adds a note using BPM-relative timing |
| `scr_rhythmgame_addnote_snap` | Adds a note with quantization snapping |
| `scr_rhythmgame_draw` | Renders the note track and hit indicators |
| `scr_rhythmgame_tools` | Utility functions for the rhythm runtime |
| `scr_rhythmgame_lyrics` | Lyrics display system |
| `scr_rhythmgame_score_save` | Persists high scores to `global.flag[]` |
| `scr_rhythmgame_score_load` | Loads a single song score |
| `scr_rhythmgame_score_load_all` | Loads all rhythm scores at once |
| `scr_rhythmgame_song_flag` | Resolves song/difficulty to flag index |
| `scr_rhythmgame_song_load` | Loads a song for playback |

---

## `scr_rhythmgame_init` — Initialization

```gml
function scr_rhythmgame_init(arg0, arg1, arg2 = false, arg3 = true)
```

| Argument | Purpose |
|---|---|
| `arg0` | Instrument id (0 = lead, 1 = drums, 2 = vocals) |
| `arg1` | Song/chart id passed to notechart script |
| `arg2` | Whether to create performer visuals (`false` = chart only, `true` = full display) |
| `arg3` | Whether to load the notechart (vocals only — allows skip) |

### Instrument Configuration

| Instrument | Performer | Sprite | Note Colors | Position |
|---:|---|---|---|---|
| 0 (lead) | Kris | `spr_kris_rock_2` | `#01EA9E`, `#17EEFF`, orange | (280, 316) |
| 1 (drums) | Susie | `spr_susie_drum` | `#D1176A`, `#EA79C8` | (56, 281) |
| 2 (vocals) | Ralsei | `spr_ralsei_rock_1` | green, `#B5E61D`, lime | (486, 304) |

Each instrument has custom note colors. Drums use a 2-color palette; lead and vocals use 3 colors.

Performer sprites are scaled 2x and placed at fixed positions. The performer keeps a back-reference to the rhythm controller via `performer.rhythmer = id`.

---

## Note Chart Format

Note charts are hardcoded procedural sequences of `scr_rhythmgame_addnote` calls. Each call adds one note:

```gml
function scr_rhythmgame_addnote(arg0, arg1, arg2 = 0, arg3 = 0, arg4 = false)
{
    notetime[maxnote] = arg0;      // Time position (seconds)
    notetype[maxnote] = arg1;      // Note type (0, 1, 2 = lane/color)
    noteend[maxnote] = arg2;       // Hold-note end time (0 = tap note)
    noteanim[maxnote] = arg3;      // Animation trigger
    notealive[maxnote] = 1;        // Active flag
    notescore[maxnote] = 0;        // Score accumulator
    maxnote++;
}
```

### Note Types

| `notetype` | Meaning |
|---:|---|
| 0 | Lane 0 / color 0 |
| 1 | Lane 1 / color 1 |
| 2 | Lane 2 / color 2 |

Multiple notes at the same `notetime` create chords (e.g. drum + cymbal simultaneously).

### Hold Notes

When `noteend > 0`, the note is a sustained hold from `notetime` to `noteend`. The player must hold the input for the full duration.

### Chart Selection

The dispatcher `scr_rhythmgame_notechart` uses dynamic script execution:

```gml
Script_execute("scr_rhythmgame_notechart_" + arg0, arg1);
```

Available chart functions:
- `scr_rhythmgame_notechart_lead(song_id)`
- `scr_rhythmgame_notechart_drums(song_id)`
- `scr_rhythmgame_notechart_vocals(song_id)`

Each function branches on `song_id` (the `arg0` passed from init) to select the specific chart. The notechart file is 5067 lines of dense note data across all songs and instruments.

---

## BPM-Relative Note Addition

```gml
function scr_rhythmgame_addnote_bpm(arg0, arg1, arg2 = 0)
{
    arg0 *= meter;
    arg0 -= startoffset;
    // ...
}
```

The `meter` variable converts beat-relative positions to absolute time. `startoffset` accounts for intro silence. This allows charts to be authored in beats rather than raw seconds.

---

## Range-Limited Notes

```gml
function scr_rhythmgame_addnote_range(arg0, arg1, arg2 = 0, arg3 = 0, arg4 = false)
```

Used for partial chart loading (e.g. when only a section of a song is played). Notes outside the `chart_start` to `chart_end` range are skipped. Notes before the visible window are pre-scored at 40 points.

---

## Score Persistence (Chapter 4)

### `scr_rhythmgame_score_save`

```gml
function scr_rhythmgame_score_save(arg0, arg1, arg2, arg3, arg4)
{
    if (arg3 == 0)
        arg3 = scr_rhythmgame_song_flag(arg0, arg2);
    if (!arg4 || arg1 >= global.flag[arg3])
        global.flag[arg3] = arg1;
}
```

- `arg0` = song id
- `arg1` = score value
- `arg2` = difficulty
- `arg3` = explicit flag index (0 = auto-resolve)
- `arg4` = best-only mode (true = only save if higher)

### `scr_rhythmgame_song_flag` — Flag Index Resolution

```gml
function scr_rhythmgame_song_flag(arg0, arg1)
{
    if (arg0 == 2)
        return arg1 ? 1667 : 1666;
    else if (arg0 == 10)
        return arg1 ? 1669 : 1668;
    else
        return arg1 ? 1279 : 1195;
}
```

| Song ID | Easy Flag | Hard Flag |
|---:|---:|---:|
| default | 1195 | 1279 |
| 2 | 1666 | 1667 |
| 10 | 1668 | 1669 |

`arg1` = difficulty (0 = easy, 1 = hard). Scores are stored in `global.flag[]` and persisted through the save system.

---

## Performer System

`obj_rhythmgame_performer` handles the on-screen character animation:

| Property | Purpose |
|---|---|
| `name` | Character identifier |
| `sprite_index` | Active animation sprite |
| `image_speed` | Animation speed (0 for manual, 0.5 for auto) |
| `loop` | Whether animation loops |
| `animspeed` | Custom animation timing |
| `mid` | Mid-performance sprite (vocals) |
| `idle` | Idle sprite (vocals) |
| `rhythmer` | Back-reference to rhythm controller |

Ralsei (vocals) has distinct `mid`/`idle` sprites (`spr_ralsei_sing_polite`, `spr_ralsei_sing_polite_closed`) for mouth open/closed states.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a new song chart | Add a case in the appropriate `scr_rhythmgame_notechart_*` function |
| Change note colors | Edit `note_color[]` in `scr_rhythmgame_init` |
| Change performer visuals | Edit sprite/position assignments in `scr_rhythmgame_init` |
| Add a new instrument | Add an `else if` branch in `scr_rhythmgame_init` |
| Change score persistence | Edit `scr_rhythmgame_song_flag` to map new flag indices |
| Change note timing | Edit `scr_rhythmgame_addnote` calls in the chart function |
| Add BPM-based charting | Use `scr_rhythmgame_addnote_bpm` with `meter` and `startoffset` |

---

## Relationship To Other Pages

- [Global Variables](global-variables.md) explains the `global.flag[]` storage model used for scores
- [Save & Load System](save-load-system.md) explains how flag values persist across sessions
- [Battle System](battle-system.md) — some rhythm segments occur during battle sequences