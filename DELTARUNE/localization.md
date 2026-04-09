# Localization System

DELTARUNE's shipped runtime supports English and Japanese, but it does not implement them the same way in every target.

This page documents the behavior visible in the extracted runtime data, not an editor-side source workflow.

---

## Supported Languages

`global.lang` uses:

| Value | Language |
|---|---|
| `"en"` | English |
| `"ja"` | Japanese |

---

## Runtime Split

| Target | Main localization style |
|---|---|
| Chapter 1 | direct string-map lookup |
| Chapter 2 | inline English fallback plus `stringsetloc()` |
| Chapter 3 | same as Chapter 2, with stronger missing-string diagnostics |
| Chapter 4 | same as Chapter 3 |
| Chapter Select | hardcoded launcher strings behind `global.lang` checks |

---

## Language Data Files

### Chapter 1

Ships:

- `datafiles/lang/lang_en.json`
- `datafiles/lang/lang_ja.json`

### Chapters 2, 3, and 4

Ship:

- `datafiles/lang/lang_ja.json`

The practical meaning is:

- English is largely embedded directly in code in later chapters
- Japanese is retrieved through the localization map

### Chapter Select

- no chapter-style `lang` JSON files
- no `stringsetloc()` runtime

---

## `scr_84_get_lang_string()`

### Chapter 1

The Chapter 1 form is minimal:

```gml
function scr_84_get_lang_string(arg0)
{
    return ds_map_find_value(global.lang_map, arg0);
}
```

Chapter 1 lacks the stronger missing-string diagnostics added in Chapter 3+.

### Chapters 2, 3, and 4

The later form:

- reads from `global.lang_map`
- returns `"--missing-string--"` if a key is absent
- tracks missing ids in `global.lang_missing_map` logic
- Chapters 3 and 4 also print a debug message with the missing id

So the old statement that all chapters behave identically here is incorrect.

---

## `stringsetloc(fallback, key)`

Present in Chapters 2, 3, and 4:

```gml
function stringsetloc(arg0, arg1)
{
    var str = arg0;
    if (!is_english())
    {
        str = scr_84_get_lang_string(arg1);
    }
    return stringset(str);
}
```

Behavior:

- English mode: use the inline fallback string from code
- Japanese mode: resolve the provided localization key from `global.lang_map`
- return the processed string through `stringset(...)`

This is the main Chapter 2+ localization pattern.

---

## What Actually Changed After Chapter 1

### Chapter 1

Typical code pattern:

```gml
global.charname[1] = scr_84_get_lang_string("...");
```

### Chapters 2, 3, and 4

Typical code pattern:

```gml
weaponnametemp = stringsetloc("Wood Blade", "scr_weaponinfo_...");
```

This is a real structural shift:

- Chapter 1 leans more directly on the loaded string database
- later chapters embed the English text directly in the script and only look up Japanese when needed

---

## Missing-String Diagnostics

### Chapter 2

If a key is missing:

- it is tracked
- `"--missing-string--"` is returned

### Chapters 3 and 4

If a key is missing:

- it is tracked
- `"--missing-string--"` is returned
- `show_debug_message(...)` logs the problem

This makes Chapter 3 and 4 safer for runtime localization debugging.

---

## Language Selection Priority

The launcher and chapters resolve language using the config and OS locale.

Common priority:

1. `true_config.ini`
2. OS locale
3. on Switch, `switch_language_get_desired_language()` where applicable

`CHAPTER_SELECT` clearly reads and writes:

- `[LANG] LANG`

inside `true_config.ini`.

---

## `CHAPTER_SELECT`

The launcher does not use the chapter string-map pipeline.

Important facts:

- no `stringsetloc`
- no `global.lang_map`
- no external chapter-style localization JSON dependency
- launcher strings are selected directly with `global.lang == "en"` checks

That makes `CHAPTER_SELECT` a separate localization model from the numbered chapters.

---

## Why This Matters For Modding

If you are editing numbered chapters in UndertaleModTool:

- Chapter 1 localization patches often involve string-map usage directly
- Chapters 2, 3, and 4 often require patching both the inline English fallback and the Japanese key usage model
- launcher text is patched separately in `CHAPTER_SELECT`

Do not assume one global text pipeline covers the whole shipped game.
