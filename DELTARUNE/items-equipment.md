# Items & Equipment

This page documents DELTARUNE's item, weapon, and armor data as seen through UndertaleModTool.

The three core data scripts are:

- `scripts/scr_iteminfo/scr_iteminfo.gml`
- `scripts/scr_weaponinfo/scr_weaponinfo.gml`
- `scripts/scr_armorinfo/scr_armorinfo.gml`

and the main startup cache helpers are:

- `scripts/scr_iteminfo_all/scr_iteminfo_all.gml`
- `scripts/scr_weaponinfo_all/scr_weaponinfo_all.gml`
- `scripts/scr_armorinfo_all/scr_armorinfo_all.gml`

These scripts do not return a struct. They write a bundle of temporary variables into the caller's scope, and the cache helpers then copy those values into persistent `global.*` arrays.

For general array/scope behavior in GameMaker, see:

- https://manual.gamemaker.io/monthly/en/GameMaker_Language/GML_Overview/Variables_And_Variable_Scope.htm
- https://manual.gamemaker.io/lts/en/GameMaker_Language/GML_Overview/Arrays.htm

---

## Runtime Model

DELTARUNE splits inventory data into several layers:

- item ids stored in runtime inventory arrays such as `global.item[]`
- metadata generated on demand by `scr_iteminfo`
- cached display/value/usable data filled by `scr_iteminfo_all`
- separate but parallel weapon and armor metadata scripts

Inventory slots and item definitions are separate layers.

If `global.item[3] = 8`, slot 3 contains item id `8` (`Darkburger` in Chapter 4 data), but the descriptive fields still come from running `scr_iteminfo(8)` or reading the arrays filled by `scr_iteminfo_all()`.

---

## Cache Helpers

The Chapter 4 item cache helper is small and revealing:

```gml
function scr_iteminfo_all()
{
    for (i = 0; i < 12; i += 1)
    {
        itemid = global.item[i];
        scr_iteminfo(itemid);
        global.itemnameb[i] = itemnameb;
        global.itemdescb[i] = itemdescb;
        global.itemvalue[i] = value;
        global.itemusable[i] = usable;
    }
}
```

The helper caches current inventory contents, not the full master item table. The cache arrays are slot-based, and effect logic still depends on the definition scripts.

The same broad pattern exists for weapons and armor.

---

## `scr_iteminfo(id)` Output Fields

At the start of the script, DELTARUNE zeroes a common set of output variables:

```gml
Usable = 0;
replaceable = 0;
value = 0;
itemtarget = 0;
itemnameb = " ";
itemdescb = " ";
```

These fields mean:

| Field | Meaning |
|---|---|
| `usable` | whether the item can be consumed from the relevant menu/battle context |
| `replaceable` | alternate item id produced by certain multi-stage consumables |
| `value` | item shop/sell economy value |
| `itemtarget` | targeting mode |
| `itemnameb` | display name |
| `itemdescb` | display description |

`itemtarget` is especially important because battle menus use it to decide whether to open ally selection, enemy selection, or no target at all.

In Chapter 4's `scr_iteminfo` the main target values are:

- `0`: no target / not battle-usable / direct effectless item shell
- `1`: single ally target
- `2`: multi-target or special target flow used by team-wide and utility items

---

## `scr_weaponinfo(id)` Output Fields

Weapons expose a much larger temporary bundle:

- `weaponnametemp`
- `weapondesctemp`
- `wmessage2temp`
- `wmessage3temp`
- `wmessage4temp`
- `weaponattemp`
- `weapondftemp`
- `weaponmagtemp`
- `weaponboltstemp`
- `weaponstyletemp`
- `weapongrazeamttemp`
- `weapongrazesizetemp`
- `weaponchar1temp`
- `weaponchar2temp`
- `weaponchar3temp`
- `weaponchar4temp`
- `weaponabilitytemp`
- `weaponabilityicontemp`
- `weaponicontemp`
- `value`

Weapon definitions also carry:

- character reaction lines for equip/examine menus
- graze modifiers
- bolt-count modifiers
- ability icon metadata
- chapter-appropriate fourth-party support in later chapters through `weaponchar4temp`

---

## `scr_armorinfo(id)` Output Fields

Armor mirrors the weapon model closely, with armor-specific fields:

- `armornametemp`
- `armordesctemp`
- `amessage2temp`
- `amessage3temp`
- `amessage4temp`
- `armorattemp`
- `armordftemp`
- `armormagtemp`
- `armorboltstemp`
- `armorgrazeamttemp`
- `armorgrazesizetemp`
- `armorchar1temp`
- `armorchar2temp`
- `armorchar3temp`
- `armorchar4temp`
- `armorabilitytemp`
- `armorabilityicontemp`
- `armoricontemp`
- `armorelementtemp`
- `armorelementamounttemp`
- `value`

The element fields allow equipment to modify elemental mitigation directly, beyond raw AT/DF/MAG.

---

## Consumable Item Families

Chapter 4 `scr_iteminfo` defines the largest item catalog, with cases:

- `0..39`
- `60..63`

That split matters. The item namespace is not one dense block forever. Later-special items can live in higher id bands.

### Baseline healing items

Representative direct-heal items:

- `1 (Darker Candy)` -> `"Heals#120HP"`
- `5 (BrokenCake)` -> `"Heals#20HP"`
- `8 (Darkburger)` -> `"Heals#70HP"`
- `9 (LancerCookie)` -> `"Heals#50HP"`
- `10 (GigaSalad)` -> `"Heals#4HP"`
- `16 (CD Bagel)` -> `"Heals#80 HP"`
- `24 (ButJuice)` -> `"Heals#100HP"`
- `34 (TVDinner)` -> `"Heals#100HP"`
- `37 (TVSlop)` -> `"Heals#80HP"`
- `39 (DeluxeDinner)` -> `"Heals#140HP"`
- `61 (Rhapsotea)` -> `"Heals#115HP"`
- `62 (Scarlixir)` -> `"Heals#160HP"`

### Revive items

- `2 (ReviveMint)` -> `"Heal#Downed#Ally"`
- `30 (ReviveDust)` -> `"Revives#team#25%"`
- `31 (ReviveBrite)` -> `"Revives#team#100%"`

These are important because revive behavior is not handled only by a generic heal amount. The description and downstream item-spell behavior identify them as revive-capable branches.

### Team-wide healing

- `6 (Top Cake)` -> `"Heals#team#160HP"`
- `7 (Spincake)` -> team heal amount varies by chapter
- `11 (ClubsSandwich)` -> `"Heals#team#70HP"`
- `25 (SpagettiCode)` -> `"Heals#team#30HP"`
- `38 (ExecBuffet)` -> `"Heals#team#100HP"`

### TP utility items

- `27 (TensionBit)` -> `"Raises#TP#32%"`
- `28 (TensionGem)` -> `"Raises#TP#50%"`
- `29 (TensionMax)` -> `"Raises#TP#Max"`

These items are structurally important because they route into battle-resource management rather than HP restoration.

### Character-dependent healing

- `12 (HeartsDonut)` -> `"Healing#varies"`
- `13 (ChocDiamond)` -> `"Healing#varies"`
- `26 (JavaCookie)` -> `"Healing#varies"`
- `60 (AncientSweet)` -> `"Kris only#+400"`
- `63 (BitterTear)` -> `"Heals#All HP"`

The item definition script intentionally leaves these as abstract descriptions because the actual effect depends on later runtime logic that knows the consumer.

### Non-standard items

- `3 (Glowshard)` -> sell-only item, value `200 + (global.chapter * 100)`
- `4 (Manual)` -> not battle-usable, target field still used by menu flow
- `17 (Mannequin)` -> `"Useless"`
- `32 (S.POISON)` -> hurts the target party member
- `33 (DogDollar)` -> value `floor(200 / global.chapter)`
- `35 (Pipis)` -> `"Does#nothing"`

These cases matter because they prove the item system is not a pure positive-effect consumable list. It also stores shop objects, joke items, harmful items, and utility/menu-only entries.

---

## Chapter-Sensitive Item Cases

Some item definitions are explicitly chapter-aware.

### `7 (Spincake)`

Chapter 4 still preserves an earlier cross-chapter behavior branch:

```gml
var healamount = (global.chapter == 1) ? 80 : 140;
if (global.chapter == 3)
{
    healamount = 150;
}
if (global.chapter >= 4)
{
    healamount = 160;
}
itemnameb = stringsetloc("Spincake", ...);
itemdescb = stringsetsubloc("Heals#team#~1HP", string(healamount), ...);
```

Same item id, different stats by chapter:

- Chapter 1: 80 HP to team
- Chapter 2: 140 HP to team
- Chapter 3: 150 HP to team
- Chapter 4+: 160 HP to team

### `3 (Glowshard)`

Its value scales with chapter:

```gml
Value = 200 + (global.chapter * 100);
```

### `33 (DogDollar)`

Its value scales inversely:

```gml
Value = floor(200 / global.chapter);
```

These are good reminders that item definitions in DELTARUNE are not always static lookup rows.

---

## Replaceable Items

Chapter 4 explicitly marks `22 (DD-Burger)` as:

```gml
Replaceable = 8;
```

`replaceable` supports consumables that downgrade or convert into another item id after use.

---

## Localization Strategy In Item Data

Most later item names/descriptions are built with `stringsetloc(...)`, for example:

```gml
Itemnameb = stringsetloc("Darkburger", "scr_iteminfo_slash_scr_iteminfo_gml_65_0");
itemdescb = stringsetloc("Heals#70HP", "scr_iteminfo_slash_scr_iteminfo_gml_66_0");
```

but some entries still use `scr_text(...)`, such as ids `18..21`.

That mixed model is important:

- later chapters prefer inline English plus localization key
- some special/joke/debug-like entries still route through older text-id access

Modders should not assume one universal string-loading path even inside a single definition script.

---

## Weapon Catalog Structure

Chapter 4 `scr_weaponinfo` defines weapon ids:

- `0..26`
- `50..54`

Again, later-game or special equipment uses higher id bands rather than extending the early block forever.

Representative baseline weapons include:

- `1 (Wood Blade)` -> Kris-only starter blade
- `2 (Mane Ax)` -> early Susie-side weapon family entry
- `3 (Red Scarf)` -> Ralsei starter scarf
- `4 (EverybodyWeapon)` -> broad all-party novelty weapon
- `5 (Spookysword)` -> ability `"Spookiness UP"`
- `6 (Brave Ax)` -> ability `"Guts Up"`
- `7 (Devilsknife)` -> ability `"Buster TP DOWN"`
- `8 (Trefoil)` -> ability `"Money Earned UP"`
- `10 (DaintyScarf)` -> ability `"Fluffiness UP"`
- `11 (TwistedSwd)` -> stronger Kris weapon

The weapon definitions are also full of contextual reaction lines. For example `Wood Blade` stores:

```gml
Wmessage2temp = stringsetloc("What's this!? A CHOPSTICK?", ...);
if (global.plot < 30 && global.chapter == 1)
{
    wmessage2tempt = stringsetloc("... You have a SWORD!?", ...);
}
wmessage3temp = stringsetloc("That's yours, Kris...", ...);
wmessage4temp = stringsetloc("(It has bite marks...)", ...);
```

Equipment scripts are partly stat tables and partly menu-dialogue databases.

---

## Weapon Character Restrictions

The weapon scripts use `weaponchar1temp` through `weaponchar4temp` to express who may equip the weapon.

Representative patterns:

- `weaponchar1temp = 1` on `Wood Blade` marks it as Kris equipment
- `weaponchar2temp = 1` on `Brave Ax` marks it as Susie equipment
- `weaponchar3temp = 1` on `Red Scarf` marks it as Ralsei equipment
- all four set to `1` on `EverybodyWeapon` makes it universally legal in the later-party model

Because later chapters may involve four party positions, the fourth restriction field is a real runtime expansion over the earlier three-member baseline.

---

## Weapon Stat Fields Beyond AT

Weapons also carry:

- defense modifiers
- magic modifiers
- bolt-count modifiers
- graze amount modifiers
- graze size modifiers
- ability icon metadata

Even when many entries leave some fields at zero, the structure is broad enough to support more than “attack power.”

---

## Armor Catalog Structure

Chapter 4 `scr_armorinfo` defines armor ids:

- `0..27`
- `50..54`

Representative pieces include:

- `1 (Amber Card)` -> `+1 DF`
- `2 (Dice Brace)` -> `+2 DF`
- `3 (Pink Ribbon)` -> `+1 DF`, graze-size bonus, ability `GrazeArea`
- `4 (White Ribbon)` -> `+2 DF`, ability `Cuteness`
- `5 (IronShackle)` -> `+1 AT`, `+2 DF`
- `6 (MouseToken)` -> `+2 MAG`, plus elemental reduction fields
- `7 (Jevilstail)` -> `+2 AT`, `+2 DF`, `+2 MAG`
- `8 (Silver Card)` -> `+2 DF`, ability `"$ +5%"`
- `9 (TwinRibbon)` -> `+3 DF`, graze-size bonus

Armor overlaps with:

- direct stat growth
- graze manipulation
- money modifiers
- elemental mitigation

---

## Armor Element Fields

`MouseToken` is a good example of armor-side elemental data:

```gml
Armorelementtemp = 7;
armorelementamounttemp = 0.5;
```

The armor definition passes two values into the damage layer:

- which element id it modifies
- by what amount

Elemental resistance is attached to equipment metadata, not only used in battle scripts.

---

## Chapter-Sensitive Equipment Text

The equipment scripts also branch on chapter for dialogue flavor. For example `Pink Ribbon` and `White Ribbon` change character reaction lines in Chapter 2:

```gml
if (global.chapter == 2)
{
    amessage2temp = stringsetloc("I said NO! C'mon already!", ...);
    amessage3temp = stringsetloc("It's nice dressing up...", ...);
}
```

Stat blocks and equip/examine text can branch independently by chapter.

---

## Relationship To Battle Item Use

Consumables do not directly implement their final effect in `scr_iteminfo`. The definition script provides:

- target mode
- usability
- descriptive metadata

The actual battle effect is usually routed through the spell/item-spell runtime, where item ids are converted into consumable actions. That is why this page should be read together with [Spells & Abilities](spells-abilities.md).

---

## Chapter Differences

## Chapter 1

- much smaller item/equipment catalogs
- three-party assumption dominates
- fewer element and utility fields matter in practice

## Chapter 2
---

## Key Items — `scr_keyiteminfo`

Key items are stored in `global.keyitem[0..11]`. The info script returns name, description, and usability.

### Complete Key Item Catalog (Chapter 4)

| ID | Name | Usable | Description |
|---:|---|:---:|---|
| 0 | *(empty)* | — | — |
| 1 | Cell Phone | ✓ | Can be used to make calls |
| 2 | Egg | ✓ | Not too important, not too unimportant |
| 3 | BrokenCake | — | Seethes with power; a smith could fix it |
| 4 | Broken Key A | — | Top part of a key |
| 5 | Door Key | — | Key to a mysterious cell |
| 6 | Broken Key B | — | Middle part of a key |
| 7 | Broken Key C | — | Bottom part of a key |
| 8 | Lancer | ✓ | Dynamic description changes with `global.plot` progression (20+ unique lines) |
| 9 | Rouxls Kaard | — | Description changes at plot ≥ 200 |
| 10 | EmptyDisk | — | A data disk from a strange machine |
| 11 | LoadedDisk | — | A strange disk with something stored |
| 12 | KeyGen | — | Shady program that opens certain doors |
| 13 | ShadowCrystal | ✓ | Count display: "You have collected [n]" |
| 14 | Starwalker | — | "The original (Starwalker)" |
| 15 | PureCrystal | — | The shadow purified by the cat |
| 16 | OddController | — | Gamepad with ugly pink and yellow buttons |
| 17 | BackstagePass | — | Show to Ramb to access backstage |
| 18 | TripTicket | — | Ticket showing a map with a red X |
| 19 | LancerCon | — | Lancer's controller (count tracked in `global.flag[1099]`) |
| 30 | SheetMusic | ✓ | Music Susie attempted to transcribe |
| 31 | ClaimbClaws | — | Tiny claws for climbing walls |

### Key Item Scripts

| Script | Purpose |
|---|---|
| `scr_keyiteminfo(id)` | Returns name, description, usability for id |
| `scr_keyiteminfo_all()` | Bulk-caches all key item metadata |
| `scr_keyitemget(id)` | Adds key item to first empty slot |
| `scr_keyitemremove(id)` | Removes key item from inventory |
| `scr_keyitemcheck(id)` | Returns true if key item is held |
| `scr_keyitemshift()` | Compacts key item array (removes gaps) |

### Lancer Dynamic Description

Key item 8 (Lancer) has 14+ unique description strings that change based on `global.plot`:

- Progresses through commentary about current events (plot 20, 55, 60, 65, 66, 70, 75, 79, 85, 90, 99, 200)
- Room-specific overrides in `room_dw_castle_restaurant`, `room_cc_lancer`, `room_dw_ralsei_castle_2f`
- Side-B phase checks for sleeping/stone states

---

## Light World Item System

Light World items use a separate script family:

| Script | Purpose |
|---|---|
| `scr_litemname(id)` | Returns Light World item name |
| `scr_litemdesc(id)` | Returns Light World item description |
| `scr_litemuseb(id)` | Returns use-in-battle flag |
| `scr_litemget(id)` | Adds Light World item to inventory |
| `scr_litemremove(id)` | Removes Light World item |
| `scr_litemcheck(id)` | Checks if Light World item is held |
| `scr_litemshift()` | Compacts Light World item array |

Light World items are stored in `global.litem[0..11]` with names cached in `global.litemname[]`.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a new Dark World consumable | Add a case in `scr_iteminfo` and `scr_spell` (200+ range) |
| Add a new weapon | Add a case in `scr_weaponinfo` |
| Add a new armor | Add a case in `scr_armorinfo` |
| Add a new key item | Add a case in `scr_keyiteminfo` |
| Change item stats | Edit the temp variable assignments in the info script |
| Change elemental resistance | Edit `armorelementtemp` and `armorelementamounttemp` in `scr_armorinfo` |
| Change item descriptions | Edit the string in the matching case |
| Change Light World items | Edit `scr_litemname` / `scr_litemuseb` |

---

## Relationship To Other Pages

- [Spells & Abilities](spells-abilities.md) explains the battle-side execution of consumable item effects
- [Damage System](damage-system.md) explains how equipment stats and elemental modifiers feed into battle calculations
- [Save & Load System](save-load-system.md) explains how inventory and equipment ids are serialized
- [Fusion System](fusion-system.md) explains equipment crafting recipes