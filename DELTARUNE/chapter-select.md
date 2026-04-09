# CHAPTER_SELECT

`CHAPTER_SELECT` is the shipped launcher runtime for DELTARUNE. It is not a gameplay chapter and it does not share the numbered chapter gameplay stack.

Its role is to:

- initialize launcher-side config
- read save metadata
- decide which chapters are visible
- display chapter / slot UI
- launch the selected chapter payload with the correct runtime arguments

The extracted runtime is very small compared with the numbered chapters:

- 56 scripts
- 18 objects
- 3 rooms

---

## What It Does Not Contain

`CHAPTER_SELECT` does not include the core numbered-chapter systems:

- no `scr_gamestart`
- no `scr_load`
- no `scr_saveprocess`
- no `scr_spell`
- no `scr_damage`
- no battle controller stack
- no chapter overworld stack

So it should be documented as a launcher/runtime shell, not as a fifth chapter.

---

## Important Objects

| Object | Purpose |
|---|---|
| `obj_CHAPTER_SELECT` | main launcher state machine |
| `obj_screen_start` | start screen |
| `obj_screen_select` | chapter / slot selection shell |
| `obj_screen_select_list` | save list / chapter list drawing |
| `obj_screen_select_footer` | footer prompts and UI hints |
| `obj_screen_transition` | screen transition handling |
| `obj_screen_loading` | loading transition |
| `obj_init_pc` | PC startup, config, language, window setup |
| `obj_init_console` | console startup path |
| `obj_input` | frame-by-frame input polling |
| `obj_gamecontroller` | controller/input bootstrap |

---

## Important Scripts

The launcher script set is intentionally small. Core ones include:

- `scr_init`
- `scr_init_launch_parameters`
- `scr_chapter_save_file_exists`
- `scr_ini_chapter`
- `scr_os_checks`
- `scr_ossafe_init`

It also includes the same low-level input helpers used elsewhere:

- `button1_*`
- `button2_*`
- `button3_*`
- directional `*_h` / `*_p`

---

## Launcher Parameters

The launcher and numbered chapters communicate through launch arguments.

`scr_init_launch_parameters()` parses values such as:

- `launcher`
- `switch_<id>`
- `returning_<slot>`

These parameters are used by the chapter runtime to understand how it was entered.

This is the practical reason a numbered chapter payload does not behave the same way when launched cold versus being entered through the launcher flow.

---

## Windows Launch Model

On Windows, `obj_CHAPTER_SELECT` uses `game_change()` to switch into the selected chapter payload and passes chapter-specific launch arguments.

The runtime path pattern uses chapter-specific game payloads such as:

- `chapter1_windows`
- `chapter2_windows`
- `chapter3_windows`
- `chapter4_windows`

with `-game data.win ...` style arguments appended.

For modders, this is the runtime boundary between:

- launcher data / UI
- chapter gameplay code

---

## Save Visibility Logic

The launcher decides which chapters should appear based on save presence and completion state.

It does not blindly show everything from the start. Chapter visibility is tied to:

- current chapter save existence
- previous chapter completion
- current chapter completion

This behavior is part of the launcher runtime, not the numbered chapter runtimes.

---

## `dr.ini` Section Naming

`scr_ini_chapter()` is used for launcher metadata section naming.

Its behavior distinguishes:

- Chapter 1 metadata sections
- Chapter 2+ metadata sections

That is why `dr.ini` chapter metadata naming does not match the actual numbered chapter save filenames one-to-one.

The launcher-facing metadata scheme and the numbered chapter save-file scheme are related, but they are not identical systems.

---

## Secret Boss Metadata

The launcher maintains boss-related metadata in `dr.ini`, including migrated state for secret-boss progress.

One documented example is the `[URA]` section, which is populated through launcher-side conversion logic rather than through chapter-select gameplay code.

This is one of the clearest examples of `CHAPTER_SELECT` acting as a shared metadata coordinator instead of a gameplay runtime.

---

## Language Handling

`CHAPTER_SELECT` uses:

- `true_config.ini`
- OS locale checks
- direct `global.lang` comparisons

It does not use:

- chapter `lang_map`
- `stringsetloc`
- chapter JSON localization loading

So launcher text edits should be treated separately from chapter text edits.

---

## Window / Display Setup

`obj_init_pc` is responsible for launcher-side startup configuration on PC, including:

- reading `true_config.ini`
- language initialization
- fullscreen / window configuration
- integer-like window scaling decisions based on available display size

Each numbered chapter then performs its own startup logic again after the launcher hands over control.

---

## Why This Matters For Modders

If you are patching DELTARUNE through UndertaleModTool:

- patch `CHAPTER_SELECT` for launcher UI, chapter visibility, metadata presentation, and launch flow
- patch numbered chapters for battle, overworld, cutscenes, items, saves, and chapter-specific systems

Treating `CHAPTER_SELECT` as “just another chapter” will hide the real runtime split and cause documentation errors.
