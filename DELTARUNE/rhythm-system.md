# Rhythm System

The rhythm-game runtime is another major Chapter 3 addition that continues into Chapter 4. Like the board system, it is large enough to deserve its own page instead of being buried as a side note elsewhere.

The main roots are:

- `scripts/scr_rhythmgame_*`
- `objects/obj_rhythmgame*`
- performer/effect helper objects spawned by the initializer

---

## Initializer

`scr_rhythmgame_init` chooses the chart, note palette, and on-screen performer based on the requested instrument.

Representative Chapter 3 structure:

```gml
if (instrument == 0)
{
    scr_rhythmgame_notechart_lead(arg1);
    performer = instance_create(x, y, obj_rhythmgame_performer);
    performer.sprite_index = spr_kris_rock_2;
    performer.performer_name = "kris";
}
if (instrument == 1)
{
    scr_rhythmgame_notechart_drums(arg1);
    performer = instance_create(x, y, obj_rhythmgame_performer);
    performer.sprite_index = spr_susie_drum;
    performer.performer_name = "susie";
}
if (instrument == 2)
{
    scr_rhythmgame_notechart_vocals(arg1);
    performer = instance_create(x, y, obj_rhythmgame_performer);
    performer.sprite_index = spr_ralsei_rock_1;
    performer.performer_name = "ralsei";
}
performer.image_xscale = 2;
performer.image_yscale = 2;
performer.rhythmer = id;
```

This tells us:

- note charts are selected by function, not one flat table
- performer visuals are created at runtime
- the performer keeps a back-reference to the rhythm controller

---

## Instrument-Specific Runtime

## Instrument 0: lead

- chart source: `scr_rhythmgame_notechart_lead(arg1)`
- performer: Kris
- sprite: `spr_kris_rock_2`

## Instrument 1: drums

- chart source: `scr_rhythmgame_notechart_drums(arg1)`
- performer: Susie
- sprite: `spr_susie_drum`

## Instrument 2: vocals

- chart source: `scr_rhythmgame_notechart_vocals(arg1)`
- performer: Ralsei
- sprite: `spr_ralsei_rock_1`

---

## Chapter 4 Score Persistence

Chapter 4 adds explicit save integration through `scr_rhythmgame_score_save`:

```gml
function scr_rhythmgame_score_save(arg0, arg1, arg2, arg3, arg4)
{
    if (arg3 == 0)
        arg3 = scr_rhythmgame_song_flag(arg0, arg2);
    if (!arg4 || arg1 >= global.flag[arg3])
        global.flag[arg3] = arg1;
}
```

So rhythm high scores are stored in normal `global.flag[]` space, with helper logic to resolve the correct song/difficulty flag and optionally preserve only best scores.

---

## Chapter Differences

## Chapter 3

- establishes the rhythm subsystem
- introduces chart-selection scripts and performer objects

## Chapter 4

- keeps the same broad runtime model
- adds stronger persistence-facing helpers such as score saving into `global.flag[]`

---

## Modding Implications

- If the wrong note pattern loads, the likely problem is the selected notechart script.
- If the wrong character performs, inspect the instrument id passed into `scr_rhythmgame_init`.
- If high scores do not persist, inspect the resolved flag index from `scr_rhythmgame_song_flag`.

---

## Relationship To Other Pages

- [Global Variables](global-variables.md) explains the broader `global.flag[]` storage model.
- [Save & Load System](save-load-system.md) explains how those flags persist.
