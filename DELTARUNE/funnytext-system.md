# Funnytext System

`obj_funnytext` is an animated text-object family used for title cards, board labels, TV callouts, and other non-standard text reveals. It runs alongside `obj_writer` and is integrated through writer-owned object slots in Chapters 3 and 4.

The main roots are:

- `scripts/scr_funnytext_init/scr_funnytext_init.gml`
- `objects/obj_funnytext/Create_0.gml`
- `objects/obj_funnytext/Step_0.gml`
- `global.writerobj[]` and related writer-routing arrays

---

## Writer Registration

The core initializer is:

```gml
function scr_funnytext_init(arg0, arg1, arg2, arg3, arg4, arg5)
{
    global.writerobj[arg0] = obj_funnytext;
    global.writerobjx[arg0] = arg1;
    global.writerobjy[arg0] = arg2;
    global.writerimg[arg0] = arg3;
    global.writerobjsettinga[arg0] = arg4;
    global.writerobjsettingb[arg0] = arg5;
}
```

Funnytext is usually selected through the shared writer-routing system rather than hardcoded everywhere with direct instance creation.

---

## Default Runtime Slots

Chapter 3 and Chapter 4 `scr_gamestart` preinitialize several writer-object slots to funnytext-capable defaults:

```gml
global.writerimg[i] = spr_btact;
global.writerobj[i] = obj_funnytext;
global.writerobjsettinga[i] = 0;
global.writerobjsettingb[i] = 0;
global.writerobjx[i] = 0;
global.writerobjy[i] = 0;
```

These defaults make funnytext part of the standard writer-owned object insertion system.

---

## How To Configure Funnytext Before Inserting It In Text

The intended setup flow is:

1. choose a writer-object slot, usually `0..9`
2. configure that slot with `scr_funnytext_init(slot, x, y, sprite, settinga, settingb)`
3. later place `\O<slot>` inside the dialogue string

`obj_writer/Draw_0.gml` inserts those configured objects through the `\O` tag:

```gml
var writerobj = instance_create(wx + global.writerobjx[nextchar2var], wy + global.writerobjy[nextchar2var], global.writerobj[nextchar2var]);
writerobj.sprite_index = global.writerimg[nextchar2var];
writerobj.settinga = global.writerobjsettinga[nextchar2var];
writerobj.settingb = global.writerobjsettingb[nextchar2var];
object_made[nextchar2var] = 1;
```

The inline text tag does not decide funnytext behavior by itself. It only consumes the configuration already stored in the global writer-object tables.

The configured fields are:

- `global.writerobj[slot]`: object class to spawn, usually `obj_funnytext`
- `global.writerimg[slot]`: sprite assigned to the spawned object
- `global.writerobjx[slot]`: X offset relative to the current writer cursor
- `global.writerobjy[slot]`: Y offset relative to the current writer cursor
- `global.writerobjsettinga[slot]`: copied into the object's `settinga`
- `global.writerobjsettingb[slot]`: copied into the object's `settingb`

This is the funnytext insertion pipeline in Chapters 3 and 4.

---

## Relationship To Inline Writer Tags

The text runtime uses several related tag families:

- `\I?` draws an inline sprite from `global.writerimg[]`
- `\m?` draws a mini inline image / mini portrait using `global.writerimg[]`
- `\O?` spawns a configured writer-owned object, often `obj_funnytext`

`funnytext` is one member of the writer-side asset insertion system.

---

## Sound Map Initialization

Chapter 3 adds `scr_funnytext_init_sounds()` and helper lookups:

- `scr_funnytext_get_sound(arg0)`
- `scr_funnytext_new_sound(arg0, arg1)`

Representative sprite-to-sound mappings include:

- `spr_funnytext_fun_loop` -> `snd_crowd_cheer_single`
- `spr_funnytext_big` -> `snd_ftext_bounce`
- `spr_funnytext_physical_challenge` -> `snd_ftext_bounce`
- `spr_funnytext_board` -> `snd_ftext_woodblock`
- `spr_funnytext_bonus_round` -> `snd_ftext_prize`
- `spr_funnytext_hall_of_fame` -> `snd_ftext_prize`

---

## Object Initialization

Chapter 3 `obj_funnytext/Create_0.gml` initializes:

```gml
Settinga = 0;
settingb = 0;
typingstyle = 0;
typingspeed = 3;
typingnoise = 144;
charshake = 1;
init = 0;
chartimer = -1;
charmax = 1;
typingfinished = 0;
writerfinished = 0;
image_speed = 0;
idealxscale = 1;
idealyscale = 1;
con = 0;
loopsprite = sprite_index;
playsound = 0;
```

Chapter 4 is very similar, but changes `typingnoise` to `190`.

---

## First-Step Bootstrap

On first Step, the object:

- auto-selects a sound with `scr_funnytext_get_sound(sprite_index)` if needed
- copies `settinga` into the effective style behavior
- for `typingstyle == 0`, tries to find a loop sprite named `sprite_name + "_loop"`
- prepares scale/reveal timers for other styles

This delayed bootstrap means funnytext inherits its sprite and settings from the writer-routing arrays.

---

## Typing Styles

### Style 0

Animated intro sprite with optional loop-sprite follow-up.

### Style 1

Character reveal using:

- `chartimer`
- `typingspeed`
- `charmax`

### Style 2

Intro animation followed by a looping display state.

Funnytext is not one effect. It is a mini-framework for several stylized text behaviors.

---

## Relationship To `obj_writer`

The Step event watches writer lifecycle:

- if `obj_writer.halt` is reached, it marks `writerfinished = 1`
- if no `obj_writer` exists anymore, the funnytext object destroys itself

`obj_funnytext` still follows writer lifecycle and destroys itself when the owning writer is gone.

---

## Chapter Differences

## Chapter 3

- first major funnytext-heavy chapter
- large sprite/sound registry
- strong TV/game-show usage
- default `typingnoise = 144`

## Chapter 4

- keeps the same broad system
- retunes defaults such as `typingnoise = 190`

Funnytext is a Chapter 3/4 specialization. Chapter 1 does not use this insertion model.

---

## Modding Implications

- If funnytext appears but has no sound, check the sprite-to-sound mapping.
- If it vanishes too early, inspect the owning `obj_writer` lifecycle.
- If the wrong looping animation plays, inspect the `"_loop"` sprite naming expectation.

---

## Relationship To Other Pages

- [Dialogue System](dialogue-system.md) explains the writer pipeline.
- [Cutscene System](cutscene-system.md) explains the scenes that often trigger funnytext-backed text events.