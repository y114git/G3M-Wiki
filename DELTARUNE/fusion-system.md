# Fusion System

Equipment fusion allows combining two items or equipment pieces into a stronger
result. The system is defined in `scr_fusion_info` and executed by
`scr_fusion_queue`.

---

## Fusion Recipes

The same six definition cases exist in Chapters 2, 3, and 4:

The former wrapped summary table was removed. The records below list runtime
values.

The queue caller proves the execution API, not that every definition case is
enumerated by a production menu. Recipe status below therefore remains
definition-only or uncertain unless an exact UI enumeration, gate, placed
controller, and ingredient acquisition chain were all joined. In particular,
case 6 must not be described as production-reachable from the generic queue call
alone.

---

## `scr_fusion_info` Output Fields

The former wrapped summary table was removed. The records below list runtime
values.

---

## Cross-Type Fusion

Recipes can mix types:

- Recipe 5 combines an **armor** with a consumable **item** to produce **armor**
- Recipe 6 combines a **weapon** with a **key item** to produce a **weapon**

The fusion system is not limited to same-type ingredients.

---

## Modding Reference

The former wrapped summary table was removed. The records below list runtime
values.

An exact new recipe requires both metadata and queue support:

```gml
// scr_fusion_info
case NEW_RECIPE_CASE:
    ingredient[0] = 8; ingredienttype[0] = "item";
    ingredient[1] = 27; ingredienttype[1] = "item";
    result = NEW_ITEM_ID; resulttype = "item";
    resultdesc = "Heal and tension";
    break;
```

Increase the fusion menu's recipe count and ensure `scr_fusion_queue` recognizes
the same four type strings. Test missing ingredients, duplicate ingredients,
full destination inventory, queue completion, cancel, save, and reload.

## Complete recipe catalog

### Recipe ch2-case-1

- inputs: `item:8 x1, item:8 x1`
- output: `item:22`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch2-case-2

- inputs: `armor:1 x1, armor:1 x1`
- output: `armor:8`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch2-case-3

- inputs: `armor:3 x1, armor:4 x1`
- output: `armor:9`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch2-case-4

- inputs: `armor:10 x1, armor:5 x1`
- output: `armor:13`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch2-case-5

- inputs: `armor:12 x1, item:27 x1`
- output: `armor:15`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch2-case-6

- inputs: `weapon:13 x1, key:15 x1`
- output: `weapon:11`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch3-case-1

- inputs: `item:8 x1, item:8 x1`
- output: `item:22`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch3-case-2

- inputs: `armor:1 x1, armor:1 x1`
- output: `armor:8`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch3-case-3

- inputs: `armor:3 x1, armor:4 x1`
- output: `armor:9`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch3-case-4

- inputs: `armor:10 x1, armor:5 x1`
- output: `armor:13`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch3-case-5

- inputs: `armor:12 x1, item:27 x1`
- output: `armor:15`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch3-case-6

- inputs: `weapon:13 x1, key:15 x1`
- output: `weapon:11`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch4-case-1

- inputs: `item:8 x1, item:8 x1`
- output: `item:22`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch4-case-2

- inputs: `armor:1 x1, armor:1 x1`
- output: `armor:8`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch4-case-3

- inputs: `armor:3 x1, armor:4 x1`
- output: `armor:9`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch4-case-4

- inputs: `armor:10 x1, armor:5 x1`
- output: `armor:13`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch4-case-5

- inputs: `armor:12 x1, item:27 x1`
- output: `armor:15`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch4-case-6

- inputs: `weapon:13 x1, key:15 x1`
- output: `weapon:11`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-1

- inputs: `item:8 x1, item:8 x1`
- output: `item:22`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-2

- inputs: `armor:1 x1, armor:1 x1`
- output: `armor:8`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-3

- inputs: `armor:3 x1, armor:4 x1`
- output: `armor:9`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-4

- inputs: `armor:10 x1, armor:5 x1`
- output: `armor:13`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-5

- inputs: `armor:12 x1, item:27 x1`
- output: `armor:15`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-6

- inputs: `weapon:13 x1, key:15 x1`
- output: `weapon:11`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-7

- inputs: `weapon:51 x1, armor:53 x1`
- output: `armor:30`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-8

- inputs: `armor:27 x1, armor:20 x1`
- output: `armor:31`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-9

- inputs: `item:37 x1, item:37 x1`
- output: `item:34`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-10

- inputs: `item:34 x1, item:34 x1`
- output: `item:39`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-11

- inputs: `item:62 x1, armor:52 x1`
- output: `item:40`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-12

- inputs: `item:62 x1, armor:51 x1`
- output: `item:29`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`

### Recipe ch5-case-13

- inputs: `armor:54 x1, item:33 x1`
- output: `armor:32`
- cost: `0`
- conditions: `none in recipe case`
- reachability: `definition-only`
- reachability basis: `no literal UI enumeration; generic queue dispatch`
  `excluded`
- caller count: `1`
