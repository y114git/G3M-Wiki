# Items and equipment definition catalog

listed from the shipped `scr_*info` switch cases. Each record preserves the
exact case-local assignments. Status is deliberately conservative: a definition
is not called obtainable without a literal acquisition site.

## Chapter 1

### Chapter 1 armor 0

- Chapter: 1
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`

### Chapter 1 armor 1

- Chapter: 1
- Name: Amber Card
- Effect: A thin square charm that sticks#to you, increasing defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 1 armor 2

- Chapter: 1
- Name: Dice Brace
- Effect: A bracelet made out of various#symbol-inscribed cubes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 1 armor 3

- Chapter: 1
- Name: Pink Ribbon
- Effect: A cute hair ribbon that increases#the range bullets increase tension.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=20`
- Stat/value: `value=100`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`

### Chapter 1 armor 4

- Chapter: 1
- Name: White Ribbon
- Effect: A crinkly hair ribbon that slightly#increases your defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 armor 5

- Chapter: 1
- Name: IronShackle
- Effect: Shackle that ironically increases#your attack and defense.
- Status: literal acquisition call found
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 1 armor 6

- Chapter: 1
- Name: MouseToken
- Effect: A golden coin with a once-powerful mousewizard engraved on it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=120`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 1 armor 7

- Chapter: 1
- Name: Jevilstail
- Effect: A J-shaped tail that gives you devilenergy.
- Status: literal acquisition call found
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 1 item 0

- Chapter: 1
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 item 1

- Chapter: 1
- Name: Dark Candy
- Effect: Heals#40HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=25`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 2

- Chapter: 1
- Name: ReviveMint
- Effect: Heal#Downed#Ally
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=400`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 3

- Chapter: 1
- Name: Glowshard
- Effect: Sell#at#shops
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=200`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 1 item 4

- Chapter: 1
- Name: Manual
- Effect: Read#out of#battle
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=1`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 1 item 5

- Chapter: 1
- Name: BrokenCake
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 6

- Chapter: 1
- Name: Top Cake
- Effect: Heals#team#160HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=150`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 7

- Chapter: 1
- Name: Spincake
- Effect: Heals#team#80HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 8

- Chapter: 1
- Name: Darkburger
- Effect: Heals#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 9

- Chapter: 1
- Name: LancerCookie
- Effect: Heals#50HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 10

- Chapter: 1
- Name: GigaSalad
- Effect: Heals#4HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 11

- Chapter: 1
- Name: ClubsSandwich
- Effect: Heals#team#30HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 12

- Chapter: 1
- Name: HeartsDonut
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 13

- Chapter: 1
- Name: ChocDiamond
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 14

- Chapter: 1
- Name: Favwich
- Effect: Heals#ALL HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 item 15

- Chapter: 1
- Name: RouxlsRoux
- Effect: Heals#50 HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=50`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 1 key 0

- Chapter: 1
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 key 1

- Chapter: 1
- Name: Cell Phone
- Effect: It can be used to make calls.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 1 key 2

- Chapter: 1
- Name: Egg
- Effect: Not too important, not too unimportant.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 1 key 3

- Chapter: 1
- Name: BrokenCake
- Effect: Though broken, it seethes with power.#A master smith could fix it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 key 4

- Chapter: 1
- Name: Broken Key A
- Effect: It's the top part of a key.#A smith could fix all three parts.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 key 5

- Chapter: 1
- Name: Door Key
- Effect: The key to a mysterious cell.#Something feels strange about it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 key 6

- Chapter: 1
- Name: Broken Key B
- Effect: It's the middle part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 key 7

- Chapter: 1
- Name: Broken Key C
- Effect: It's the bottom part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 key 13

- Chapter: 1
- Name: ShadowCrystal
- Effect: A sharp shadow moves like water in the hand.#You have collected 1.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 1 weapon 0

- Chapter: 1
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=0`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 1 weapon 1

- Chapter: 1
- Name: Wood Blade
- Effect: A wooden practice blade with a carbon-#reinforced core.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 1 weapon 2

- Chapter: 1
- Name: Mane Ax
- Effect: Beginner's ax forged from the#mane of a dragon whelp.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=80`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 1 weapon 3

- Chapter: 1
- Name: Red Scarf
- Effect: A basic scarf made of lightly#magical fiber.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 1 weapon 4

- Chapter: 1
- Name: EverybodyWeapon
- Effect: It felt right for everyone.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=6`
- Stat/value: `weaponmagtemp=8`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=1`

### Chapter 1 weapon 5

- Chapter: 1
- Name: Spookysword
- Effect: A black-and-orange sword with a bat hilt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 1 weapon 6

- Chapter: 1
- Name: Brave Ax
- Effect: A glossy ax from a block warrior.#Suitable for heroes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 1 weapon 7

- Chapter: 1
- Name: Devilsknife
- Effect: Skull-emblazoned scythe-ax.#Reduces Rudebuster's cost by 10
- Status: literal acquisition call found
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 1 weapon 8

- Chapter: 1
- Name: Trefoil
- Effect: Mossy rapier with a clover emblem.#Increases $ found by 5%.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 1 weapon 9

- Chapter: 1
- Name: Ragger
- Effect: A rugged scarf that cuts enemies like a dagger.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 1 weapon 10

- Chapter: 1
- Name: DaintyScarf
- Effect: Delicate scarf that increases healing#power but has no attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

## Chapter 2

### Chapter 2 armor 0

- Chapter: 2
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 1

- Chapter: 2
- Name: Amber Card
- Effect: A thin square charm that sticks#to you, increasing defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 2

- Chapter: 2
- Name: Dice Brace
- Effect: A bracelet made out of various#symbol-inscribed cubes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 3

- Chapter: 2
- Name: Pink Ribbon
- Effect: A cute hair ribbon that increases#the range bullets increase tension.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 armor 4

- Chapter: 2
- Name: White Ribbon
- Effect: A crinkly hair ribbon that slightly#increases your defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 armor 5

- Chapter: 2
- Name: IronShackle
- Effect: Shackle that ironically increases#your attack and defense.
- Status: literal acquisition call found
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 6

- Chapter: 2
- Name: MouseToken
- Effect: A golden coin with a once-powerful mousewizard engraved on it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=120`
- Stat/value: `armorelementtemp=7`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 7

- Chapter: 2
- Name: Jevilstail
- Effect: A J-shaped tail that gives you devilenergy.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 8

- Chapter: 2
- Name: Silver Card
- Effect: A square charm that increases#dropped money by 5%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 9

- Chapter: 2
- Name: TwinRibbon
- Effect: Two ribbons. You'll have to put#your hair into pigtails.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=20`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 10

- Chapter: 2
- Name: GlowWrist
- Effect: A tough bracelet made of green wires,#and studded with sharp glowing
  lights.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 11

- Chapter: 2
- Name: ChainMail
- Effect: Chain-armor. Send it to 10 others#or it'll lose its defensive rating
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 12

- Chapter: 2
- Name: B.ShotBowtie
- Effect: A handsome bowtie. Looks like the brand#name has been cut off.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 13

- Chapter: 2
- Name: SpikeBand
- Effect: A black wristband covered in spikes.#Has the tendency to get stuck to
  itself.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 14

- Chapter: 2
- Name: Silver Watch
- Effect: Grazing bullets affects#the turn length by 10% more
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 15

- Chapter: 2
- Name: TensionBow
- Effect: Gain 10% more tension from#grazing bullets
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 16

- Chapter: 2
- Name: Mannequin
- Effect: It's a mannequin with the clothes#permanently attached. Useless
- Status: literal acquisition call found
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.35`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 2 armor 17

- Chapter: 2
- Name: DarkGoldBand
- Effect: A black metal with a golden shine.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=(global.chapter * 200) + ((global.chapter - 1) * 220)`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 2 armor 18

- Chapter: 2
- Name: SkyMantle
- Effect: A cape that shimmers fluorescently.#Protects against Elec and Holy
  attacks.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1`
- Stat/value: `armorelementtemp=1`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 19

- Chapter: 2
- Name: SpikeShackle
- Effect: (empty)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=3`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 20

- Chapter: 2
- Name: FrayedBowtie
- Effect: An old bowtie. It seems to have#lost much of its defensive value.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.15`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 armor 21

- Chapter: 2
- Name: Dealmaker
- Effect: Fashionable pink and yellow glasses.#Greatly increase $ gained,
  and...?
- Status: literal acquisition call found
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=5`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.4`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 2 armor 22

- Chapter: 2
- Name: RoyalPin
- Effect: A brooch engraved with Queen's face.#Careful of the sharp part.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 2 item 0

- Chapter: 2
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 item 1

- Chapter: 2
- Name: Dark Candy
- Effect: Heals#40HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=25`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 2

- Chapter: 2
- Name: ReviveMint
- Effect: Heal#Downed#Ally
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=400`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 3

- Chapter: 2
- Name: Glowshard
- Effect: Sell#at#shops
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=200 + (global.chapter * 100)`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 2 item 4

- Chapter: 2
- Name: Manual
- Effect: Read#out of#battle
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=1`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 2 item 5

- Chapter: 2
- Name: BrokenCake
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 6

- Chapter: 2
- Name: Top Cake
- Effect: Heals#team#160HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=150`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 7

- Chapter: 2
- Name: Spincake
- Effect: Heals#team#~1HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 8

- Chapter: 2
- Name: Darkburger
- Effect: Heals#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 9

- Chapter: 2
- Name: LancerCookie
- Effect: Heals#50HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 10

- Chapter: 2
- Name: GigaSalad
- Effect: Heals#4HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 11

- Chapter: 2
- Name: ClubsSandwich
- Effect: Heals#team#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 12

- Chapter: 2
- Name: HeartsDonut
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 13

- Chapter: 2
- Name: ChocDiamond
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 14

- Chapter: 2
- Name: Favwich
- Effect: Heals#ALL HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 15

- Chapter: 2
- Name: RouxlsRoux
- Effect: Heals#50 HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=50`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 16

- Chapter: 2
- Name: CD Bagel
- Effect: Heals#80 HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 17

- Chapter: 2
- Name: Mannequin
- Effect: Useless
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=0`
- Stat/value: `value=300`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 2 item 18

- Chapter: 2
- Name: Kris Tea
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 19

- Chapter: 2
- Name: Noelle Tea
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 20

- Chapter: 2
- Name: Ralsei Tea
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 21

- Chapter: 2
- Name: Susie Tea
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 22

- Chapter: 2
- Name: DD-Burger
- Effect: Heals#60HP 2x
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 23

- Chapter: 2
- Name: LightCandy
- Effect: Heals#120HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 24

- Chapter: 2
- Name: ButJuice
- Effect: Heals#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 25

- Chapter: 2
- Name: SpagettiCode
- Effect: Heals#team#30HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=180`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 26

- Chapter: 2
- Name: JavaCookie
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=160`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 27

- Chapter: 2
- Name: TensionBit
- Effect: Raises#TP#32%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 28

- Chapter: 2
- Name: TensionGem
- Effect: Raises#TP#50%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=300`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 29

- Chapter: 2
- Name: TensionMax
- Effect: Raises#TP#Max
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=1000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 30

- Chapter: 2
- Name: ReviveDust
- Effect: Revives#team#25%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 31

- Chapter: 2
- Name: ReviveBrite
- Effect: Revives#team#100%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=4000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 32

- Chapter: 2
- Name: S.POISON
- Effect: Hurts#party#member
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 2 item 33

- Chapter: 2
- Name: DogDollar
- Effect: Not#so#useful
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=floor(200 / global.chapter)`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 2 key 0

- Chapter: 2
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 1

- Chapter: 2
- Name: Cell Phone
- Effect: It can be used to make calls.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 2 key 2

- Chapter: 2
- Name: Egg
- Effect: Not too important, not too unimportant.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 2 key 3

- Chapter: 2
- Name: BrokenCake
- Effect: Though broken, it seethes with power.#A master smith could fix it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 4

- Chapter: 2
- Name: Broken Key A
- Effect: It's the top part of a key.#A smith could fix all three parts.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 5

- Chapter: 2
- Name: Door Key
- Effect: The key to a mysterious cell.#Something feels strange about it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 6

- Chapter: 2
- Name: Broken Key B
- Effect: It's the middle part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 7

- Chapter: 2
- Name: Broken Key C
- Effect: It's the bottom part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 8

- Chapter: 2
- Name: not assigned
- Effect: Hohoho! ROUXLS jumped out of your#pocket! How dadcrobatic! (Lesser)
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 9

- Chapter: 2
- Name: Rouxls Kaard
- Effect: Oh, milord! Tis I, your humblest servante,#righte here where I never
  lefteth!
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 10

- Chapter: 2
- Name: EmptyDisk
- Effect: A data disk from a strange machine.#Didn't someone want this?
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 11

- Chapter: 2
- Name: LoadedDisk
- Effect: A strange disk. You can feel it#smiling in your hand.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 12

- Chapter: 2
- Name: KeyGen
- Effect: A shady-looking program that can#open certain doors.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 13

- Chapter: 2
- Name: not assigned
- Effect: not assigned
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 14

- Chapter: 2
- Name: Starwalker
- Effect: The original # (Starwalker)
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 key 15

- Chapter: 2
- Name: PureCrystal
- Effect: The shadow purified by the cat
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 weapon 0

- Chapter: 2
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=0`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 1

- Chapter: 2
- Name: Wood Blade
- Effect: A wooden practice blade with a carbon-#reinforced core.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 weapon 2

- Chapter: 2
- Name: Mane Ax
- Effect: Beginner's ax forged from the#mane of a dragon whelp.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=80`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 2 weapon 3

- Chapter: 2
- Name: Red Scarf
- Effect: A basic scarf made of lightly#magical fiber.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 2 weapon 4

- Chapter: 2
- Name: EverybodyWeapon
- Effect: It felt right for everyone.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=6`
- Stat/value: `weaponmagtemp=8`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=1`

### Chapter 2 weapon 5

- Chapter: 2
- Name: Spookysword
- Effect: A black-and-orange sword with a bat hilt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 2 weapon 6

- Chapter: 2
- Name: Brave Ax
- Effect: A glossy ax from a block warrior.#Suitable for heroes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 2 weapon 7

- Chapter: 2
- Name: Devilsknife
- Effect: Skull-emblazoned scythe-ax.#Reduces Rudebuster's cost by 10
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 2 weapon 8

- Chapter: 2
- Name: Trefoil
- Effect: Mossy rapier with a clover emblem.#Increases $ found by 5%.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 2 weapon 9

- Chapter: 2
- Name: Ragger
- Effect: A rugged scarf that cuts enemies like a dagger.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 2 weapon 10

- Chapter: 2
- Name: DaintyScarf
- Effect: Delicate scarf that increases healing#power but has no attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 2 weapon 11

- Chapter: 2
- Name: TwistedSwd
- Effect: A strange blade
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 2 weapon 12

- Chapter: 2
- Name: SnowRing
- Effect: A ring with the emblem of the#snowflake
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 2 weapon 13

- Chapter: 2
- Name: ThornRing
- Effect: Wearer takes damage from pain#Reduces the TP cost of ice spells
- Status: literal acquisition call found
- Stat/value: `weaponattemp=14`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=12`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 2 weapon 14

- Chapter: 2
- Name: BounceBlade
- Effect: A pink saber with a rubber blade.#Weak, but increases defence.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 15

- Chapter: 2
- Name: CheerScarf
- Effect: A scarf with colorful you-can-do-it#imagery. Gains more TP from
  criticals.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=1`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 16

- Chapter: 2
- Name: MechaSaber
- Effect: The blade extends when you press the hilt.#CHA-CHK!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 17

- Chapter: 2
- Name: AutoAxe
- Effect: Make sure to charge it by#plugging it into the wall.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 18

- Chapter: 2
- Name: FiberScarf
- Effect: A scarf made of soft microfiber.#Balances attack and magic.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 19

- Chapter: 2
- Name: Ragger2
- Effect: A sharp and scratchy scarf.#Worse healing, better attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 20

- Chapter: 2
- Name: BrokenSwd
- Effect: A rejected sword cut into 2 pieces.#Not even you can equip this...
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 21

- Chapter: 2
- Name: PuppetScarf
- Effect: A scarf made of strange strings.#For those that abandon healing.
- Status: literal acquisition call found
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-6`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 2 weapon 22

- Chapter: 2
- Name: FreezeRing
- Effect: A ring with a snowglobe on it.#... is that someone inside?
- Status: literal acquisition call found
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

## Chapter 3

### Chapter 3 armor 0

- Chapter: 3
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 1

- Chapter: 3
- Name: Amber Card
- Effect: A thin square charm that sticks#to you, increasing defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 2

- Chapter: 3
- Name: Dice Brace
- Effect: A bracelet made out of various#symbol-inscribed cubes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 3

- Chapter: 3
- Name: Pink Ribbon
- Effect: A cute hair ribbon. Increases the range#at which bullets raise
  tension.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 armor 4

- Chapter: 3
- Name: White Ribbon
- Effect: A crinkly hair ribbon that slightly#increases your defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 armor 5

- Chapter: 3
- Name: IronShackle
- Effect: Shackle that ironically increases#your attack and defense.
- Status: literal acquisition call found
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 6

- Chapter: 3
- Name: MouseToken
- Effect: A golden coin with a once-powerful mouse#wizard engraved on it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=120`
- Stat/value: `armorelementtemp=7`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 7

- Chapter: 3
- Name: Jevilstail
- Effect: A J-shaped tail that gives you devilenergy.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 8

- Chapter: 3
- Name: Silver Card
- Effect: A square charm that increases#dropped money by 5%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 9

- Chapter: 3
- Name: TwinRibbon
- Effect: Two ribbons. You'll have to put#your hair into pigtails.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=20`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 10

- Chapter: 3
- Name: GlowWrist
- Effect: A tough bracelet made of green wires,#and studded with sharp glowing
  lights.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 11

- Chapter: 3
- Name: ChainMail
- Effect: Chain-armor. Send it to 10 others#or it'll lose its defensive rating
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 12

- Chapter: 3
- Name: B.ShotBowtie
- Effect: A handsome bowtie. Looks like the brand#name has been cut off.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 13

- Chapter: 3
- Name: SpikeBand
- Effect: A black wristband covered in spikes.#Has the tendency to get stuck to
  itself.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 14

- Chapter: 3
- Name: Silver Watch
- Effect: Grazing bullets affects#the turn length by 10% more
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 15

- Chapter: 3
- Name: TensionBow
- Effect: Gain 10% more tension from#grazing bullets
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 16

- Chapter: 3
- Name: Mannequin
- Effect: It's a mannequin with the clothes#permanently attached. Useless
- Status: literal acquisition call found
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.35`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 3 armor 17

- Chapter: 3
- Name: DarkGoldBand
- Effect: A black metal with a golden shine.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=(global.chapter * 200) + ((global.chapter - 1) * 220)`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 3 armor 18

- Chapter: 3
- Name: SkyMantle
- Effect: A cape that shimmers fluorescently.#Protects against Elec and Holy
  attacks.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1`
- Stat/value: `armorelementtemp=1`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 19

- Chapter: 3
- Name: SpikeShackle
- Effect: (empty)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=3`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 20

- Chapter: 3
- Name: FrayedBowtie
- Effect: An old bowtie. It seems to have#lost much of its defensive value.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.15`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 21

- Chapter: 3
- Name: Dealmaker
- Effect: Fashionable pink and yellow glasses.#Greatly increase $ gained,
  and...?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=5`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.4`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 3 armor 22

- Chapter: 3
- Name: RoyalPin
- Effect: A brooch engraved with Queen's face.#Careful of the sharp part.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 23

- Chapter: 3
- Name: ShadowMantle
- Effect: Shadows slip off like water.#Greatly protects against Dark and Star
  attacks.
- Status: literal acquisition call found
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=global.chapter`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=5`
- Stat/value: `armorelementamounttemp=0.66`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=0`

### Chapter 3 armor 24

- Chapter: 3
- Name: LodeStone
- Effect: not assigned
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 armor 25

- Chapter: 3
- Name: GingerGuard
- Effect: A steel bangle tempered by extreme flame.#Its shape is humanoid in
  nature.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=862`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 26

- Chapter: 3
- Name: BlueRibbon
- Effect: A blue cheer bow. When the user uses a#healing move, it recovers
  slightly more HP.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 armor 27

- Chapter: 3
- Name: TennaTie
- Effect: A giant, heavy-duty, bullet-proof tie.#How to even wear it...?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=-2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=600`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 3 item 0

- Chapter: 3
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 item 1

- Chapter: 3
- Name: Dark Candy
- Effect: Heals#40HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=25`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 2

- Chapter: 3
- Name: ReviveMint
- Effect: Heal#Downed#Ally
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=400`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 3

- Chapter: 3
- Name: Glowshard
- Effect: Sell#at#shops
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=200 + (global.chapter * 100)`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 3 item 4

- Chapter: 3
- Name: Manual
- Effect: Read#out of#battle
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=1`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 3 item 5

- Chapter: 3
- Name: BrokenCake
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 6

- Chapter: 3
- Name: Top Cake
- Effect: Heals#team#160HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=150`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 7

- Chapter: 3
- Name: not assigned
- Effect: not assigned
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 item 8

- Chapter: 3
- Name: Darkburger
- Effect: Heals#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 9

- Chapter: 3
- Name: LancerCookie
- Effect: Heals#50HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 10

- Chapter: 3
- Name: GigaSalad
- Effect: Heals#4HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 11

- Chapter: 3
- Name: ClubsSandwich
- Effect: Heals#team#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 12

- Chapter: 3
- Name: HeartsDonut
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 13

- Chapter: 3
- Name: ChocDiamond
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 14

- Chapter: 3
- Name: Favwich
- Effect: Heals#ALL HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 15

- Chapter: 3
- Name: RouxlsRoux
- Effect: Heals#50 HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=50`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 16

- Chapter: 3
- Name: CD Bagel
- Effect: Heals#80 HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 17

- Chapter: 3
- Name: Mannequin
- Effect: Useless
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=0`
- Stat/value: `value=300`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 3 item 18

- Chapter: 3
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 19

- Chapter: 3
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 20

- Chapter: 3
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 21

- Chapter: 3
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 22

- Chapter: 3
- Name: DD-Burger
- Effect: Heals#60HP 2x
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 23

- Chapter: 3
- Name: LightCandy
- Effect: Heals#120HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 24

- Chapter: 3
- Name: ButJuice
- Effect: Heals#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 25

- Chapter: 3
- Name: SpagettiCode
- Effect: Heals#team#30HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=180`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 26

- Chapter: 3
- Name: JavaCookie
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=160`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 27

- Chapter: 3
- Name: TensionBit
- Effect: Raises#TP#32%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 28

- Chapter: 3
- Name: TensionGem
- Effect: Raises#TP#50%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=300`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 29

- Chapter: 3
- Name: TensionMax
- Effect: Raises#TP#Max
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=1000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 30

- Chapter: 3
- Name: ReviveDust
- Effect: Revives#team#25%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 31

- Chapter: 3
- Name: ReviveBrite
- Effect: Revives#team#100%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=4000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 32

- Chapter: 3
- Name: S.POISON
- Effect: Hurts#party#member
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 33

- Chapter: 3
- Name: DogDollar
- Effect: Not#so#useful
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=0`
- Stat/value: `value=floor(200 / global.chapter)`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 3 item 34

- Chapter: 3
- Name: TVDinner
- Effect: Heals#100HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 35

- Chapter: 3
- Name: Pipis
- Effect: Does#nothing
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=0`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 36

- Chapter: 3
- Name: FlatSoda
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 37

- Chapter: 3
- Name: TVSlop
- Effect: Heals#80HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=180`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 38

- Chapter: 3
- Name: ExecBuffet
- Effect: Heals#team#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 item 39

- Chapter: 3
- Name: DeluxeDinner
- Effect: Heals#140HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 3 key 0

- Chapter: 3
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 1

- Chapter: 3
- Name: Cell Phone
- Effect: It can be used to make calls.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 3 key 2

- Chapter: 3
- Name: Egg
- Effect: Not too important, not too unimportant.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 3 key 3

- Chapter: 3
- Name: BrokenCake
- Effect: Though broken, it seethes with power.#A master smith could fix it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 4

- Chapter: 3
- Name: Broken Key A
- Effect: It's the top part of a key.#A smith could fix all three parts.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 5

- Chapter: 3
- Name: Door Key
- Effect: The key to a mysterious cell.#Something feels strange about it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 6

- Chapter: 3
- Name: Broken Key B
- Effect: It's the middle part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 7

- Chapter: 3
- Name: Broken Key C
- Effect: It's the bottom part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 8

- Chapter: 3
- Name: not assigned
- Effect: Hohoho! ROUXLS jumped out of your#pocket! How dadcrobatic! (Lesser)
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 9

- Chapter: 3
- Name: Rouxls Kaard
- Effect: Oh, milord! Tis I, your humblest servante,#righte here where I never
  lefteth!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 10

- Chapter: 3
- Name: EmptyDisk
- Effect: A data disk from a strange machine.#Didn't someone want this?
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 11

- Chapter: 3
- Name: LoadedDisk
- Effect: A strange disk. You can feel it#smiling in your hand.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 12

- Chapter: 3
- Name: KeyGen
- Effect: A shady-looking program that can#open certain doors.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 13

- Chapter: 3
- Name: not assigned
- Effect: not assigned
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 14

- Chapter: 3
- Name: Starwalker
- Effect: The original # (Starwalker)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 15

- Chapter: 3
- Name: PureCrystal
- Effect: The shadow purified by the cat
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 16

- Chapter: 3
- Name: OddController
- Effect: A gamepad no one wanted to use.#The buttons are an ugly pink and
  yellow.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 17

- Chapter: 3
- Name: BackstagePass
- Effect: A pass for big shots allowed backstage.#Show it to Ramb in front of
  the door.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 18

- Chapter: 3
- Name: TripTicket
- Effect: A ticket to nowhere. It shows a map#pointing to the left of a red X...
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 key 19

- Chapter: 3
- Name: LancerConX~1
- Effect: Lancer's controllers. They're covered in dirt.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 weapon 0

- Chapter: 3
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=0`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 1

- Chapter: 3
- Name: Wood Blade
- Effect: A wooden practice blade with a carbon-#reinforced core.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 weapon 2

- Chapter: 3
- Name: Mane Ax
- Effect: Beginner's ax forged from the#mane of a dragon whelp.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=80`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 3 weapon 3

- Chapter: 3
- Name: Red Scarf
- Effect: A basic scarf made of lightly#magical fiber.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 3 weapon 4

- Chapter: 3
- Name: EverybodyWeapon
- Effect: It felt right for everyone.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=6`
- Stat/value: `weaponmagtemp=8`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=1`

### Chapter 3 weapon 5

- Chapter: 3
- Name: Spookysword
- Effect: A black-and-orange sword with a bat hilt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 3 weapon 6

- Chapter: 3
- Name: Brave Ax
- Effect: A glossy ax from a block warrior.#Suitable for heroes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 3 weapon 7

- Chapter: 3
- Name: Devilsknife
- Effect: Skull-emblazoned scythe-ax.#Reduces Rudebuster's cost by 10
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 3 weapon 8

- Chapter: 3
- Name: Trefoil
- Effect: Mossy rapier with a clover emblem.#Increases $ found by 5%.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 3 weapon 9

- Chapter: 3
- Name: Ragger
- Effect: A rugged scarf that cuts enemies like a dagger.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 3 weapon 10

- Chapter: 3
- Name: DaintyScarf
- Effect: Delicate scarf that increases healing#power but has no attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 3 weapon 11

- Chapter: 3
- Name: TwistedSwd
- Effect: A strange blade
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 3 weapon 12

- Chapter: 3
- Name: SnowRing
- Effect: A ring with the emblem of the#snowflake
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 3 weapon 13

- Chapter: 3
- Name: ThornRing
- Effect: Wearer takes damage from pain#Reduces the TP cost of ice spells
- Status: literal acquisition call found
- Stat/value: `weaponattemp=14`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=12`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 3 weapon 14

- Chapter: 3
- Name: BounceBlade
- Effect: A pink saber with a rubber blade.#Weak, but increases defence.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 15

- Chapter: 3
- Name: CheerScarf
- Effect: A scarf with colorful you-can-do-it#imagery. Gains more TP from
  criticals.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=1`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 16

- Chapter: 3
- Name: MechaSaber
- Effect: The blade extends when you press the hilt.#CHA-CHK!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 17

- Chapter: 3
- Name: AutoAxe
- Effect: Make sure to charge it by#plugging it into the wall.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 18

- Chapter: 3
- Name: FiberScarf
- Effect: A scarf made of soft microfiber.#Balances attack and magic.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=3`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 19

- Chapter: 3
- Name: Ragger2
- Effect: A sharp and scratchy scarf.#Worse healing, better attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 20

- Chapter: 3
- Name: BrokenSwd
- Effect: A rejected sword cut into 2 pieces.#Not even you can equip this...
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 21

- Chapter: 3
- Name: PuppetScarf
- Effect: A scarf made of strange strings.#For those that abandon healing.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-6`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 22

- Chapter: 3
- Name: FreezeRing
- Effect: A ring with a snowglobe on it.#... is that someone inside?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 3 weapon 23

- Chapter: 3
- Name: Saber10
- Effect: A saber made of 10 cactus needles.#Fortunately, can deal more than 10
  damage.
- Status: literal acquisition call found
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=610`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 24

- Chapter: 3
- Name: ToxicAxe
- Effect: An axe used to clear wastelands#in a fetid swamp. Not poison, but
  gross.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=600`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 25

- Chapter: 3
- Name: FlexScarf
- Effect: A scarf that is warm and fuzzy, but with#a metal core that lets it
  keep its shape.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=620`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 3 weapon 26

- Chapter: 3
- Name: BlackShard
- Effect: A dagger-like shard of the Black Knife.#Strikes the weakness of
  dark-element enemies.
- Status: literal acquisition call found
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

## Chapter 4

### Chapter 4 armor 0

- Chapter: 4
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 1

- Chapter: 4
- Name: Amber Card
- Effect: A thin square charm that sticks#to you, increasing defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 2

- Chapter: 4
- Name: Dice Brace
- Effect: A bracelet made out of various#symbol-inscribed cubes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 3

- Chapter: 4
- Name: Pink Ribbon
- Effect: A cute hair ribbon that increases#the range bullets increase tension.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 armor 4

- Chapter: 4
- Name: White Ribbon
- Effect: A crinkly hair ribbon that slightly#increases your defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 armor 5

- Chapter: 4
- Name: IronShackle
- Effect: Shackle that ironically increases#your attack and defense.
- Status: literal acquisition call found
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 6

- Chapter: 4
- Name: MouseToken
- Effect: A golden coin with a once-powerful mousewizard engraved on it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=120`
- Stat/value: `armorelementtemp=7`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 7

- Chapter: 4
- Name: Jevilstail
- Effect: A J-shaped tail that gives you devilenergy.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 8

- Chapter: 4
- Name: Silver Card
- Effect: A square charm that increases#dropped money by 5%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 9

- Chapter: 4
- Name: TwinRibbon
- Effect: Two ribbons. You'll have to put#your hair into pigtails.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=20`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 10

- Chapter: 4
- Name: GlowWrist
- Effect: A tough bracelet made of green wires,#and studded with sharp glowing
  lights.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 11

- Chapter: 4
- Name: ChainMail
- Effect: Chain-armor. Send it to 10 others#or it'll lose its defensive rating
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 12

- Chapter: 4
- Name: B.ShotBowtie
- Effect: A handsome bowtie. Looks like the brand#name has been cut off.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 13

- Chapter: 4
- Name: SpikeBand
- Effect: A black wristband covered in spikes.#Has the tendency to get stuck to
  itself.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 14

- Chapter: 4
- Name: Silver Watch
- Effect: Grazing bullets affects#the turn length by 10% more
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 15

- Chapter: 4
- Name: TensionBow
- Effect: Gain 10% more tension from#grazing bullets
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 16

- Chapter: 4
- Name: Mannequin
- Effect: It's a mannequin with the clothes#permanently attached. Useless
- Status: literal acquisition call found
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.35`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 4 armor 17

- Chapter: 4
- Name: DarkGoldBand
- Effect: A black metal with a golden shine.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=(global.chapter * 200) + ((global.chapter - 1) * 220)`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 4 armor 18

- Chapter: 4
- Name: SkyMantle
- Effect: A cape that shimmers fluorescently.#Protects against Elec and Holy
  attacks.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1`
- Stat/value: `armorelementtemp=1`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 19

- Chapter: 4
- Name: SpikeShackle
- Effect: (empty)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=3`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 20

- Chapter: 4
- Name: FrayedBowtie
- Effect: An old bowtie. It seems to have#lost much of its defensive value.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.15`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 21

- Chapter: 4
- Name: Dealmaker
- Effect: Fashionable pink and yellow glasses.#Greatly increase $ gained,
  and...?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=5`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.4`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 4 armor 22

- Chapter: 4
- Name: RoyalPin
- Effect: A brooch engraved with Queen's face.#Careful of the sharp part.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 23

- Chapter: 4
- Name: ShadowMantle
- Effect: Shadows slip off like water.#Greatly protects against Dark and Star
  attacks.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=global.chapter`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=5`
- Stat/value: `armorelementamounttemp=0.66`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=0`

### Chapter 4 armor 24

- Chapter: 4
- Name: LodeStone
- Effect: not assigned
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 armor 25

- Chapter: 4
- Name: GingerGuard
- Effect: A steel bangle tempered by extreme flame.#Its shape is humanoid in
  nature.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=862`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 26

- Chapter: 4
- Name: BlueRibbon
- Effect: A blue cheer bow. When the user uses a#healing move, it recovers
  slightly more HP.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 27

- Chapter: 4
- Name: TennaTie
- Effect: A giant, heavy-duty, bullet-proof tie.#How to even wear it...?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=-2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=600`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 50

- Chapter: 4
- Name: Waferguard
- Effect: Although it looks brittle, it contains a magical#energy that blunts
  damage on impact. +4DF
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=900`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 51

- Chapter: 4
- Name: MysticBand
- Effect: A silver armlet stained with amber.#Increases magic only. MAG +4
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=4`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 52

- Chapter: 4
- Name: PowerBand
- Effect: A silver armlet stained with red essence.#Increases strength only. ATK
  +4
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=4`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 53

- Chapter: 4
- Name: PrincessRBN
- Effect: Elegant lace ribbon with gloves,#delicate enough to see through. +4
  DEF +2 ATK
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 4 armor 54

- Chapter: 4
- Name: GoldWidow
- Effect: A spider made of gold. It gathers coins#into it, reducing $ gained.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=5000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=0`

### Chapter 4 item 0

- Chapter: 4
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 item 1

- Chapter: 4
- Name: Darker Candy
- Effect: Heals#120HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=120`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 2

- Chapter: 4
- Name: ReviveMint
- Effect: Heal#Downed#Ally
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=400`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 3

- Chapter: 4
- Name: Glowshard
- Effect: Sell#at#shops
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=200 + (global.chapter * 100)`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 4 item 4

- Chapter: 4
- Name: Manual
- Effect: Read#out of#battle
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=1`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 4 item 5

- Chapter: 4
- Name: BrokenCake
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 6

- Chapter: 4
- Name: Top Cake
- Effect: Heals#team#160HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=150`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 7

- Chapter: 4
- Name: not assigned
- Effect: not assigned
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 item 8

- Chapter: 4
- Name: Darkburger
- Effect: Heals#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 9

- Chapter: 4
- Name: LancerCookie
- Effect: Heals#50HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 10

- Chapter: 4
- Name: GigaSalad
- Effect: Heals#4HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 11

- Chapter: 4
- Name: ClubsSandwich
- Effect: Heals#team#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 12

- Chapter: 4
- Name: HeartsDonut
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 13

- Chapter: 4
- Name: ChocDiamond
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 14

- Chapter: 4
- Name: Favwich
- Effect: Heals#ALL HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 15

- Chapter: 4
- Name: RouxlsRoux
- Effect: Heals#50 HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=50`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 16

- Chapter: 4
- Name: CD Bagel
- Effect: Heals#80 HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 17

- Chapter: 4
- Name: Mannequin
- Effect: Useless
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=0`
- Stat/value: `value=300`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 4 item 18

- Chapter: 4
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 19

- Chapter: 4
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 20

- Chapter: 4
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 21

- Chapter: 4
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 22

- Chapter: 4
- Name: DD-Burger
- Effect: Heals#60HP 2x
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 23

- Chapter: 4
- Name: LightCandy
- Effect: Heals#120HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 24

- Chapter: 4
- Name: ButJuice
- Effect: Heals#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 25

- Chapter: 4
- Name: SpagettiCode
- Effect: Heals#team#30HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=180`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 26

- Chapter: 4
- Name: JavaCookie
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=160`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 27

- Chapter: 4
- Name: TensionBit
- Effect: Raises#TP#32%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 28

- Chapter: 4
- Name: TensionGem
- Effect: Raises#TP#50%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=300`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 29

- Chapter: 4
- Name: TensionMax
- Effect: Raises#TP#Max
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=1000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 30

- Chapter: 4
- Name: ReviveDust
- Effect: Revives#team#25%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 31

- Chapter: 4
- Name: ReviveBrite
- Effect: Revives#team#100%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=4000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 32

- Chapter: 4
- Name: S.POISON
- Effect: Hurts#party#member
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 33

- Chapter: 4
- Name: DogDollar
- Effect: Not#so#useful
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=floor(200 / global.chapter)`
- Stat/value: `usable=0`
- Equip-owner assignments: none

### Chapter 4 item 34

- Chapter: 4
- Name: TVDinner
- Effect: Heals#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 35

- Chapter: 4
- Name: Pipis
- Effect: Does#nothing
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=0`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 36

- Chapter: 4
- Name: FlatSoda
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 37

- Chapter: 4
- Name: TVSlop
- Effect: Heals#80HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 38

- Chapter: 4
- Name: ExecBuffet
- Effect: Heals#team#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 39

- Chapter: 4
- Name: DeluxeDinner
- Effect: Heals#140HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 60

- Chapter: 4
- Name: AncientSweet
- Effect: Kris only#+400
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=1000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 61

- Chapter: 4
- Name: Rhapsotea
- Effect: Heals#115HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=250`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 62

- Chapter: 4
- Name: Scarlixir
- Effect: Heals#160HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=450`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 item 63

- Chapter: 4
- Name: BitterTear
- Effect: Heals#All HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=0`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 4 key 0

- Chapter: 4
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 1

- Chapter: 4
- Name: Cell Phone
- Effect: It can be used to make calls.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 4 key 2

- Chapter: 4
- Name: Egg
- Effect: Not too important, not too unimportant.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 4 key 3

- Chapter: 4
- Name: BrokenCake
- Effect: Though broken, it seethes with power.#A master smith could fix it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 4

- Chapter: 4
- Name: Broken Key A
- Effect: It's the top part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 5

- Chapter: 4
- Name: Door Key
- Effect: The key to a mysterious cell.#Something feels strange about it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 6

- Chapter: 4
- Name: Broken Key B
- Effect: It's the middle part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 7

- Chapter: 4
- Name: Broken Key C
- Effect: It's the bottom part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 8

- Chapter: 4
- Name: not assigned
- Effect: Hohoho! ROUXLS jumped out of your#pocket! How dadcrobatic! (Lesser)
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 9

- Chapter: 4
- Name: Rouxls Kaard
- Effect: Oh, milord! Tis I, your humblest servante,#righte here where I never
  lefteth!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 10

- Chapter: 4
- Name: EmptyDisk
- Effect: A data disk from a strange machine.#Didn't someone want this?
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 11

- Chapter: 4
- Name: LoadedDisk
- Effect: A strange disk. You can feel it#smiling in your hand.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 12

- Chapter: 4
- Name: KeyGen
- Effect: A shady-looking program that can#open certain doors.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 13

- Chapter: 4
- Name: ShadowCrystal
- Effect: A sharp shadow moves like water in the hand.#You have collected [~1].
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 4 key 14

- Chapter: 4
- Name: Starwalker
- Effect: The original # (Starwalker)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 15

- Chapter: 4
- Name: PureCrystal
- Effect: The shadow purified by the cat
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 16

- Chapter: 4
- Name: OddController
- Effect: A gamepad no one wanted to use.#The buttons are an ugly pink and
  yellow.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 17

- Chapter: 4
- Name: BackstagePass
- Effect: A pass for big shots allowed backstage.#Show it to Ramb in front of
  the door.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 18

- Chapter: 4
- Name: TripTicket
- Effect: A ticket to nowhere. It shows a map#pointing to the left of a red X...
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 19

- Chapter: 4
- Name: LancerConX~1
- Effect: Lancer's controllers. They're covered in dirt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 key 30

- Chapter: 4
- Name: SheetMusic
- Effect: Music that Susie attempted to transcribe.#USE it to read it.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 4 key 31

- Chapter: 4
- Name: ClaimbClaws
- Effect: Claws so small they conveniently can't#be seen. Use them to climb up
  obvious walls.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 weapon 0

- Chapter: 4
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=0`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 1

- Chapter: 4
- Name: Wood Blade
- Effect: A wooden practice blade with a carbon-#reinforced core.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 weapon 2

- Chapter: 4
- Name: Mane Ax
- Effect: Beginner's ax forged from the#mane of a dragon whelp.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=80`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 4 weapon 3

- Chapter: 4
- Name: Red Scarf
- Effect: A basic scarf made of lightly#magical fiber.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 4 weapon 4

- Chapter: 4
- Name: EverybodyWeapon
- Effect: It felt right for everyone.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=6`
- Stat/value: `weaponmagtemp=8`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=1`

### Chapter 4 weapon 5

- Chapter: 4
- Name: Spookysword
- Effect: A black-and-orange sword with a bat hilt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 4 weapon 6

- Chapter: 4
- Name: Brave Ax
- Effect: A glossy ax from a block warrior.#Suitable for heroes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 4 weapon 7

- Chapter: 4
- Name: Devilsknife
- Effect: Skull-emblazoned scythe-ax.#Reduces Rudebuster's cost by 10
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 4 weapon 8

- Chapter: 4
- Name: Trefoil
- Effect: Mossy rapier with a clover emblem.#Increases $ found by 5%.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 4 weapon 9

- Chapter: 4
- Name: Ragger
- Effect: A rugged scarf that cuts enemies like a dagger.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 4 weapon 10

- Chapter: 4
- Name: DaintyScarf
- Effect: Delicate scarf that increases healing#power but has no attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 4 weapon 11

- Chapter: 4
- Name: TwistedSwd
- Effect: A strange blade
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 4 weapon 12

- Chapter: 4
- Name: SnowRing
- Effect: A ring with the emblem of the#snowflake
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 4 weapon 13

- Chapter: 4
- Name: ThornRing
- Effect: Wearer takes damage from pain#Reduces the TP cost of ice spells
- Status: literal acquisition call found
- Stat/value: `weaponattemp=14`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=12`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 4 weapon 14

- Chapter: 4
- Name: BounceBlade
- Effect: A pink saber with a rubber blade.#Weak, but increases defence.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 15

- Chapter: 4
- Name: CheerScarf
- Effect: A scarf with colorful you-can-do-it#imagery. Gains more TP from
  criticals.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=1`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 16

- Chapter: 4
- Name: MechaSaber
- Effect: The blade extends when you press the hilt.#CHA-CHK!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 17

- Chapter: 4
- Name: AutoAxe
- Effect: Make sure to charge it by#plugging it into the wall.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 18

- Chapter: 4
- Name: FiberScarf
- Effect: A scarf made of soft microfiber.#Balances attack and magic.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 19

- Chapter: 4
- Name: Ragger2
- Effect: A sharp and scratchy scarf.#Worse healing, better attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 20

- Chapter: 4
- Name: BrokenSwd
- Effect: A rejected sword cut into 2 pieces.#Not even you can equip this...
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 21

- Chapter: 4
- Name: PuppetScarf
- Effect: A scarf made of strange strings.#For those that abandon healing.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-6`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 22

- Chapter: 4
- Name: FreezeRing
- Effect: A ring with a snowglobe on it.#... is that someone inside?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 4 weapon 23

- Chapter: 4
- Name: Saber10
- Effect: A saber made of 10 cactus needles.#Fortunately, can deal more than 10
  damage.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=710`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 24

- Chapter: 4
- Name: ToxicAxe
- Effect: An axe used to clear wastelands#in a fetid swamp. Not poison, but
  gross.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=700`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 25

- Chapter: 4
- Name: FlexScarf
- Effect: A scarf that is warm and fuzzy, but with#a metal core that lets it
  keep its shape.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=720`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 26

- Chapter: 4
- Name: BlackShard
- Effect: A dagger-like shard of the Black Knife.#Strikes the weakness of
  dark-element enemies.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 4 weapon 50

- Chapter: 4
- Name: JingleBlade
- Effect: A lance-like sword with red-and-white stripes.#Perfect for jousting.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=7`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 4 weapon 51

- Chapter: 4
- Name: ScarfMark
- Effect: A thin scarf with a deep sheen. Holy writing has#been pressed into it,
  imbuing it with magic.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=900`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 52

- Chapter: 4
- Name: JusticeAxe
- Effect: It has no special powers. However, in order to#attain this item, you
  became much stronger!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 53

- Chapter: 4
- Name: Winglade
- Effect: A majestic sword with a white feathered hilt.#Slightly increases money
  won.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=8`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=999`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 4 weapon 54

- Chapter: 4
- Name: AbsorbAx
- Effect: A long, curved axe with an indent.#Scoop up HP when you attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=8`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

## Chapter 5

### Chapter 5 armor 0

- Chapter: 5
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 1

- Chapter: 5
- Name: Amber Card
- Effect: A thin square charm that sticks#to you, increasing defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 2

- Chapter: 5
- Name: Dice Brace
- Effect: A bracelet made out of various#symbol-inscribed cubes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 3

- Chapter: 5
- Name: Pink Ribbon
- Effect: A cute hair ribbon that increases#the range bullets increase tension.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=20`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`

### Chapter 5 armor 4

- Chapter: 5
- Name: White Ribbon
- Effect: A crinkly hair ribbon that slightly#increases your defense.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`

### Chapter 5 armor 5

- Chapter: 5
- Name: IronShackle
- Effect: Shackle that ironically increases#your attack and defense.
- Status: literal acquisition call found
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 6

- Chapter: 5
- Name: MouseToken
- Effect: A golden coin with a once-powerful mousewizard engraved on it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=120`
- Stat/value: `armorelementtemp=7`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 7

- Chapter: 5
- Name: Jevilstail
- Effect: A J-shaped tail that gives you devilenergy.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 8

- Chapter: 5
- Name: Silver Card
- Effect: A square charm that increases#dropped money by 5%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 9

- Chapter: 5
- Name: TwinRibbon
- Effect: Two ribbons. You'll have to put#your hair into pigtails.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=20`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`

### Chapter 5 armor 10

- Chapter: 5
- Name: GlowWrist
- Effect: A tough bracelet made of green wires,#and studded with sharp glowing
  lights.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 11

- Chapter: 5
- Name: ChainMail
- Effect: Chain-armor. Send it to 10 others#or it'll lose its defensive rating
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 12

- Chapter: 5
- Name: B.ShotBowtie
- Effect: A handsome bowtie. Looks like the brand#name has been cut off.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 13

- Chapter: 5
- Name: SpikeBand
- Effect: A black wristband covered in spikes.#Has the tendency to get stuck to
  itself.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 14

- Chapter: 5
- Name: Silver Watch
- Effect: Grazing bullets affects#the turn length by 10% more
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 15

- Chapter: 5
- Name: TensionBow
- Effect: Gain 10% more tension from#grazing bullets
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=2`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=400`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 16

- Chapter: 5
- Name: Mannequin
- Effect: It's a mannequin with the clothes#permanently attached. Useless
- Status: literal acquisition call found
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.2`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 5 armor 17

- Chapter: 5
- Name: DarkGoldBand
- Effect: A black metal with a golden shine.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=(global.chapter * 200) + ((global.chapter - 1) * 220)`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=0`

### Chapter 5 armor 18

- Chapter: 5
- Name: SkyMantle
- Effect: A cape that shimmers fluorescently.#Protects against Elec and Holy
  attacks.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1`
- Stat/value: `armorelementtemp=1`
- Stat/value: `armorelementamounttemp=0.5`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 19

- Chapter: 5
- Name: SpikeShackle
- Effect: (empty)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=3`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=300`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 20

- Chapter: 5
- Name: FrayedBowtie
- Effect: An old bowtie. It seems to have#lost much of its defensive value.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=100`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.15`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 21

- Chapter: 5
- Name: Dealmaker
- Effect: Fashionable pink and yellow glasses.#Greatly increase $ gained,
  and...?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=5`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.2`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`

### Chapter 5 armor 22

- Chapter: 5
- Name: RoyalPin
- Effect: A brooch engraved with Queen's face.#Careful of the sharp part.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 23

- Chapter: 5
- Name: ShadowMantle
- Effect: Shadows slip off like water.#Greatly protects against Dark and Star
  attacks.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=global.chapter`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=0`
- Stat/value: `armorelementtemp=5`
- Stat/value: `armorelementamounttemp=0.66`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=0`

### Chapter 5 armor 24

- Chapter: 5
- Name: LodeStone
- Effect: not assigned
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 armor 25

- Chapter: 5
- Name: GingerGuard
- Effect: A steel bangle tempered by extreme flame.#Its shape is humanoid in
  nature.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=3`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=862`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 26

- Chapter: 5
- Name: BlueRibbon
- Effect: A blue cheer bow. When the user uses a#healing move, it recovers
  slightly more HP.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=1`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`

### Chapter 5 armor 27

- Chapter: 5
- Name: TennaTie
- Effect: A giant, heavy-duty, bullet-proof tie.#How to even wear it...?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=-2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=600`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 30

- Chapter: 5
- Name: MonarchRBN
- Effect: A ribbon like the wings of a butterfly.#Increases healing ability when
  equipped.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=6`
- Stat/value: `armormagtemp=2`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`

### Chapter 5 armor 31

- Chapter: 5
- Name: TrueTie
- Effect: The genuine tie worn by a forgotten TV star.#Defends against the
  Puppet&Cat element.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1000`
- Stat/value: `armorelementtemp=6`
- Stat/value: `armorelementamounttemp=0.2`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 32

- Chapter: 5
- Name: DogWidow
- Effect: A brooch in the shape of a golden pooch.#You lose almost all money
  after battle.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=6`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=6000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 33

- Chapter: 5
- Name: RedRibbon
- Effect: A ribbon with an inscription to drive#away resident spirits, if they
  don't pay.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=0`

### Chapter 5 armor 34

- Chapter: 5
- Name: NetskieHat
- Effect: A white-yellow hat for someone with fox#ears. Somehow you can wear
  more than one.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=6`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1500`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 35

- Chapter: 5
- Name: SethSpecs
- Effect: A tactician's glasses. Become invulnerable for#longer after being
  damaged.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=6`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=0`

### Chapter 5 armor 36

- Chapter: 5
- Name: YellowHat
- Effect: The hat of a just cowboy. Makes spells#20% more effective.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=4`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=4`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 37

- Chapter: 5
- Name: O.Glove
- Effect: The glove of a brave fighter.#Susie's SCYTHEMARE will cost less TP.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=4`
- Stat/value: `armordftemp=8`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `armorchar1temp=0`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=0`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 38

- Chapter: 5
- Name: GreenApron
- Effect: The apron of a kind chef. The wearer#recovers 16% of their max HP
  after defending.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=7`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 50

- Chapter: 5
- Name: Waferguard
- Effect: Although it looks brittle, it contains a magical#energy that blunts
  damage on impact. +4DF
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=900`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 51

- Chapter: 5
- Name: MysticBand
- Effect: A silver armlet stained with amber.#Increases magic only. MAG +4
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=0`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=4`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 52

- Chapter: 5
- Name: PowerBand
- Effect: A silver armlet stained with red essence.#Increases strength only. ATK
  +4
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=4`
- Stat/value: `armordftemp=0`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=1`

### Chapter 5 armor 53

- Chapter: 5
- Name: PrincessRBN
- Effect: Elegant lace ribbon with gloves,#delicate enough to see through. +4
  DEF +2 ATK
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=2`
- Stat/value: `armordftemp=4`
- Stat/value: `armormagtemp=0`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`

### Chapter 5 armor 54

- Chapter: 5
- Name: GoldWidow
- Effect: A spider made of gold. It gathers coins#into it, reducing $ gained.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `armorattemp=1`
- Stat/value: `armordftemp=5`
- Stat/value: `armormagtemp=1`
- Stat/value: `armorboltstemp=0`
- Stat/value: `armorgrazeamttemp=0`
- Stat/value: `armorgrazesizetemp=0`
- Stat/value: `value=5000`
- Equip owner: `armorchar1temp=1`
- Equip owner: `armorchar2temp=1`
- Equip owner: `armorchar3temp=1`
- Equip owner: `armorchar4temp=0`

### Chapter 5 item 0

- Chapter: 5
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 item 1

- Chapter: 5
- Name: Darker Candy
- Effect: Heals#120HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=120`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 2

- Chapter: 5
- Name: ReviveMint
- Effect: Heal#Downed#Ally
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=400`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 3

- Chapter: 5
- Name: Glowshard
- Effect: Sell#at#shops
- Status: literal acquisition call found
- Stat/value: `itemtarget=0`
- Stat/value: `value=200 + (global.chapter * 100)`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 4

- Chapter: 5
- Name: Manual
- Effect: Read#out of#battle
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=1`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 5

- Chapter: 5
- Name: BrokenCake
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=5`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 6

- Chapter: 5
- Name: Top Cake
- Effect: Heals#team#160HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=2`
- Stat/value: `value=150`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 7

- Chapter: 5
- Name: not assigned
- Effect: not assigned
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 item 8

- Chapter: 5
- Name: Darkburger
- Effect: Heals#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 9

- Chapter: 5
- Name: LancerCookie
- Effect: Heals#50HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 10

- Chapter: 5
- Name: GigaSalad
- Effect: Heals#4HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 11

- Chapter: 5
- Name: ClubsSandwich
- Effect: Heals#team#70HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=70`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 12

- Chapter: 5
- Name: HeartsDonut
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 13

- Chapter: 5
- Name: ChocDiamond
- Effect: Healing#varies
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=40`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 14

- Chapter: 5
- Name: Favwich
- Effect: Heals#ALL HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=10`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 15

- Chapter: 5
- Name: RouxlsRoux
- Effect: Heals#50 HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=50`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 16

- Chapter: 5
- Name: CD Bagel
- Effect: Heals#80 HP
- Status: literal acquisition call found
- Stat/value: `itemtarget=1`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 17

- Chapter: 5
- Name: Mannequin
- Effect: Useless
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=0`
- Stat/value: `value=300`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 18

- Chapter: 5
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 19

- Chapter: 5
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 20

- Chapter: 5
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 21

- Chapter: 5
- Name: scr_text(1458)
- Effect: scr_text(1459)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 22

- Chapter: 5
- Name: DD-Burger
- Effect: Heals#60HP 2x
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 23

- Chapter: 5
- Name: LightCandy
- Effect: Heals#120HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 24

- Chapter: 5
- Name: ButJuice
- Effect: Heals#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 25

- Chapter: 5
- Name: SpagettiCode
- Effect: Heals#team#30HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=180`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 26

- Chapter: 5
- Name: JavaCookie
- Effect: Healing#varies
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=160`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 27

- Chapter: 5
- Name: TensionBit
- Effect: Raises#TP#32%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 28

- Chapter: 5
- Name: TensionGem
- Effect: Raises#TP#50%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=300`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 29

- Chapter: 5
- Name: TensionMax
- Effect: Raises#TP#Max
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=1000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 30

- Chapter: 5
- Name: ReviveDust
- Effect: Revives#team#25%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=100`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 31

- Chapter: 5
- Name: ReviveBrite
- Effect: Revives#team#100%
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=4000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 32

- Chapter: 5
- Name: S.POISON
- Effect: Hurts#party#member
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=110`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 33

- Chapter: 5
- Name: DogDollar
- Effect: Not#so#useful
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=0`
- Stat/value: `value=floor(200 / global.chapter)`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 34

- Chapter: 5
- Name: TVDinner
- Effect: Heals#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 35

- Chapter: 5
- Name: Pipis
- Effect: Does#nothing
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=0`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 36

- Chapter: 5
- Name: FlatSoda
- Effect: Heals#20HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=2`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 37

- Chapter: 5
- Name: TVSlop
- Effect: Heals#80HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 38

- Chapter: 5
- Name: ExecBuffet
- Effect: Heals#team#100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 39

- Chapter: 5
- Name: DeluxeDinner
- Effect: Heals#140HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 40

- Chapter: 5
- Name: PunchBowl
- Effect: Heals#team#200HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 41

- Chapter: 5
- Name: Flavigne
- Effect: Heals#130HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=333`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 42

- Chapter: 5
- Name: GreenTea
- Effect: Heals#180HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=777`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 43

- Chapter: 5
- Name: OrangeJuice
- Effect: Heals#80HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=222`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 60

- Chapter: 5
- Name: AncientSweet
- Effect: Kris only#+400
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=1000`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 61

- Chapter: 5
- Name: Rhapsotea
- Effect: Heals#115HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=250`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 62

- Chapter: 5
- Name: Scarlixir
- Effect: Heals#160HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=450`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 63

- Chapter: 5
- Name: BitterTear
- Effect: Heals#All HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=0`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 64

- Chapter: 5
- Name: Schadenbrot
- Effect: Heals#team#200HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=600`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 65

- Chapter: 5
- Name: TreeCake
- Effect: Heals#team#160HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=200`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 66

- Chapter: 5
- Name: S.POTION
- Effect: Heals#party#member
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=500`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 67

- Chapter: 5
- Name: Raw Moon
- Effect: Raises#TP 16%#+100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=222`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 68

- Chapter: 5
- Name: Phanta
- Effect: Raises#TP 16%#+100HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=222`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 69

- Chapter: 5
- Name: FlowerySoda
- Effect: Raises#TP 16%#+50HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=1`
- Stat/value: `value=222`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 item 70

- Chapter: 5
- Name: Shikacola
- Effect: Heals#team#80HP
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `itemtarget=2`
- Stat/value: `value=222`
- Stat/value: `usable=1`
- Equip-owner assignments: none

### Chapter 5 key 0

- Chapter: 5
- Name: (empty)
- Effect: ---
- Status: empty sentinel
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 1

- Chapter: 5
- Name: Cell Phone
- Effect: It can be used to make calls.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 5 key 2

- Chapter: 5
- Name: Egg
- Effect: It's evidence. You'll know what it was#evidence for when it happens.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 3

- Chapter: 5
- Name: BrokenCake
- Effect: Though broken, it seethes with power.#A master smith could fix it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 4

- Chapter: 5
- Name: Broken Key A
- Effect: It's the top part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 5

- Chapter: 5
- Name: Door Key
- Effect: The key to a mysterious cell.#Something feels strange about it.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 6

- Chapter: 5
- Name: Broken Key B
- Effect: It's the middle part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 7

- Chapter: 5
- Name: Broken Key C
- Effect: It's the bottom part of a key.#A smith could fix all three parts.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 8

- Chapter: 5
- Name: not assigned
- Effect: Hohoho! ROUXLS jumped out of your#pocket! How dadcrobatic! (Lesser)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 9

- Chapter: 5
- Name: Rouxls Kaard
- Effect: Oh, milord! Tis I, your humblest servante,#righte here where I never
  lefteth!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 10

- Chapter: 5
- Name: EmptyDisk
- Effect: A data disk from a strange machine.#Didn't someone want this?
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 11

- Chapter: 5
- Name: LoadedDisk
- Effect: A strange disk. You can feel it#smiling in your hand.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 12

- Chapter: 5
- Name: KeyGen
- Effect: A shady-looking program that can#open certain doors.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 13

- Chapter: 5
- Name: ShadowCrystal
- Effect: A sharp shadow moves like water in the hand.#You have collected [~1].
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 5 key 14

- Chapter: 5
- Name: Starwalker
- Effect: The original # (Starwalker)
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 15

- Chapter: 5
- Name: PureCrystal
- Effect: The shadow purified by the cat
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 16

- Chapter: 5
- Name: OddController
- Effect: A gamepad no one wanted to use.#The buttons are an ugly pink and
  yellow.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 17

- Chapter: 5
- Name: BackstagePass
- Effect: A pass for big shots allowed backstage.#Show it to Ramb in front of
  the door.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 18

- Chapter: 5
- Name: TripTicket
- Effect: A ticket to nowhere. It shows a map#pointing to the left of a red X...
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 19

- Chapter: 5
- Name: LancerConX~1
- Effect: Lancer's controllers. They're covered in dirt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 20

- Chapter: 5
- Name: Scissors
- Effect: Obviously stolen scissors which could easily#be used to cut up cloth.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 21

- Chapter: 5
- Name: YellowShred
- Effect: A shred of yellow fabric with a corn pattern.#The edge is black and
  smells.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 22

- Chapter: 5
- Name: BootOil
- Effect: A black, opaque oil with no distinctive odor.#Used to unsqueaken
  Cowboy boots.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 23

- Chapter: 5
- Name: RedSplatter
- Effect: A mysterious puddle of red criminal#liquid.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 24

- Chapter: 5
- Name: BromideR
- Effect: \"Good night, sweet prince\"#USE this item to observe it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 5 key 25

- Chapter: 5
- Name: PetalFeather
- Effect: Allows use of MYSTERIOUS STATUES.#Not to be confused with a certain
  other feather.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 26

- Chapter: 5
- Name: PerpBook
- Effect: A purple book with a decidedly floral scent.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 27

- Chapter: 5
- Name: BlueString
- Effect: String which could be used to bound something#in care.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 28

- Chapter: 5
- Name: TrainPlan
- Effect: A blueprint which details how to alter tracks#into a smashing machine
  with 2 rollercoasts.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 29

- Chapter: 5
- Name: YellowKey
- Effect: A yellow key that looks like it could#open a yellow door. Smells of
  corn.
- Status: literal acquisition call found
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 30

- Chapter: 5
- Name: SheetMusic
- Effect: Music that Susie attempted to transcribe.#USE it to read it.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 5 key 31

- Chapter: 5
- Name: ClaimbClaws
- Effect: Claws so small they conveniently can't#be seen. Use them to climb up
  obvious walls.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 32

- Chapter: 5
- Name: MysteryKey
- Effect: A pink key with an ectoplasmic aura.#Maybe it's a family heirloom.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 key 33

- Chapter: 5
- Name: BromideF
- Effect: \"Secret Steamy Bathtime\"#USE this item to observe it.
- Status: literal acquisition call found
- Stat/value: `tempkeyitemusable=1`
- Equip-owner assignments: none

### Chapter 5 weapon 0

- Chapter: 5
- Name: (empty)
- Effect: (empty)
- Status: empty sentinel
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=0`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 1

- Chapter: 5
- Name: Wood Blade
- Effect: A wooden practice blade with a carbon-#reinforced core.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 5 weapon 2

- Chapter: 5
- Name: Mane Ax
- Effect: Beginner's ax forged from the#mane of a dragon whelp.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=80`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 5 weapon 3

- Chapter: 5
- Name: Red Scarf
- Effect: A basic scarf made of lightly#magical fiber.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 5 weapon 4

- Chapter: 5
- Name: EverybodyWeapon
- Effect: It felt right for everyone.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=6`
- Stat/value: `weaponmagtemp=8`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 5

- Chapter: 5
- Name: Spookysword
- Effect: A black-and-orange sword with a bat hilt.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 5 weapon 6

- Chapter: 5
- Name: Brave Ax
- Effect: A glossy ax from a block warrior.#Suitable for heroes.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=150`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 5 weapon 7

- Chapter: 5
- Name: Devilsknife
- Effect: Skull-emblazoned scythe-ax.#Reduces Rudebuster's cost by 10
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`

### Chapter 5 weapon 8

- Chapter: 5
- Name: Trefoil
- Effect: Mossy rapier with a clover emblem.#Increases $ found by 5%.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 5 weapon 9

- Chapter: 5
- Name: Ragger
- Effect: A rugged scarf that cuts enemies like a dagger.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 5 weapon 10

- Chapter: 5
- Name: DaintyScarf
- Effect: Delicate scarf that increases healing#power but has no attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=200`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`

### Chapter 5 weapon 11

- Chapter: 5
- Name: TwistedSwd
- Effect: A strange blade
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`

### Chapter 5 weapon 12

- Chapter: 5
- Name: SnowRing
- Effect: A ring with the emblem of the#snowflake
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=100`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 13

- Chapter: 5
- Name: ThornRing
- Effect: Wearer takes damage from pain#Reduces the TP cost of ice spells
- Status: literal acquisition call found
- Stat/value: `weaponattemp=14`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=12`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 14

- Chapter: 5
- Name: BounceBlade
- Effect: A pink saber with a rubber blade.#Weak, but increases defence.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 15

- Chapter: 5
- Name: CheerScarf
- Effect: A scarf with colorful you-can-do-it#imagery. Gains more TP from
  criticals.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=1`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 16

- Chapter: 5
- Name: MechaSaber
- Effect: The blade extends when you press the hilt.#CHA-CHK!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 17

- Chapter: 5
- Name: AutoAxe
- Effect: Make sure to charge it by#plugging it into the wall.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 18

- Chapter: 5
- Name: FiberScarf
- Effect: A scarf made of soft microfiber.#Balances attack and magic.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 19

- Chapter: 5
- Name: Ragger2
- Effect: A sharp and scratchy scarf.#Worse healing, better attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=5`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=250`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 20

- Chapter: 5
- Name: BrokenSwd
- Effect: A rejected sword cut into 2 pieces.#Not even you can equip this...
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 21

- Chapter: 5
- Name: PuppetScarf
- Effect: A scarf made of strange strings.#For those that abandon healing.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=-6`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 22

- Chapter: 5
- Name: FreezeRing
- Effect: A ring with a snowglobe on it.#... is that someone inside?
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=4`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 23

- Chapter: 5
- Name: Saber10
- Effect: A saber made of 10 cactus needles.#Fortunately, can deal more than 10
  damage.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=710`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 24

- Chapter: 5
- Name: ToxicAxe
- Effect: An axe used to clear wastelands#in a fetid swamp. Not poison, but
  gross.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=700`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 25

- Chapter: 5
- Name: FlexScarf
- Effect: A scarf that is warm and fuzzy, but with#a metal core that lets it
  keep its shape.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=720`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 26

- Chapter: 5
- Name: BlackShard
- Effect: A dagger-like shard of the Black Knife.#Strikes the weakness of
  dark-element enemies.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 30

- Chapter: 5
- Name: WoodBlade2
- Effect: A sword that is arbitrarily stronger#because it fits the setting of
  Chapter 5.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=500`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 31

- Chapter: 5
- Name: Thatchet
- Effect: An axe made of brambles. It's rumored its#wickedness infects anything
  it touches.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 32

- Chapter: 5
- Name: BlueShoes
- Effect: Shoes from a prestigious dancer.#Ralsei's PACIFY costs 0% TP.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=2`
- Stat/value: `weapondftemp=4`
- Stat/value: `weaponmagtemp=6`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 33

- Chapter: 5
- Name: AquaKnife
- Effect: A mischievous blade. Attacks with this#weapon are easier to make
  critical.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=10`
- Stat/value: `weapondftemp=2`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 34

- Chapter: 5
- Name: FloweryScarf
- Effect: A scarf which says \"I <3 Flowery\" on it.#It's the perfect size for
  Ralsei.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=70`
- Stat/value: `weapondftemp=70`
- Stat/value: `weaponmagtemp=70`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 35

- Chapter: 5
- Name: BrokenScarf
- Effect: A scarf that was torn to pieces in the#battle, revealing it was all
  for show.
- Status: literal acquisition call found
- Stat/value: `weaponattemp=0`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=2`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 36

- Chapter: 5
- Name: GildedRose
- Effect: Armour rings with a rose motif. Any thorns are#pointed outwards so you
  don't hurt yourself.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=16`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1111`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 37

- Chapter: 5
- Name: MistleWP
- Effect: A parasitic ivy whip with a nature's power.#Only experts can use it as
  a scarf.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=6`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=2`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1000`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 50

- Chapter: 5
- Name: JingleBlade
- Effect: A lance-like sword with red-and-white stripes.#Perfect for jousting.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=7`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=1`

### Chapter 5 weapon 51

- Chapter: 5
- Name: ScarfMark
- Effect: A thin scarf with a deep sheen. Holy writing has#been pressed into it,
  imbuing it with magic.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=4`
- Stat/value: `weapondftemp=1`
- Stat/value: `weaponmagtemp=1`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=900`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=1`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 52

- Chapter: 5
- Name: JusticeAxe
- Effect: It has no special powers. However, in order to#attain this item, you
  became much stronger!
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=12`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=0`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 53

- Chapter: 5
- Name: Winglade
- Effect: A majestic sword with a white feathered hilt.#Slightly increases money
  won.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=8`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=999`
- Equip owner: `weaponchar1temp=1`
- Equip owner: `weaponchar2temp=0`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

### Chapter 5 weapon 54

- Chapter: 5
- Name: AbsorbAx
- Effect: A long, curved axe with an indent.#Scoop up HP when you attack.
- Status: defined; no literal acquisition call (dynamic, transfer, or unplaced)
- Stat/value: `weaponattemp=8`
- Stat/value: `weapondftemp=0`
- Stat/value: `weaponmagtemp=0`
- Stat/value: `weaponboltstemp=1`
- Stat/value: `weapongrazeamttemp=0`
- Stat/value: `weapongrazesizetemp=0`
- Stat/value: `value=1234`
- Equip owner: `weaponchar1temp=0`
- Equip owner: `weaponchar2temp=1`
- Equip owner: `weaponchar3temp=0`
- Equip owner: `weaponchar4temp=0`

## Acquisition and output chains

### Acquisition record 0001

- chapter: `2`
- definition: `item:22`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0002

- chapter: `2`
- definition: `armor:8`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0003

- chapter: `2`
- definition: `armor:9`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0004

- chapter: `2`
- definition: `armor:13`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0005

- chapter: `2`
- definition: `armor:15`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0006

- chapter: `2`
- definition: `weapon:11`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0007

- chapter: `3`
- definition: `item:22`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0008

- chapter: `3`
- definition: `armor:8`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0009

- chapter: `3`
- definition: `armor:9`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0010

- chapter: `3`
- definition: `armor:13`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0011

- chapter: `3`
- definition: `armor:15`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0012

- chapter: `3`
- definition: `weapon:11`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0013

- chapter: `4`
- definition: `item:22`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0014

- chapter: `4`
- definition: `armor:8`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0015

- chapter: `4`
- definition: `armor:9`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0016

- chapter: `4`
- definition: `armor:13`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0017

- chapter: `4`
- definition: `armor:15`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0018

- chapter: `4`
- definition: `weapon:11`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0019

- chapter: `5`
- definition: `item:22`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0020

- chapter: `5`
- definition: `armor:8`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0021

- chapter: `5`
- definition: `armor:9`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0022

- chapter: `5`
- definition: `armor:13`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0023

- chapter: `5`
- definition: `armor:15`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0024

- chapter: `5`
- definition: `weapon:11`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0025

- chapter: `5`
- definition: `armor:30`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0026

- chapter: `5`
- definition: `armor:31`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0027

- chapter: `5`
- definition: `item:34`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0028

- chapter: `5`
- definition: `item:39`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0029

- chapter: `5`
- definition: `item:40`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0030

- chapter: `5`
- definition: `item:29`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0031

- chapter: `5`
- definition: `armor:32`
- chain: `fusion-output`
- join: `matched`
- status: `definition-only`
- rooms: `none joined`

### Acquisition record 0032

- chapter: `1`
- definition: `item:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0033

- chapter: `1`
- definition: `item:8`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0034

- chapter: `1`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0035

- chapter: `1`
- definition: `weapon:5`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0036

- chapter: `1`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0037

- chapter: `1`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0038

- chapter: `1`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0039

- chapter: `1`
- definition: `item:15`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0040

- chapter: `1`
- definition: `weapon:6`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0041

- chapter: `1`
- definition: `weapon:10`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0042

- chapter: `1`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0043

- chapter: `1`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0044

- chapter: `1`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0045

- chapter: `1`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop2`

### Acquisition record 0046

- chapter: `2`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0047

- chapter: `2`
- definition: `item:8`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0048

- chapter: `2`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0049

- chapter: `2`
- definition: `weapon:5`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0050

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0051

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0052

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0053

- chapter: `2`
- definition: `item:15`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0054

- chapter: `2`
- definition: `weapon:6`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0055

- chapter: `2`
- definition: `weapon:10`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0056

- chapter: `2`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0057

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0058

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0059

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0060

- chapter: `2`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0061

- chapter: `2`
- definition: `armor:10`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0062

- chapter: `2`
- definition: `weapon:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0063

- chapter: `2`
- definition: `weapon:17`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0064

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0065

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0066

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_music`

### Acquisition record 0067

- chapter: `2`
- definition: `item:24`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0068

- chapter: `2`
- definition: `item:25`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0069

- chapter: `2`
- definition: `armor:12`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0070

- chapter: `2`
- definition: `armor:22`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0071

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0072

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0073

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_swatch`

### Acquisition record 0074

- chapter: `2`
- definition: `key:12`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0075

- chapter: `2`
- definition: `item:32`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0076

- chapter: `2`
- definition: `weapon:20`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0077

- chapter: `2`
- definition: `armor:20`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0078

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0079

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0080

- chapter: `2`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0081

- chapter: `3`
- definition: `item:34`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0082

- chapter: `3`
- definition: `item:39`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0083

- chapter: `3`
- definition: `armor:24`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0084

- chapter: `3`
- definition: `armor:25`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0085

- chapter: `3`
- definition: `item:37`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0086

- chapter: `3`
- definition: `weapon:24`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0087

- chapter: `3`
- definition: `weapon:23`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0088

- chapter: `3`
- definition: `weapon:25`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0089

- chapter: `3`
- definition: `item:37`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0090

- chapter: `3`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0091

- chapter: `3`
- definition: `item:8`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0092

- chapter: `3`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0093

- chapter: `3`
- definition: `weapon:5`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0094

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0095

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0096

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0097

- chapter: `3`
- definition: `item:15`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0098

- chapter: `3`
- definition: `weapon:6`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0099

- chapter: `3`
- definition: `weapon:10`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0100

- chapter: `3`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0101

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0102

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0103

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0104

- chapter: `3`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0105

- chapter: `3`
- definition: `armor:10`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0106

- chapter: `3`
- definition: `weapon:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0107

- chapter: `3`
- definition: `weapon:17`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0108

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0109

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0110

- chapter: `3`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0111

- chapter: `4`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0112

- chapter: `4`
- definition: `item:8`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0113

- chapter: `4`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0114

- chapter: `4`
- definition: `weapon:5`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0115

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0116

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0117

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0118

- chapter: `4`
- definition: `item:15`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0119

- chapter: `4`
- definition: `weapon:6`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0120

- chapter: `4`
- definition: `weapon:10`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0121

- chapter: `4`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0122

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0123

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0124

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0125

- chapter: `4`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0126

- chapter: `4`
- definition: `armor:10`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0127

- chapter: `4`
- definition: `weapon:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0128

- chapter: `4`
- definition: `weapon:17`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0129

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0130

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0131

- chapter: `4`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0132

- chapter: `5`
- definition: `item:67`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0133

- chapter: `5`
- definition: `item:68`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0134

- chapter: `5`
- definition: `item:69`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0135

- chapter: `5`
- definition: `item:70`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0136

- chapter: `5`
- definition: `item:67`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0137

- chapter: `5`
- definition: `item:68`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0138

- chapter: `5`
- definition: `item:69`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0139

- chapter: `5`
- definition: `item:70`
- chain: `shop-output`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0140

- chapter: `5`
- definition: `item:41`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0141

- chapter: `5`
- definition: `weapon:30`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0142

- chapter: `5`
- definition: `armor:34`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0143

- chapter: `5`
- definition: `key:32`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0144

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0145

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0146

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch5`

### Acquisition record 0147

- chapter: `5`
- definition: `item:34`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0148

- chapter: `5`
- definition: `item:39`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0149

- chapter: `5`
- definition: `armor:24`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0150

- chapter: `5`
- definition: `armor:25`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0151

- chapter: `5`
- definition: `item:43`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0152

- chapter: `5`
- definition: `item:41`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0153

- chapter: `5`
- definition: `item:42`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0154

- chapter: `5`
- definition: `item:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0155

- chapter: `5`
- definition: `item:8`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0156

- chapter: `5`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0157

- chapter: `5`
- definition: `weapon:5`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0158

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0159

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0160

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0161

- chapter: `5`
- definition: `item:15`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0162

- chapter: `5`
- definition: `weapon:6`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0163

- chapter: `5`
- definition: `weapon:10`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0164

- chapter: `5`
- definition: `armor:1`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0165

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0166

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0167

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0168

- chapter: `5`
- definition: `item:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0169

- chapter: `5`
- definition: `armor:10`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0170

- chapter: `5`
- definition: `weapon:16`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0171

- chapter: `5`
- definition: `weapon:17`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0172

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0173

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0174

- chapter: `5`
- definition: `item:0`
- chain: `shop-output`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_music`

### Acquisition record 0175

- chapter: `1`
- definition: `item:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0176

- chapter: `1`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0177

- chapter: `1`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0178

- chapter: `1`
- definition: `key:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0179

- chapter: `1`
- definition: `armor:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0180

- chapter: `1`
- definition: `item:6`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0181

- chapter: `1`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0182

- chapter: `1`
- definition: `item:12`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0183

- chapter: `1`
- definition: `item:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0184

- chapter: `1`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0185

- chapter: `1`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0186

- chapter: `1`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0187

- chapter: `1`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0188

- chapter: `1`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_cc_joker`

### Acquisition record 0189

- chapter: `1`
- definition: `weapon:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_cc_joker`

### Acquisition record 0190

- chapter: `1`
- definition: `armor:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_cc_joker`

### Acquisition record 0191

- chapter: `1`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_castle_tutorial`

### Acquisition record 0192

- chapter: `1`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_castle_tutorial`

### Acquisition record 0193

- chapter: `1`
- definition: `key:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_forest_smith`

### Acquisition record 0194

- chapter: `1`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_beach, room_cc_clover, room_cc_hathy, room_cc_kingbattle,`
  `room_cc_preroof, room_cc_prison_cells, room_cc_prison2,`
  `room_cc_rudinn, room_cc_throneroom, room_diner, room_field_checkers7,`
  `room_field_maze, room_field_puzzle1, room_field_puzzletutorial,`
  `room_field_topchef, room_field2A, room_forest_area1,`
  `room_forest_area2A, room_forest_area3A, room_forest_area4,`
  `room_forest_fightsusie, room_forest_savepoint_relax,`
  `room_forest_savepoint1, room_forest_savepoint2, room_graveyard,`
  `room_hospital_lobby, room_krisroom, room_library, room_torhouse,`
  `room_town_church, room_town_mid, room_town_north, room_town_south,`
  `room_townhall`

### Acquisition record 0195

- chapter: `1`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_castle_darkdoor, room_castle_front, room_castle_outskirts,`
  `room_castle_town, room_castle_tutorial, room_cc_1f, room_cc_2f,`
  `room_cc_3f, room_cc_4f, room_cc_5f, room_cc_6f, room_cc_clover,`
  `room_cc_elevator, room_cc_entrance, room_cc_hathy, room_cc_joker,`
  `room_cc_kingbattle, room_cc_lancer, room_cc_prefountain,`
  `room_cc_preroof, room_cc_prison_cells, room_cc_prison_prejoker,`
  `room_cc_prison_to_elevator, room_cc_prison2, room_cc_prisonelevator,`
  `room_cc_prisonlancer, room_cc_rudinn, room_cc_rurus1, room_cc_rurus2,`
  `room_cc_throneroom, room_dark_chase1, room_dark_chase2,`
  `room_dark_eyepuzzle, room_dark_wobbles, room_dark1, room_dark1a,`
  `room_dark2, room_dark3, room_dark3a, room_dark7, room_DARKempty,`
  `room_field_boxpuzzle, room_field_checkers1, room_field_checkers2,`
  `room_field_checkers3, room_field_checkers4, room_field_checkers5,`
  `room_field_checkers6, room_field_checkers7, room_field_checkersboss,`
  `room_field_forest, room_field_getsusie, room_field_maze,`
  `room_field_puzzle1, room_field_puzzle2, room_field_puzzletutorial,`
  `room_field_secret1, room_field_shop1, room_field_start,`
  `room_field_topchef, room_field1, room_field2, room_field2A,`
  `room_field3, room_field4, room_forest_afterthrash2,`
  `room_forest_afterthrash3, room_forest_afterthrash4,`
  `room_forest_area0, room_forest_area1, room_forest_area2,`
  `room_forest_area2A, room_forest_area3, room_forest_area3A,`
  `room_forest_area4, room_forest_area5, room_forest_beforeclover,`
  `room_forest_castlefront, room_forest_castleview, room_forest_chase1,`
  `room_forest_chase2, room_forest_dancers1, room_forest_fightsusie,`
  `room_forest_maze_deadend, room_forest_maze_deadend2,`
  `room_forest_maze_susie, room_forest_maze1, room_forest_maze2,`
  `room_forest_puzzle1, room_forest_savepoint_relax,`
  `room_forest_savepoint1, room_forest_savepoint2,`
  `room_forest_savepoint3, room_forest_secret1, room_forest_smith,`
  `room_forest_starwalker, room_forest_thrashmaker, room_man`

### Acquisition record 0196

- chapter: `1`
- definition: `key:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0197

- chapter: `2`
- definition: `item:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0198

- chapter: `2`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0199

- chapter: `2`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0200

- chapter: `2`
- definition: `key:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0201

- chapter: `2`
- definition: `armor:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0202

- chapter: `2`
- definition: `item:6`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0203

- chapter: `2`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0204

- chapter: `2`
- definition: `item:12`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0205

- chapter: `2`
- definition: `item:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0206

- chapter: `2`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0207

- chapter: `2`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0208

- chapter: `2`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0209

- chapter: `2`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0210

- chapter: `2`
- definition: `armor:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0211

- chapter: `2`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0212

- chapter: `2`
- definition: `key:10`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0213

- chapter: `2`
- definition: `item:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0214

- chapter: `2`
- definition: `weapon:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0215

- chapter: `2`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0216

- chapter: `2`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0217

- chapter: `2`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0218

- chapter: `2`
- definition: `weapon:21`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_dw_mansion_fountain`

### Acquisition record 0219

- chapter: `2`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_dw_mansion_fountain`

### Acquisition record 0220

- chapter: `2`
- definition: `key:8`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_krisroom`

### Acquisition record 0221

- chapter: `2`
- definition: `key:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0222

- chapter: `2`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_castle_town,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_DARKempty, room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_castle_area_1,`
  `room_dw_castle_area_2, room_dw_castle_area_2_transformed,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_hallway, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_lancer, room_dw_castle_rooms_susie,`
  `room_dw_castle_west_cliff, room_dw_castle_west_cliff_old,`
  `room_dw_city_baseball, room_dw_city_berdly, room_dw_city_big_1,`
  `room_dw_city_big_1_original, room_dw_city_big_2,`
  `room_dw_city_big_2_OG, room_dw_city_big_3,`
  `room_dw_city_big_3_backup_2exits, room_dw_city_big_3_og,`
  `room_dw_city_carnival, room_dw_city_cheese, room_dw_city_cheesemaze,`
  `room_dw_city_dog_traffic, room_dw_city_entrance, room_dw_city_hacker,`
  `room_dw_city_intro, room_dw_city_man, room_dw_city_mansion_front,`
  `room_dw_city_mice, room_dw_city_mice2, room_dw_city_mice2_og,`
  `room_dw_city_mice3, room_dw_city_mirrorfriend,`
  `room_dw_city_monologue, room_dw_city_monologue_old,`
  `room_dw_city_moss, room_dw_city_noelle_fight_intro,`
  `room_dw_city_poppup, room_dw_city_postbaseball_1,`
  `room_dw_city_postbaseball_2, room_dw_city_postbaseball_3,`
  `room_dw_city_prototype_01, room_dw_city_prototype_02,`
  `room_dw_city_queen_drunk, room_dw_city_roadblock,`
  `room_dw_city_savepoint, room_dw_city_sidewayscars,`
  `room_dw_city_spamton_alley, room_dw_city_spamton_house,`
  `room_dw_city_spamton_shop_exterior,`
  `room_dw_city_spamton_shop_interior, room_dw_city_split,`
  `room_dw_city_susie_ralsei_fun_1, room_dw_city_traffic_1,`
  `room_dw_city_traffic_2, room_dw_city_traffic_2_old,`
  `room_dw_city_traffic_3, room_dw_city_traffic_3_2Entrances,`
  `room_dw_city_traffic_3_backup, room_dw_city_traffic_4,`
  `room_dw_city_traffic_5_old, room_dw_city_treasure,`
  `room_dw_cyber_battle_maze_1, room_dw_cyber_battle_maze_1_Original,`
  `room_dw_cyber_battle_maze_2, room_dw_cyber_battle_maze_2_old,`
  `room_dw_cyber_battle_maze_2_toby, room_dw_cyber_battle_maze_3,`
  `room_dw_cyber_escalator_slide, room_dw_cyber_intro_1,`
  `room_dw_cyber_intro_2, room_dw_cyber_intro_connector,`
  `room_dw_cyber_keyboard_puzzle_1, room_dw_cyber_keyboard_puzzle_1_old,`
  `room_dw_cyber_keyboard_puzzle_2, room_dw_cyber_keyboard_puzzle_3,`
  `room_dw_cyber_keyboardexample, room_dw_cyber_maze_fireworks,`
  `room_dw_cyber_maze_queenscreen, room_dw_cyber_maze_rhythm,`
  `room_dw_cyber_maze_tasque, room_dw_cyber_maze_virokun,`
  `room_dw_cyber_maze_virokun_backuo, room_dw_cyber_music_bullet,`
  `room_dw_cyber_music_bullet_original, room_dw_cyber_music_fight,`
  `room_dw_cyber_music_final, room_dw_cyber_musical_door,`
  `room_dw_cyber_musical_shop, room_dw_cyber_nuberts_treasure,`
  `room_dw_cyber_post_music_boss_slide, room_dw_cyber_queen_boxing,`
  `room_dw_cyber_rhythm_slide, room_dw_cyber_rollercoaster,`
  `room_dw_cyber_savepoint, room_dw_cyber_savepoint_original,`
  `room_dw_cyber_shaunsmusicalbullettunnel, room_dw_cyber_tasque_battle,`
  `room_dw_cyber_tasque_battle_og, room_dw_cyber_teacup_1,`
  `room_dw_cyber_teacup_2, room_dw_cyber_teacup_final,`
  `room_dw_cyber_viro_ring, room_dw_cyber_viromaze2,`
  `room_dw_cyber_virovirokun_fight, room_dw_mansion_acid_tunnel,`
  `room_dw_mansion_acid_tunnel_exit,`
  `room_dw_mansion_acid_tunnel_loop_rouxls,`
  `room_dw_mansion_acid_tunnel_old,`
  `room_dw_mansion_acid_tunnel_puzzle_entrance,`
  `room_dw_mansion_b_central, room_dw_mansion_b_east,`
  `room_dw_mansion_b_east_a, room_dw_mansion_b_east_b,`
  `room_dw_mansion_b_east_transformed, room_dw_mansion_b_entrance,`
  `room_dw_mansion_b_stairs, room_dw_mansion_b_west_1f,`
  `room_dw_mansion_b_west_1f_a, room_dw_mansion_b_west_1f_b,`
  `room_dw_mansion_b_west_2f, room_dw_mansion_bridges,`
  `room_dw_mansion_bridges_funny, room_dw_mansion_bridgesold,`
  `room_dw_mansion_darkbulb_1, room_dw_mansion_darkbulb_2,`
  `room_dw_mansion_darkbulb_3, room_dw_mansion_dining_a,`
  `room_dw_mansion_dining_storage, room_dw_mansion_dining_storage_old,`
  `room_dw_mansion_dining3, room_dw_mansion_dininghall,`
  `room_dw_mansion_east_1f_a, room_dw_mansion_east_1f_b,`
  `room_dw_mansion_east_1f_c, room_dw_mansion_east_1f_d,`
  `room_dw_mansion_east_1f_e, room_dw_mansion_east_1f_secret,`
  `room_dw_mansion_east_2f_a, room_dw_mansion_east_2f_c,`
  `room_dw_mansion_east_2f_c_a, room_dw_mansion_east_2f_c_b,`
  `room_dw_mansion_east_2f_d, room_dw_mansion_east_2f_d_backup,`
  `room_dw_mansion_east_2f_shortcut, room_dw_mansion_east_2f_teacup,`
  `room_dw_mansion_east_2f_transformed_new,`
  `room_dw_mansion_east_2f_ufo_old, room_dw_mansion_east_3f,`
  `room_dw_mansion_east_3f_projection, room_dw_mansion_east_3f_toilet,`
  `room_dw_mansion_east_4f_a, room_dw_mansion_east_4f_b,`
  `room_dw_mansion_east_4f_c, room_dw_mansion_east_4f_d,`
  `room_dw_mansion_east_4f_e, room_dw_mansion_east_teacup,`
  `room_dw_mansion_east_teacup_2, room_dw_mansion_east_teacup_3,`
  `room_dw_mansion_east_teacup_4, room_dw_mansion_east_teacup_4_old,`
  `room_dw_mansion_elevator, room_dw_mansion_entrance,`
  `room_dw_mansion_ferris_wheel, room_dw_mansion_ferris_wheel_post,`
  `room_dw_mansion_fire_paintings, room_dw_mansion_fountain,`
  `room_dw_mansion_hands, room_dw_mansion_kitchen,`
  `room_dw_mansion_krisroom, room_dw_mansion_lightner_hallway,`
  `room_dw_mansion_mouseLottery, room_dw_mansion_noelle_room,`
  `room_dw_mansion_potBalance, room_dw_mansion_prefountain,`
  `room_dw_mansion_single_pot, room_dw_mansion_sparks,`
  `room_dw_mansion_susieroom, room_dw_mansion_tasquePaintings,`
  `room_dw_mansion_top, room_dw_mansion_top_post,`
  `room_dw_mansion_top_post_old, room_dw_mansion_traffic,`
  `room_dw_mansion_traffic_original, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_front,`
  `room_GMS2_test, room_shaun_puzzle, room_teacup_demoauto,`
  `room_teacup_demobullets`

### Acquisition record 0223

- chapter: `2`
- definition: `item:33`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_city_dog_traffic`

### Acquisition record 0224

- chapter: `2`
- definition: `key:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0225

- chapter: `2`
- definition: `key:11`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop_ch2_spamton`

### Acquisition record 0226

- chapter: `2`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_battletest`

### Acquisition record 0227

- chapter: `2`
- definition: `item:23`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_schooldoor, room_schoollobby, room_town_krisyard`

### Acquisition record 0228

- chapter: `2`
- definition: `key:14`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Acquisition record 0229

- chapter: `2`
- definition: `key:8`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Acquisition record 0230

- chapter: `2`
- definition: `key:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_castle_area_2_transformed`

### Acquisition record 0231

- chapter: `2`
- definition: `key:8`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_mansion_krisroom`

### Acquisition record 0232

- chapter: `2`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_mansion_b_east_a`

### Acquisition record 0233

- chapter: `2`
- definition: `weapon:21`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_mansion_b_east_a`

### Acquisition record 0234

- chapter: `2`
- definition: `armor:21`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_mansion_b_east_a`

### Acquisition record 0235

- chapter: `2`
- definition: `key:8`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Acquisition record 0236

- chapter: `2`
- definition: `key:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_castle_area_1`

### Acquisition record 0237

- chapter: `2`
- definition: `weapon:22`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_city_big_2`

### Acquisition record 0238

- chapter: `3`
- definition: `item:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0239

- chapter: `3`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0240

- chapter: `3`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0241

- chapter: `3`
- definition: `key:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0242

- chapter: `3`
- definition: `armor:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0243

- chapter: `3`
- definition: `item:6`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0244

- chapter: `3`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0245

- chapter: `3`
- definition: `item:12`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0246

- chapter: `3`
- definition: `item:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0247

- chapter: `3`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0248

- chapter: `3`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0249

- chapter: `3`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0250

- chapter: `3`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0251

- chapter: `3`
- definition: `armor:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0252

- chapter: `3`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0253

- chapter: `3`
- definition: `key:10`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0254

- chapter: `3`
- definition: `item:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0255

- chapter: `3`
- definition: `weapon:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0256

- chapter: `3`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0257

- chapter: `3`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0258

- chapter: `3`
- definition: `key:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0259

- chapter: `3`
- definition: `key:18`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_b3bs_bibliox`

### Acquisition record 0260

- chapter: `3`
- definition: `armor:23`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_board_postshadowmantle`

### Acquisition record 0261

- chapter: `3`
- definition: `key:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_rouxls_lanina`

### Acquisition record 0262

- chapter: `3`
- definition: `item:34`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0263

- chapter: `3`
- definition: `item:34`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0264

- chapter: `3`
- definition: `key:19`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0265

- chapter: `3`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_ch3_man`

### Acquisition record 0266

- chapter: `3`
- definition: `key:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_console_room`

### Acquisition record 0267

- chapter: `3`
- definition: `key:8`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_krisroom`

### Acquisition record 0268

- chapter: `3`
- definition: `key:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0269

- chapter: `3`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_alphysalley, room_alphysclass, room_cc_clover, room_cc_lancer,`
  `room_debug_loc, room_diner, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_east_door, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_susie, room_dw_castle_town,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_flowershop_1f, room_flowershop_2f, room_graveyard,`
  `room_hospital_hallway, room_hospital_lobby, room_hospital_room2,`
  `room_hospital_rudy, room_krishallway, room_krisroom, room_library,`
  `room_lw_computer_lab, room_lw_conbini, room_lw_icee_pizza,`
  `room_lw_library_upstairs, room_lw_police, room_school_unusedroom,`
  `room_schooldoor, room_schoollobby, room_torbathroom, room_torhouse,`
  `room_torielclass, room_town_mid, room_town_north, room_town_south,`
  `room_townhall`

### Acquisition record 0270

- chapter: `3`
- definition: `weapon:26`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_alphysalley, room_alphysclass, room_cc_clover, room_cc_lancer,`
  `room_debug_loc, room_diner, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_east_door, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_susie, room_dw_castle_town,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_flowershop_1f, room_flowershop_2f, room_graveyard,`
  `room_hospital_hallway, room_hospital_lobby, room_hospital_room2,`
  `room_hospital_rudy, room_krishallway, room_krisroom, room_library,`
  `room_lw_computer_lab, room_lw_conbini, room_lw_icee_pizza,`
  `room_lw_library_upstairs, room_lw_police, room_school_unusedroom,`
  `room_schooldoor, room_schoollobby, room_torbathroom, room_torhouse,`
  `room_torielclass, room_town_mid, room_town_north, room_town_south,`
  `room_townhall`

### Acquisition record 0271

- chapter: `3`
- definition: `weapon:26`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_alphysalley, room_alphysclass, room_cc_clover, room_cc_lancer,`
  `room_debug_loc, room_diner, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_east_door, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_susie, room_dw_castle_town,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_flowershop_1f, room_flowershop_2f, room_graveyard,`
  `room_hospital_hallway, room_hospital_lobby, room_hospital_room2,`
  `room_hospital_rudy, room_krishallway, room_krisroom, room_library,`
  `room_lw_computer_lab, room_lw_conbini, room_lw_icee_pizza,`
  `room_lw_library_upstairs, room_lw_police, room_school_unusedroom,`
  `room_schooldoor, room_schoollobby, room_torbathroom, room_torhouse,`
  `room_torielclass, room_town_mid, room_town_north, room_town_south,`
  `room_townhall`

### Acquisition record 0272

- chapter: `3`
- definition: `weapon:23`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_alphysalley, room_alphysclass, room_cc_clover, room_cc_lancer,`
  `room_debug_loc, room_diner, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_east_door, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_susie, room_dw_castle_town,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_flowershop_1f, room_flowershop_2f, room_graveyard,`
  `room_hospital_hallway, room_hospital_lobby, room_hospital_room2,`
  `room_hospital_rudy, room_krishallway, room_krisroom, room_library,`
  `room_lw_computer_lab, room_lw_conbini, room_lw_icee_pizza,`
  `room_lw_library_upstairs, room_lw_police, room_school_unusedroom,`
  `room_schooldoor, room_schoollobby, room_torbathroom, room_torhouse,`
  `room_torielclass, room_town_mid, room_town_north, room_town_south,`
  `room_townhall`

### Acquisition record 0273

- chapter: `3`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_adventureboardtest, room_battletest, room_board_1,`
  `room_board_1_sword, room_board_1_sword_trees, room_board_2,`
  `room_board_2_sword, room_board_3, room_board_3_sword, room_board_3b,`
  `room_board_boattest, room_board_designTest, room_board_dungeon_2,`
  `room_board_dungeon_3, room_board_empty, room_board_gsa02_b0,`
  `room_board_intro, room_board_postshadowmantle,`
  `room_board_postshadowmantle_test, room_board_prepostshadowmantle,`
  `room_board_preshadowmantle, room_board_preshadowmantle_repeat,`
  `room_board_sword_intro, room_board_tests, room_board1_oldtest,`
  `room_boardtest, room_boardtest_old, room_bullettest,`
  `room_bullettest_new, room_castle_tutorial, room_cc_clover,`
  `room_cc_lancer, room_ch3_gacharoom_unknown, room_ch3_gameshowroom,`
  `room_ch3_gameshowroom_tennatest, room_cutscene_tester,`
  `room_cutscene_tester_b, room_DARKbase_GMS2, room_DARKempty,`
  `room_debug_battleBalloon, room_debug_choicer_dark,`
  `room_debug_smallface_dark, room_dw_b3bs_bibliox,`
  `room_dw_b3bs_camerareminder, room_dw_b3bs_cheaterpippins,`
  `room_dw_b3bs_cooltrashy, room_dw_b3bs_extrapuzzle,`
  `room_dw_b3bs_idcardpuzzle, room_dw_b3bs_interstitial,`
  `room_dw_b3bs_intro, room_dw_b3bs_jail1, room_dw_b3bs_jail2,`
  `room_dw_b3bs_lancerget, room_dw_b3bs_mysterypuzzle,`
  `room_dw_b3bs_rabbick_a, room_dw_b3bs_rabbick_b,`
  `room_dw_b3bs_rouxls_boss, room_dw_b3bs_rouxls_lanina,`
  `room_dw_b3bs_sadshadowguys, room_dw_b3bs_shop, room_dw_b3bs_template,`
  `room_dw_b3bs_watercooler, room_dw_b3bs_zapper_a,`
  `room_dw_b3bs_zapper_a_old, room_dw_b3bs_zapper_b,`
  `room_dw_b3bs_zapper_c, room_dw_b3bs_zapper_d, room_dw_b3bstest,`
  `room_dw_b3bstest_big, room_dw_backstage, room_dw_castle_area_1,`
  `room_dw_castle_cafe, room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_restaurant,`
  `room_dw_castle_rooms_kris, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_west_cliff, room_dw_ch3_man,`
  `room_dw_changing_room, room_dw_channelchange_test, room_dw_chef,`
  `room_dw_chef_empty, room_dw_console_room, room_dw_couch_overworld_01,`
  `room_dw_couch_overworld_02, room_dw_couch_overworld_03,`
  `room_dw_couch_overworld_04, room_dw_couch_overworld_05,`
  `room_dw_couch_overworld_intro, room_dw_couch_overworld_intro_left,`
  `room_dw_couch_points, room_dw_green_room, room_dw_inbetween,`
  `room_dw_inbetweenhall, room_dw_puzzlecloset_0,`
  `room_dw_puzzlecloset_1, room_dw_puzzlecloset_1a,`
  `room_dw_puzzlecloset_2, room_dw_puzzlecloset_3,`
  `room_dw_ralsei_castle_1f, room_dw_ralsei_castle_2f,`
  `room_dw_ralsei_castle_front, room_dw_ranking_a, room_dw_ranking_b,`
  `room_dw_ranking_c, room_dw_ranking_hub, room_dw_ranking_t,`
  `room_dw_ranking_z, room_dw_ranking_z_hallway, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rhythm_empty, room_dw_snow_zone,`
  `room_dw_snow_zone_battle, room_dw_snow_zone_east_door,`
  `room_dw_susiezilla, room_dw_susiezilla_empty,`
  `room_dw_teevie_audiencepits, room_dw_teevie_bonus_zone,`
  `room_dw_teevie_chef, room_dw_teevie_cowboy_zone_01_after,`
  `room_dw_teevie_cowboy_zone_01_intro,`
  `room_dw_teevie_cowboy_zone_02_after,`
  `room_dw_teevie_cowboy_zone_02_intro, room_dw_teevie_cutscene_final,`
  `room_dw_teevie_dust, room_dw_teevie_dust_south,`
  `room_dw_teevie_failure_cage, room_dw_teevie_intro,`
  `room_dw_teevie_large_01, room_dw_teevie_large_02,`
  `room_dw_teevie_lightmaze, room_dw_teevie_maze,`
  `room_dw_teevie_maze_chef, room_dw_teevie_maze_final,`
  `room_dw_teevie_maze_points, room_dw_teevie_maze_quiz,`
  `room_dw_teevie_preview, room_dw_teevie_preview_south,`
  `room_dw_teevie_rhythm, room_dw_teevie_ribbick,`
  `room_dw_teevie_ribbicks_a, room_dw_teevie_ribbicks_b,`
  `room_dw_teevie_sams, room_dw_teevie_shadow_guys,`
  `room_dw_teevie_shuttahmaze, room_dw_teevie_stealth,`
  `room_dw_teevie_stealth_c, room_dw_teevie_stealth_d,`
  `room_dw_teevie_susiebridge, room_dw_teevie_susiezilla,`
  `room_dw_teevie_watercooler, room_dw_tv_closet, room_dw_tv_curtain,`
  `room_dw_tv_cutscene1g, room_genanimtest, room_GMS2_test,`
  `room_overworldBulletEnemyTest, room_perspective_testing,`
  `room_rhythmgame_editor, room_rhythmgame_tenna_test,`
  `room_shadowmantle, room_shootout, room_susiezilla,`
  `room_susiezilla_singleScreenMockup, room_tennaAnimTest,`
  `room_tennaCutsceneTest`

### Acquisition record 0274

- chapter: `3`
- definition: `key:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_shop1`

### Acquisition record 0275

- chapter: `3`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_battletest`

### Acquisition record 0276

- chapter: `3`
- definition: `key:18`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_ranking_b`

### Acquisition record 0277

- chapter: `3`
- definition: `item:34`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0278

- chapter: `4`
- definition: `item:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0279

- chapter: `4`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0280

- chapter: `4`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0281

- chapter: `4`
- definition: `key:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0282

- chapter: `4`
- definition: `armor:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0283

- chapter: `4`
- definition: `item:6`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0284

- chapter: `4`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0285

- chapter: `4`
- definition: `item:12`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0286

- chapter: `4`
- definition: `item:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0287

- chapter: `4`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0288

- chapter: `4`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0289

- chapter: `4`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0290

- chapter: `4`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0291

- chapter: `4`
- definition: `armor:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0292

- chapter: `4`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0293

- chapter: `4`
- definition: `key:10`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0294

- chapter: `4`
- definition: `item:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0295

- chapter: `4`
- definition: `weapon:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0296

- chapter: `4`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0297

- chapter: `4`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0298

- chapter: `4`
- definition: `item:33`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_church_bellplay, room_dw_church_smallbells`

### Acquisition record 0299

- chapter: `4`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_church_darkmaze`

### Acquisition record 0300

- chapter: `4`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_church_arena`

### Acquisition record 0301

- chapter: `4`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_lw_church_main`

### Acquisition record 0302

- chapter: `4`
- definition: `item:60`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_lw_church_main`

### Acquisition record 0303

- chapter: `4`
- definition: `key:30`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_debug_pianotest, room_dw_church_bellhall_central,`
  `room_dw_church_organpuzzle, room_test_pianoGimmick`

### Acquisition record 0304

- chapter: `4`
- definition: `key:30`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_debug_pianotest, room_dw_church_bellhall_central,`
  `room_dw_church_organpuzzle, room_test_pianoGimmick`

### Acquisition record 0305

- chapter: `4`
- definition: `key:30`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_debug_pianotest, room_dw_church_bellhall_central,`
  `room_dw_church_organpuzzle, room_test_pianoGimmick`

### Acquisition record 0306

- chapter: `4`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_churchb_man`

### Acquisition record 0307

- chapter: `4`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0308

- chapter: `4`
- definition: `key:8`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_krisroom`

### Acquisition record 0309

- chapter: `4`
- definition: `key:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0310

- chapter: `4`
- definition: `key:31`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_church_jackenstein`

### Acquisition record 0311

- chapter: `4`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer,`
  `room_cutscene_tester, room_cutscene_tester_b, room_dark_twostoryTest,`
  `room_DARKbase_GMS2, room_DARKempty, room_darkness_example,`
  `room_darkness_example_2, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_layeredLevelTest,`
  `room_debug_pianotest, room_debug_smallface_dark,`
  `room_debug_windowEffect, room_dw_3d_tower_test,`
  `room_dw_castle_area_1, room_dw_castle_cafe, room_dw_castle_dojo,`
  `room_dw_castle_dungeon, room_dw_castle_east_door,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_kris_susie, room_dw_castle_rooms_queen,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_rooms_tenna, room_dw_castle_town, room_dw_castle_tv,`
  `room_dw_castle_tv_rhythm, room_dw_castle_tv_zone_1,`
  `room_dw_castle_tv_zone_2, room_dw_castle_tv_zone_3,`
  `room_dw_castle_tv_zone_battle, room_dw_castle_tv_zone_minigame,`
  `room_dw_castle_west_cliff, room_dw_church_arena,`
  `room_dw_church_b_intro, room_dw_church_bellclimb,`
  `room_dw_church_bellhall_bookroom, room_dw_church_bellhall_central,`
  `room_dw_church_bellhall_curtain, room_dw_church_bellhall_east,`
  `room_dw_church_bellhall_west, room_dw_church_bellplay,`
  `room_dw_church_bellsareawest, room_dw_church_biblioxencounter,`
  `room_dw_church_bookcase, room_dw_church_bookenemywest,`
  `room_dw_church_bookshelfpuzzle, room_dw_church_bookshelfpuzzle_rev,`
  `room_dw_church_bookshelfpuzzle1, room_dw_church_bookshelfpuzzle2,`
  `room_dw_church_candlelighting, room_dw_church_candlesroom1,`
  `room_dw_church_chase_old, room_dw_church_claw,`
  `room_dw_church_climbtut, room_dw_church_crumbletower,`
  `room_dw_church_dark_fire_puzzle, room_dw_church_darkbell_old,`
  `room_dw_church_darkclimb, room_dw_church_darkmaze,`
  `room_dw_church_darkroom_old, room_dw_church_darkroom1_old,`
  `room_dw_church_dogclimb, room_dw_church_fastwater,`
  `room_dw_church_fountainconnection, room_dw_church_gersonstudy,`
  `room_dw_church_glass, room_dw_church_guei, room_dw_church_gueitest,`
  `room_dw_church_holywatercooler, room_dw_church_intro_gerson,`
  `room_dw_church_intro_guei, room_dw_church_intro1,`
  `room_dw_church_intro3, room_dw_church_intropiano,`
  `room_dw_church_jackenstein, room_dw_church_knightclimb,`
  `room_dw_church_knightclimb_post, room_dw_church_lantern_hallway,`
  `room_dw_church_lantern_hallway_old, room_dw_church_lantern1_old,`
  `room_dw_church_lantern1_old_old, room_dw_church_lantern2,`
  `room_dw_church_librarybookenemy, room_dw_church_minorlegend,`
  `room_dw_church_mizzleencounter, room_dw_church_moneyfountain,`
  `room_dw_church_northprophecies, room_dw_church_npcroom_pools1,`
  `room_dw_church_npcroom_shelfclimb, room_dw_church_nwconnect,`
  `room_dw_church_offering, room_dw_church_organpuzzle,`
  `room_dw_church_pianopiece_left, room_dw_church_pianopiece_left_b,`
  `room_dw_church_pianopiece_right,`
  `room_dw_church_pianopiece_rightprophecy, room_dw_church_pianopuzzle,`
  `room_dw_church_poolsroom1, room_dw_church_poolsroom1_east,`
  `room_dw_church_poolsroom2, room_dw_church_poolsroom2south,`
  `room_dw_church_quicktest, room_dw_church_rightconnect,`
  `room_dw_church_ripplepuzzle, room_dw_church_ripplepuzzle_postgers,`
  `room_dw_church_rippletest, room_dw_church_rippleworship,`
  `room_dw_church_ripseq1, room_dw_church_ripseq2,`
  `room_dw_church_savepoint, room_dw_church_secretpiano,`
  `room_dw_church_shadowgerson, room_dw_church_shelfclimb1,`
  `room_dw_church_shelfclimb2, room_dw_church_shiftclimb,`
  `room_dw_church_sideclimb, room_dw_church_slidingbookshelf,`
  `room_dw_church_smallbells, room_dw_church_solowaterfall,`
  `room_dw_church_stainedglasspreview, room_dw_church_staircase,`
  `room_dw_church_stairs_stainedglass, room_dw_church_stairs_topleft,`
  `room_dw_church_stairs_topright, room_dw_church_stairs_west_bell,`
  `room_dw_church_stairspreview, room_dw_church_statueclimb,`
  `room_dw_church_statueclimb_npcroom, room_dw_church_statueroom,`
  `room_dw_church_statueroom_old, room_dw_church_swingingbell,`
  `room_dw_church_tallbookcases, room_dw_church_tallbookcases_backup,`
  `room_dw_church_tower1, room_dw_church_trueclimbadventure,`
  `room_dw_church_turtles, room_dw_church_waterfallroom,`
  `room_dw_church_waterfalltearoom, room_dw_church_worshiproom,`
  `room_dw_churchb_bellroom, room_dw_churchb_bookshelf,`
  `room_dw_churchb_darkclimb, room_dw_churchb_darkclimb_scene,`
  `room_dw_churchb_escherstaircase, room_dw_churchb_extinguisher,`
  `room_dw_churchb_fireplace, room_dw_churchb_fountain,`
  `room_dw_churchb_gallery, room_dw_churchb_gersonchase,`
  `room_dw_churchb_gersonstudy, room_dw_churchb_library,`
  `room_dw_churchb_library_alternate, room_dw_churchb_libraryconnector,`
  `room_dw_churchb_man, room_dw_churchb_moneyfountain,`
  `room_dw_churchb_nongerson, room_dw_churchb_nongerson_post,`
  `room_dw_churchb_prophecyencounter, room_dw_churchb_prophecymaze,`
  `room_dw_churchb_prophecymaze_old, room_dw_churchb_ripple1,`
  `room_dw_churchb_ripplepost, room_dw_churchb_rotatingtower,`
  `room_dw_churchb_rotatingtower_old,`
  `room_dw_churchb_rotatingtower_tiled, room_dw_churchb_rotatingtower2,`
  `room_dw_churchb_savepoint, room_dw_churchb_staircaseintro,`
  `room_dw_churchb_windows, room_dw_churchb_worshiproom,`
  `room_dw_churchc_angelprophecy,`
  `room_dw_churchc_angelprophecy_encounter, room_dw_churchc_darkswords,`
  `room_dw_churchc_dodge, room_dw_churchc_encounter1,`
  `room_dw_churchc_encounter2, room_dw_churchc_final_prophecy,`
  `room_dw_churchc_finalclimb, room_dw_churchc_insidetitan,`
  `room_dw_churchc_prepretitan, room_dw_churchc_pretitan,`
  `room_dw_churchc_prophecies, room_dw_churchc_prophecies_backup,`
  `room_dw_churchc_ripplesneak_poc, room_dw_churchc_savepoint,`
  `room_dw_churchc_slidingpiano, room_dw_churchc_superprophecies,`
  `room_dw_churchc_titanclimb1, room_dw_churchc_titanclimb1_old,`
  `room_dw_churchc_titanclimb1_post, room_dw_churchc_titanclimb1_tiled,`
  `room_dw_churchc_titanclimb2, room_dw_churchc_titanclimb2_old,`
  `room_dw_churchc_titanclimb2_old2, room_dw_churchc_titanclimb2_post,`
  `room_dw_churchc_titanclimb2_tiled, room_dw_churchc_titandefeated,`
  `room_dw_churchc_treasurechest, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_front, room_dw_rhythm,`
  `room_dw_rhythm_countdown, room_dw_rotating_tower,`
  `room_dw_titan_tower_test, room_gersonbattleroomtest, room_GMS2_test,`
  `room_overworld_darkmaku_blocks, room_overworld_darkmaku_ring,`
  `room_overworld_darkmakumaze, room_overworldBulletEnemyTest,`
  `room_overworldDarknessBulletTest, room_ripple_test,`
  `room_rotating_tower_new_example, room_rotating_tower_new_test,`
  `room_shapetest, room_test_climb_0001, room_test_climb_cameratest,`
  `room_test_climb_enterexit, room_test_climb_new, room_test_climb_new2,`
  `room_test_pianoGimmick, room_test_remotePiano`

### Acquisition record 0312

- chapter: `4`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_battletest`

### Acquisition record 0313

- chapter: `5`
- definition: `item:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0314

- chapter: `5`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0315

- chapter: `5`
- definition: `item:1`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0316

- chapter: `5`
- definition: `key:3`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0317

- chapter: `5`
- definition: `armor:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0318

- chapter: `5`
- definition: `item:6`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0319

- chapter: `5`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0320

- chapter: `5`
- definition: `item:12`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0321

- chapter: `5`
- definition: `item:9`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0322

- chapter: `5`
- definition: `item:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0323

- chapter: `5`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0324

- chapter: `5`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0325

- chapter: `5`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0326

- chapter: `5`
- definition: `armor:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0327

- chapter: `5`
- definition: `item:7`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0328

- chapter: `5`
- definition: `key:10`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0329

- chapter: `5`
- definition: `item:16`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0330

- chapter: `5`
- definition: `weapon:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0331

- chapter: `5`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0332

- chapter: `5`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-uncertain`
- rooms: `none joined`

### Acquisition record 0333

- chapter: `5`
- definition: `key:13`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_pink_encounter`

### Acquisition record 0334

- chapter: `5`
- definition: `key:20`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0335

- chapter: `5`
- definition: `key:27`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_yellow_miniboss`

### Acquisition record 0336

- chapter: `5`
- definition: `weapon:35`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production-subsystem`
- rooms: `room_dw_post_fountain_close`

### Acquisition record 0337

- chapter: `5`
- definition: `key:22`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_sandtrap`

### Acquisition record 0338

- chapter: `5`
- definition: `key:23`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_sandtrap`

### Acquisition record 0339

- chapter: `5`
- definition: `key:21`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_sandtrap`

### Acquisition record 0340

- chapter: `5`
- definition: `key:2`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_man`

### Acquisition record 0341

- chapter: `5`
- definition: `key:33`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_bromides`

### Acquisition record 0342

- chapter: `5`
- definition: `key:25`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_garden_aquashrine`

### Acquisition record 0343

- chapter: `5`
- definition: `key:26`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_dangerous_platforming`

### Acquisition record 0344

- chapter: `5`
- definition: `key:28`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_dangerous_platforming`

### Acquisition record 0345

- chapter: `5`
- definition: `key:29`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `production`
- rooms: `room_dw_fcastle_yellow_miniboss`

### Acquisition record 0346

- chapter: `5`
- definition: `key:5`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Acquisition record 0347

- chapter: `5`
- definition: `item:4`
- chain: `exact-acquisition-call`
- join: `matched`
- status: `debug`
- rooms: `room_battletest, room_bullettest, room_bullettest_new,`
  `room_castle_tutorial, room_cc_clover, room_cc_lancer, room_climbtest,`
  `room_cutscene_tester, room_cutscene_tester_b, room_DARKbase_GMS2,`
  `room_darkbulbTest, room_DARKempty, room_debug_battleBalloon,`
  `room_debug_choicer_dark, room_debug_smallface_dark,`
  `room_dogplatforming, room_dw_castle_area_1, room_dw_castle_cafe,`
  `room_dw_castle_church_climb, room_dw_castle_church_entrance,`
  `room_dw_castle_dojo, room_dw_castle_dungeon,`
  `room_dw_castle_east_door, room_dw_castle_music,`
  `room_dw_castle_restaurant, room_dw_castle_rooms_kris,`
  `room_dw_castle_rooms_ralsei, room_dw_castle_rooms_susie,`
  `room_dw_castle_town, room_dw_castle_tv, room_dw_castle_tv_kikky,`
  `room_dw_castle_tv_mike, room_dw_castle_tv_rhythm,`
  `room_dw_castle_west_cliff, room_dw_cliff_bonuscombat,`
  `room_dw_cliff_bunnyfarm, room_dw_cliff_climbrefresher,`
  `room_dw_cliff_cutdown_tutorial, room_dw_cliff_dash_runner,`
  `room_dw_cliff_eastcliff, room_dw_cliff_finaldash,`
  `room_dw_cliff_gardentransition_new, room_dw_cliff_kawkawdash,`
  `room_dw_cliff_netskieclimb, room_dw_cliff_netskieclimb_behind,`
  `room_dw_cliff_precipice, room_dw_cliff_seth_miniboss,`
  `room_dw_cliff_sethaqua_battle, room_dw_cliff_shicave,`
  `room_dw_cliff_shop, room_dw_cliff_silver_hammer,`
  `room_dw_cliff_twirlflowerplatforming, room_dw_cliff_twirlflowerwind,`
  `room_dw_cliff_verticalwind, room_dw_cliff_verticalwind_post,`
  `room_dw_cliff_yellowcave, room_dw_dogballoon, room_dw_fcastle_asgore,`
  `room_dw_fcastle_blueroom, room_dw_fcastle_bounce_1,`
  `room_dw_fcastle_bounce_3, room_dw_fcastle_bromides,`
  `room_dw_fcastle_cafe, room_dw_fcastle_dangerous_platforming,`
  `room_dw_fcastle_entrance, room_dw_fcastle_final_save,`
  `room_dw_fcastle_flowerclimb, room_dw_fcastle_flowerclimb_for_tiling,`
  `room_dw_fcastle_flowery, room_dw_fcastle_flowerydash,`
  `room_dw_fcastle_foxhunt, room_dw_fcastle_foxhunt_chaos,`
  `room_dw_fcastle_foxhunt_secret, room_dw_fcastle_foxhunt_socks,`
  `room_dw_fcastle_foxhunt_terakota, room_dw_fcastle_foyer,`
  `room_dw_fcastle_fusumadodge, room_dw_fcastle_gloves_tower,`
  `room_dw_fcastle_green_checkpoint,`
  `room_dw_fcastle_green_orange_battle, room_dw_fcastle_heldmushrooms,`
  `room_dw_fcastle_left_penultimate, room_dw_fcastle_left_twodoors,`
  `room_dw_fcastle_left_wing_floweryscene,`
  `room_dw_fcastle_obscured_bullets, room_dw_fcastle_onsen,`
  `room_dw_fcastle_orange_gauntlet,`
  `room_dw_fcastle_orange_puppet_introduction,`
  `room_dw_fcastle_partyjail, room_dw_fcastle_pinkroom,`
  `room_dw_fcastle_pinkshop, room_dw_fcastle_post_party_jail,`
  `room_dw_fcastle_right_endingscene, room_dw_fcastle_right_penultimate,`
  `room_dw_fcastle_right_puzzle,`
  `room_dw_fcastle_right_wing_floweryscene, room_dw_fcastle_sandtrap,`
  `room_dw_fcastle_second_diner, room_dw_fcastle_seth_encounter,`
  `room_dw_fcastle_shadowplatformTest, room_dw_fcastle_shinobeetle_3d,`
  `room_dw_fcastle_shinobeetle_encounter, room_dw_fcastle_sidepuzzle,`
  `room_dw_fcastle_terracotta_bonus,`
  `room_dw_fcastle_terracotta_encounter,`
  `room_dw_fcastle_terracotta_puzzle, room_dw_fcastle_top_ascent,`
  `room_dw_fcastle_top_challenge, room_dw_fcastle_top_descent,`
  `room_dw_fcastle_top_entrance, room_dw_fcastle_top_fountain,`
  `room_dw_fcastle_top_intro, room_dw_fcastle_top_pinkdoor,`
  `room_dw_fcastle_top_staircase_1, room_dw_fcastle_top_staircase_2,`
  `room_dw_fcastle_trainroom, room_dw_fcastle_ultradash,`
  `room_dw_fcastle_yellow_miniboss, room_dw_fcastle_yellowblue,`
  `room_dw_fcastle_yellowjail, room_dw_fcastle_zenlooker,`
  `room_dw_flowery_tree, room_dw_garden_aqua,`
  `room_dw_garden_aquadarkness, room_dw_garden_aquadash,`
  `room_dw_garden_aquadash_plat, room_dw_garden_aquahole,`
  `room_dw_garden_aquahole_left, room_dw_garden_aquaplatforming,`
  `room_dw_garden_aquashrine, room_dw_garden_aquatransition,`
  `room_dw_garden_cliffexit, room_dw_garden_diner,`
  `room_dw_garden_enemyrush, room_dw_garden_finalplatforming,`
  `room_dw_garden_finalplatforming_right, room_dw_garden_firstdash,`
  `room_dw_garden_fishingspot, room_dw_garden_floradinnencounter,`
  `room_dw_garden_flowerygardening, room_dw_garden_hardpressureplates,`
  `room_dw_garden_hopschef, room_dw_garden_hospital,`
  `room_dw_garden_intro, room_dw_garden_meetflowery,`
  `room_dw_garden_mushrooms, room_dw_garden_newdash,`
  `room_dw_garden_pedestal, room_dw_garden_platshortcut,`
  `room_dw_garden_ralseicupboard, room_dw_garden_riverchest,`
  `room_dw_garden_shearydodge, room_dw_garden_shearyguide,`
  `room_dw_garden_starwalkerdash, room_dw_garden_susiechase,`
  `room_dw_garden_wateringcan_aqua, room_dw_petaltest,`
  `room_dw_pink_encounter, room_dw_post_flowery_battle,`
  `room_dw_post_fountain_close, room_dw_ralsei_castle_1f,`
  `room_dw_ralsei_castle_2f, room_dw_ralsei_castle_3f,`
  `room_dw_ralsei_castle_basketball, room_dw_ralsei_castle_front,`
  `room_dw_rhythm, room_dw_rhythm_countdown, room_floortex_test,`
  `room_GMS2_test, room_man, room_overworldBulletEnemyTest,`
  `room_plat_lab`

### Runtime effect record 0001

- chapter: `1`
- definition: `item:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0002

- chapter: `1`
- definition: `item:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0003

- chapter: `1`
- definition: `item:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0004

- chapter: `1`
- definition: `item:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0005

- chapter: `1`
- definition: `item:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0006

- chapter: `1`
- definition: `item:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0007

- chapter: `1`
- definition: `item:7`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0008

- chapter: `1`
- definition: `item:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0009

- chapter: `1`
- definition: `item:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0010

- chapter: `1`
- definition: `item:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0011

- chapter: `1`
- definition: `item:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0012

- chapter: `1`
- definition: `item:12`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0013

- chapter: `1`
- definition: `item:13`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0014

- chapter: `1`
- definition: `item:14`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0015

- chapter: `1`
- definition: `item:15`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0016

- chapter: `1`
- definition: `item:300`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0017

- chapter: `1`
- definition: `item:301`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0018

- chapter: `1`
- definition: `item:302`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0019

- chapter: `1`
- definition: `item:313`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0020

- chapter: `1`
- definition: `spell:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0021

- chapter: `1`
- definition: `spell:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0022

- chapter: `1`
- definition: `spell:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0023

- chapter: `1`
- definition: `spell:3`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0024

- chapter: `1`
- definition: `spell:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0025

- chapter: `1`
- definition: `spell:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0026

- chapter: `1`
- definition: `spell:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0027

- chapter: `1`
- definition: `spell:100`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0028

- chapter: `1`
- definition: `spell:200`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0029

- chapter: `1`
- definition: `spell:201`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0030

- chapter: `1`
- definition: `spell:202`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0031

- chapter: `1`
- definition: `spell:203`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0032

- chapter: `1`
- definition: `spell:204`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0033

- chapter: `1`
- definition: `spell:205`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0034

- chapter: `1`
- definition: `spell:206`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0035

- chapter: `1`
- definition: `spell:207`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0036

- chapter: `1`
- definition: `spell:208`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0037

- chapter: `1`
- definition: `spell:209`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0038

- chapter: `1`
- definition: `spell:210`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0039

- chapter: `1`
- definition: `spell:211`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0040

- chapter: `1`
- definition: `spell:212`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0041

- chapter: `1`
- definition: `spell:213`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0042

- chapter: `1`
- definition: `spell:214`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0043

- chapter: `1`
- definition: `spell:215`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0044

- chapter: `2`
- definition: `item:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0045

- chapter: `2`
- definition: `item:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0046

- chapter: `2`
- definition: `item:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0047

- chapter: `2`
- definition: `item:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0048

- chapter: `2`
- definition: `item:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0049

- chapter: `2`
- definition: `item:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0050

- chapter: `2`
- definition: `item:7`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0051

- chapter: `2`
- definition: `item:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0052

- chapter: `2`
- definition: `item:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0053

- chapter: `2`
- definition: `item:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0054

- chapter: `2`
- definition: `item:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0055

- chapter: `2`
- definition: `item:12`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0056

- chapter: `2`
- definition: `item:13`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0057

- chapter: `2`
- definition: `item:14`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0058

- chapter: `2`
- definition: `item:15`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0059

- chapter: `2`
- definition: `item:16`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0060

- chapter: `2`
- definition: `item:17`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0061

- chapter: `2`
- definition: `item:18`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0062

- chapter: `2`
- definition: `item:19`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0063

- chapter: `2`
- definition: `item:20`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0064

- chapter: `2`
- definition: `item:21`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0065

- chapter: `2`
- definition: `item:22`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0066

- chapter: `2`
- definition: `item:23`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0067

- chapter: `2`
- definition: `item:24`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0068

- chapter: `2`
- definition: `item:25`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0069

- chapter: `2`
- definition: `item:26`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0070

- chapter: `2`
- definition: `item:27`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0071

- chapter: `2`
- definition: `item:28`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0072

- chapter: `2`
- definition: `item:29`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0073

- chapter: `2`
- definition: `item:30`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0074

- chapter: `2`
- definition: `item:31`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0075

- chapter: `2`
- definition: `item:32`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0076

- chapter: `2`
- definition: `item:33`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0077

- chapter: `2`
- definition: `item:300`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0078

- chapter: `2`
- definition: `item:301`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0079

- chapter: `2`
- definition: `item:302`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0080

- chapter: `2`
- definition: `item:308`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0081

- chapter: `2`
- definition: `item:313`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0082

- chapter: `2`
- definition: `spell:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0083

- chapter: `2`
- definition: `spell:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0084

- chapter: `2`
- definition: `spell:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0085

- chapter: `2`
- definition: `spell:3`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0086

- chapter: `2`
- definition: `spell:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0087

- chapter: `2`
- definition: `spell:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0088

- chapter: `2`
- definition: `spell:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0089

- chapter: `2`
- definition: `spell:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0090

- chapter: `2`
- definition: `spell:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0091

- chapter: `2`
- definition: `spell:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0092

- chapter: `2`
- definition: `spell:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0093

- chapter: `2`
- definition: `spell:100`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0094

- chapter: `2`
- definition: `spell:200`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0095

- chapter: `2`
- definition: `spell:201`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0096

- chapter: `2`
- definition: `spell:202`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0097

- chapter: `2`
- definition: `spell:203`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0098

- chapter: `2`
- definition: `spell:204`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0099

- chapter: `2`
- definition: `spell:205`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0100

- chapter: `2`
- definition: `spell:206`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0101

- chapter: `2`
- definition: `spell:207`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0102

- chapter: `2`
- definition: `spell:208`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0103

- chapter: `2`
- definition: `spell:209`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0104

- chapter: `2`
- definition: `spell:210`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0105

- chapter: `2`
- definition: `spell:211`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0106

- chapter: `2`
- definition: `spell:212`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0107

- chapter: `2`
- definition: `spell:213`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0108

- chapter: `2`
- definition: `spell:214`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0109

- chapter: `2`
- definition: `spell:215`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0110

- chapter: `2`
- definition: `spell:216`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0111

- chapter: `2`
- definition: `spell:217`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0112

- chapter: `2`
- definition: `spell:218`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0113

- chapter: `2`
- definition: `spell:219`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0114

- chapter: `2`
- definition: `spell:220`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0115

- chapter: `2`
- definition: `spell:221`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0116

- chapter: `2`
- definition: `spell:222`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0117

- chapter: `2`
- definition: `spell:223`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0118

- chapter: `2`
- definition: `spell:224`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0119

- chapter: `2`
- definition: `spell:225`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0120

- chapter: `2`
- definition: `spell:226`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0121

- chapter: `2`
- definition: `spell:227`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0122

- chapter: `2`
- definition: `spell:228`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0123

- chapter: `2`
- definition: `spell:229`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0124

- chapter: `2`
- definition: `spell:230`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0125

- chapter: `2`
- definition: `spell:231`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0126

- chapter: `2`
- definition: `spell:232`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0127

- chapter: `2`
- definition: `spell:233`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0128

- chapter: `3`
- definition: `item:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0129

- chapter: `3`
- definition: `item:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0130

- chapter: `3`
- definition: `item:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0131

- chapter: `3`
- definition: `item:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0132

- chapter: `3`
- definition: `item:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0133

- chapter: `3`
- definition: `item:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0134

- chapter: `3`
- definition: `item:7`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0135

- chapter: `3`
- definition: `item:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0136

- chapter: `3`
- definition: `item:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0137

- chapter: `3`
- definition: `item:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0138

- chapter: `3`
- definition: `item:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0139

- chapter: `3`
- definition: `item:12`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0140

- chapter: `3`
- definition: `item:13`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0141

- chapter: `3`
- definition: `item:14`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0142

- chapter: `3`
- definition: `item:15`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0143

- chapter: `3`
- definition: `item:16`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0144

- chapter: `3`
- definition: `item:17`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0145

- chapter: `3`
- definition: `item:18`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0146

- chapter: `3`
- definition: `item:19`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0147

- chapter: `3`
- definition: `item:20`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0148

- chapter: `3`
- definition: `item:21`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0149

- chapter: `3`
- definition: `item:22`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0150

- chapter: `3`
- definition: `item:23`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0151

- chapter: `3`
- definition: `item:24`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0152

- chapter: `3`
- definition: `item:25`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0153

- chapter: `3`
- definition: `item:26`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0154

- chapter: `3`
- definition: `item:27`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0155

- chapter: `3`
- definition: `item:28`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0156

- chapter: `3`
- definition: `item:29`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0157

- chapter: `3`
- definition: `item:30`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0158

- chapter: `3`
- definition: `item:31`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0159

- chapter: `3`
- definition: `item:32`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0160

- chapter: `3`
- definition: `item:33`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0161

- chapter: `3`
- definition: `item:34`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0162

- chapter: `3`
- definition: `item:35`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0163

- chapter: `3`
- definition: `item:36`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0164

- chapter: `3`
- definition: `item:37`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0165

- chapter: `3`
- definition: `item:38`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0166

- chapter: `3`
- definition: `item:39`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0167

- chapter: `3`
- definition: `item:300`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0168

- chapter: `3`
- definition: `item:301`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0169

- chapter: `3`
- definition: `item:302`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0170

- chapter: `3`
- definition: `item:308`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0171

- chapter: `3`
- definition: `item:313`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0172

- chapter: `3`
- definition: `spell:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0173

- chapter: `3`
- definition: `spell:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0174

- chapter: `3`
- definition: `spell:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0175

- chapter: `3`
- definition: `spell:3`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0176

- chapter: `3`
- definition: `spell:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0177

- chapter: `3`
- definition: `spell:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0178

- chapter: `3`
- definition: `spell:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0179

- chapter: `3`
- definition: `spell:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0180

- chapter: `3`
- definition: `spell:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0181

- chapter: `3`
- definition: `spell:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0182

- chapter: `3`
- definition: `spell:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0183

- chapter: `3`
- definition: `spell:100`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0184

- chapter: `3`
- definition: `spell:200`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0185

- chapter: `3`
- definition: `spell:201`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0186

- chapter: `3`
- definition: `spell:202`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0187

- chapter: `3`
- definition: `spell:203`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0188

- chapter: `3`
- definition: `spell:204`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0189

- chapter: `3`
- definition: `spell:205`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0190

- chapter: `3`
- definition: `spell:206`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0191

- chapter: `3`
- definition: `spell:207`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0192

- chapter: `3`
- definition: `spell:208`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0193

- chapter: `3`
- definition: `spell:209`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0194

- chapter: `3`
- definition: `spell:210`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0195

- chapter: `3`
- definition: `spell:211`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0196

- chapter: `3`
- definition: `spell:212`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0197

- chapter: `3`
- definition: `spell:213`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0198

- chapter: `3`
- definition: `spell:214`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0199

- chapter: `3`
- definition: `spell:215`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0200

- chapter: `3`
- definition: `spell:216`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0201

- chapter: `3`
- definition: `spell:217`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0202

- chapter: `3`
- definition: `spell:218`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0203

- chapter: `3`
- definition: `spell:219`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0204

- chapter: `3`
- definition: `spell:220`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0205

- chapter: `3`
- definition: `spell:221`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0206

- chapter: `3`
- definition: `spell:222`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0207

- chapter: `3`
- definition: `spell:223`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0208

- chapter: `3`
- definition: `spell:224`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0209

- chapter: `3`
- definition: `spell:225`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0210

- chapter: `3`
- definition: `spell:226`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0211

- chapter: `3`
- definition: `spell:227`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0212

- chapter: `3`
- definition: `spell:228`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0213

- chapter: `3`
- definition: `spell:229`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0214

- chapter: `3`
- definition: `spell:230`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0215

- chapter: `3`
- definition: `spell:231`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0216

- chapter: `3`
- definition: `spell:232`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0217

- chapter: `3`
- definition: `spell:233`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0218

- chapter: `3`
- definition: `spell:234`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0219

- chapter: `3`
- definition: `spell:235`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0220

- chapter: `3`
- definition: `spell:236`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0221

- chapter: `3`
- definition: `spell:237`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0222

- chapter: `3`
- definition: `spell:238`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0223

- chapter: `3`
- definition: `spell:239`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0224

- chapter: `4`
- definition: `item:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0225

- chapter: `4`
- definition: `item:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0226

- chapter: `4`
- definition: `item:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0227

- chapter: `4`
- definition: `item:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0228

- chapter: `4`
- definition: `item:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0229

- chapter: `4`
- definition: `item:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0230

- chapter: `4`
- definition: `item:7`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0231

- chapter: `4`
- definition: `item:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0232

- chapter: `4`
- definition: `item:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0233

- chapter: `4`
- definition: `item:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0234

- chapter: `4`
- definition: `item:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0235

- chapter: `4`
- definition: `item:12`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0236

- chapter: `4`
- definition: `item:13`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0237

- chapter: `4`
- definition: `item:14`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0238

- chapter: `4`
- definition: `item:15`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0239

- chapter: `4`
- definition: `item:16`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0240

- chapter: `4`
- definition: `item:17`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0241

- chapter: `4`
- definition: `item:18`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0242

- chapter: `4`
- definition: `item:19`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0243

- chapter: `4`
- definition: `item:20`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0244

- chapter: `4`
- definition: `item:21`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0245

- chapter: `4`
- definition: `item:22`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0246

- chapter: `4`
- definition: `item:23`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0247

- chapter: `4`
- definition: `item:24`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0248

- chapter: `4`
- definition: `item:25`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0249

- chapter: `4`
- definition: `item:26`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0250

- chapter: `4`
- definition: `item:27`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0251

- chapter: `4`
- definition: `item:28`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0252

- chapter: `4`
- definition: `item:29`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0253

- chapter: `4`
- definition: `item:30`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0254

- chapter: `4`
- definition: `item:31`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0255

- chapter: `4`
- definition: `item:32`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0256

- chapter: `4`
- definition: `item:33`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0257

- chapter: `4`
- definition: `item:34`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0258

- chapter: `4`
- definition: `item:35`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0259

- chapter: `4`
- definition: `item:36`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0260

- chapter: `4`
- definition: `item:37`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0261

- chapter: `4`
- definition: `item:38`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0262

- chapter: `4`
- definition: `item:39`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0263

- chapter: `4`
- definition: `item:60`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0264

- chapter: `4`
- definition: `item:61`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0265

- chapter: `4`
- definition: `item:62`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0266

- chapter: `4`
- definition: `item:63`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0267

- chapter: `4`
- definition: `item:300`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0268

- chapter: `4`
- definition: `item:301`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0269

- chapter: `4`
- definition: `item:302`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0270

- chapter: `4`
- definition: `item:308`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0271

- chapter: `4`
- definition: `item:313`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0272

- chapter: `4`
- definition: `item:330`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0273

- chapter: `4`
- definition: `item:331`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0274

- chapter: `4`
- definition: `spell:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0275

- chapter: `4`
- definition: `spell:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0276

- chapter: `4`
- definition: `spell:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0277

- chapter: `4`
- definition: `spell:3`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0278

- chapter: `4`
- definition: `spell:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0279

- chapter: `4`
- definition: `spell:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0280

- chapter: `4`
- definition: `spell:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0281

- chapter: `4`
- definition: `spell:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0282

- chapter: `4`
- definition: `spell:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0283

- chapter: `4`
- definition: `spell:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0284

- chapter: `4`
- definition: `spell:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0285

- chapter: `4`
- definition: `spell:100`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0286

- chapter: `4`
- definition: `spell:200`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0287

- chapter: `4`
- definition: `spell:201`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0288

- chapter: `4`
- definition: `spell:202`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0289

- chapter: `4`
- definition: `spell:203`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0290

- chapter: `4`
- definition: `spell:204`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0291

- chapter: `4`
- definition: `spell:205`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0292

- chapter: `4`
- definition: `spell:206`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0293

- chapter: `4`
- definition: `spell:207`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0294

- chapter: `4`
- definition: `spell:208`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0295

- chapter: `4`
- definition: `spell:209`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0296

- chapter: `4`
- definition: `spell:210`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0297

- chapter: `4`
- definition: `spell:211`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0298

- chapter: `4`
- definition: `spell:212`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0299

- chapter: `4`
- definition: `spell:213`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0300

- chapter: `4`
- definition: `spell:214`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0301

- chapter: `4`
- definition: `spell:215`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0302

- chapter: `4`
- definition: `spell:216`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0303

- chapter: `4`
- definition: `spell:217`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0304

- chapter: `4`
- definition: `spell:218`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0305

- chapter: `4`
- definition: `spell:219`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0306

- chapter: `4`
- definition: `spell:220`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0307

- chapter: `4`
- definition: `spell:221`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0308

- chapter: `4`
- definition: `spell:222`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0309

- chapter: `4`
- definition: `spell:223`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0310

- chapter: `4`
- definition: `spell:224`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0311

- chapter: `4`
- definition: `spell:225`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0312

- chapter: `4`
- definition: `spell:226`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0313

- chapter: `4`
- definition: `spell:227`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0314

- chapter: `4`
- definition: `spell:228`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0315

- chapter: `4`
- definition: `spell:229`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0316

- chapter: `4`
- definition: `spell:230`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0317

- chapter: `4`
- definition: `spell:231`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0318

- chapter: `4`
- definition: `spell:232`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0319

- chapter: `4`
- definition: `spell:233`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0320

- chapter: `4`
- definition: `spell:234`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0321

- chapter: `4`
- definition: `spell:235`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0322

- chapter: `4`
- definition: `spell:236`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0323

- chapter: `4`
- definition: `spell:237`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0324

- chapter: `4`
- definition: `spell:238`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0325

- chapter: `4`
- definition: `spell:239`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0326

- chapter: `4`
- definition: `spell:260`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0327

- chapter: `4`
- definition: `spell:261`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0328

- chapter: `4`
- definition: `spell:262`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0329

- chapter: `4`
- definition: `spell:263`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0330

- chapter: `5`
- definition: `item:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0331

- chapter: `5`
- definition: `item:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0332

- chapter: `5`
- definition: `item:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0333

- chapter: `5`
- definition: `item:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0334

- chapter: `5`
- definition: `item:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0335

- chapter: `5`
- definition: `item:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0336

- chapter: `5`
- definition: `item:7`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0337

- chapter: `5`
- definition: `item:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0338

- chapter: `5`
- definition: `item:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0339

- chapter: `5`
- definition: `item:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0340

- chapter: `5`
- definition: `item:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0341

- chapter: `5`
- definition: `item:12`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0342

- chapter: `5`
- definition: `item:13`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0343

- chapter: `5`
- definition: `item:14`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0344

- chapter: `5`
- definition: `item:15`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0345

- chapter: `5`
- definition: `item:16`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0346

- chapter: `5`
- definition: `item:17`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0347

- chapter: `5`
- definition: `item:18`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0348

- chapter: `5`
- definition: `item:19`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0349

- chapter: `5`
- definition: `item:20`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0350

- chapter: `5`
- definition: `item:21`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0351

- chapter: `5`
- definition: `item:22`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0352

- chapter: `5`
- definition: `item:23`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0353

- chapter: `5`
- definition: `item:24`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0354

- chapter: `5`
- definition: `item:25`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0355

- chapter: `5`
- definition: `item:26`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0356

- chapter: `5`
- definition: `item:27`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0357

- chapter: `5`
- definition: `item:28`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0358

- chapter: `5`
- definition: `item:29`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0359

- chapter: `5`
- definition: `item:30`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0360

- chapter: `5`
- definition: `item:31`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0361

- chapter: `5`
- definition: `item:32`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0362

- chapter: `5`
- definition: `item:33`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0363

- chapter: `5`
- definition: `item:34`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0364

- chapter: `5`
- definition: `item:35`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0365

- chapter: `5`
- definition: `item:36`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0366

- chapter: `5`
- definition: `item:37`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0367

- chapter: `5`
- definition: `item:38`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0368

- chapter: `5`
- definition: `item:39`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0369

- chapter: `5`
- definition: `item:40`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0370

- chapter: `5`
- definition: `item:41`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0371

- chapter: `5`
- definition: `item:42`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0372

- chapter: `5`
- definition: `item:43`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0373

- chapter: `5`
- definition: `item:60`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0374

- chapter: `5`
- definition: `item:61`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0375

- chapter: `5`
- definition: `item:62`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0376

- chapter: `5`
- definition: `item:63`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0377

- chapter: `5`
- definition: `item:64`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0378

- chapter: `5`
- definition: `item:65`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0379

- chapter: `5`
- definition: `item:66`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0380

- chapter: `5`
- definition: `item:67`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0381

- chapter: `5`
- definition: `item:68`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0382

- chapter: `5`
- definition: `item:69`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0383

- chapter: `5`
- definition: `item:70`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0384

- chapter: `5`
- definition: `item:300`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0385

- chapter: `5`
- definition: `item:301`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0386

- chapter: `5`
- definition: `item:302`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0387

- chapter: `5`
- definition: `item:308`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0388

- chapter: `5`
- definition: `item:313`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0389

- chapter: `5`
- definition: `item:324`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0390

- chapter: `5`
- definition: `item:333`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0391

- chapter: `5`
- definition: `spell:0`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0392

- chapter: `5`
- definition: `spell:1`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0393

- chapter: `5`
- definition: `spell:2`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0394

- chapter: `5`
- definition: `spell:3`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0395

- chapter: `5`
- definition: `spell:4`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0396

- chapter: `5`
- definition: `spell:5`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0397

- chapter: `5`
- definition: `spell:6`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0398

- chapter: `5`
- definition: `spell:8`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0399

- chapter: `5`
- definition: `spell:9`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0400

- chapter: `5`
- definition: `spell:10`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0401

- chapter: `5`
- definition: `spell:11`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0402

- chapter: `5`
- definition: `spell:12`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0403

- chapter: `5`
- definition: `spell:13`
- join: `matched`
- effect status: `runtime-case`

### Runtime effect record 0404

- chapter: `5`
- definition: `spell:100`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0405

- chapter: `5`
- definition: `spell:200`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0406

- chapter: `5`
- definition: `spell:201`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0407

- chapter: `5`
- definition: `spell:202`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0408

- chapter: `5`
- definition: `spell:203`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0409

- chapter: `5`
- definition: `spell:204`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0410

- chapter: `5`
- definition: `spell:205`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0411

- chapter: `5`
- definition: `spell:206`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0412

- chapter: `5`
- definition: `spell:207`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0413

- chapter: `5`
- definition: `spell:208`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0414

- chapter: `5`
- definition: `spell:209`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0415

- chapter: `5`
- definition: `spell:210`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0416

- chapter: `5`
- definition: `spell:211`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0417

- chapter: `5`
- definition: `spell:212`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0418

- chapter: `5`
- definition: `spell:213`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0419

- chapter: `5`
- definition: `spell:214`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0420

- chapter: `5`
- definition: `spell:215`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0421

- chapter: `5`
- definition: `spell:216`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0422

- chapter: `5`
- definition: `spell:217`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0423

- chapter: `5`
- definition: `spell:218`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0424

- chapter: `5`
- definition: `spell:219`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0425

- chapter: `5`
- definition: `spell:220`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0426

- chapter: `5`
- definition: `spell:221`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0427

- chapter: `5`
- definition: `spell:222`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0428

- chapter: `5`
- definition: `spell:223`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0429

- chapter: `5`
- definition: `spell:224`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0430

- chapter: `5`
- definition: `spell:225`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0431

- chapter: `5`
- definition: `spell:226`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0432

- chapter: `5`
- definition: `spell:227`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0433

- chapter: `5`
- definition: `spell:228`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0434

- chapter: `5`
- definition: `spell:229`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0435

- chapter: `5`
- definition: `spell:230`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0436

- chapter: `5`
- definition: `spell:231`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0437

- chapter: `5`
- definition: `spell:232`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0438

- chapter: `5`
- definition: `spell:233`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0439

- chapter: `5`
- definition: `spell:234`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0440

- chapter: `5`
- definition: `spell:235`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0441

- chapter: `5`
- definition: `spell:236`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0442

- chapter: `5`
- definition: `spell:237`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0443

- chapter: `5`
- definition: `spell:238`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0444

- chapter: `5`
- definition: `spell:239`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0445

- chapter: `5`
- definition: `spell:240`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0446

- chapter: `5`
- definition: `spell:241`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0447

- chapter: `5`
- definition: `spell:242`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0448

- chapter: `5`
- definition: `spell:243`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0449

- chapter: `5`
- definition: `spell:260`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0450

- chapter: `5`
- definition: `spell:261`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0451

- chapter: `5`
- definition: `spell:262`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0452

- chapter: `5`
- definition: `spell:263`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0453

- chapter: `5`
- definition: `spell:264`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0454

- chapter: `5`
- definition: `spell:265`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0455

- chapter: `5`
- definition: `spell:266`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0456

- chapter: `5`
- definition: `spell:267`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0457

- chapter: `5`
- definition: `spell:268`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0458

- chapter: `5`
- definition: `spell:269`
- join: `unmatched-dispatch`
- effect status: `runtime-case`

### Runtime effect record 0459

- chapter: `5`
- definition: `spell:270`
- join: `unmatched-dispatch`
- effect status: `runtime-case`
