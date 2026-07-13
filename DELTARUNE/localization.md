# Localization System

The shipped runtimes support English (`en`) and Japanese (`ja`), with three
separate concerns: language selection, string lookup, and localized assets.

## Language Selection

On PC, the launcher and numbered chapters derive a default from
`os_get_language()` and then read `[LANG] LANG` from `true_config.ini`. Changing
language writes the same key and reinitializes localization. established Switch
branches use `switch_language_get_desired_language()`. PS4 and PS5 are
classified as console by the launcher, but the shipped code does not justify
claiming that they use the Switch locale API.

## String Lookup by Target

| Target          | English        | Japanese       | Missing-key behavior  |
| --------------- | -------------- | -------------- | --------------------- |
| Chapter 1       | `lang_en.json` | `lang_ja.json` | Direct map lookup     |
| Chapters 2 to 5 | Inline text    | `lang_ja.json` | Marker and tracking   |
| Launcher        | Inline branch  | Inline branch  | No chapter string map |

Chapter 1's `scr_84_get_lang_string()` reads `global.lang_map` directly.
Chapters 2 through 5 normally call `stringsetloc(english, key)`: English keeps
the inline text, while Japanese resolves the key. Later runtimes return
`--missing-string--` and track missing identifiers; Chapters 3 through 5 also
emit stronger diagnostics.

There is no documented cascade from a missing Japanese key to the inline English
argument: once the non-English path is chosen, the lookup result is used. Mods
should therefore keep the Japanese map synchronized.

## Fonts, Sprites, and Sounds

`scr_84_init_localization()` builds more than a text map. It selects localized
font resources and fills maps for language-dependent sprites and sounds. Chapter
5 has especially broad mappings, including Japanese font variants, translated
UI/sign sprites, and Japanese voice clips. Switching language calls the
initializer again, so cached resource-map values are replaced with the selected
language's assets.

The exact resource set varies by chapter. Do not copy a font, sprite, or sound
mapping from one payload and assume the identifier exists in another.

## Localized Video

The Windows install contains paired Chapter 3 intro videos and Chapter 5
`vid/ch5_intro_en.mp4` and `vid/ch5_intro_jp.mp4`. Chapter 5's garden-video
controller selects the filename from `global.lang`, opens it through GameMaker's
video API, and handles packed and YUV drawing formats. This is an asset choice,
not a JSON string lookup.

## Files Shipped on Windows

- Chapter 1 ships both `lang/lang_en.json` and `lang/lang_ja.json`.
- Chapters 2 through 5 ship `lang/lang_ja.json`; English is predominantly in
  GML.
- Chapter Select ships no chapter-style language JSON.

See [CHAPTER_SELECT](chapter-select.md) for launcher UI text and
[Platform Differences](platform-differences.md) for the limits of console
runtime basis.
