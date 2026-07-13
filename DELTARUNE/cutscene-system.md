# Cutscene System

Chapters 2 through 5 use `obj_cutscene_master` as a queued scene interpreter.
Chapter 1 stages scenes directly in room and actor objects. The later system is
a command layer over ordinary instances, dialogue, audio, cameras, flags, and
room changes; it is not a separate timeline asset format.

## Construction and Data Model

`scr_cutscene_make()` creates the master and records the calling object in
`master_object`. `c_cmd()` serializes an opcode, selected actor, and up to six
arguments into parallel arrays. The arrays contain 800 slots and default to the
`"terminate"` opcode. Readable `c_*` wrappers are the intended authoring API.

```gml
cutscene = scr_cutscene_make();
scr_maincharacters_actors();
c_sel(kr);
c_walk("d", 2, 10);
c_wait(20);
c_msgsetloc(0, "* We made it./%", "mod_slash_arrival_0");
c_speaker("susie");
c_talk_wait();
c_cmd("terminate", 0, 0, 0, 0);
```

The exact actor-registration wrapper varies between payloads, so copy it from a
scene in the target chapter. Do not mix wrappers from another executable merely
because their names look compatible.

## Dispatch and Blocking

The Step event consumes non-blocking commands in the same frame. The opcode
interpreter is `scr_cutscene_commands()`. A blocking command sets `waiting` and
normally `breakme`, so dispatch stops until its completion predicate succeeds.

| Wait family | Completion condition                                 |
| ----------- | ---------------------------------------------------- |
| Timer       | `cs_wait_timer` reaches `cs_wait_amount`             |
| Dialogue    | The tracked dialoguer no longer exists               |
| Box         | The writer reaches a requested message/end state     |
| Conditional | An instance variable satisfies the stored comparison |
| Custom      | A registered callback reports completion             |
| Sound       | The requested sound duration/playback wait completes |

For `c_wait_if`, a missing instance variable also releases the wait. Destroying
the watched actor can therefore unblock a scene.

## Command Families

- Flow: waits, conditional waits, delayed commands, callbacks, termination.
- Actors: select, walk, walk-to, set/add coordinates, face, spin, halt, stick,
  sprite, image frame/speed, visibility, depth, and automatic movement/depth.
- Dialogue: message set/next, localized variants, speaker, face/expression,
  talk, box side, stay, run check, and cutscene-skip prevention.
- Camera and effects: pan, pan-to-object, pan speed, shake, fade, emote, and
  chapter-specific presentation helpers.
- Audio: sound, wait-for-sound, music, secondary music, fade and pan.
- State: create/destroy objects, invoke scripts, mutate instance/global fields,
  save/load hooks, and route flags.
- Party: convert actors to caterpillar members, restore Kris, or stage one party
  member independently.

Chapter 5 retains this interpreter and adds commands used by garden, cliff,
platforming, and flower-castle scenes. The authoritative set is the Chapter 5
`scr_cutscene_commands()` plus its shipped `c_*` scripts; Chapter 4 is no longer
the largest safe reference.

## Dialogue, Choice, and Localization

`c_msgsetloc(message_index, english, localized_string_id)` and its related
wrappers resolve localized text before handing it to the normal dialoguer and
writer. Choices remain writer/dialogue state: a scene blocks until the choice
controller produces a result, then branches through flags or owner variables.

```gml
c_msgsetloc(0, "* Open the door?/%", "mod_slash_choice_slash_prompt_0");
c_talk_wait();
// Create/configure the target chapter's choice object here.
c_wait_if(owner, "choice_done", "=", 1);
```

Use the target chapter's real choice helper or object; choice APIs differ more
than plain messages.

## Skip and Cleanup

Normal dialogue may fast-forward, but `preventcskip` can forbid scene skipping.
Instant/skip execution still has to preserve side effects. Any scene exit,
including a skipped or conditional exit, must restore all state it borrowed:

- player movement and visibility;
- party/caterpillar membership;
- actor `autowalk`, `autofacing`, and `autodepth`;
- camera target, pan, shake, and offsets;
- music and transient effects;
- dialogue and temporary objects;
- owner/controller fields and the cutscene master itself.

`kill_actors`, `stay`, owner destruction, room changes, and `terminate` affect
that lifecycle. A queue that reaches its end while a borrowed state remains is a
gameplay bug, even if the master destroys cleanly.

## Flags, Saves, and Progression

Commands that assign `global.plot`, `global.flag[]`, route fields, inventory, or
chapter completion state have save consequences. Put durable mutations after the
player commits to the event and before a transition that may save. A simple
route mutation is:

```gml
c_globalvar("filechoice_route", "_b");
c_var_instance(owner, "route_committed", 1);
```

confirm the exact helper signature in the target payload. Chapter 5 owns
`global.filechoice_route`; its established values are `""` and `"_b"`, not a
numeric Boolean. An arbitrary `global.flag[]` is not interchangeable with it.

## Debugging Checklist

1. Confirm the opcode exists in the target chapter's dispatcher.
2. Confirm the wrapper serializes arguments in the expected order.
3. Inspect which command sets `waiting`/`breakme`.
4. Inspect the precise release predicate.
5. Follow both normal and skipped cleanup paths.
6. Trace every durable flag into save/load and room-entry consumers.

See [Dialogue System](dialogue-system.md) and
[Rooms, Events, and Progression](rooms-events-and-progression.md).
