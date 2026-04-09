# Dialogue System

DELTARUNE uses one broad text runtime for overworld dialogue, battle text, cutscene speech, reaction popups, and many system messages. The two central objects are:

| Object | Role |
|---|---|
| `obj_writer` | low-level text renderer that reveals characters, processes control codes, and plays voice bleeps |
| `obj_dialoguer` | high-level dialogue-box controller that places the box, manages portrait placement, and owns the writer lifecycle |

The most important helper scripts are:

- `scripts/scr_writetext/scr_writetext.gml`
- `scripts/scr_text/scr_text.gml`
- `scripts/scr_texttype/scr_texttype.gml`
- `scripts/scr_textsetup/scr_textsetup.gml`
- `scripts/scr_textsound/scr_textsound.gml`
- Chapter 2+ message/cutscene wrappers such as `c_msgset`, `c_msgsetloc`, `c_msgnext`, `c_msgstay`

This page is written from the shipped runtime opened through UndertaleModTool.

For GameMaker alarms and scope rules, see:

- https://manual.gamemaker.io/monthly/en/The_Asset_Editors/Object_Properties/Object_Events.htm
- https://manual.gamemaker.io/lts/en/GameMaker_Language/GML_Overview/Language_Features/with.htm

---

## Core Split

## `obj_writer`

The writer is the actual typewriter. It reads `global.msg[msgno]`, parses formatting markers, reveals characters over time, and controls text sound playback.

## `obj_dialoguer`

The dialoguer is the box and scene wrapper. It decides:

- where the box appears
- whether it sits at the top or bottom of the view
- whether it stays on-screen across messages
- which face object belongs to the current line
- when a writer should be created or cleaned up

## `scr_text`

This large routing script fills `global.msg[]` for numbered scene ids and many fixed dialogue contexts.

## `scr_writetext`

This is the normal high-level entry point for spawning a dialogue scene.

---

## `scr_writetext(msc, msg, fc, typer)`

Chapter 4 still uses the same broad helper shape:

```gml
function scr_writetext(arg0, arg1, arg2, arg3)
{
    global.fc = 0;
    global.msc = arg0;
    if (arg1 != "x")
    {
        global.msg[0] = arg1;
    }
    if (arg2 != 0)
    {
        global.fc = arg2;
    }
    global.typer = 5;
    if (arg3 != 0)
    {
        global.typer = arg3;
    }
    instance_create(0, 0, obj_dialoguer);
}
```

Its arguments are:

| Argument | Meaning |
|---|---|
| `arg0` | message scene id assigned to `global.msc` |
| `arg1` | direct override for `global.msg[0]` when not equal to `"x"` |
| `arg2` | portrait index assigned to `global.fc` |
| `arg3` | writer style override assigned to `global.typer` |

This helper is important because it shows the standard DELTARUNE message bootstrap order:

1. choose portrait
2. choose scene id
3. optionally override the first message string directly
4. choose writer style
5. create `obj_dialoguer`

---

## `obj_writer` Create Event

The writer expects `global.msg[]` and `global.typer` to already be prepared. Chapter 4 Create code begins:

```gml
skipme = 0;
forcebutton1 = 0;
textsound = snd_text;
charline = 33;
originalcharline = charline;
hspace = 8;
vspace = 18;
rate = 1;
mycolor = c_white;
myfont = scr_84_get_font("main");
textalpha = 1;
textalphagain = 0;
fadeonend = 0;
shake = 0;
special = 0;
skippable = 1;
automash_timer = 0;
if (global.flag[6] == 1)
{
    skippable = 0;
}
```

and later continues with:

```gml
f = 1;
if (global.darkzone == 1)
{
    f = 2;
}
prevent_mash_buffer = 0;
formattext = true;
runcheck = false;
disablebutton1 = false;
scr_texttype();
autoaster = 1;
drawaster = 1;
pos = 2;
lineno = 0;
aster = 0;
halt = 0;
reachedend = 0;
xcolor = c_black;
wxskip = 0;
preventcskip = false;
msgno = 0;
```

and finally:

```gml
mystring = global.msg[0];
for (j = 0; j < 100; j += 1)
{
    nstring[j] = global.msg[j];
}
length = string_length(mystring);
alarm[0] = rate;
if (rate < 3)
{
    alarm[2] = 1;
}
else
{
    scr_textsound();
}
```

So the writer performs three jobs during Create:

1. initializes default rendering/timing state
2. applies a style profile through `scr_texttype()`
3. copies the current `global.msg[]` buffer into local arrays and starts the alarm-driven reveal loop

---

## Important `obj_writer` Variables

The variables below are the ones a modder usually needs to understand first.

| Variable | Meaning |
|---|---|
| `skipme` | suppresses the writer in some battle/cutscene flows |
| `forcebutton1` | later-chapter force-advance helper |
| `textsound` | sound asset played for eligible characters |
| `charline` | line-wrap width in characters |
| `originalcharline` | preserved copy of the original line width |
| `hspace` | horizontal spacing in pixels |
| `vspace` | vertical spacing between lines |
| `rate` | frames per character |
| `mycolor` | current text color |
| `myfont` | current font asset |
| `textalpha` | text opacity, important in Ch3+ fade effects |
| `textalphagain` | fade-in increment |
| `fadeonend` | whether the writer fades when finishing |
| `shake` | writer shake intensity |
| `special` | special render mode selector |
| `skippable` | whether fast-forward / skipping is allowed |
| `f` | dark-world multiplier flag, set to `2` when `global.darkzone == 1` |
| `prevent_mash_buffer` | anti-mash guard |
| `formattext` | enables formatting-code processing |
| `runcheck` | later-chapter flag used by skip/sound logic |
| `disablebutton1` | later-chapter hard disable for confirm/advance |
| `autoaster` | auto-show the star prompt at message end |
| `drawaster` | whether the prompt is drawn at all |
| `pos` | current character position in `mystring` |
| `lineno` | current line index |
| `aster` | whether the star prompt is active |
| `halt` | whether the writer is paused waiting for input |
| `reachedend` | whether the current message finished |
| `wxskip` | skip-ahead counter / accelerated reveal helper |
| `preventcskip` | Chapter 4 cutscene-aware skip suppression |
| `msgno` | current `global.msg[]` slot being rendered |
| `reachedend_sound` | sound id used when a message reaches end |
| `writingx`, `writingy` | draw origin |
| `smallface` | current small portrait object id placeholder |
| `faced`, `facedever` | face-display tracking |
| `miniface_current_pos`, `miniface_pos`, `miniface_drawn` | mini-face timing state |
| `hangonpos` | Chapter 4 position-hold flag for stricter pacing |

---

## Alarm Flow

The writer remains alarm-driven in later chapters:

```gml
alarm[0] = rate;
if (rate < 3)
{
    alarm[2] = 1;
}
else
{
    scr_textsound();
}
```

Meaning:

- `alarm[0]` is the main character tick
- `alarm[2]` is used to delay the first text sound when the rate is fast
- when the rate is slower, the code plays the first voice sound immediately from Create instead of waiting

This small branch is easy to miss, but it affects how different typer styles feel.

---

## `obj_writer` Alarm 0: Advance Logic

Chapter 4 `Alarm_0.gml` is where the writer actually advances through the string:

```gml
if (pos < (length + 2))
{
    if (rate > 2)
        alarm[1] = 1;
    else if (first_alarm == 1 && pos >= 2 && sound_timer <= 0)
        playsound = 1;
}
...
getchar = string_char_at(mystring, pos);
nextchar = string_char_at(mystring, pos + 1);
```

Important behaviors inside this event:

- the first character is handled specially through `first_alarm`
- `&` and newline advance position without drawing a printable glyph
- `` ` `` escapes the next character so it is treated literally
- `^1` through `^9` add different amounts of extra wait time to `alarm[0]`
- `/` pauses the writer and can become a stronger stop when followed by `%`
- `\` introduces a two-character inline command sequence
- when `reachedend_sound_play` is enabled, the normal per-character sound can be suppressed once the writer hits end state

The `^` timing ladder in Chapter 4 is explicit:

- `^1` adds 5 frames
- `^2` adds 10 frames
- `^3` adds 15 frames
- `^4` adds 20 frames
- `^5` adds 30 frames
- `^6` adds 40 frames
- `^7` adds 60 frames
- `^8` adds 90 frames
- `^9` adds 150 frames

So `^` is not only a generic “pause here” marker. It is a tiny embedded timing language.

---

## Draw Event Parsing Model

`obj_writer/Draw_0.gml` is not only a renderer. It is also a major parser for inline control sequences. The Draw event:

1. reads current input state (`button1`, `button2`, debug automash)
2. applies skip/force flags
3. formats the message if needed
4. iterates from `n = 1` to `pos`
5. interprets control codes while advancing `wx` and `wy`
6. draws visible characters, portraits, button icons, and special inserts

This is one of the most important architectural facts in the whole text system: DELTARUNE splits parsing work across Create, Alarm, Draw, and helper scripts rather than keeping all text interpretation in one function.

---

## Text Format Codes

Your baseline list is correct and belongs in the system page because these markers are part of DELTARUNE's own dialogue language, not just generic text.

The most important control symbols are:

| Code | Effect |
|---|---|
| `#` | line break inside the same message |
| `&` | pause / wait point |
| `^` | silent pause marker |
| `!` | suppress text sound for that character |
| `%%` | end current message and advance to the next `global.msg[]` entry |
| `%1` to `%4` | character-name substitution using `global.charname[1..4]` |
| `*` | star-prompt related marker |

These markers are one of the reasons DELTARUNE text is more than a raw string-print routine. Message strings contain embedded behavior.

---

## Backslash Tag Language

The most important later-chapter writer tags are the backslash commands parsed in `Draw_0.gml`. They are three-character inline commands of the form `\XY`, where `X` is the command family and `Y` is the argument byte.

### `\E?` — face expression

The code:

```gml
if (nextchar == "E")
{
    __nextface = ord(nextchar2);
    ...
    global.fe = ...
}
```

changes `global.fe`, the current portrait expression. It supports:

- digits `0..9`
- uppercase letters `A..Z`
- lowercase letters `a..z`

so expression ids are not limited to single decimal digits.

### `\F?` — face character

The `\F` command remaps `global.fc`, the active portrait character. Chapter 4 explicitly recognizes codes such as:

- `\F0` -> no portrait
- `\FS`
- `\FR`
- `\FN`
- `\FT`
- `\FL`
- `\Fs`
- `\FA`
- `\Fa`
- `\FB`
- `\Fb`
- `\Fr`
- `\Fu`
- `\FU`
- `\FK`
- `\FQ`
- `\FC`
- `\Fy`
- `\Fi`

The code then immediately adjusts writer layout when the dialoguer is active:

```gml
if (global.fc == 0)
{
    charline = originalcharline;
    wx = x;
}
else
{
    charline = 26;
    wx = x + (58 * f);
}
```

So portrait tags do not only change the face sprite. They also reflow the text box.

### `\f?` — small-face spawn

When `nextchar == "f"` and no face has yet been inserted, the writer reads a numeric family id and spawns or reuses `obj_smallface` using the preloaded `global.sm*` arrays:

- `global.smxx[]`
- `global.smyy[]`
- `global.smspeed[]`
- `global.smdir[]`
- `global.smtype[]`
- `global.smsprite[]`
- `global.smimagespeed[]`
- `global.smimage[]`
- `global.smalarm[]`
- `global.smstring[]`
- `global.smcolor[]`

This is a huge detail for modders because it shows that inline mini-portraits are driven by a preconfigured face-template table, not only by one-off room code.

### `\*?` — button icon embed

The writer calls:

```gml
var _sprite = scr_getbuttonsprite(nextchar2, true);
draw_sprite_ext(_sprite, 0, wx + x_offset, wy + 2 + y_offset, 2, 2, 0, c_white, 1);
```

So inline controller prompts are real writer tags, not separate HUD widgets.

### `\T?` — change typer mid-line

This is one of the most powerful inline commands. It changes `global.typer` and immediately calls `scr_texttype()`.

Representative Chapter 4 branches include:

- `\T0` -> default narrator / dark-world default
- `\T1` -> typer `2`
- `\TA` -> typer `18`
- `\Ta` -> typer `20`
- `\TN` -> Noelle family, with Chapter/Dark/Battle-aware escalation to `12`, `56`, or `59`
- `\Tn` -> typer `23`
- `\TB` -> Berdly family, with escalation to `13`, `57`, or `77`
- `\TS` -> Susie family, with escalation to `10`, `30`, or `47`
- `\TR` -> Ralsei family, with battle-specific `45`
- `\TL` -> Lancer family, with battle-specific `46`
- `\TX` -> silent typer `40`
- `\Tr` -> rude voice `55`
- `\TT` -> Toriel `7`
- `\TJ` -> Joker `35`
- `\TK` -> King family, with special Chapter 1 branch and battle-specific `48`
- `\Tq` -> Queen alt `62`
- `\TQ` -> Queen `58`
- `\Ts` -> Sans `14`
- `\TU` -> Undyne `17`
- `\Tp` -> Spamton alt `67`
- `\TC` -> car voice `87`
- `\Tk` -> jack high `82`
- `\Tj` -> jack low `83`
- `\Tg` -> Gerson `85`
- `\Tv` -> TV voice `84`

This means a single text box can swap voice, font, spacing, and special rendering multiple times inside one message.

### `\s0` / `\s1` — skippable toggle

The writer directly toggles:

- `\s0` -> `skippable = 0`
- `\s1` -> `skippable = 1`

So skippability can change mid-line.

### `\c?` — color change

Chapter 4 recognizes color tags such as:

- `\cR` -> red
- `\cB` -> blue
- `\cY` -> yellow
- `\cG` -> lime/green
- `\cW` -> white
- `\cX` -> black
- `\cP` -> purple
- `\cM` -> maroon
- `\cO` -> orange

These set `xcolor` and `colorchange = 1`, which the draw logic then uses for subsequent glyph rendering.

This is one of the most important missing pieces in most fan documentation: DELTARUNE text strings are not just line-break strings with portraits. They are inline scripting containers.

---

## Other Inline Writer Tags

Chapter 4 `obj_writer/Draw_0.gml` also implements several other tag families that are easy to miss.

### `\C?` — choice box spawn

The uppercase `\C` tag spawns choicer UI and then halts the writer with `halt = 5`.

Supported values include:

- `\C1` -> `obj_choicer_old`
- `\C2`, `\C3`, `\C4` -> `obj_choicer_neo` with `choicetotal = real(nextchar2) - 1`

So the text string itself can request a choice box.

### `\M?` — set `global.flag[20]`

The `\M` tag writes a digit directly into `global.flag[20]`:

- `\M0` through `\M9`

This is a rare example of a text string directly mutating global story/menu state.

### `\S?` — play writer-side sound slot

`Draw_0.gml` checks:

```gml
snd_play(global.writersnd[i]);
```

when `nextchar == "S"`. So `\S0` through `\S9` can trigger one of the preloaded writer sound slots. The code only allows it once per relevant window because of `sound_played`.

### `\I?` — draw inline sprite

The `\I` tag draws a sprite from `global.writerimg[i]` at the current writer position:

```gml
draw_sprite(global.writerimg[i], 0, wx, wy + 4);
```

This is different from funnytext. It is a static inline image insert.

### `\m?` — draw mini inline image face

The lowercase `\m` tag:

- disables the normal asterisk prompt with `drawaster = 0`
- uses `global.writerimg[i]`
- draws the image near the writing origin rather than at the current glyph position
- animates the frame through `miniface_pos`

So this is the mini-portrait / mini-image layer used inside the text box itself.

### `\O?` — spawn writer-owned object

This is the funnytext-related hook you specifically asked to include. The `\O` tag creates an instance from the writer object tables:

```gml
var writerobj = instance_create(wx + global.writerobjx[nextchar2var], wy + global.writerobjy[nextchar2var], global.writerobj[nextchar2var]);
writerobj.sprite_index = global.writerimg[nextchar2var];
writerobj.settinga = global.writerobjsettinga[nextchar2var];
writerobj.settingb = global.writerobjsettingb[nextchar2var];
object_made[nextchar2var] = 1;
```

This means the text system can spawn arbitrary writer-attached helper objects directly from a text string, and in Chapter 3/4 those helper objects are very often `obj_funnytext`.

That is the key bridge between:

- normal dialogue text
- writer-side configuration arrays
- funnytext presentation objects

---

## How Funnytext Is Inserted From Text

The complete Chapter 3/4 model is:

1. `scr_gamestart` preinitializes writer object tables for several slots.
2. Those slots default to:

```gml
global.writerimg[i] = spr_btact;
global.writerobj[i] = obj_funnytext;
global.writerobjsettinga[i] = 0;
global.writerobjsettingb[i] = 0;
global.writerobjx[i] = 0;
global.writerobjy[i] = 0;
```

3. Scripts such as `scr_funnytext_init(slot, x, y, sprite, settinga, settingb)` rewrite one slot's configuration.
4. A dialogue string later uses `\O<digit>` to spawn the configured object for that slot.

So if a modder wants funnytext inside dialogue, the runtime pattern is not “hardcode funnytext into the writer.” The pattern is:

- configure a writer-object slot first
- then reference that slot from the string with `\O0`..`\O9`

In practical terms:

- `global.writerobj[slot]` chooses what class to spawn, usually `obj_funnytext`
- `global.writerimg[slot]` chooses the sprite for that spawned object
- `global.writerobjx[slot]` / `global.writerobjy[slot]` offset the spawn point relative to the current text cursor
- `global.writerobjsettinga[slot]` / `global.writerobjsettingb[slot]` are copied into the new object's `settinga` / `settingb`

This is one of the most important Chapter 3/4 dialogue details and absolutely belongs in the wiki.

---

## Escape and Pause Tags

Some of the most easily overlooked tags are:

- `` ` ``: escape the next character so it is printed literally
- `|`: horizontal spacer that advances `wx` without printing a glyph
- `/`: stop point that sets `halt = 1`
- `/%`: stronger stop state that becomes `halt = 2`

These are not decorative. They change the writer state machine.

---

## `scr_textsound()`

This script is the per-character sound layer. Chapter 4 begins:

```gml
playtextsound = 1;
if (button2_h() == 1)
{
    var dontplaysound = true;
    if (variable_instance_exists(id, "runcheck"))
    {
        if (runcheck)
        {
            dontplaysound = false;
        }
    }
    if (dontplaysound)
    {
        playtextsound = 0;
    }
}
if (skippable == 0)
{
    playtextsound = 1;
}
```

So fast-forward usually suppresses voice bleeps, but:

- if `runcheck` says the line should still behave as paced text, sound may continue
- if `skippable == 0`, sound is forced on even while the player is trying to advance quickly

Then it filters which characters may make noise. Sound is suppressed for:

- spaces
- `^`
- `!`
- punctuation such as `.`, `?`, `,`, `:`
- `/`, `\`, `|`
- `*`
- `&` in most slower-rate conditions

That is why DELTARUNE voices feel speech-like instead of chirping on every glyph.

---

## Textsound Special Cases

Later chapters add several speaker-specific sound branches in `scr_textsound()` instead of only calling `snd_play(textsound)`.

Examples from Chapter 4:

- `snd_txtq` uses `snd_txtq_2` with pitch randomization
- `snd_txtspam` plays `snd_txtspam2`
- `snd_txtjack_high_cute` and `snd_txtjack_low2` randomize pitch
- `snd_tv_voice_short` chooses among `snd_tv_voice_short`, `_2`, `_3`, ... `_9`
- `snd_txtral` can pitch-shift during a specific Chapter 4 church scene depending on `obj_ch4_DCB02.voice_pitch`

This is very important for accurate recreation. `textsound` is not always a single static bleep id. Sometimes it is a key into a mini dispatcher with chapter- and room-specific logic.

At the end of the routine, Chapter 4 still drives portrait animation directly:

```gml
with (obj_face_parent)
{
    mouthmove = 1;
}
miniface_pos++;
```

So writer sound and face animation remain tightly coupled.

---

## `scr_textsetup(font, color, x, y, charline, shake, rate, sound, hspace, vspace, special)`

This helper is the low-level style applier used by `scr_texttype()`. Its classic role is still the same in later chapters:

```gml
myfont = arg0;
mycolor = arg1;
writingx = arg2;
writingy = arg3;
charline = arg4;
shake = arg5;
rate = arg6;
textsound = arg7;
hspace = arg8;
vspace = arg9;
special = arg10;
colorchange = 1;
xcolor = mycolor;
```

The big design point here is that text style changes are centralized. DELTARUNE usually does not mutate writer fields one by one in every dialogue call. It assigns a typer id, and the typer id routes into this helper.

---

## `global.typer` and `scr_texttype()`

`global.typer` is the main style code. `scr_texttype()` turns that id into:

- font
- color
- rate
- sound
- spacing
- special rendering mode

Your older typer table is still a very useful baseline, but later chapters expand it substantially. Chapter 4 contains not only the classic ids `1..55`, `60`, `666`, `667`, `999`, but also many extra speaker/presentation ids:

- `56` big Noelle voice
- `57` big Berdly voice
- `58` big Queen voice
- `59` medium big-font Noelle
- `61` medium-width Susie variant
- `62` big Queen variant using `snd_txtq_2`
- `63` faster Noelle variant
- `64` Noelle variant with shake
- `65` big-font `snd_txtrx1`
- `66` big Spamton voice
- `67` alternate big Spamton voice
- `68` black-text Spamton voice
- `69` black-text Berdly voice
- `70` and `71` black-text Queen variants
- `72` black-text Spamton alternate
- `74`, `75`, `76` black-text Ralsei/Susie/Noelle variants
- `77` medium big-font Berdly
- `78` big-font generic with `charline = 36`
- `79` slower big Susie variant
- `80` silent main-font text
- `81` silent black-text font
- `82`, `83` jack-specific big-font voices
- `84` TV voice
- `85`, `86` Gerson-specific voice styles
- `87` car voice
- `88` black-text jack low voice
- `100` 8-bit font style

So by Chapter 4, `global.typer` is not just a small speaker table. It is a large style-routing language for many UI and story contexts.

---

## Representative `scr_texttype()` Cases

The standard narrator profile is still:

```gml
case 1:
    scr_textsetup(scr_84_get_font("main"), c_white, x, y, 33, 0, 1, snd_text, 8, 18, 0);
    break;
```

Battle text remains a bigger-font style:

```gml
case 4:
    scr_textsetup(scr_84_get_font("mainbig"), c_white, x, y, 33, 0, 1, snd_text, 16, 28, 1);
    extra_ja_vspace = 2;
    break;
```

Black-text UI-like dialogue uses `dotumche`:

```gml
case 50:
    scr_textsetup(scr_84_get_font("dotumche"), c_black, x, y, 33, 0, 1, snd_text, 9, 20, 0);
    break;
```

Special slow/echo modes still exist:

```gml
case 666:
    scr_textsetup(scr_84_get_font("main"), c_white, x, y, 33, 0, 4, snd_nosound, 12, 20, 2);
    break;
case 999:
    scr_textsetup(scr_84_get_font("main"), c_white, x, y, 33, 0, 4, snd_txtecho, 8, 18, 3);
    break;
```

These are great examples of why the typer table deserves explicit documentation in the wiki instead of a hand-wave summary.

---

## Japanese Layout Adjustments

`scr_texttype()` also adjusts geometry when `global.lang == "ja"`. Chapter 4 checks the actual selected font id and then scales width/spacing differently.

Representative logic:

```gml
if (myfont == 16)
{
    hspace = ((hspace * 26) / 16) + 1;
}
else if (myfont == 11)
{
    textscale = 0.5;
    hspace = ((hspace * 13) / 8) + 3;
}
```

and at the end:

```gml
vspace += extra_ja_vspace;
```

So Japanese handling is not a generic “different strings only” layer. It directly changes writer geometry and sometimes `textscale`.

---

## `obj_dialoguer`

Chapter 4 `obj_dialoguer/Create_0.gml` shows the high-level controller state:

```gml
cur_jewel = 0;
active = 0;
alarm[0] = 1;
skippable = 1;
free = 0;
zurasu = 1;
zurasucon = 0;
stay = 0;
xxx = camerax();
yyy = cameray();
writer = 432432;
side = 1;
runcheck = 0;
preventcskip = false;
myface = -4;
drawbox = true;
boxheight = 3;
boxwidth = -1;
xoff = 0;
yoff = 0;
```

Then it decides whether the box should appear on the top or bottom of the screen by comparing `obj_mainchara.y` to the camera position:

```gml
if (instance_exists(obj_mainchara))
{
    if (global.darkzone == 0)
    {
        if (obj_mainchara.y > (yyy + 130))
            side = 0;
    }
    if (global.darkzone == 1)
    {
        if (obj_mainchara.y > (yyy + 250))
            side = 0;
    }
}
```

This means the dialog box is not always fixed. It tries to avoid covering the speaking area of the room.

Important dialoguer fields:

- `free`: freer placement mode
- `zurasu`: offset/slide behavior used heavily in later chapters
- `stay`: keep the box alive between operations
- `runcheck`: dialogue pacing guard shared with writer logic
- `preventcskip`: cutscene-side suppression of player skip
- `drawbox`: whether to render the normal frame at all
- `boxheight`, `boxwidth`, `xoff`, `yoff`: box-shape overrides

By Chapter 4 this object is far more configurable than a simple “spawn box and text” wrapper.

---

## Input, Fast-Forward, and Automash

The writer Draw event also implements input orchestration directly.

Representative logic:

```gml
if (button1_p() == 1 && prevent_mash_buffer <= 0)
    button1 = 1;
if (button2_h() == 1 && prevent_mash_buffer <= 0)
    button2 = 1;
...
if (global.flag[10] == 1 || scr_debug())
{
    ...
    if (button3_h() == 1)
    {
        prevent_mash_buffer = 3;
        if (automash_timer == 0) automash_timer = 1; else automash_timer = 0;
        if (automash_timer == 0) button1 = 1;
        if (automash_timer == 1) button2 = 1;
    }
}
```

Important consequences:

- `button1` is the confirm/advance action
- `button2` is the hold-to-run / fast-forward action
- debug or flag-enabled automash can alternate between them
- `prevent_mash_buffer` is the main anti-spam guard
- `disablebutton1`, `forcebutton1`, `preventcskip`, and `runcheck` can override the normal input path

This is another example of Chapter 4 making the writer a stricter cutscene-aware controller than in earlier chapters.

---

## `global.msg[]`

`global.msg[0..99]` is the main message buffer. A scene typically fills several slots at once:

```gml
global.msg[0] = "Hello!#How are you?";
global.msg[1] = "I am fine.%%";
```

The writer copies these into `nstring[]`, starts from `msgno = 0`, and advances across messages when it reaches `%%`.

This buffer model is essential for modders:

- `obj_writer` usually does not know how to compose the scene
- `scr_text`, cutscene helpers, battle helpers, or direct scripts prepare `global.msg[]`
- the writer only renders that prepared buffer

---

## `scr_text(msc)`

`scr_text` is the giant message-routing script. It maps `global.msc` or direct scene ids to concrete `global.msg[]` contents.

The reason the wiki needs to mention this explicitly is that DELTARUNE separates:

- scene selection logic
- string lookup/localization
- actual timed rendering

So when a line is wrong, the bug may be in `scr_text` or in a cutscene helper, not in the writer.

---

## Battle Text

Battle text is a configured use of the same writer stack, not a separate text engine. The usual pattern is:

```gml
global.msg[0] = global.battlemsg[0];
global.typer = global.battletyper;
battlewriter = scr_battletext();
```

The common default is:

- `global.battletyper = 4`

which routes into the large-font battle-style profile in `scr_texttype()`.

This is why battle dialogue, warning text, ACT results, and many enemy reactions still feel like part of one coherent text runtime.

---

## Face / Portrait System

Dialogue is tightly coupled to portrait state through:

- `global.fc`
- `global.fe`

and through objects such as:

- `obj_face_parent`
- `obj_face`
- `obj_smallface`

`scr_textsound()` still toggles:

```gml
with (obj_face_parent)
{
    mouthmove = 1;
}
```

So mouth animation is driven by character-reveal timing, not by a separate lip-sync system.

The writer also tracks face-related local fields such as:

- `smallface`
- `faced`
- `facedever`
- `miniface_current_pos`
- `miniface_pos`
- `miniface_drawn`

This becomes more important in later chapters where battle dialogue, small inline faces, and stylized dialogue variants are more common.

---

## Specialized Writer Variants

The core logic is still centered on `obj_writer`, but later chapters also use related variants or integrations such as:

- `obj_writer_stay`
- `obj_menuwriter`
- `obj_board_writer`
- `obj_funnytext`

These are not replacements for the main dialogue system. They are specialized surfaces built on top of the same overall writer/dialoguer/message-buffer architecture.

For the animated text-object side, see [Funnytext System](funnytext-system.md).

---

## Cutscene Message Layer

Beginning in Chapter 2, a large part of dialogue is no longer started only by `scr_writetext()`. It can also be staged through the cutscene command language.

Important wrappers include:

- `c_msgset`
- `c_msgsetloc`
- `c_msgnext`
- `c_msgnextloc`
- `c_msgstay`
- `c_msgpreventcskip`

These commands bridge:

- cutscene queue state
- localized string resolution
- normal `obj_dialoguer` / `obj_writer` behavior

So later DELTARUNE chapters effectively layer a small scene language on top of the base text engine instead of replacing it.

For the queue/controller side, see [Cutscene System](cutscene-system.md).

---

## Chapter Differences

## Chapter 1

- simplest writer runtime
- no late cutscene command language
- fewer control flags on writer and dialoguer
- much smaller typer surface

## Chapter 2

- major expansion of writer state
- adds stronger anti-mash, mini-face, and formatting helpers
- introduces the large `c_*` cutscene layer

## Chapter 3

- adds `textalpha`, `textalphagain`, `fadeonend`, `shadcolor`
- adds `reachedend_sound`, `reachedend_sound_played`, `reachedend_sound_play`
- adds `object_made[0..8]`
- leans much harder into presentation-heavy text scenes

## Chapter 4

- keeps the Chapter 3 writer and adds `runcheck`, `disablebutton1`, `preventcskip`, `hangonpos`
- greatly expands `global.typer`
- adds more room-/speaker-specific sound routing inside `scr_textsound()`
- gives `obj_dialoguer` more box, stay, and skip-control fields

Chapter 4 is therefore not just “the same writer with more text.” It is the most constrained and controllable shipped version of the runtime.

---

## Recreating DELTARUNE Dialogue Faithfully

To reproduce the real runtime behavior, you need all of these layers together:

1. message preparation through `global.msg[]`
2. optional `scr_text(msc)` scene routing
3. style selection through `global.typer` and `scr_texttype()`
4. `obj_dialoguer` placement and box control
5. `obj_writer` timed reveal and control-code parsing
6. `scr_textsound()` voice/pitch logic
7. face / mini-face objects
8. Chapter 2+ cutscene message wrappers

If you only rebuild a typewriter and a text box, you miss a large part of how real DELTARUNE scenes are staged.

---

## Relationship To Other Pages

- [Cutscene System](cutscene-system.md) explains the queue language that frequently drives later dialogue.
- [Funnytext System](funnytext-system.md) explains the animated text-object layer used in showier scenes.
- [Battle System](battle-system.md) explains how battle text feeds into the same writer stack.
