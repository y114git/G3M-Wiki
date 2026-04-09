# Monster Runtime

This page documents the enemy-side battle runtime: how DELTARUNE turns encounter ids into live monster instances, how enemy stats and ACT menus are assigned, and how monster state is consumed by the battle controller.

The main roots are:

- `scripts/scr_encountersetup/scr_encountersetup.gml`
- `scripts/scr_monster_statreset/scr_monster_statreset.gml`
- `scripts/scr_monster_makeinstance/scr_monster_makeinstance.gml`
- `scripts/scr_monstersetup/scr_monstersetup.gml`
- `scripts/scr_monsterdefeat/scr_monsterdefeat.gml`

---

## Runtime Flow

Monster setup is a pipeline:

1. `scr_encountersetup(encounter_id)` writes the encounter recipe into global arrays.
2. `obj_battlecontroller` Create spawns monster instances using those arrays.
3. `scr_monster_makeinstance()` creates the actual object instance.
4. `scr_monster_statreset()` normalizes battle-side fields.
5. `scr_monstersetup(myself)` fills stats, names, ACT data, and special flags based on `global.monstertype[myself]`.

---

## Important Global Arrays

The controller and monster scripts commonly communicate through:

- `global.monstertype[]`
- `global.monsterinstance[]`
- `global.monstername[]`
- `global.monsterhp[]`
- `global.monstermaxhp[]`
- `global.monsterat[]`
- `global.monsterdf[]`
- `global.monstergold[]`
- `global.monsterattackname[]`
- `global.monsteractname[][]`
- `global.monstertired[]`
- `global.monstermercy[]`

---

## `scr_monstersetup` Pattern

The setup script begins with:

```gml
scr_monster_actreset(myself);
```

Then it branches on monster type:

```gml
if (global.monstertype[myself] == 1)
{
    ...
}
if (global.monstertype[myself] == 2)
{
    ...
}
```

So enemy “classes” are largely encoded as one big runtime data switch.

---

## Representative Enemy Cases

## Type 1

- name: `"Enemy"`
- HP: `130`
- AT: `7`
- DF: `0`
- Gold: `20`
- ACTs include `Check`, `Warning`, `Victory`, `SimuDance`, `Victory (S)`, `Lecture`

## Type 2: Lancer

- HP: `540`
- AT: `5`
- DF: `1`
- intro text: `global.battlemsg[0] = "* Lancer busts in!"`
- ACTs: `Check`, `Warning`, `Compliment`

## Type 3: Dummy

- HP: `450`
- AT: `0`
- DF: `0`
- ACTs: `Check`, `Hug`, `Hug Ralsei`

## Type 5: Rudinn

- HP: `120`
- AT: `5`
- DF: `0`
- ACTs: `Check`, `Convince`, `Lecture`

## Type 6: Hathy

- HP: `150`
- AT: `6`
- DF: `0`
- ACTs: `Check`, `Flatter`, `X-Flatter`

Its setup can branch on conditions like `scr_havechar(2)` and `global.plot`, proving that ACT menus are not always fixed.

## Type 7: Clover

The script can populate one of several themed ACT trios, including:

- politics / religion / sports
- kindness / cuteboys / guncontrol
- trees / ghosts / games

## Type 10: K. Round

- HP: `1300`
- AT: `7.5`
- DF: `3`
- Gold: `100`
- ACTs include `Check` and `Bow`

---

## ACT Menu Data

Monster setup does more than set combat stats. It also constructs the ACT vocabulary seen by the player, including:

- shared ACT names
- character-specific ACT names
- check text
- special comments and reactions

This is why ACT behavior belongs partly here and partly in [Battle System](battle-system.md).

---

## Tired / Mercy / Spare State

Monster setup and follow-up logic manage:

- tiredness eligibility
- mercy percentage
- pacify compatibility
- progression flags for warning/flatter/lecture style ACTs

These values are later consumed by spare and pacify logic.

---

## Defeat and Cleanup

`scr_monsterdefeat` handles the post-defeat side of the lifecycle:

- removing or marking the instance
- awarding money / progression
- updating victory conditions
- triggering encounter-specific consequences

---

## Chapter Differences

## Chapter 1

- smaller roster
- simpler ACT data

## Chapter 2

- larger enemy roster
- more character-specific ACT logic

## Chapter 3 and Chapter 4

- keep the large Chapter 2+ monster framework
- add more staged and special-case encounters rather than simplifying the system

---

## Modding Implications

- If an ACT command is missing, check `scr_monstersetup` before changing menu rendering.
- If spare behavior looks wrong, inspect tired/mercy flags before editing controller code.
- If a boss intro line is wrong, check whether `global.battlemsg[0]` is overwritten during setup.

---

## Relationship To Other Pages

- [Battle System](battle-system.md) explains how the controller consumes monster data.
- [Damage System](damage-system.md) explains how those stats are used in calculations.
