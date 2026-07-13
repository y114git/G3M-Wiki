# Spells and abilities definition catalog

listed from the shipped `scr_*info` switch cases. Each record preserves the
exact case-local assignments. Status is deliberately conservative: a definition
is not called obtainable without a literal acquisition site.

## Chapter 1

### Chapter 1 spell 0

- Chapter: 1
- Name: (empty)
- Effect: not assigned
- Status: empty sentinel
- Stat/value: `spelltarget=0`
- Stat/value: `cost=-1`
- Equip-owner assignments: none

### Chapter 1 spell 1

- Chapter: 1
- Name: Rude Sword
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=125`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 1 spell 2

- Chapter: 1
- Name: Heal Prayer
- Effect: Heavenly light restores a little HP to#one party member. Depends on
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=80`
- Stat/value: `usable=0`
- Stat/value: `spellusable=1`
- Equip-owner assignments: none

### Chapter 1 spell 3

- Chapter: 1
- Name: Pacify
- Effect: SPARE a tired enemy by putting them to sleep.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 1 spell 4

- Chapter: 1
- Name: Rude Buster
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=100`
- Equip-owner assignments: none

### Chapter 1 spell 5

- Chapter: 1
- Name: Red Buster
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 1 spell 6

- Chapter: 1
- Name: Dual Heal
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 1 spell 7

- Chapter: 1
- Name: ACT
- Effect: Do all sorts of things.#It isn't magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

## Chapter 2

### Chapter 2 spell 0

- Chapter: 2
- Name: (empty)
- Effect: not assigned
- Status: empty sentinel
- Stat/value: `spelltarget=0`
- Stat/value: `cost=-1`
- Equip-owner assignments: none

### Chapter 2 spell 1

- Chapter: 2
- Name: Rude Sword
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=125`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 2 spell 2

- Chapter: 2
- Name: Heal Prayer
- Effect: Heavenly light restores a little HP to#one party member. Depends on
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=80`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 2 spell 3

- Chapter: 2
- Name: Pacify
- Effect: SPARE a tired enemy by putting them to sleep.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 2 spell 4

- Chapter: 2
- Name: Rude Buster
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=100`
- Equip-owner assignments: none

### Chapter 2 spell 5

- Chapter: 2
- Name: Red Buster
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 2 spell 6

- Chapter: 2
- Name: Dual Heal
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 2 spell 7

- Chapter: 2
- Name: ACT
- Effect: You can do many things.#Don't confuse it with magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 2 spell 8

- Chapter: 2
- Name: SleepMist
- Effect: A cold mist sweeps through,#sparing all TIRED enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=80`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 2 spell 9

- Chapter: 2
- Name: IceShock
- Effect: Deals magical ICE damage to#one enemy.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Equip-owner assignments: none

### Chapter 2 spell 10

- Chapter: 2
- Name: SnowGrave
- Effect: Deals the fatal damage to#all of the enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=3`
- Equip-owner assignments: none

### Chapter 2 spell 11

- Chapter: 2
- Name: UltimatHeal
- Effect: Heals 1 party member to the#best of Susie's ability.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=250`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

## Chapter 3

### Chapter 3 spell 0

- Chapter: 3
- Name: (empty)
- Effect: not assigned
- Status: empty sentinel
- Stat/value: `spelltarget=0`
- Stat/value: `cost=-1`
- Equip-owner assignments: none

### Chapter 3 spell 1

- Chapter: 3
- Name: Rude Sword
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=125`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 3 spell 2

- Chapter: 3
- Name: Heal Prayer
- Effect: Heavenly light restores a little HP to#one party member. Depends on
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=80`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 3 spell 3

- Chapter: 3
- Name: Pacify
- Effect: SPARE a tired enemy by putting them to sleep.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 3 spell 4

- Chapter: 3
- Name: Rude Buster
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=100`
- Equip-owner assignments: none

### Chapter 3 spell 5

- Chapter: 3
- Name: Red Buster
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 3 spell 6

- Chapter: 3
- Name: Dual Heal
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 3 spell 7

- Chapter: 3
- Name: ACT
- Effect: Many different skills.#It has nothing to do with magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 3 spell 8

- Chapter: 3
- Name: SleepMist
- Effect: A cold mist sweeps through,#sparing all TIRED enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=80`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 3 spell 9

- Chapter: 3
- Name: IceShock
- Effect: Deals magical ICE damage to#one enemy.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Equip-owner assignments: none

### Chapter 3 spell 10

- Chapter: 3
- Name: SnowGrave
- Effect: Deals the fatal damage to#all of the enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=global.maxtension * 2`
- Equip-owner assignments: none

### Chapter 3 spell 11

- Chapter: 3
- Name: UltraHeal
- Effect: An awesome healing spell.#... right?
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=225 - round(global.flag[1045] * 2.5)`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

## Chapter 4

### Chapter 4 spell 0

- Chapter: 4
- Name: (empty)
- Effect: not assigned
- Status: empty sentinel
- Stat/value: `spelltarget=0`
- Stat/value: `cost=-1`
- Equip-owner assignments: none

### Chapter 4 spell 1

- Chapter: 4
- Name: Rude Sword
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=125`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 4 spell 2

- Chapter: 4
- Name: Heal Prayer
- Effect: Heavenly light restores a little HP to#one party member. Depends on
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=80`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 4 spell 3

- Chapter: 4
- Name: Pacify
- Effect: SPARE a tired enemy by putting them to sleep.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 4 spell 4

- Chapter: 4
- Name: Rude Buster
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=100`
- Equip-owner assignments: none

### Chapter 4 spell 5

- Chapter: 4
- Name: Red Buster
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 4 spell 6

- Chapter: 4
- Name: Dual Heal
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 4 spell 7

- Chapter: 4
- Name: ACT
- Effect: Execute various behaviors.#It can't be considered magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value assignments: none
- Equip-owner assignments: none

### Chapter 4 spell 8

- Chapter: 4
- Name: SleepMist
- Effect: A cold mist sweeps through,#sparing all TIRED enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=80`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 4 spell 9

- Chapter: 4
- Name: IceShock
- Effect: Deals magical ICE damage to#one enemy.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Equip-owner assignments: none

### Chapter 4 spell 10

- Chapter: 4
- Name: SnowGrave
- Effect: Deals the fatal damage to#all of the enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=global.maxtension * 2`
- Equip-owner assignments: none

### Chapter 4 spell 11

- Chapter: 4
- Name: OKHeal
- Effect: It's not the best healing spell, but#it may have its uses.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `spellusable=0`
- Stat/value: `cost=212.5`
- Equip-owner assignments: none

## Chapter 5

### Chapter 5 spell 0

- Chapter: 5
- Name: (empty)
- Effect: not assigned
- Status: empty sentinel
- Stat/value: `spelltarget=0`
- Stat/value: `cost=-1`
- Equip-owner assignments: none

### Chapter 5 spell 1

- Chapter: 5
- Name: Rude Sword
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=125`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 2

- Chapter: 5
- Name: Heal Prayer
- Effect: Heavenly light restores a little HP to#one party member. Depends on
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=80`
- Stat/value: `usable=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 3

- Chapter: 5
- Name: Pacify
- Effect: SPARE a tired enemy by putting them to sleep.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=0`
- Equip-owner assignments: none

### Chapter 5 spell 4

- Chapter: 5
- Name: Rude Buster
- Effect: Deals moderate Rude-elemental damage to#one foe. Depends on Attack &
  Magic.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=100`
- Equip-owner assignments: none

### Chapter 5 spell 5

- Chapter: 5
- Name: Red Buster
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 6

- Chapter: 5
- Name: Dual Heal
- Effect: (empty)
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 7

- Chapter: 5
- Name: ACT
- Effect: It's not magic, is it?#No, not something like this.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=0`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 8

- Chapter: 5
- Name: SleepMist
- Effect: A cold mist sweeps through,#sparing all TIRED enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=80`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 9

- Chapter: 5
- Name: IceShock
- Effect: Deals magical ICE damage to#one enemy.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=2`
- Stat/value: `cost=40`
- Equip-owner assignments: none

### Chapter 5 spell 10

- Chapter: 5
- Name: SnowGrave
- Effect: Deals the fatal damage to#all of the enemies.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=global.maxtension * 2`
- Equip-owner assignments: none

### Chapter 5 spell 11

- Chapter: 5
- Name: OKHeal
- Effect: It's not the best healing spell, but#it may have its uses.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `spellusable=0`
- Stat/value: `cost=212.5`
- Equip-owner assignments: none

### Chapter 5 spell 12

- Chapter: 5
- Name: ReviveSong
- Effect: Revives a DOWNed ally and heals them.#Otherwise, heals a lot of HP.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=1`
- Stat/value: `cost=212`
- Stat/value: `spellusable=0`
- Equip-owner assignments: none

### Chapter 5 spell 13

- Chapter: 5
- Name: Scythemare
- Effect: Inflicts all enemies with bad dreams.#All TIRED enemies will be
  SPAREd.
- Status: defined spell; ownership is recorded by spell-array writes
- Stat/value: `spelltarget=0`
- Stat/value: `cost=50`
- Equip-owner assignments: none

## Acquisition and output chains

### Spell ownership record 0001

- chapter: `1`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 70; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0002

- chapter: `1`
- owner: `1`
- slot: `0`
- spell expression: `7`
- spell ID: `7`
- join: `matched`
- condition: `line 98; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0003

- chapter: `1`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 99; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0004

- chapter: `1`
- owner: `3`
- slot: `0`
- spell expression: `3`
- spell ID: `3`
- join: `matched`
- condition: `line 100; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0005

- chapter: `1`
- owner: `3`
- slot: `1`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 101; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0006

- chapter: `1`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 174; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0007

- chapter: `1`
- owner: `thischar`
- slot: `spellcoord + 2`
- spell expression: `= 0)                 {                     cango = 0`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 267; if (spellcoord >= 10) > if (`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0008

- chapter: `1`
- owner: `thischar`
- slot: `7`
- spell expression: `= 0)                 {                     cango = 2`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 271; if (global.spell[thischar][spellcoord + 2] == 0) > if`
  `(spellcoord == 5 && global.spell[thischar][6] != 0 &&`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0009

- chapter: `1`
- owner: `thischar`
- slot: `(page * 6) + (i * 2)`
- spell expression: `= 3)         {             pacify_glow = 0`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 160; if (global.tension < global.spellcost[thischar][(page *`
  `6) + (i * 2)]) > else if (`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0010

- chapter: `1`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 31; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0011

- chapter: `1`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 51; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0012

- chapter: `1`
- owner: `3`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 52; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0013

- chapter: `2`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0014

- chapter: `2`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 166; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0015

- chapter: `2`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= arg1)         {             __haveit = 1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 8; if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0016

- chapter: `2`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= 0)             {                 __openslot = __spellj`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 14; if (__openslot == -1) > if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0017

- chapter: `2`
- owner: `arg0`
- slot: `__openslot`
- spell expression: `arg1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 22; if (__openslot >= 0 && __haveit == 0)`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0018

- chapter: `2`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 109; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0019

- chapter: `2`
- owner: `1`
- slot: `0`
- spell expression: `7`
- spell ID: `7`
- join: `matched`
- condition: `line 167; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0020

- chapter: `2`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 168; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0021

- chapter: `2`
- owner: `3`
- slot: `0`
- spell expression: `3`
- spell ID: `3`
- join: `matched`
- condition: `line 169; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0022

- chapter: `2`
- owner: `3`
- slot: `1`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0023

- chapter: `2`
- owner: `4`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 171; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0024

- chapter: `2`
- owner: `4`
- slot: `1`
- spell expression: `8`
- spell ID: `8`
- join: `matched`
- condition: `line 172; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0025

- chapter: `2`
- owner: `4`
- slot: `2`
- spell expression: `9`
- spell ID: `9`
- join: `matched`
- condition: `line 173; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0026

- chapter: `2`
- owner: `thischar`
- slot: `spellcoord + 2`
- spell expression: `= 0)                 {                     cango = 0`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 292; if (spellcoord >= 10) > if (`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0027

- chapter: `2`
- owner: `thischar`
- slot: `7`
- spell expression: `= 0)                 {                     cango = 2`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 296; if (global.spell[thischar][spellcoord + 2] == 0) > if`
  `(spellcoord == 5 && global.spell[thischar][6] != 0 &&`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0028

- chapter: `2`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 32; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0029

- chapter: `2`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 52; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0030

- chapter: `2`
- owner: `3`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 53; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0031

- chapter: `2`
- owner: `4`
- slot: `3`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 263; if (con == 14 && !d_ex())`
- status: `production`
- rooms: `room_dw_city_berdly`

### Spell ownership record 0032

- chapter: `2`
- owner: `4`
- slot: `3`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 536; if (con == 20)`
- status: `production`
- rooms: `room_dw_city_berdly`

### Spell ownership record 0033

- chapter: `3`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0034

- chapter: `3`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 166; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0035

- chapter: `3`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= arg1)         {             __haveit = 1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 8; if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0036

- chapter: `3`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= 0)             {                 __openslot = __spellj`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 14; if (__openslot == -1) > if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0037

- chapter: `3`
- owner: `arg0`
- slot: `__openslot`
- spell expression: `arg1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 22; if (__openslot >= 0 && __haveit == 0)`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0038

- chapter: `3`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 109; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0039

- chapter: `3`
- owner: `1`
- slot: `0`
- spell expression: `7`
- spell ID: `7`
- join: `matched`
- condition: `line 196; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0040

- chapter: `3`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 197; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0041

- chapter: `3`
- owner: `2`
- slot: `1`
- spell expression: `11`
- spell ID: `11`
- join: `matched`
- condition: `line 198; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0042

- chapter: `3`
- owner: `3`
- slot: `0`
- spell expression: `3`
- spell ID: `3`
- join: `matched`
- condition: `line 199; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0043

- chapter: `3`
- owner: `3`
- slot: `1`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 200; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0044

- chapter: `3`
- owner: `4`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 201; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0045

- chapter: `3`
- owner: `4`
- slot: `1`
- spell expression: `8`
- spell ID: `8`
- join: `matched`
- condition: `line 202; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0046

- chapter: `3`
- owner: `4`
- slot: `2`
- spell expression: `9`
- spell ID: `9`
- join: `matched`
- condition: `line 203; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0047

- chapter: `3`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0048

- chapter: `3`
- owner: `1`
- slot: `0`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 92; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0049

- chapter: `3`
- owner: `1`
- slot: `0`
- spell expression: `7`
- spell ID: `7`
- join: `matched`
- condition: `line 9; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0050

- chapter: `3`
- owner: `thischar`
- slot: `spellcoord + 2`
- spell expression: `= 0)                 {                     cango = 0`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 597; if (spellcoord >= 10) > if (`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0051

- chapter: `3`
- owner: `thischar`
- slot: `7`
- spell expression: `= 0)                 {                     cango = 2`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 601; if (global.spell[thischar][spellcoord + 2] == 0) > if`
  `(spellcoord == 5 && global.spell[thischar][6] != 0 &&`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0052

- chapter: `3`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 32; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0053

- chapter: `3`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 52; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0054

- chapter: `3`
- owner: `3`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 53; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0055

- chapter: `4`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0056

- chapter: `4`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0057

- chapter: `4`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0058

- chapter: `4`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 166; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0059

- chapter: `4`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= arg1)         {             __haveit = 1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 8; if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0060

- chapter: `4`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= 0)             {                 __openslot = __spellj`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 14; if (__openslot == -1) > if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0061

- chapter: `4`
- owner: `arg0`
- slot: `__openslot`
- spell expression: `arg1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 22; if (__openslot >= 0 && __haveit == 0)`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0062

- chapter: `4`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 109; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0063

- chapter: `4`
- owner: `1`
- slot: `0`
- spell expression: `7`
- spell ID: `7`
- join: `matched`
- condition: `line 237; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0064

- chapter: `4`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 238; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0065

- chapter: `4`
- owner: `2`
- slot: `1`
- spell expression: `11`
- spell ID: `11`
- join: `matched`
- condition: `line 239; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0066

- chapter: `4`
- owner: `3`
- slot: `0`
- spell expression: `3`
- spell ID: `3`
- join: `matched`
- condition: `line 240; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0067

- chapter: `4`
- owner: `3`
- slot: `1`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 241; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0068

- chapter: `4`
- owner: `4`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 242; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0069

- chapter: `4`
- owner: `4`
- slot: `1`
- spell expression: `8`
- spell ID: `8`
- join: `matched`
- condition: `line 243; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0070

- chapter: `4`
- owner: `4`
- slot: `2`
- spell expression: `9`
- spell ID: `9`
- join: `matched`
- condition: `line 244; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0071

- chapter: `4`
- owner: `thischar`
- slot: `spellcoord + 2`
- spell expression: `= 0)                 {                     cango = 0`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 385; if (spellcoord >= 10) > if (`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0072

- chapter: `4`
- owner: `thischar`
- slot: `7`
- spell expression: `= 0)                 {                     cango = 2`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 389; if (global.spell[thischar][spellcoord + 2] == 0) > if`
  `(spellcoord == 5 && global.spell[thischar][6] != 0 &&`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0073

- chapter: `4`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 32; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0074

- chapter: `4`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 52; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0075

- chapter: `4`
- owner: `3`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 53; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0076

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0077

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0078

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0079

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 166; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0080

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `ossafe_file_text_read_real(myfileid)`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 170; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0081

- chapter: `5`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= arg1)         {             __haveit = 1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 8; if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0082

- chapter: `5`
- owner: `arg0`
- slot: `__spellj`
- spell expression: `= 0)             {                 __openslot = __spellj`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 14; if (__openslot == -1) > if (`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0083

- chapter: `5`
- owner: `arg0`
- slot: `__openslot`
- spell expression: `arg1`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 22; if (__openslot >= 0 && __haveit == 0)`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0084

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 109; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0085

- chapter: `5`
- owner: `1`
- slot: `0`
- spell expression: `7`
- spell ID: `7`
- join: `matched`
- condition: `line 235; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0086

- chapter: `5`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 236; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0087

- chapter: `5`
- owner: `2`
- slot: `1`
- spell expression: `11`
- spell ID: `11`
- join: `matched`
- condition: `line 237; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0088

- chapter: `5`
- owner: `2`
- slot: `2`
- spell expression: `13`
- spell ID: `13`
- join: `matched`
- condition: `line 238; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0089

- chapter: `5`
- owner: `3`
- slot: `0`
- spell expression: `3`
- spell ID: `3`
- join: `matched`
- condition: `line 239; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0090

- chapter: `5`
- owner: `3`
- slot: `1`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 240; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0091

- chapter: `5`
- owner: `3`
- slot: `2`
- spell expression: `12`
- spell ID: `12`
- join: `matched`
- condition: `line 241; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0092

- chapter: `5`
- owner: `4`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 242; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0093

- chapter: `5`
- owner: `4`
- slot: `1`
- spell expression: `8`
- spell ID: `8`
- join: `matched`
- condition: `line 243; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0094

- chapter: `5`
- owner: `4`
- slot: `2`
- spell expression: `9`
- spell ID: `9`
- join: `matched`
- condition: `line 244; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0095

- chapter: `5`
- owner: `2`
- slot: `2`
- spell expression: `13`
- spell ID: `13`
- join: `matched`
- condition: `line 72; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0096

- chapter: `5`
- owner: `3`
- slot: `2`
- spell expression: `12`
- spell ID: `12`
- join: `matched`
- condition: `line 77; unconditional in entry`
- status: `production-uncertain`
- rooms: `none joined`

### Spell ownership record 0097

- chapter: `5`
- owner: `thischar`
- slot: `spellcoord + 2`
- spell expression: `= 0)                 {                     cango = 0`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 367; if (spellcoord >= 10) > if (`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0098

- chapter: `5`
- owner: `thischar`
- slot: `7`
- spell expression: `= 0)                 {                     cango = 2`
- spell ID: `None`
- join: `dynamic-or-unmatched`
- condition: `line 371; if (global.spell[thischar][spellcoord + 2] == 0) > if`
  `(spellcoord == 5 && global.spell[thischar][6] != 0 &&`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0099

- chapter: `5`
- owner: `i`
- slot: `j`
- spell expression: `0`
- spell ID: `0`
- join: `matched`
- condition: `line 32; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0100

- chapter: `5`
- owner: `2`
- slot: `0`
- spell expression: `4`
- spell ID: `4`
- join: `matched`
- condition: `line 52; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`

### Spell ownership record 0101

- chapter: `5`
- owner: `3`
- slot: `0`
- spell expression: `2`
- spell ID: `2`
- join: `matched`
- condition: `line 53; unconditional in entry`
- status: `unplaced-or-uncertain`
- rooms: `none joined`
