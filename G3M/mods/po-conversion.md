# PO Translation File Conversion

G3M includes a PO file conversion feature for creating text translation mods. PO (Portable Object) files are a standard format for software translations, and G3M can convert them into game data patches.

---

## What Are PO Files?

PO files are the standard GNU gettext format for translations:

```
#: original text context
msgid "Hello, world!"
msgstr "Привет, мир!"

msgid "Save"
msgstr "Сохранить"
```

Each entry has:

- **msgid** — The original (source language) string.
- **msgstr** — The translated string.
- Optional comments and context markers.

---

## How It Works in G3M

G3M can process PO files to create text modification patches for GameMaker games:

### The Process

1. **Extract strings** — G3M (via G3MTool) extracts all text strings from the game's data file into a PO template file (.pot or .po).
2. **Translate** — You (or a translator) fills in the `msgstr` entries with the translated text.
3. **Convert back** — G3M applies the translated PO file to the original game data, producing a patched data file or g3mpatch with all strings replaced.

### Step-by-Step

#### Extracting Strings

1. Open Modding Tools.
2. Use the Info or Convert tab with a game data file.
3. G3MTool can output a PO-compatible file listing all game strings.
4. Save this file as a `.po` or `.pot` template.

#### Translating

1. Open the PO file in any PO editor (e.g., Poedit, Lokalize, or a plain text editor).
2. Translate each `msgstr` entry.
3. Leave `msgstr` empty for strings you don't want to change.
4. Save the translated PO file.

#### Applying the Translation

1. Open Modding Tools → Patch or Convert tab.
2. Select the original game data file.
3. Apply the translated PO file.
4. G3MTool replaces matching strings in the game data with their translations.
5. Save the result as a patched data file or create a g3mpatch from it.

---

## Creating a Translation Mod

After applying the PO translations to create a patched data file:

1. Create a g3mpatch from the patched file (Modding Tools → Convert DATA → g3mpatch).
2. Create a new mod in the Library (Add Mod → Create Mod).
3. Assign the g3mpatch as the data file.
4. Set the mod metadata: name (e.g., "Russian Translation"), author, tags (`textedit`).
5. Export and share the mod.

---

## PO File Format Details

G3M follows the standard PO format:

```
# Comment line
#. Extracted comment
#: reference:location
msgctxt "context"
msgid "Source text"
msgstr "Translated text"
```

### Multi-line Strings

```
msgid ""
"This is a very long string that "
"spans multiple lines."
msgstr ""
"Это очень длинная строка, "
"которая занимает несколько строк."
```

### Plural Forms

G3M does not use PO plural forms (msgid_plural/msgstr[N]). All strings are treated as singular.

### Encoding

PO files should be saved in UTF-8 encoding. The header should include:

```
"Content-Type: text/plain; charset=UTF-8\n"
```

---

## Limitations

- PO conversion only affects text strings in the game data. It cannot change sprites, sounds, code logic, or other non-text resources.
- String matching is exact — if the game updates and changes a string, the PO entry for the old string will no longer match.
- Some games use encoded or formatted strings (with placeholders like `{0}`, `\n`, color codes). These must be preserved in the translation.
- Very long translations may overflow text boxes in the game if the game's UI doesn't dynamically resize.

---

## Tips for Translators

- **Preserve formatting codes.** If the original has `\n` (newline), `\t` (tab), or `{0}` (placeholder), keep them in the translation.
- **Preserve leading/trailing spaces.** Some strings include intentional spaces for alignment.
- **Test in-game.** After creating the translation mod, launch the game with it applied to verify all strings display correctly.
- **Use context.** The PO file may include context markers (#: comments) showing where in the game each string is used. This helps choose the right translation.
- **Iterate.** Use G3M's Mod Versions feature to save snapshots of your translation as you progress.
