# Dialogue System

Dialogue is a pipeline: scene code fills `global.msg[]`, a dialoguer owns the
box, `obj_writer` reveals and interprets the text, and speaker/portrait state
selects its presentation. Battle, cutscene, board, and Chapter 5 platforming
surfaces reuse or specialize this pipeline.

## Message Storage and Routing

`global.msg[0..99]` is the transient message buffer. `scr_text()` and room, NPC,
battle, or cutscene code populate it; a writer copies the entries into its own
string array. `%%` ends a message entry. Scene selection (`global.msc`) is
separate from rendering, so search both the caller and `scr_text()` when tracing
a line.

Later cutscenes commonly use `c_msgset`, `c_msgnext`, localized variants, and
substitution variants instead of writing the buffer directly.

## Dialoguer and Writer

`obj_dialoguer` decides box placement, creates the writer, and tracks lifecycle.
It can select the top or bottom according to Kris and the camera. Important
fields include `side`, `stay`, `free`, `drawbox`, `boxheight`, `boxwidth`,
`zurasu`, `runcheck`, and `preventcskip`.

`obj_writer` owns timed reveal, character spacing, input, inline commands,
faces, sounds, and completion. `button1` advances, `button2` fast-forwards, and
anti-mash fields can delay either action. Cutscene controls can disable confirm
or prevent skipping. `obj_writer_stay`, battle/menu/board writers, and Chapter
5's platforming dialoguer are specialized surfaces, not independent text data.

## Type, Voice, and Effects

`global.typer` selects a case in `scr_texttype()`. Each case configures font,
color, origin, line width, speed, sound, spacing, scale, and style. Typewriter
sound is selected by the typer/speaker context and character reveal triggers
portrait mouth movement. Special cases provide silent, echo, black-text, battle,
TV, character, and 8-bit voices.

Inline control codes change pacing and presentation inside a line. The shipped
writer is the authority for the target chapter: it handles pauses, face and
expression changes, typer changes, sound/effects, color, shaking, inline
sprites, mini-faces, and writer-owned objects. Escaping is significant; confirm
the actual stored string rather than copying a rendered line.

## Speakers and Portraits

`scr_speaker(name)` sets `global.typer` and `global.fc`; `global.fe` selects the
expression. Face-parent objects draw full or small portraits and receive mouth
animation from writer timing. Context can change a speaker's voice in Light
World, Dark World, battle, a disguise, or a chapter-specific scene. See
[Speaker System](speaker-system.md).

## Choices

Choices are configured message/choice objects whose result is read by the
caller. They are not embedded localization keys. A robust branch records the
answer before destroying the chooser and only then advances the scene:

```gml
if (choice_result == 0) {
    scr_flag_set(1201, 1);
    global.msg[0] = stringsetloc("* You agreed.%%", "mod_slash_choice_yes_0");
} else {
    global.msg[0] = stringsetloc("* You declined.%%", "mod_slash_choice_no_0");
}
scr_writetext();
```

Choice object fields and numbering differ by payload. Copy a working choice from
the same chapter and trace the result consumer.

## Localization

`stringsetloc(english, localized_string_id)` returns the English argument in
English and looks up the second argument in other languages. Localize the stable
source entry, not a writer's post-processed buffer:

```gml
global.msg[0] = stringsetloc(
    "* The flowers lean toward you.%%",
    "mod_slash_garden_slash_greeting_0"
);
```

Preserve control codes, placeholders, message terminators, and substitution
order in every locale. Japanese is not strings-only: `scr_texttype()` adjusts
spacing, scale, and vertical layout for Japanese fonts. See
[Localization](localization.md).

## Chapter Evolution

### Chapter 1

**Dialogue characteristics:** Direct room/actor staging and the smallest writer
surface

### Chapter 2

**Dialogue characteristics:** Cutscene command bridge, more typer and anti-mash
state

### Chapter 3

**Dialogue characteristics:** Writer-owned objects, alpha/fade/shadow and
funnytext-heavy scenes

### Chapter 4

**Dialogue characteristics:** More typer cases, box controls, run checks and
skip prevention

### Chapter 5

**Dialogue characteristics:** Retains the full stack; adds speakers, effects and
platforming dialogue

## Trace Checklist

1. Find the line key or English fallback.
2. Identify who fills `global.msg[]`.
3. Follow the dialoguer/writer variant.
4. Resolve speaker, typer, face, and expression.
5. Inspect inline codes and substitutions.
6. Follow choice output and durable route flags.
7. Check both locale fallback and Japanese layout behavior.

Related: [Cutscene System](cutscene-system.md),
[Funnytext System](funnytext-system.md), and
[Rooms, Events, and Progression](rooms-events-and-progression.md).
