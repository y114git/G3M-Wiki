# Speaker System

`scr_speaker(name)` resets the portrait/expression, applies a Light World, Dark
World, or battle default, then maps a string identifier to `global.typer`,
`global.fc`, and sometimes `global.fe`. The mapping below is the shipped Chapter
5 implementation; earlier payloads contain subsets.

## Chapter 5 Mapping

- **Speaker strings:** `silent`
  - **Face:** 0
  - **Typer and context:** 2 light, 36 dark

- **Speaker strings:** `balloon`, `enemy`
  - **Face:** 0
  - **Typer and context:** 50

- **Speaker strings:** `sans`
  - **Face:** 6
  - **Typer and context:** 14

- **Speaker strings:** `undyne`, `und`
  - **Face:** 9
  - **Typer and context:** 17

- **Speaker strings:** `temmie`, `tem`
  - **Face:** 0
  - **Typer and context:** 21

- **Speaker strings:** `jevil`
  - **Face:** 0
  - **Typer and context:** 35

- **Speaker strings:** `catti` / `jockington`, `joc`
  - **Face:** 13 / 14
  - **Typer and context:** Context default

- **Speaker strings:** `catty`, `caddy` / `bratty`, `bra`
  - **Face:** 16 / 17
  - **Typer and context:** Context default

- **Speaker strings:** `rouxls`, `rou` / `burgerpants`, `bur`
  - **Face:** 18 / 19
  - **Typer and context:** Context default

- **Speaker strings:** `spamton`
  - **Face:** 0
  - **Typer and context:** 66 overworld, 68 battle

- **Speaker strings:** `sneo`
  - **Face:** 0
  - **Typer and context:** 67

- **Speaker strings:** `susie`, `sus`
  - **Face:** 1
  - **Typer and context:** 10 light, 30 dark, 47 dark battle

- **Speaker strings:** `ralsei`, `ral`
  - **Face:** 2
  - **Typer and context:** 31, 45 battle, 6 while flag 30 is set

- **Speaker strings:** `noelle`, `noe`
  - **Face:** 3
  - **Typer and context:** 12 light, 56 dark, 59 battle

- **Speaker strings:** `toriel`, `tor`
  - **Face:** 4
  - **Typer and context:** 7

- **Speaker strings:** `asgore`, `asg`
  - **Face:** 10
  - **Typer and context:** 18 light, 89 dark

- **Speaker strings:** `king`, `kin`
  - **Face:** 20
  - **Typer and context:** 33, 36 in early Chapter 1, 48 battle

- **Speaker strings:** `rudy`, `rud`
  - **Face:** 15
  - **Typer and context:** 55

- **Speaker strings:** `lancer`, `lan`
  - **Face:** 5
  - **Typer and context:** 32, 46 battle

- **Speaker strings:** `berdly`, `ber`
  - **Face:** 12
  - **Typer and context:** 13 light, 57 dark, 77 battle

- **Speaker strings:** `alphys`, `alp`
  - **Face:** 11
  - **Typer and context:** 20

- **Speaker strings:** `queen`, `que` / `queen_2`, `que_2`
  - **Face:** 21
  - **Typer and context:** 58 / 62

- **Speaker strings:** `carol`
  - **Face:** 22
  - **Typer and context:** 87

- **Speaker strings:** `flowery` / `flowery_noface` / `flowery_s`
  - **Face:** 23 / 0 / 23
  - **Typer and context:** 88 / 88 / 86

- **Speaker strings:** `tenna` / `jackenstein`
  - **Face:** 0
  - **Typer and context:** 84 / 83

- **Speaker strings:** `aqua`
  - **Face:** 0
  - **Typer and context:** 90

- **Speaker strings:** `seth`, `purple`
  - **Face:** 0
  - **Typer and context:** 91

- **Speaker strings:** `yellow` / `orange` / `blue` / `green`
  - **Face:** 0
  - **Typer and context:** 92 / 93 / 94 / 95

- **Speaker strings:** `bluef`
  - **Face:** 25
  - **Typer and context:** 94

- **Speaker strings:** `pink`
  - **Face:** 0
  - **Typer and context:** 97, expression reset to 0

- **Speaker strings:** `opuppet`
  - **Face:** 0
  - **Typer and context:** 98

The function resets `global.fe = 0` at entry in Chapter 5. Set a non-default
expression after calling it. Unknown strings retain the context default and no
portrait; there is no validation error.

## Portrait IDs Added by Chapter 5

The long-standing IDs include Susie 1, Ralsei 2, Noelle 3, Toriel 4, Lancer 5,
Sans 6, Undyne 9, Asgore 10, Alphys 11, Berdly 12, Rudy 15, King 20, Queen 21,
and Carol 22. Chapter 5 verifies Flowery at 23 and the faced blue speaker at 25.
Portrait sprites and expression ranges are resolved by the face objects, so an
unused numeric ID alone does not create a portrait.

## Modding Pattern

Add a speaker branch after the defaults and assign all state it owns:

```gml
if (_speaker == "modspeaker") {
    global.fc = 26;
    global.fe = 0;
    global.typer = global.fighting ? 101 : 100;
}
```

Then add matching `scr_texttype()` cases and face/expression assets. Use
`c_speaker("modspeaker")` in a cutscene or call `scr_speaker()` before creating
the writer. Check the target chapter: Chapter 5 names such as `flowery` and
`aqua` do not exist in older payload mappings.

See [Dialogue System](dialogue-system.md) for writer behavior and
[Cutscene System](cutscene-system.md) for `c_speaker`.
