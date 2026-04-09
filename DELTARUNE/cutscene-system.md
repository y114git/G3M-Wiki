# Cutscene System

DELTARUNE's later chapters do not drive story scenes by hardcoding every action inside one giant room event. Instead, they build a command queue inside `obj_cutscene_master` and then execute that queue step by step. In practice this becomes a lightweight cutscene language layered on top of normal GML.

The most important runtime roots are:

- `scripts/scr_cutscene_make/scr_cutscene_make.gml`
- `scripts/scr_cutscene_master_commands_initialize/scr_cutscene_master_commands_initialize.gml`
- `objects/obj_cutscene_master/Create_0.gml`
- `objects/obj_cutscene_master/Step_0.gml`
- `scripts/c_cmd/c_cmd.gml`
- many helper wrappers named `c_*`

This page focuses on the shipped runtime as seen through UndertaleModTool.

For GameMaker event basics, `with`, and alarms, see:

- https://manual.gamemaker.io/monthly/en/The_Asset_Editors/Object_Properties/Object_Events.htm
- https://manual.gamemaker.io/lts/en/GameMaker_Language/GML_Overview/Language_Features/with.htm

---

## Runtime Entry Point

The typical pattern is that an overworld object creates a cutscene controller and stores its own instance id as the owner:

```gml
function scr_cutscene_make()
{
    _cutscene_master = instance_create(0, 0, obj_cutscene_master);
    _cutscene_master.master_object = id;
    return _cutscene_master;
}
```

This matters for modders because the cutscene object is usually not the scene author. The author is the room object that calls `scr_cutscene_make()`, then fills the queue by calling `c_*` helpers.

---

## Internal Data Model

Chapter 4 shows the fullest shipped version of the controller state:

```gml
waiting = 0;
cs_wait_timer = 0;
cs_wait_amount = 0;
cs_wait_dialogue = 0;
cs_wait_custom = 0;
cs_wait_box = 0;
cs_wait_box_end = 0;
customfunc = -1;
customfuncs = array_create(10, -1);
customfuncs_delayed = array_create(10, 0);
cs_wait_if = false;
mydialoguer = noone;
kill_actors = 0;
loadedState = 0;
instant = 0;
breakme = 0;
debug_pause = 0;
current_command = 0;
maximum_command = 1;
master_object = noone;
msgside = 0;
stay = 0;
runcheck = 0;
preventcskip = 0;
zurasu = 0;
mysound = 138;
actor_selected = "No one";
actor_selected_id = 99999999;
actor_id = array_create(20, 99999999);
actor_name = array_create(20, "noone");
save_object = array_create(10, 99999999);
command = array_create(800, "terminate");
command_actor = array_create(800, 99999999);
command_arg1 = array_create(800, 0);
command_arg2 = array_create(800, 0);
command_arg3 = array_create(800, 0);
command_arg4 = array_create(800, 0);
command_arg5 = array_create(800, 0);
command_arg6 = array_create(800, 0);
```

The queue is a parallel-array command tape:

- `command[i]` stores the opcode such as `"walk"` or `"msgset"`
- `command_actor[i]` stores the bound actor instance
- `command_arg1..command_arg6[i]` store operands

---

## Queue Initialization

Chapter 2 explicitly resets all 800 command slots:

```gml
for (i = 0; i < 800; i += 1)
{
    command[i] = "terminate";
    command_actor[i] = 99999999;
    command_arg1[i] = 0;
    command_arg2[i] = 0;
    command_arg3[i] = 0;
    command_arg4[i] = 0;
    command_arg5[i] = 0;
    command_arg6[i] = 0;
}
current_command = 0;
maximum_command = 1;
```

The `"terminate"` default acts as a safe end marker.

---

## How Commands Are Enqueued

The generic enqueue helper is `c_cmd`:

```gml
function c_cmd(arg0, arg1, arg2, arg3, arg4, arg5, arg6)
{
    with (obj_cutscene_master)
    {
        command[maximum_command - 1] = arg0;
        command_actor[maximum_command - 1] = arg1;
        command_arg1[maximum_command - 1] = arg2;
        command_arg2[maximum_command - 1] = arg3;
        command_arg3[maximum_command - 1] = arg4;
        command_arg4[maximum_command - 1] = arg5;
        command_arg5[maximum_command - 1] = arg6;
        maximum_command += 1;
    }
}
```

Most wrappers are readable aliases over this serializer. For example:

```gml
function c_walk(arg0, arg1, arg2)
{
    c_cmd("walk", arg0, arg1, arg2, 0);
}
```

and Chapter 4's localization-aware message wrapper is:

```gml
function c_msgsetloc(arg0, arg1)
{
    c_msgset(stringsetloc(arg0, arg1));
}
```

---

## Execution Loop

The Step event processes as many queued commands as possible until one of them introduces a wait:

```gml
if (!waiting)
{
    for (i = current_command; i < maximum_command; i += 1)
    {
        current_command = i;
        actor_selected_id = command_actor[i];
        scr_cutscene_commands();
        if (waiting)
            break;
    }
}
```

This is why DELTARUNE cutscenes can chain multiple instant staging operations in one frame and only pause when speech, movement, timers, or conditional checks require it.

---

## Real Step-Event Behavior

Chapter 4's actual Step logic is slightly richer than the simplified model:

```gml
for (i = current_command; i < maximum_command; i += 1)
{
    command_actor[i] = actor_selected_id;
    _c = command[i];
    scr_cutscene_commands();
    if (breakme == 1)
    {
        breakme = 0;
        break;
    }
}
current_command = i + 1;
```

Two details matter here:

- the currently selected actor is copied into `command_actor[i]` at execution time, so actor selection is not only an enqueue-time concern
- `breakme` is the low-level “stop processing further commands this frame” flag used by wait-producing commands

This is why some commands do not merely set `waiting = 1`; they also set `breakme = 1` so the loop stops immediately.

---

## Waiting Modes

Chapter 4 supports several wait families:

- timed waits through `cs_wait_amount` / `cs_wait_timer`
- dialogue waits through `cs_wait_dialogue`
- box lifecycle waits through `cs_wait_box` and `cs_wait_box_end`
- custom waits through `cs_wait_custom` and `customfunc`
- conditional waits through `cs_wait_if`

The conditional layer supports operators:

- `=`
- `!=`
- `>=`
- `<=`
- `>`
- `<`

This makes Chapter 4 scenes notably more flexible than simple Chapter 2 “say line, wait, move” sequences.

---

## Wait-State Semantics

The Step event reveals the exact success conditions for several waits.

### `cs_wait_box`

The queue resumes when:

- `mydialoguer` no longer exists, or
- the writer has reached the required `msgno`, and
- if `cs_wait_box_end` is enabled, the writer must also be halted at message end

This is more precise than a simple “wait until dialogue exists no more.”

### `cs_wait_dialogue`

This is the coarse-grained wait. It resumes only when the whole `mydialoguer` instance is gone.

### `cs_wait_if`

The controller checks an arbitrary instance variable by:

1. testing `variable_instance_exists(cs_wait_if_objectid, cs_wait_if_varname)`
2. reading it through `variable_instance_get(...)`
3. comparing it with the stored operator/value

If the variable is missing entirely, the wait also passes. That is important for modders because destroying an object can satisfy a wait intended for one of its fields.

---

## Actor Selection Layer

The controller maintains:

- `actor_id[0..19]`
- `actor_name[0..19]`
- `actor_selected`
- `actor_selected_id`

so the queue is not only an opcode list. It is also a small actor-routing environment.

---

## Opcode Dispatch Layer

The real opcode interpreter lives in `scr_cutscene_commands()`, where `_c` is compared against literal strings such as:

- `"walk"`
- `"walkto"`
- `"walkdirect"`
- `"msgset"`
- `"msgnext"`
- `"talk"`
- `"msgface"`
- `"msgside"`
- `"msgstay"`
- `"msgruncheck"`
- `"msgpreventcskip"`
- `"speaker"`
- `"fe"`
- `"msc"`
- `"instancecreate"`
- `"varadd"`
- `"varto"`
- `"var"`
- `"script"`
- `"globalvar"`
- `"autowalk"`
- `"autofacing"`
- `"autodepth"`
- `"depth"`
- `"depthobject"`
- `"flip"`
- `"facing"`
- `"halt"`
- `"spin"`
- `"stick"`
- `"sprite"`
- `"specialsprite"`
- `"tenna"`
- `"visible"`
- `"imagespeed"`
- `"imageindex"`
- `"animate"`
- `"soundplay"`
- `"mus"` / `"music"`
- `"fadeout"`
- `"panspeed"`
- `"pan"`
- `"panobj"`

The wrapper-script names and the internal opcode strings do not always match one-for-one, so the wiki should document both levels.

---

## Command Families

The exact helper count is large, but most commands fall into clear groups.

### Flow control

- `c_wait`
- `c_runcheck`
- `c_var`
- `c_customfunc`
- `c_delaycmd`
- `c_wait_if`
- `c_wait_box`
- `c_wait_box_end`
- `c_wait_soundlength`

### Actor movement and staging

- `c_walk`
- `c_setxy`
- `c_walkdirect`
- `c_walktoobject`
- `c_addxy`
- `c_facing`
- `c_facenext`
- `c_pan`
- `c_panobj`
- `c_panspeed`
- `c_depth`
- `c_depthobject`
- `c_autowalk`
- `c_autofacing`
- `c_autodepth`
- `c_stickto`
- `c_stickto_stop`
- `c_flip`
- `c_spin`

### Dialogue/UI

- `c_msgset`
- `c_msgsetloc`
- `c_msgsetsub`
- `c_msgsetsubloc`
- `c_msgnext`
- `c_msgnextloc`
- `c_msgnextsub`
- `c_msgnextsubloc`
- `c_msgface`
- `c_fe`
- `c_fefc`
- `c_msc`
- `c_speaker`
- `c_talk`
- `c_talk_wait`
- `c_msgside`
- `c_msgstay`
- `c_msgpreventcskip`
- `c_msgzurasu`

### Audio/effects

- `c_soundplay`
- `c_soundplay_x`
- `c_soundplay_wait`
- `c_mus`
- `c_mus2`
- `c_shake`
- `c_shakex`
- `c_shakeobj`
- `c_shakeobj_x`
- `c_shakestep`
- `c_shakestep_x`
- `c_fadein`
- `c_fadeout`
- `c_fadeout_color`
- `c_emote`
- `c_animate`
- `c_visible`
- `c_imageindex`
- `c_imagespeed`
- `c_specialsprite`

### Object/script/state mutation

- `c_instance`
- `c_script_instance`
- `c_script_instance_stop`
- `c_globalvar`
- `c_var_extra`
- `c_var_instance`
- `c_var_lerp`
- `c_var_lerp_instance`
- `c_move_instance`
- `c_move_extra`
- `c_customfunc`
- `c_debugprint`
- `c_saveload`

### Chapter-specific actor helpers

- `c_actormoveparty`
- `c_actormoveparty_single`
- `c_actortocaterpillar`
- `c_actortokris`
- `c_actortoobject`
- `c_tenna_preset`
- `c_tenna_sprite`

---

## Representative Commands And Their Arguments

## `c_walk(actor, direction, speed, time)`

Internally the `"walk"` opcode creates `obj_move_actor`:

```gml
actor_move.target = command_actor[i];
actor_move.direction_word = command_arg1[i];
actor_move.speed = command_arg2[i];
actor_move.time = command_arg3[i];
```

So the effective argument mapping is:

- actor -> `command_actor[i]`
- direction word -> `arg1`
- speed -> `arg2`
- duration/time -> `arg3`

In instant mode, the controller computes the destination directly with `lengthdir_x/y`.

## `c_walkdirect(actor, x, y, movemax_or_speed, waitflag)`

The `"walkdirect"` opcode instead creates `obj_move_to_point`:

```gml
actor_move.movex = command_arg1[i];
actor_move.movey = command_arg2[i];
...
if (command_arg3[i] >= 0)
    actor_move.movemax = command_arg3[i];
else
    __walktime = point_distance(...) / -command_arg3[i];
```

This means `arg3` is overloaded:

- non-negative -> direct move duration / max steps
- negative -> interpret absolute value as speed and derive travel time from distance

If `command_arg4[i] == 1`, the command also sets a timed wait based on the computed walk time.

## `c_walktoobject(actor, object, xoff, yoff, movemax, align_x, align_y)`

The `"walkto"` opcode first derives a target position from another object's coordinates, then rewrites itself into `"walkdirect"`. It can also compensate for sprite width/height offsets when `align_x` / `align_y` are enabled.

This is a great example of DELTARUNE using opcodes as a macro language rather than only as primitive actions.

## `c_msgset(index, text)`

Internally:

```gml
if (_c == "msgset")
{
    msgset(command_arg1[i], command_arg2[i]);
}
```

So the wrapper populates one `global.msg[]` slot, usually before a later `c_talk`.

## `c_msgnext(text)`

This appends or advances the next message buffer slot through `msgnext(command_arg1[i])`.

## `c_talk()`

The talk opcode creates the actual `obj_dialoguer`:

```gml
mydialoguer = instance_create(0, 0, obj_dialoguer);
if (msgside >= 0)
    mydialoguer.side = msgside;
if (stay)
    mydialoguer.stay = stay;
if (runcheck)
    mydialoguer.runcheck = runcheck;
if (preventcskip)
    mydialoguer.preventcskip = preventcskip;
mydialoguer.zurasu = zurasu;
```

So message setup and box spawning are separate queue operations.

## `c_msgside(...)`

The internal `"msgside"` opcode accepts symbolic arguments:

- `"any"` -> `msgside = -1`
- `"top"` -> `msgside = 0`
- `"bottom"` -> `msgside = 1`
- `"zurasuon"` -> `zurasu = 1`
- `"zurasuoff"` -> `zurasu = 0`

This command therefore controls both side and sliding-offset mode.

## `c_msgstay(value)`

Sets the controller-local `stay` flag, which the next `c_talk` copies into the dialoguer.

## `c_msgpreventcskip(value)`

Sets the controller-local `preventcskip` flag, again for the next spawned dialoguer.

## `c_fe(expression, face?)`

The `"fe"` opcode sets:

```gml
global.fe = command_arg1[i];
if (command_arg2[i] != -2)
    global.fc = command_arg2[i];
```

So it can change only expression, or expression plus face character.

## `c_msc(id)`

This command changes the current message-scene id and immediately runs:

```gml
global.msc = command_arg1[i];
scr_text(global.msc);
```

So cutscenes can switch into any `scr_text` scene block without calling `scr_writetext`.

## `c_var(...)`

The `"var"` opcode is one of the most powerful commands. It can:

- directly set an instance variable
- lerp an instance variable over time
- apply easing modes encoded in `command_arg6`

When `command_arg5 == 0`, it does a direct `variable_instance_set(...)`.
When non-zero, it calls `scr_lerpvar_instance(...)`.

The helper opcodes `"varadd"` and `"varto"` rewrite into `"var"` after computing the effective start/end values.

## `c_script_instance(...)`

The `"script"` opcode can:

- execute a script immediately on a target instance
- schedule repeated execution via `scr_script_repeat`
- cancel delayed scripts when `command_arg3 == -10`

This makes the cutscene layer a true general-purpose scene orchestrator, not only a movement/text tool.

## `c_mus(...)`

The `"mus"` / `"music"` opcode is actually a family of subcommands selected by `command_arg1[i]`, including:

- `"loop"`
- `"play"`
- `"stop"`
- `"free_all"`
- `"free"`
- `"pause"`
- `"resume"`
- `"init"`
- `"initplay"`
- `"initloop"`
- `"volume"`
- `"pitch"`
- `"pitchtime"`
- `"loopsfx"`
- `"loopsfxpitch"`
- `"loopsfxpitchtime"`
- `"loopsfxstop"`
- `"loopsfxvolume"`

So one wrapper family covers both background music and looped sound-effect control.

## `c_soundplay(sound, volume, pitch)`

The internal opcode:

```gml
var _snd = snd_play(command_arg1[i]);
if (command_arg2[i] != 0)
    snd_volume(_snd, command_arg2[i], 0);
if (command_arg2[i] != 0)
    snd_pitch(_snd, command_arg3[i]);
```

So the effective meaning is:

- `arg1` -> sound asset
- `arg2` -> optional volume override
- `arg3` -> optional pitch override

## `c_pan(x, y, time)` and `c_panspeed(dx, dy, time)`

- `"pan"` calls `scr_pan_lerp(...)`
- `"panspeed"` calls `scr_pan(...)`

In instant mode:

- `"pan"` teleports the camera directly to absolute coordinates
- `"panspeed"` offsets the camera by velocity-times-time

That difference is easy to miss unless the wiki spells it out.

---

## Dialogue-Related Command Semantics

Several cutscene commands are really state setters for the next dialogue action rather than dialogue actions by themselves:

- `c_msgside`
- `c_msgstay`
- `c_runcheck`
- `c_msgpreventcskip`
- `c_msgzurasu`
- `c_msgface`
- `c_fe`
- `c_speaker`

The actual box does not appear until `c_talk` runs. This two-stage design is one of the main reasons later cutscenes are composable.

---

## Movement-Related Command Semantics

Movement commands also have a staging pattern:

- some commands mutate actor defaults such as `auto_facing`, `auto_walk`, `auto_depth`
- some spawn mover helper objects such as `obj_move_actor` or `obj_move_to_point`
- some rewrite themselves from higher-level forms into lower-level forms before execution

This is why a scene script that looks simple can still produce very nuanced runtime behavior.

---

## Chapter Differences

## Chapter 2

- establishes the queue model
- smaller command vocabulary
- mostly timer/dialogue waits

## Chapter 3

- reuses the same framework for TV-show pacing and board-adjacent scenes
- more theatrical presentation wrappers

## Chapter 4

- broadest shipped version
- richer wait conditions
- more message-control helpers
- more custom-function hooks

---

## Modding Implications

- If a scene freezes, inspect `waiting`, `cs_wait_*`, `current_command`, and `maximum_command`.
- If a command targets the wrong actor, inspect `command_actor[i]` and `actor_selected_id`.
- If dialogue ordering breaks, the cause is often an unsatisfied wait on `mydialoguer` or `cs_wait_box`, not the text string itself.

---

## Relationship To Other Pages

- [Dialogue System](dialogue-system.md) explains how message commands feed the writer/dialoguer layer.
- [Overworld Movement](overworld.md) explains the room actors that cutscenes commonly drive.
- [Chapter Differences](chapter-differences.md) summarizes controller evolution by chapter.
