# Rendering, Animation, and Audio

Presentation is distributed across object events and helper scripts rather than
one renderer. Every numbered payload uses sprites, room layers, draw events,
surfaces, transitions, sound resources and two audio groups. Chapter 5 ships
8,522 sprites, 764 sounds, 66 shaders, 75 embedded textures and 37 texture
groups; it has no timeline resources, so animation timing is code- and
sprite-driven.

## Animation state and draw order

Objects select `sprite_index` and control `image_index`, `image_speed`, loop,
alpha, blend, angle and scale. State machines switch these values in Create,
Step, Alarm and animation-end events. Room layers and instance depth establish
world, actor, foreground, UI and transition order. Specialized renderers, such
as the Chapter 5 platform actor renderer, may draw an actor to a surface before
compositing it into the room.

Practical example: for a new platform dash animation, keep locomotion state on
the player, change sprite and image speed when dash begins, emit dash-line VFX
on the effects layer, then restore the idle/run sprite at the existing end or
cancel branch. Test left/right scale, slope contact, pause and room swap.

## Surfaces, particles and lighting

Surfaces support centered, pivoted and position-fixed drawing, battle boxes,
platform actors, floor textures, reflections, shadows and full-screen effects.
Always check `surface_exists` or the shipped surface helper and recreate targets
after device loss. Do not persist a surface ID in save data.

Particles range from GameMaker particle systems to object pools and custom draw
objects: wind, petals, snowflakes, sparks, smoke, dash trails and battle
markers. Lighting combines light-source objects, garden lights,
self-shadow/sun-shadow registries, shadow-cast drawing and shader compositing.
These are distinct pipelines; a sprite named “particle” or “light” does not
prove use of a native particle or lighting API.

## Shaders and transitions

Chapter 5's shipped shaders cover alpha thresholds, blur, masks, palette and
tone changes, CRT/video, depth and fake depth, reflection, ripple/water,
platform dash, petals, wind, shadow blending, outlines and fades. A typical
effect sets the shader, supplies uniforms, draws the sprite or surface, then
resets shader state. Failure to reset leaks the effect into later draw calls.

Practical example: a garden wind layer can render its source to a surface, set
`shd_windwave`, update time/direction uniforms, draw the surface on the intended
layer, reset the shader, then draw UI outside the effect.

The shipped shader resources include GLSL ES, desktop GLSL, HLSL 9 text and HLSL
11 binary variants where available. Their presence does not mean that the
Windows build executes every variant. Chapter 5 also ships
`shader_replace_simple_x64.dll`; GML calls replace, synchronize and select
shader hooks. The runtime basis supports dynamic Windows shader replacement, but
not an undocumented implementation or console behavior.
`execute_program_pipe_x64.dll` is also shipped; its internal behavior is not
inferred here.

Transitions include fade objects and shaders, square/star/board wipes, battle
transitions, platform swaps and room-specific cutscene staging. Preserve their
flag/plot writes and input locks when replacing only the visual portion.

## Sound, music and routing

All five numbered payloads inventory `audiogroup_default` and `audio_sfx`. Sound
metadata records the assigned resource/group; code provides play, loop, stop,
pause, resume, pitch, volume, delayed and positional helpers. Music uses the
default group and persistent music instances/controllers; effects use the SFX
route where assigned. A resource name is not a stable cross-payload numeric ID.

Chapter 5 adds music-event managers and beat/user-event callbacks, cutscene
music save/load, mute helpers, Flowery voice routing and rhythm song/event
loading. Practical music extension: select a named sound resource, create it
through the target room's existing music controller, register beat events only
after the instance exists, preserve its position across a cutscene if required,
and clear callbacks before room exit. Practical SFX extension: use the existing
wrapper, retain the SFX group, store the returned instance only when later
pitch/volume/stop control is needed, and free or stop it on teardown.

## Video playback

The installed Windows build ships four localized movie files: Chapter 3's
English/Japanese Tenna pair and Chapter 5's `ch5_intro_en.mp4` and
`ch5_intro_jp.mp4`. `obj_ch3_couch_video` owns playback in the production
`room_dw_couch_video`; `obj_room_garden_video` owns playback in the production
`room_dw_garden_video`. The Chapter 5 controller selects the English or Japanese
filename from `global.lang`, calls `video_open`, draws frames, handles close and
cleanup, and records watched state in the `video_ch5` INI section.
`shd_video_yuv` provides video color conversion. This defines the shipped
Windows playback path, not codecs for unshipped platforms.

Practical video extension: add the localized files beside the existing Chapter 5
videos, branch filename selection through the same locale path, preserve skip
and watched-state behavior, and test missing-file, focus loss, audio restoration
and transition cleanup.

## Related pages

- [Chapter 5 Systems](chapter-5-systems.md)
- [Cutscene System](cutscene-system.md)
- [Localization](localization.md)
