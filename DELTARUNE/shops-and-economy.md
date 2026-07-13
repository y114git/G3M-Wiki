# Shops and Economy

Shop stock is object-owned data. There is no single master shop table: each shop
Create event fills parallel arrays of merchandise IDs, types, buy prices, sell
behavior, dialogue, and sold-out flags. Consequently an item definition's
`value` is not proof that a shop sells it, and a shop price need not equal that
value.

## Economy data flow

The shared menu reads a stock slot, dispatches its type to `scr_iteminfo`,
`scr_weaponinfo`, `scr_armorinfo`, or key-item helpers, checks inventory/storage
space, subtracts Dark Dollars, and inserts the numeric ID. Selling uses the
definition value or the shop's branch. Glowshard is chapter-scaled at
`200 + 100 * global.chapter`; DogDollar uses `floor(200 / global.chapter)`.
Those expressions must remain runtime expressions if chapter-dependent behavior
is desired.

The shipped Create events prove these shop families across Chapters 1–4:

The former wrapped summary table was removed. The records below list runtime
values.

Exact stock must therefore be reviewed from every `obj_shop*_Create_0` and other
shop-family Create event in the target payload, together with room placement and
plot gates. Searching only `scr_shopmenu` misses object-specific arrays.

## Inventory and storage rules

Dark-world consumables, weapons, armor, and key items use separate 12-slot
arrays. The `*_get` helpers insert into the first zero slot; `*_remove` clears a
matching slot; `*_shift` compacts holes. Equipment records are character-indexed
and do not occupy inventory while equipped. Storage uses parallel type/ID slots
and the same zero-sentinel convention; transfer code must check both source and
destination capacity before clearing the source. Light-world items use the
separate `global.litem[0..11]` family.

The save process writes IDs, not copied metadata. Definition changes appear on
reload, while ID renumbering silently transforms old possessions into different
objects.

## Adding a shop entry safely

Do not reserve a fixed ID from this page. First scan every target chapter's
`scr_iteminfo`, `scr_itemuse`, acquisition calls, shop stock, fusion outputs,
save migration, and imported chapter data. Select an ID only if it is absent
from every one of those surfaces in every supported payload.

For an existing implementation, copy the exact assignment pattern from the
target shop Create event. Chapter 1 `obj_shop1_Create_0` uses `item`,
`itemtype`, `buyvalue`, and `itemtotal`; it does not use the generic array names
shown in older versions of this page:

```gml
// After proving NEW_ITEM_ID is unused in every supported payload:
var slot = itemtotal;
item[slot] = NEW_ITEM_ID;
itemtype[slot] = "item";
buyvalue[slot] = 320;
itemtotal += 1;
```

Add the same selected ID to that chapter's definition and runtime-use switches.
Never derive a use-case ID by adding an offset. Test full inventory, full
storage, insufficient funds, purchase, sale, save/reload, and chapter transfer.

## Related pages

- [Items and Equipment](items-equipment.md)
- [Fusion System](fusion-system.md)
- [Save and Load System](save-load-system.md)

## Shop stock and reachability catalog

### Shop record 0001

- chapter: `1`
- slot: `0`
- definition: `item:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `40`
- price status: `exact-assignment`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `3`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0002

- chapter: `1`
- slot: `1`
- definition: `item:8`
- stock status: `purchasable-or-branch-stock`
- price expression: `70`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0003

- chapter: `1`
- slot: `2`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0004

- chapter: `1`
- slot: `3`
- definition: `weapon:5`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0005

- chapter: `1`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0006

- chapter: `1`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0007

- chapter: `1`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0008

- chapter: `1`
- slot: `0`
- definition: `item:15`
- stock status: `purchasable-or-branch-stock`
- price expression: `50`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0009

- chapter: `1`
- slot: `1`
- definition: `weapon:6`
- stock status: `purchasable-or-branch-stock`
- price expression: `150`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0010

- chapter: `1`
- slot: `2`
- definition: `weapon:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0011

- chapter: `1`
- slot: `3`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0012

- chapter: `1`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0013

- chapter: `1`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0014

- chapter: `1`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop2`

### Shop record 0015

- chapter: `2`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-assignment`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `5`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0016

- chapter: `2`
- slot: `1`
- definition: `item:8`
- stock status: `purchasable-or-branch-stock`
- price expression: `70`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0017

- chapter: `2`
- slot: `2`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0018

- chapter: `2`
- slot: `3`
- definition: `weapon:5`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0019

- chapter: `2`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0020

- chapter: `2`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0021

- chapter: `2`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0022

- chapter: `2`
- slot: `0`
- definition: `item:15`
- stock status: `purchasable-or-branch-stock`
- price expression: `50`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0023

- chapter: `2`
- slot: `1`
- definition: `weapon:6`
- stock status: `purchasable-or-branch-stock`
- price expression: `150`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0024

- chapter: `2`
- slot: `2`
- definition: `weapon:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0025

- chapter: `2`
- slot: `3`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0026

- chapter: `2`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0027

- chapter: `2`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0028

- chapter: `2`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0029

- chapter: `2`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0030

- chapter: `2`
- slot: `1`
- definition: `armor:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0031

- chapter: `2`
- slot: `2`
- definition: `weapon:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0032

- chapter: `2`
- slot: `3`
- definition: `weapon:17`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0033

- chapter: `2`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0034

- chapter: `2`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0035

- chapter: `2`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Shop record 0036

- chapter: `2`
- slot: `0`
- definition: `item:24`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0037

- chapter: `2`
- slot: `1`
- definition: `item:25`
- stock status: `purchasable-or-branch-stock`
- price expression: `180`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0038

- chapter: `2`
- slot: `2`
- definition: `armor:12`
- stock status: `purchasable-or-branch-stock`
- price expression: `300`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0039

- chapter: `2`
- slot: `3`
- definition: `armor:22`
- stock status: `purchasable-or-branch-stock`
- price expression: `1000`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0040

- chapter: `2`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0041

- chapter: `2`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0042

- chapter: `2`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Shop record 0043

- chapter: `2`
- slot: `0`
- definition: `key:12`
- stock status: `purchasable-or-branch-stock`
- price expression: `unresolved: runtime definition value expression`
- price status: `unresolved-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0044

- chapter: `2`
- slot: `1`
- definition: `item:32`
- stock status: `purchasable-or-branch-stock`
- price expression: `110`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 31; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0045

- chapter: `2`
- slot: `2`
- definition: `weapon:20`
- stock status: `purchasable-or-branch-stock`
- price expression: `2`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0046

- chapter: `2`
- slot: `3`
- definition: `armor:20`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0047

- chapter: `2`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 37; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0048

- chapter: `2`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 49; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0049

- chapter: `2`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 50; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0050

- chapter: `2`
- slot: `0`
- definition: `None:None`
- stock status: `purchasable-or-branch-stock`
- price expression: `floor(random(60))`
- price status: `exact-assignment`
- currency: `global.gold`
- currency status: `exact-transaction`
- gate: `line 175; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0051

- chapter: `2`
- slot: `1`
- definition: `None:None`
- stock status: `purchasable-or-branch-stock`
- price expression: `50 + floor(random(100))`
- price status: `exact-assignment`
- currency: `global.gold`
- currency status: `exact-transaction`
- gate: `line 49; unconditional in entry`
- branch assignments: `1`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0052

- chapter: `2`
- slot: `2`
- definition: `None:None`
- stock status: `purchasable-or-branch-stock`
- price expression: `50 + floor(random(100))`
- price status: `exact-assignment`
- currency: `global.gold`
- currency status: `exact-transaction`
- gate: `line 204; if (menu == 0)`
- branch assignments: `1`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0053

- chapter: `2`
- slot: `3`
- definition: `None:None`
- stock status: `purchasable-or-branch-stock`
- price expression: `50 + floor(random(100))`
- price status: `exact-assignment`
- currency: `global.gold`
- currency status: `exact-transaction`
- gate: `line 205; if (menu == 0)`
- branch assignments: `1`
- reachability: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Shop record 0054

- chapter: `3`
- slot: `constructor@2`
- definition: `item:34`
- stock status: `purchasable-or-branch-stock`
- price expression: `60`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0055

- chapter: `3`
- slot: `constructor@2`
- definition: `item:39`
- stock status: `purchasable-or-branch-stock`
- price expression: `120`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0056

- chapter: `3`
- slot: `constructor@2`
- definition: `armor:24`
- stock status: `purchasable-or-branch-stock`
- price expression: `60`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0057

- chapter: `3`
- slot: `constructor@2`
- definition: `armor:25`
- stock status: `purchasable-or-branch-stock`
- price expression: `111`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0058

- chapter: `3`
- slot: `constructor@2`
- definition: `item:37`
- stock status: `purchasable-or-branch-stock`
- price expression: `20`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0059

- chapter: `3`
- slot: `constructor@2`
- definition: `weapon:24`
- stock status: `purchasable-or-branch-stock`
- price expression: `80`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `700`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0060

- chapter: `3`
- slot: `constructor@2`
- definition: `weapon:23`
- stock status: `purchasable-or-branch-stock`
- price expression: `80`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `710`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0061

- chapter: `3`
- slot: `constructor@2`
- definition: `weapon:25`
- stock status: `purchasable-or-branch-stock`
- price expression: `80`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `720`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0062

- chapter: `3`
- slot: `constructor@2`
- definition: `item:37`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `200`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0063

- chapter: `3`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-assignment`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `5`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0064

- chapter: `3`
- slot: `1`
- definition: `item:8`
- stock status: `purchasable-or-branch-stock`
- price expression: `70`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0065

- chapter: `3`
- slot: `2`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0066

- chapter: `3`
- slot: `3`
- definition: `weapon:5`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0067

- chapter: `3`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0068

- chapter: `3`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0069

- chapter: `3`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0070

- chapter: `3`
- slot: `0`
- definition: `item:15`
- stock status: `purchasable-or-branch-stock`
- price expression: `50`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0071

- chapter: `3`
- slot: `1`
- definition: `weapon:6`
- stock status: `purchasable-or-branch-stock`
- price expression: `150`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0072

- chapter: `3`
- slot: `2`
- definition: `weapon:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0073

- chapter: `3`
- slot: `3`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0074

- chapter: `3`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0075

- chapter: `3`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0076

- chapter: `3`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0077

- chapter: `3`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0078

- chapter: `3`
- slot: `1`
- definition: `armor:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0079

- chapter: `3`
- slot: `2`
- definition: `weapon:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0080

- chapter: `3`
- slot: `3`
- definition: `weapon:17`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0081

- chapter: `3`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0082

- chapter: `3`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0083

- chapter: `3`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0084

- chapter: `4`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-assignment`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `5`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0085

- chapter: `4`
- slot: `1`
- definition: `item:8`
- stock status: `purchasable-or-branch-stock`
- price expression: `70`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0086

- chapter: `4`
- slot: `2`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0087

- chapter: `4`
- slot: `3`
- definition: `weapon:5`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0088

- chapter: `4`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0089

- chapter: `4`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0090

- chapter: `4`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0091

- chapter: `4`
- slot: `0`
- definition: `item:15`
- stock status: `purchasable-or-branch-stock`
- price expression: `50`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0092

- chapter: `4`
- slot: `1`
- definition: `weapon:6`
- stock status: `purchasable-or-branch-stock`
- price expression: `150`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0093

- chapter: `4`
- slot: `2`
- definition: `weapon:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0094

- chapter: `4`
- slot: `3`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0095

- chapter: `4`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0096

- chapter: `4`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0097

- chapter: `4`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0098

- chapter: `4`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0099

- chapter: `4`
- slot: `1`
- definition: `armor:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0100

- chapter: `4`
- slot: `2`
- definition: `weapon:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0101

- chapter: `4`
- slot: `3`
- definition: `weapon:17`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0102

- chapter: `4`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0103

- chapter: `4`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0104

- chapter: `4`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0105

- chapter: `5`
- slot: `constructor@4`
- definition: `item:67`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `[1777, 1]`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0106

- chapter: `5`
- slot: `constructor@4`
- definition: `item:68`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `[1778, 1]`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0107

- chapter: `5`
- slot: `constructor@4`
- definition: `item:69`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `[1779, 1]`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0108

- chapter: `5`
- slot: `constructor@4`
- definition: `item:70`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `[1800, 1]`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0109

- chapter: `5`
- slot: `constructor@14`
- definition: `item:67`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0110

- chapter: `5`
- slot: `constructor@14`
- definition: `item:68`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0111

- chapter: `5`
- slot: `constructor@14`
- definition: `item:69`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0112

- chapter: `5`
- slot: `constructor@14`
- definition: `item:70`
- stock status: `purchasable-or-branch-stock`
- price expression: `30`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `production-uncertain`
- rooms: `none joined`

### Shop record 0113

- chapter: `5`
- slot: `0`
- definition: `item:41`
- stock status: `purchasable-or-branch-stock`
- price expression: `333`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; if (snd_is_playing(global.currentsong[1]))`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0114

- chapter: `5`
- slot: `1`
- definition: `weapon:30`
- stock status: `purchasable-or-branch-stock`
- price expression: `500`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 32; if (snd_is_playing(global.currentsong`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0115

- chapter: `5`
- slot: `2`
- definition: `armor:34`
- stock status: `purchasable-or-branch-stock`
- price expression: `1500`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 41; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0116

- chapter: `5`
- slot: `3`
- definition: `key:32`
- stock status: `purchasable-or-branch-stock`
- price expression: `unresolved: runtime definition value expression`
- price status: `unresolved-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 42; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0117

- chapter: `5`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 43; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0118

- chapter: `5`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 54; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0119

- chapter: `5`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 55; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_ch5`

### Shop record 0120

- chapter: `5`
- slot: `constructor@2`
- definition: `item:34`
- stock status: `purchasable-or-branch-stock`
- price expression: `60`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0121

- chapter: `5`
- slot: `constructor@2`
- definition: `item:39`
- stock status: `purchasable-or-branch-stock`
- price expression: `120`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0122

- chapter: `5`
- slot: `constructor@2`
- definition: `armor:24`
- stock status: `purchasable-or-branch-stock`
- price expression: `60`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0123

- chapter: `5`
- slot: `constructor@2`
- definition: `armor:25`
- stock status: `purchasable-or-branch-stock`
- price expression: `111`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0124

- chapter: `5`
- slot: `constructor@54`
- definition: `item:43`
- stock status: `purchasable-or-branch-stock`
- price expression: `prices[0]`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0125

- chapter: `5`
- slot: `constructor@54`
- definition: `item:41`
- stock status: `purchasable-or-branch-stock`
- price expression: `prices[1]`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0126

- chapter: `5`
- slot: `constructor@54`
- definition: `item:42`
- stock status: `purchasable-or-branch-stock`
- price expression: `prices[2]`
- price status: `exact-constructor-expression`
- currency: `point_value (vending transaction)`
- currency status: `exact-constructor-contract`
- gate: `—`
- branch assignments: `1`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0127

- chapter: `5`
- slot: `0`
- definition: `item:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-assignment`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 38; unconditional in entry`
- branch assignments: `3`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0128

- chapter: `5`
- slot: `1`
- definition: `item:8`
- stock status: `purchasable-or-branch-stock`
- price expression: `70`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 39; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0129

- chapter: `5`
- slot: `2`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 43; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0130

- chapter: `5`
- slot: `3`
- definition: `weapon:5`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 44; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0131

- chapter: `5`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 45; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0132

- chapter: `5`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 56; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0133

- chapter: `5`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 57; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop1`

### Shop record 0134

- chapter: `5`
- slot: `0`
- definition: `item:15`
- stock status: `purchasable-or-branch-stock`
- price expression: `50`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0135

- chapter: `5`
- slot: `1`
- definition: `weapon:6`
- stock status: `purchasable-or-branch-stock`
- price expression: `150`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0136

- chapter: `5`
- slot: `2`
- definition: `weapon:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0137

- chapter: `5`
- slot: `3`
- definition: `armor:1`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0138

- chapter: `5`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0139

- chapter: `5`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0140

- chapter: `5`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `unplaced-or-uncertain`
- rooms: `none joined`

### Shop record 0141

- chapter: `5`
- slot: `0`
- definition: `item:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `100`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 29; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0142

- chapter: `5`
- slot: `1`
- definition: `armor:10`
- stock status: `purchasable-or-branch-stock`
- price expression: `200`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 30; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0143

- chapter: `5`
- slot: `2`
- definition: `weapon:16`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 34; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0144

- chapter: `5`
- slot: `3`
- definition: `weapon:17`
- stock status: `purchasable-or-branch-stock`
- price expression: `250`
- price status: `exact-runtime-definition-expression`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 35; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0145

- chapter: `5`
- slot: `4`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 36; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0146

- chapter: `5`
- slot: `5`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 47; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`

### Shop record 0147

- chapter: `5`
- slot: `6`
- definition: `item:0`
- stock status: `empty-sentinel-slot`
- price expression: `not applicable`
- price status: `empty-slot`
- currency: `global.gold (shop convention; transaction caller unresolved)`
- currency status: `shop-convention-unresolved-caller`
- gate: `line 48; unconditional in entry`
- branch assignments: `2`
- reachability: `production-subsystem`
- rooms: `room_shop_music`
