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
file = "filech" + string(global.chapter) + "_" + string(arg0);
```

Chapter 1 hardcodes `filech1_`.

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

So each character block is:

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

That is the actual Chapter 4 PC field order.

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
audio_group_set_gain(1, global.flag[15], 0);
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

So room restoration is not just “read saved room id and go there.”

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

So sparse or sentinel item ids in `global.item[]` can be stripped during load.

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
