# PizzaOven & AFOM/CYOP Conversion

G3M supports importing and converting mods created for Pizza Tower's **PizzaOven** modding framework, as well as **AFOM/CYOP** custom level mods. Both formats are detected and converted automatically on import.

---

## PizzaOven Mods

### What Is PizzaOven?

PizzaOven is a third-party mod manager for Pizza Tower widely used in the community. PizzaOven mods are distributed as `.zip` archives containing a `mod.json` metadata file and mod content files. G3M auto-detects and converts eligible PizzaOven mods into the native G3M format — no manual steps required from the player.

### PizzaOven Mod Structure

A PizzaOven mod archive typically contains:

- **`mod.json`** — The mod's metadata file. Key fields:
  - `title` — Mod display name.
  - `submitter` — Author name.
  - `description` — Mod description.
  - `homepage` — Link to the mod's page.
  - `preview` — Icon file name.
  - `cat` — Mod category. Absent or blank means a regular NORMAL mod. `"CYOP/AFOM"` means a custom levels mod. `"GMLoader"` means a GMLoader scripting mod.
- **Mod content files** (for NORMAL mods):

| File type | Extensions | Destination in game folder |
| --- | --- | --- |
| Binary patch | `.xdelta`, `.vcdiff` | Applied to `data.win` (or sound banks) |
| Full data replacement | `.win` | Replaces `data.win` |
| Audio bank | `.bank` | `sound/Desktop/` |
| Language/text file | `.txt` | `lang/` (if contains `lang =`), or game root (credits files) |
| Font | `.ttf`, `.otf` | `lang/fonts/` |
| Language definition | `.def` | `lang/` |
| Language graphics | `.png` | `lang/graphics/` |
| Language graphics config | `.json` | `lang/graphics/` |
| Plugin DLL / video | `.dll`, `.mp4` | Game root |

### Opt-Out Markers

Mod authors can place hidden marker files in their archive to prevent automatic conversion:

| File | Effect |
| --- | --- |
| `.disable_gb1click` | Disables G3M conversion entirely |
| `.disable_gb1click_pizzaoven` | Disables PizzaOven-style conversion |
| `.disable_gb1click_pizzaovenplus` | Disables PizzaOven+ conversion |

If both `.disable_gb1click_pizzaoven` and `.disable_gb1click_pizzaovenplus` are present, G3M will not convert the mod.

### How G3M Converts a PizzaOven NORMAL Mod

Converting a PizzaOven NORMAL mod requires the **Pizza Tower game path** to be configured in Settings → Game.

The conversion pipeline:

1. **Inspection** — G3M reads `mod.json`, checks opt-out markers, confirms the mod type is NORMAL, and verifies at least one eligible mod file exists. If any check fails, conversion is skipped with an explanatory message.
2. **Game copy** — G3M copies the entire Pizza Tower installation to a temporary directory. This temporary copy is the "sandbox" the mod will be applied to.
3. **Simulation** — G3M applies all the mod's eligible files to the temporary game copy, replicating what PizzaOven would do natively (xdelta patches applied via G3MTool, files placed in the correct subfolders).
4. **Diff** — G3M compares the original game files with the modified temporary copies using SHA-256 hashing to identify exactly which files were changed.
5. **G3M mod creation** — From the diff:
   - If `data.win` changed: G3M creates a `.g3mpatch` (preferred). If that fails verification, it falls back to `.xdelta`, then to a full `.win` copy.
   - All other changed files (audio banks, language files, fonts, etc.) become `extra_files` in the G3M mod.
   - `mod_config.json` is written with metadata from `mod.json` and/or GameBanana.
6. **Cleanup** — The temporary game copy is deleted.

The resulting G3M mod behaves like any native mod: it patches `data.win` and copies extra files on launch, then restores everything after the game exits.

If the same mod (matched by GameBanana mod ID) is imported again, G3M reconverts it and replaces the existing mod content while preserving the mod's version snapshots folder.

### Unsupported PizzaOven Mod Types

| Type | Detection | G3M Support |
| --- | --- | --- |
| **NORMAL** | No `cat` in `mod.json`, or has xdelta patches at root | ✅ Auto-converted |
| **CYOP/AFOM** | `cat: "CYOP/AFOM"` in `mod.json`, or has `levels/` with `.json` and `.ini` | See below |
| **GMLoader** | `cat: "GMLoader"` in `mod.json`, or has GML folders (`audio/`, `code/`, `lib/`, etc.) | ❌ Not supported |

**GMLoader** mods use a scripting framework that requires GMLoader to be installed separately inside the game. G3M cannot convert them.

---

## AFOM/CYOP Custom Level Mods

### What Are AFOM/CYOP Mods?

**CYOP** (Create Your Own Pizza) is Pizza Tower's built-in custom level system. **AFOM** (Another Fixed Objects Mod) is a community name for the same custom level format. Unlike regular mods, AFOM/CYOP mods do not patch the game's data file — instead they supply custom tower (level) data that Pizza Tower reads from `%APPDATA%\PizzaTower_GM2\towers\`.

### AFOM/CYOP Mod Structure

An AFOM/CYOP mod archive contains one or more **tower folders** at its root. Each tower folder must include an `.ini` file with a `[properties]` section containing at minimum:

- `name` — Display name of the tower.
- `mainlevel` — Path to the tower's main level file.

Example:

```
My Custom Tower/
├── MyTower.ini      ← [properties] with name and mainlevel
├── levels/
│   ├── mainlevel.json
│   └── room2.json
└── music/
    └── theme.ogg
```

The archive must contain **only folders** at its root. Any file directly at the archive root causes G3M to reject the AFOM/CYOP detection.

### How G3M Handles AFOM/CYOP Mods

**On import:**

1. G3M extracts the archive to a temporary folder.
2. It inspects the root: every root entry must be a folder, and each folder must contain a valid `.ini` with `[properties]`, `name`, and `mainlevel`.
3. If valid, G3M creates a mod directory and copies all tower folder(s) into a `towers/` subfolder inside it.
4. A `mod_config.json` is created with:
   - Game: `pizzatower`
   - Tag: `CYOP/AFOM`
   - `extra_files: ["towers/"]`

**On launch:**

1. When you launch Pizza Tower with an AFOM/CYOP mod selected, G3M copies the contents of `towers/` from the mod directory into `%APPDATA%\PizzaTower_GM2\towers\` (Pizza Tower's custom level directory). Existing files at the destination are backed up first.
2. Pizza Tower is launched. The game reads the installed tower data from `%APPDATA%\PizzaTower_GM2\towers\`.
3. After the game exits, G3M removes the installed tower folders and restores any previously backed-up files — identical to how extra files work for all other mods.

### Creating an AFOM/CYOP Mod

To create and distribute an AFOM/CYOP mod compatible with G3M:

1. **Build your tower** using the in-game CYOP editor or compatible community tools.
2. **Collect the tower folder** — the directory produced by the editor that contains an `.ini` and level data.
3. **Package it** — create a `.zip` archive with each tower folder directly at the archive root (no wrapping folder above the tower folder).
4. **Validate the `.ini`** — ensure a `[properties]` section is present with valid `name` and `mainlevel` keys.
5. **Distribute** — upload to GameBanana with the `CYOP/AFOM` category, or share the `.zip` directly. G3M will recognize and convert it automatically on import.
