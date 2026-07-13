# Level-Up & Stat Growth

`scr_levelup` is an encounter-count-based stat growth system present in Chapters
2, 3, and 4. Chapter 1 does not have this script.

---

## Core Script

```gml
function scr_levelup()
```

Called after battles when `global.flag[63] == 1` (the XP-granting victory
condition).

---

## Per-Chapter Differences

Each chapter uses different flag indices and HP caps:

The former wrapped summary table was removed. The records below list runtime
values.

Chapter 2 uses raw flag numbers directly. Chapters 3 and 4 store the cap values
and flag indices in local variables (`krismaxhp`, `susiemaxhp`, `ralseimaxhp`,
`encountercountflag`, `attackpluscountflag`).

---

## HP Growth

Each call grants +2 max HP to Kris, Susie, and Ralsei (if below their cap), and
+1 extra to Susie every 2nd encounter.

Current HP also increases by the same amount (no healing gap).

Noelle gains +4 max HP per encounter if she is in the party (`scr_havechar(4)`),
tracked separately in `global.flag[919]`.

---

## AT & MAG Growth

Every 10th encounter, if attack bonus count < 2:

The former wrapped summary table was removed. The records below list runtime
values.

Noelle gains +1 AT and +1 MAG every 4th encounter (if in party).

Maximum 2 attack bonuses per chapter run.

---

## Chapter 2 Source (for comparison)

```gml
function scr_levelup()
{
    global.flag[65]++;
    global.maxhp[1] += 2;
    global.maxhp[2] += 2;
    global.maxhp[3] += 2;
    global.hp[1] += 2;
    global.hp[2] += 2;
    global.hp[3] += 2;
    if ((global.flag[65] % 2) == 0)
        global.maxhp[2] += 1;
    if ((global.flag[65] % 10) == 0)
    {
        global.at[1] += 1; global.at[2] += 1; global.mag[2] += 1;
        global.at[3] += 1; global.mag[3] += 1;
        global.flag[66]++;
    }
    if (scr_havechar(4))
    {
        global.flag[919]++;
        global.maxhp[4] += 4; global.hp[4] += 4;
        if ((global.flag[65] % 4) == 0)
        { global.at[4] += 1; global.mag[4] += 1; }
    }
    global.maxhp[1] = clamp(global.maxhp[1], 10, 160);
    global.maxhp[2] = clamp(global.maxhp[2], 10, 190);
    global.maxhp[3] = clamp(global.maxhp[3], 10, 140);
    global.maxhp[4] = clamp(global.maxhp[4], 10, 999);
    for (var _i = 1; _i < 5; _i++)
        global.hp[_i] = min(global.hp[_i], global.maxhp[_i]);
    // triggers event_user event via obj_event_manager
}
```

Chapter 2 does not check whether HP is already at cap before adding. Chapters 3
and 4 add explicit `if (global.maxhp[i] < cap)` guards and return a
`gainedstats` flag.

---

## Chapter 4 Source

```gml
function scr_levelup()
{
    var krismaxhp = 240;
    var susiemaxhp = 290;
    var ralseimaxhp = 210;
    var encountercountflag = 1580;
    var attackpluscountflag = 1618;
    var gainedstats = 0;
    global.flag[encountercountflag]++;

    if (global.maxhp[1] < krismaxhp || global.maxhp[2] < susiemaxhp || global.ma
xhp[3] < ralseimaxhp)
    {
        gainedstats = 1;
        if (global.maxhp[1] < krismaxhp) { global.maxhp[1] += 2; global.hp[1] +=
 2; }
        if (global.maxhp[2] < susiemaxhp) { global.maxhp[2] += 2; global.hp[2] +
= 2; }
        if (global.maxhp[3] < ralseimaxhp) { global.maxhp[3] += 2; global.hp[3]
+= 2; }
        if ((global.flag[encountercountflag] % 2) == 0) { global.maxhp[2] += 1;
}
    }

    if ((global.flag[encountercountflag] % 10) == 0 && global.flag[attackpluscou
ntflag] < 2)
    {
        gainedstats = 1;
        global.at[1] += 1; global.at[2] += 1; global.mag[2] += 1;
        global.at[3] += 1; global.mag[3] += 1;
        global.flag[attackpluscountflag]++;
    }

    if (scr_havechar(4))
    {
        global.flag[919]++;
        global.maxhp[4] += 4; global.hp[4] += 4;
        if ((global.flag[1580] % 4) == 0) { global.at[4] += 1; global.mag[4] +=
1; }
    }

    global.maxhp[1] = clamp(global.maxhp[1], 10, krismaxhp);
    global.maxhp[2] = clamp(global.maxhp[2], 10, susiemaxhp);
    global.maxhp[3] = clamp(global.maxhp[3], 10, ralseimaxhp);
    global.maxhp[4] = clamp(global.maxhp[4], 10, 999);
    for (var _i = 1; _i < 5; _i++)
        global.hp[_i] = min(global.hp[_i], global.maxhp[_i]);

    return gainedstats;
}
```

---

## Modding Reference

The former wrapped summary table was removed. The records below list runtime
values.

## Save compatibility

These counters and base stats are serialized. Changing caps is compatible with
old files, but changing flag IDs resets or aliases progression. Reserve a new
migration flag and clamp after load:

```gml
if (global.flag[1997] == 0)
{
    global.maxhp[2] = min(global.maxhp[2], 320);
    global.hp[2] = min(global.hp[2], global.maxhp[2]);
    global.flag[1997] = 1;
}
```

Chapter 1 has no `scr_levelup`, so applying this encounter-growth description to
it is incorrect. Chapter 5 has its own runtime growth code and must not be
assumed to use Chapter 4's cap and flag constants. The character arrays and
chapter handoff rules are cataloged in
[Characters, Stats, and Progression](characters-stats-and-progression.md).

## Value-inventory reconciliation

The complete 2138-row initialization/import inventory is published in
[Party Management](party-management.md#generated-party-stat-equipment-spell-and-import-assignments).
It covers HP, AT, DF, MAG, Guts, equipment, spells, active party, and Chapters
1–4 import into Chapter 5.
