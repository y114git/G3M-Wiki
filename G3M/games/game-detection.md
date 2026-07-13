# Game Detection

G3M validates game paths by matching each game definition against
platform-specific executable names and known data file names.

---

## Executable Candidates

The current built-in executable candidates are:

- **Game:** DELTARUNE
  - **Windows:** `DELTARUNE.exe`, `DELTARUNE`
  - **Linux:** `DELTARUNE`, `DELTARUNE.exe`
  - **macOS:** `DELTARUNE.app`, `DELTARUNEdemo.app`

- **Game:** DELTARUNEdemo
  - **Windows:** `DELTARUNE.exe`, `DELTARUNE`
  - **Linux:** `DELTARUNE`, `DELTARUNE.exe`
  - **macOS:** `DELTARUNEdemo.app`, `DELTARUNE.app`

- **Game:** UNDERTALE
  - **Windows:** `UNDERTALE.exe`, `UNDERTALE`
  - **Linux:** `UNDERTALE`, `UNDERTALE.exe`
  - **macOS:** `UNDERTALE.app`

- **Game:** UNDERTALE Yellow
  - **Windows:** `Undertale Yellow.exe`, `Undertale Yellow`, `UNDERTALE.exe`,
    `UNDERTALE`
  - **Linux:** `Undertale Yellow`, `UNDERTALE`, `Undertale Yellow.exe`,
    `UNDERTALE.exe`
  - **macOS:** `UNDERTALE.app`

- **Game:** Pizza Tower
  - **Windows:** `PizzaTower.exe`, `PizzaTower`
  - **Linux:** `PizzaTower`, `PizzaTower.exe`
  - **macOS:** `PizzaTower.app`

- **Game:** Sugary Spire
  - **Windows:** `SugarySpire_ExhibitionNight.exe`,
    `SugarySpire_ExhibitionNight`
  - **Linux:** `SugarySpire_ExhibitionNight`, `SugarySpire_ExhibitionNight.exe`
  - **macOS:** `SugarySpire_ExhibitionNight.app`

- **Game:** FRICKBEARS3
  - **Windows:** `Frickbears3.exe`, `Frickbears3`
  - **Linux:** `Frickbears3`, `Frickbears3.exe`
  - **macOS:** `Frickbears3.app`

Custom games contribute exactly one executable candidate per platform: the file
name stored in their registry record.

---

## Auto-Detection

`autodetect_path()` only returns built-in paths for:

- DELTARUNE
- DELTARUNEdemo
- UNDERTALE
- Pizza Tower

It intentionally does not auto-detect:

- UNDERTALE Yellow
- Sugary Spire
- FRICKBEARS3

On Windows the search checks common Steam locations across drive letters. On
Linux and macOS it checks known Steam roots and a small set of additional
platform-specific locations.

---

## Data File Resolution

The preferred game data file names are platform-aware:

- Windows: `data.win`
- Linux: `game.unx`, then `data.win`, then `game.ios`
- macOS: `game.ios`, then `data.win`

If the preferred file is missing, G3M falls back to any file in the folder with
one of these extensions:

- `.win`
- `.unx`
- `.ios`
- `.droid`

Custom games use the configured `data_file_name` as the preferred match.

---

## Process Names

Process monitoring uses the names declared by each game definition. The built-in
set currently includes:

- `DELTARUNE.exe`
- `DELTARUNE`
- `UNDERTALE.exe`
- `UNDERTALE`
- `Undertale Yellow.exe`
- `Undertale Yellow`
- `PizzaTower.exe`
- `PizzaTower`
- `SugarySpire_ExhibitionNight.exe`
- `SugarySpire_ExhibitionNight`
- `Frickbears3.exe`
- `Frickbears3`
- `runner`

---

## Chapter Resource Paths

DELTARUNE is the only built-in game with multiple tabs. Its current folder
mapping is:

- `deltarune_0` -> `chapter_0`
- `deltarune_1` -> `chapter_1`
- `deltarune_2` -> `chapter_2`
- `deltarune_3` -> `chapter_3`
- `deltarune_4` -> `chapter_4`

Single-tab games use their own game id as the folder key.
