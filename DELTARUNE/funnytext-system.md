# Funnytext System

`obj_funnytext` is a writer-owned animated sprite/text effect used for title
cards, labels, callouts, and other non-standard reveals. It becomes prominent in
Chapter 3 and remains present through Chapter 5.

## Registration and Insertion

`scr_funnytext_init(slot, x, y, sprite, setting_a, setting_b)` stores an object,
offsets, sprite, and two settings in the shared writer-object arrays:

```gml
scr_funnytext_init(0, 8, -12, spr_funnytext_dump_her, 0, 0);
global.msg[0] = "* Look! \\O0%%";
scr_writetext();
```

When `obj_writer` reaches the `\O` slot code, it creates the configured object
at the current cursor plus offsets, copies the sprite/settings, and records that
the slot was made. `\I` and `\m` use related writer image arrays for inline
images and mini-images but do not imply `obj_funnytext`.

## Runtime

The object starts with `typingstyle = 0`, `typingspeed = 3`, `charshake = 1`,
and a stopped sprite. Its first Step resolves an optional sound, interprets the
settings, and searches for a loop sprite derived from the assigned sprite name.

### 0

**Behavior:** Play an intro animation, then use an optional `_loop` sprite

### 1

**Behavior:** Reveal characters/frames through `chartimer` and `charmax`

### 2

**Behavior:** Play an intro and retain a looping display state

It observes the writer's halt/end lifecycle and destroys itself after the owning
writer disappears. A persistent effect therefore needs an explicit ownership
change rather than merely changing its depth.

## Sound Registry

`scr_funnytext_init_sounds()`, `scr_funnytext_new_sound()`, and
`scr_funnytext_get_sound()` form a sprite-name-to-sound registry. The registry
stores sprite names and resolves them through `scr_84_get_sprite()`, which keeps
locale/resource remapping in the lookup path.

The registry is payload-specific. Chapter 5's shipped initializer contains the
established mapping `spr_funnytext_dump_her` to `snd_ftext_bounce`; do not copy
the much larger Chapter 3 TV registry and assume every asset remains registered.

## Chapter Differences

### Chapters 1-2

**established behavior:** No standard writer-object funnytext workflow

### Chapter 3

**established behavior:** Large TV/game-show sprite and sound registry; default
noise 144

### Chapter 4

**established behavior:** Same architecture; default noise 190

### Chapter 5

**established behavior:** Same architecture; default noise 289 and a reduced
shipped registry

Those numbers are asset IDs in each payload, not portable sound constants.

## Modding Checks

- Configure a slot before the writer reaches its `\O` code.
- Use a slot not already consumed by the same writer.
- Add the sprite to the target payload and, if needed, its sound registry.
- Supply the expected `_loop` sprite for style 0.
- Preserve writer ownership or implement explicit cleanup.
- confirm localized strings retain the same writer-object control code.

See [Dialogue System](dialogue-system.md) and
[Cutscene System](cutscene-system.md).
