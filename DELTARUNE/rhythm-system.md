# Rhythm System

The rhythm framework begins in Chapter 3 and is retained through Chapters 4
and 5. Unlike the board game, it has production room runtime basis in all three
payloads: `room_dw_rhythm` and `room_dw_teevie_rhythm` in Chapter 3, then
`room_dw_castle_tv_rhythm` in Chapters 4 and 5. Editor rooms are debug tools;
similarly named empty/countdown rooms have presentation or unresolved-ingress
statuses and are not automatically production entry points.

## Runtime stack

`obj_rhythmgame` owns timing, score, input, health, chart position and performer
references. `obj_rhythmgame_chart` draws notes; performer, crowd, parallax,
spotlight, effects and event-manager objects provide presentation. Chapters 4
and 5 add castle-TV doors, scrollers, speakers and symbols. Chapter 5
additionally retains `obj_rhythmgame_jackenstein_events`.

`scr_rhythmgame_init(instrument, song, create_performer, load_chart)` selects
the instrument palette and performer. Note-chart dispatch reaches lead, drums,
vocals, lyrics, solo and finale functions. Each note records start time, lane,
optional hold end, animation trigger, alive state and score. Range, BPM and snap
helpers author sections without changing that stored note contract.

Chapter 5 expands the stack with beat checks, separated draw helpers for border,
combo, chart, tap, hold and clap notes, note looping/skipping, damage flash,
song lists and ranks, BPM/time-signature changes, event-track loading, lyric
parsing and kanji timing. Its editor helpers for insert, delete, move, undo,
redo, clipboard and file load/save are shipped tooling; editor presence is not
runtime basis of a production file-writing path.

## Animation and audiovisual timing

Performers use `sprite_index`, `image_speed`, loop state, custom animation speed
and controller back-references. The note `noteanim` field triggers performance
animation. Spotlights, crowd, backing, parallax and effects are separate draw
layers. Music loading/reset/select helpers establish the audio timeline; beat
and user-event helpers schedule callbacks against it. Sound effects remain
separate from the music instance, allowing hit, miss, damage and UI cues without
restarting the song.

## Score persistence

`scr_rhythmgame_score_save` resolves a flag with
`scr_rhythmgame_song_flag(song, difficulty)` unless an explicit flag is passed,
then optionally enforces best-only replacement. established mappings include
default easy/hard flags 1195/1279, song 2 flags 1666/1667, and song 10 flags
1668/1669. Chapter 5 retains score loading and saving, but a retained chart or
score helper does not establish that every song case is reachable.

## Practical extension

For a new Chapter 5 chart, add the song metadata and audio selection, create the
appropriate lead/drums/vocals chart case, register BPM and signature changes,
and assign unused save flags. Add performer/event animation through `noteanim`
or the event manager, not by keying visuals to wall-clock time. confirm easy and
hard score reload, pause/resume, song reset, hold-note release, damage flash,
lyrics, and the production room's completion branch.

## Related pages

- [Global Variables](global-variables.md)
- [Save and Load System](save-load-system.md)
- [Rendering, Animation, and Audio](rendering-animation-audio.md)
