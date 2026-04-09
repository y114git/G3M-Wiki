# Save & Load System

Each numbered DELTARUNE chapter owns its own save/load scripts:

- `scr_saveprocess`
- `scr_load`

The launcher does not. Numbered chapters write plain-text save files through `ossafe_*` wrappers. The exact filename and payload order differ between Chapter 1 and Chapter 2+.

---

## File Names

| Runtime | Main save file |
|---|---|
| Chapter 1 | `filech1_<slot>` |
| Chapter 2 | `filech2_<slot>` |
| Chapter 3 | `filech3_<slot>` |
| Chapter 4 | `filech4_<slot>` |

Chapter 4 uses:

```gml
File = "filech" + string(global.chapter) + "_" + string(arg0);
```

Chapter 1 hardcodes `filech1_`.

---

## Slot Number Map

The numeric suffix after `filech<chapter>_` is part of the runtime contract. Numbered chapters do not treat all suffixes as interchangeable user save slots.

Confirmed slot meanings:

| Slot suffix | Meaning | Evidence |
|---:|---|---|
| `0` | main save file 1 | checked by launcher/device menu as primary save slot |
| `1` | main save file 2 | checked by launcher/device menu as primary save slot |
| `2` | main save file 3 | checked by launcher/device menu as primary save slot |
| `3` | completion copy for file 1 | `scr_completed_chapter_in_slot(arg0, 0)` checks `filech<chapter>_3` |
| `4` | completion copy for file 2 | `scr_completed_chapter_in_slot(arg0, 1)` checks `filech<chapter>_4` |
| `5` | completion copy for file 3 | `scr_completed_chapter_in_slot(arg0, 2)` checks `filech<chapter>_5` |
| `9` | temp / recent recovery slot | written by `scr_save()` and `scr_tempsave()`, loaded by `scr_tempload()` in Chapters 1, 2, 3, and 4 |

The code uses three distinct suffix groups:

- `0..2`: primary user-facing save slots
- `3..5`: completion-copy slots associated with `0..2`
- `9`: temp/recovery slot used by `scr_tempsave()` and `scr_tempload()`

### Primary slots `0..2`

Primary slot detection in `CHAPTER_SELECT` and `DEVICE_MENU` only checks:

- `filech<chapter>_0`
- `filech<chapter>_1`
- `filech<chapter>_2`

For example, Chapter 4 `DEVICE_MENU/Create_0.gml` uses:

```gml
if (ossafe_file_exists("filech" + CH + "_0")) FILE[0] = 1;
if (ossafe_file_exists("filech" + CH + "_1")) FILE[1] = 1;
if (ossafe_file_exists("filech" + CH + "_2")) FILE[2] = 1;
```

Visible user-facing save slots are the `0..2` group.

### Completion slots `3..5`

Completion-file checks are not launcher-only. They exist in chapter runtime code as well.

`CHAPTER_SELECT/scripts/scr_chapter_save_file_exists.gml`:

```gml
function scr_completed_chapter_any_slot(arg0)
{
    for (var i = 0; i < 3; i++)
    {
        if (ossafe_file_exists("filech" + string(arg0) + "_" + string(i + 3)))
        {
            ...
        }
    }
}
```

And:

```gml
function scr_completed_chapter_in_slot(arg0, arg1)
{
    var _file_exists = ossafe_file_exists("filech" + string(arg0) + "_" + string(arg1 + 3));
    return _file_exists;
}
```

The same `scr_chapter_save_file_exists.gml` helper already exists in Chapter 1 and Chapter 2. Chapter 3 and Chapter 4 additionally expose an explicit completion-write helper.

`CHAPTER_3/scripts/scr_complete_save_file.gml`:

```gml
_remfilechoice = global.filechoice;
global.filechoice += 3;
scr_set_ini_value(global.chapter, global.filechoice, "SideB", scr_sideb_active());
scr_save();
global.filechoice = _remfilechoice;
```

A normal filechoice of:

- `0` saves completion data into slot `3`
- `1` saves completion data into slot `4`
- `2` saves completion data into slot `5`

The practical chapter split is:

- Chapter 1: completion slots `3..5` are part of the shared file-existence and metadata model
- Chapter 2: same `3..5` completion-slot checks are present
- Chapter 3: `scr_complete_save_file()` writes to `filechoice + 3`
- Chapter 4: same explicit completion-write path as Chapter 3

### Temp / recent slot `9`

Slot `9` is not Chapter 4-specific. The same pattern exists in Chapters 1, 2, 3, and 4.

Chapter 1 `scr_save()`:

```gml
scr_saveprocess(global.filechoice);
filechoicebk2 = global.filechoice;
global.filechoice = 9;
scr_saveprocess(9);
global.filechoice = filechoicebk2;
```

The Chapter 2, Chapter 3, and Chapter 4 `scr_save()` scripts use the same sequence.

Chapter 1 `scr_tempsave()`:

```gml
Filechoicebk2 = global.filechoice;
global.filechoice = 9;
scr_saveprocess(global.filechoice);
global.filechoice = filechoicebk2;
```

Chapter 1 `scr_tempload()`:

```gml
Filechoicebk3 = global.filechoice;
global.filechoice = 9;
scr_load();
global.filechoice = filechoicebk3;
```

The same helper pair exists in:

- `CHAPTER_1/scripts/scr_tempsave.gml`
- `CHAPTER_1/scripts/scr_tempload.gml`
- `CHAPTER_2/scripts/scr_tempsave.gml`
- `CHAPTER_2/scripts/scr_tempload.gml`
- `CHAPTER_3/scripts/scr_tempsave.gml`
- `CHAPTER_3/scripts/scr_tempload.gml`
- `CHAPTER_4/scripts/scr_tempsave.gml`
- `CHAPTER_4/scripts/scr_tempload.gml`

Each numbered chapter also refreshes slot `9` after a successful load:

- Chapter 1 `scr_load.gml` ends with `scr_tempsave();`
- Chapter 2 `scr_load.gml` ends with `scr_tempsave();`
- Chapter 3 `scr_load.gml` ends with `scr_tempsave();`
- Chapter 4 `scr_load.gml` ends with `scr_tempsave();`

This makes slot `9` a rolling post-load / post-save recovery image, not a normal save-select slot.

### Slot `9` load semantics by chapter

Slot `9` also affects room-fixup behavior during `scr_load()`.

- Chapter 1: `scr_load.gml` wraps room validation in `if (global.filechoice != 9)`
- Chapter 2: same `if (global.filechoice != 9)` guard
- Chapter 3: no equivalent `filechoice != 9` guard in the final room-resolution block
- Chapter 4: same `if (global.filechoice != 9)` guard as Chapters 1 and 2

Representative Chapter 1 / 2 / 4 pattern:

```gml
if (global.filechoice != 9)
{
    var valid_room_index = scr_get_valid_room(global.chapter, global.currentroom);
    global.currentroom = scr_get_id_by_room_index(valid_room_index);
    ...
}
```

In Chapters 1, 2, and 4, slot `9` also bypasses the normal room-repair path used for primary save slots.

---

## Wrapper Layer

Main file I/O uses:

- `ossafe_file_text_open_write`
- `ossafe_file_text_open_read`
- `ossafe_file_text_write_real`
- `ossafe_file_text_write_string`
- `ossafe_file_text_writeln`
- `ossafe_file_text_read_real`
- `ossafe_file_text_read_string`
- `ossafe_file_text_readln`
- `ossafe_file_text_close`

Console serialization also uses:

- `scr_ds_list_write`
- `scr_ds_list_read`

The runtime keeps the same logical field order on PC and console, but the physical text layout differs.

---

## Chapter 4 Save Order

Chapter 4 `scr_saveprocess` is the clearest reference for the Chapter 2+ layout.

### Header

Written first:

1. `global.truename`
2. `global.othername[0..5]` on PC, or one DS-list block on console
3. `global.char[0]`
4. `global.char[1]`
5. `global.char[2]`
6. `global.gold`
7. `global.xp`
8. `global.lv`
9. `global.inv`
10. `global.invc`
11. `global.darkzone`

### Character block

For each `i = 0 .. 4`, Chapter 4 writes:

On PC:

1. `global.hp[i]`
2. `global.maxhp[i]`
3. `global.at[i]`
4. `global.df[i]`
5. `global.mag[i]`
6. `global.guts[i]`
7. `global.charweapon[i]`
8. `global.chararmor1[i]`
9. `global.chararmor2[i]`
10. `global.weaponstyle[i]`

Then for each equipment/stat subslot `q = 0 .. 3`:

1. `global.itemat[i][q]`
2. `global.itemdf[i][q]`
3. `global.itemmag[i][q]`
4. `global.itembolts[i][q]`
5. `global.itemgrazeamt[i][q]`
6. `global.itemgrazesize[i][q]`
7. `global.itemboltspeed[i][q]`
8. `global.itemspecial[i][q]`
9. `global.itemelement[i][q]`
10. `global.itemelementamount[i][q]`

Then spell loadout for `j = 0 .. 11`:

1. `global.spell[i][j]`

Each character block is:

- 10 base fields
- 4 × 10 modifier fields
- 12 spell ids

### Global battle-tuning block

After the five character blocks:

1. `global.boltspeed`
2. `global.grazeamt`
3. `global.grazesize`

### Inventory block

On PC:

For `j = 0 .. 12`:

1. `global.item[j]`
2. `global.keyitem[j]`

For `j = 0 .. 47`:

1. `global.weapon[j]`
2. `global.armor[j]`

For `j = 0 .. 71`:

1. `global.pocketitem[j]`

### Tension and Light World block

Then:

1. `global.tension`
2. `global.maxtension`
3. `global.lweapon`
4. `global.larmor`
5. `global.lxp`
6. `global.llv`
7. `global.lgold`
8. `global.lhp`
9. `global.lmaxhp`
10. `global.lat`
11. `global.ldf`
12. `global.lwstrength`
13. `global.ladef`

### Legacy item/phone and flags

For `i = 0 .. 7`:

1. `global.litem[i]`
2. `global.phone[i]`

Then for `i = 0 .. 2499`:

1. `global.flag[i]`

### Footer

Written last:

1. `global.plot`
2. `global.currentroom`
3. `global.time`

Chapter 4 PC field order:

---

## Chapter 4 Load Order

`scr_load()` mirrors the same order. Representative start:

```gml
global.truename = ossafe_file_text_read_string(myfileid);
...
global.char[0] = ossafe_file_text_read_real(myfileid);
global.char[1] = ossafe_file_text_read_real(myfileid);
global.char[2] = ossafe_file_text_read_real(myfileid);
global.gold = ossafe_file_text_read_real(myfileid);
...
global.darkzone = ossafe_file_text_read_real(myfileid);
```

Then it reads:

- 5 character blocks
- 3 global battle-tuning values
- item/keyitem block
- weapon/armor block
- pocketitem block
- tension and Light World block
- litem/phone block
- 2500 flags
- plot/currentroom/time

The loader is a field-for-field mirror of the saver. Any inserted field must be added in both places in the same position.

---

## Console vs PC

### PC

Writes one value per line with repeated `ossafe_file_text_write_real/string`.

### Console

Uses grouped DS-list blocks, for example:

- `scr_ds_list_write(global.othername, 6)`
- `scr_ds_list_write(global.hp, 5)`
- `scr_ds_list_write(global.item, 13)`
- `scr_ds_list_write(global.weapon, 48)`
- `scr_ds_list_write(global.pocketitem, 72)`
- `scr_ds_list_write(global.flag, 2500)`

The logical order stays the same.

---

## Room Repair

After loading the payload, Chapter 4 restores audio:

```gml
Audio_group_set_gain(1, global.flag[15], 0);
audio_set_master_gain(0, global.flag[17]);
```

Then it repairs room ids:

```gml
var room_id = global.currentroom;
if (room_id < 10000)
{
    room_id = scr_get_id_by_room_index(global.currentroom);
    if (room_id == room_gms_debug_failsafe)
    {
        room_id += (global.chapter * 10000);
    }
    global.currentroom = room_id;
}
```

Chapter 4 also applies post-load chapter-specific room overrides:

```gml
if (scr_completed_chapter_any_slot(4) && global.plot >= 243)
{
    global.flag[1658] = 1;
    if (global.flag[1659] == 0)
    {
        global.currentroom = scr_get_id_by_room_index(261);
    }
}
```

Room restoration involves remapping saved room ids through `scr_room_index`, not a direct `room_goto`.

---

## Post-Load Item Compaction

Chapter 4 compacts the main item list after load:

```gml
var adjusted_list = [];
for (var i = 0; i < array_length(global.item); i += 1)
{
    if (global.item[i] == 0 || global.item[i] >= 999)
        continue;
    adjusted_list[array_length(adjusted_list)] = global.item[i];
}
...
for (var i = 0; i < array_length(adjusted_list); i += 1)
{
    global.item[i] = adjusted_list[i];
}
```

Sparse or sentinel item ids in `global.item[]` can be stripped during load.

---

## Chapter 1 vs Chapter 2+

The structural breakpoint is:

## Chapter 1

- older filename logic
- smaller inventory structures
- no `global.pocketitem`
- no `global.itemelement` / `global.itemelementamount`
- older room-id assumptions

## Chapter 2+

- generic `"filech" + string(global.chapter)` naming
- 5-character stat blocks
- 4 modifier subslots per character
- 12 spell ids per character
- `global.pocketitem[0..71]`
- elemental equipment data
- 48-entry weapon and armor blocks
- room-id repair through helper functions

---

## Metadata Outside Main Saves

The main chapter save files are separate from launcher/config metadata such as:

- `dr.ini`
- `true_config.ini`

Those belong to `CHAPTER_SELECT` and settings flow, not to the numbered-chapter payload format.

---

## Modding Rules

If a mod changes saved state:

1. patch that chapter's `scr_saveprocess`
2. patch the matching `scr_load`
3. preserve exact field order
4. update `scr_gamestart` defaults
5. account for post-load repair and cleanup logic