# Fusion System

Equipment fusion allows combining two items or equipment pieces into a stronger result. The system is defined in `scr_fusion_info` and executed by `scr_fusion_queue`.

---

## Fusion Recipes

The same 6 recipes exist identically in Chapters 2, 3, and 4:

| Recipe | Ingredient A | Type | Ingredient B | Type | Result | Type | Description |
|---:|---|---|---|---|---|---|---|
| 1 | Item 8 | item | Item 8 | item | Item 22 | item | Heal 60 HPx2 |
| 2 | Armor 1 | armor | Armor 1 | armor | Armor 8 | armor | $ Gained +5% |
| 3 | Armor 3 | armor | Armor 4 | armor | Armor 9 | armor | Graze Area+ |
| 4 | Armor 10 | armor | Armor 5 | armor | Armor 13 | armor | Attack+ |
| 5 | Armor 12 | armor | Item 27 | item | Armor 15 | armor | Graze TP+ |
| 6 | Weapon 13 | weapon | Key Item 15 | key | Weapon 11 | weapon | Trance |

---

## `scr_fusion_info` Output Fields

| Field | Type | Purpose |
|---|---|---|
| `ingredient[0]` | int | First ingredient id |
| `ingredienttype[0]` | string | First ingredient type: `"item"`, `"armor"`, `"weapon"`, `"key"` |
| `ingredient[1]` | int | Second ingredient id |
| `ingredienttype[1]` | string | Second ingredient type |
| `result` | int | Result item id |
| `resulttype` | string | Result item type |
| `resultdesc` | string | Display description of result |

---

## Cross-Type Fusion

Recipes can mix types:

- Recipe 5 combines an **armor** with a consumable **item** to produce **armor**
- Recipe 6 combines a **weapon** with a **key item** to produce a **weapon**

The fusion system is not limited to same-type ingredients.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Add a fusion recipe | Add a `case` block in `scr_fusion_info` |
| Change fusion result | Edit the `result`/`resulttype` in the matching case |
| Configure fusion UI | Inspect the Castle Town shop objects that call `scr_fusion_info` |