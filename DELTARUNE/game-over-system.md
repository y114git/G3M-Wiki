# Game Over System

The game over system is controlled by `scr_gameover`, which supports three modes controlled by `global.flag[35]`.

---

## `scr_gameover` — Full Source

```gml
function scr_gameover()
{
    if (global.flag[35] == 0)
    {
        audio_stop_all();
        snd_play(snd_hurt1);
        if (global.chapter == 4)
        {
            if (i_ex(obj_jackenstein_enemy))
                global.tempflag[89]++;
        }
        global.screenshot = sprite_create_from_surface(application_surface, 0, 0,
            __view_get(e__VW.WView, 0), __view_get(e__VW.HView, 0), 0, 0, 0, 0);
        snd_free_all();
        room_goto(room_gameover);
    }
    if (global.flag[35] == 1)
    {
        global.turntimer = -1;
        global.flag[36] = 1;
        global.flag[39] = 1;
    }
    if (global.flag[35] == 2)
    {
        audio_stop_all();
        snd_play(snd_hurt1);
        snd_free_all();
        global.entrance = 0;
        global.tempflag[9] = 1;
        global.fighting = 0;
        global.interact = 0;
        global.hp[0] = 1; global.hp[1] = 1;
        global.hp[2] = 1; global.hp[3] = 1;
        room_goto(room);
    }
}
```

---

## Mode 0 — Standard Game Over

Default behavior when `global.flag[35] == 0`:

1. Stops all audio
2. Plays the hurt sound
3. In Chapter 4, if fighting Jackenstein: increments `global.tempflag[89]` (death counter for Jackenstein fight — triggers 1.5x TP gain at ≥ 3 deaths)
4. Takes a screenshot of the current frame for the game over screen
5. Frees all loaded audio
6. Transitions to `room_gameover`

### Game Over Room Flow

`room_gameover` displays the screenshot, plays the game over music, and shows:
- "Don't give up!" style message
- Option to load the most recent save

---

## Mode 1 — Scripted No-Death

When `global.flag[35] == 1`:

- Battle continues despite all HP being 0
- `global.turntimer = -1` — freezes the turn timer
- `global.flag[36] = 1` and `global.flag[39] = 1` — signal the battle controller that a scripted override is active

Used for boss encounters where the fight script handles the "loss" state itself (e.g. boss dialogue after defeating the party).

---

## Mode 2 — Room Restart

When `global.flag[35] == 2`:

1. Stops all audio
2. Resets `global.entrance`, `global.fighting`, `global.interact`
3. Sets `global.tempflag[9] = 1` — signals the room that this is a restart entry
4. Sets all party HP to 1
5. Re-enters the current room

In Chapters 2, 3, and 4, this mode also creates `obj_persistentfadein` with `image_alpha = 1.2` for a visual fade effect.

---

## Death Trigger

Game over is triggered from `scr_damage` when all occupied party slots have HP ≤ 0:

```gml
Gameover = 1;
if (global.char[0] != 0 && global.hp[global.char[0]] > 0) gameover = 0;
if (global.char[1] != 0 && global.hp[global.char[1]] > 0) gameover = 0;
if (global.char[2] != 0 && global.hp[global.char[2]] > 0) gameover = 0;
if (gameover == 1) scr_gameover();
```

Empty party slots (`global.char[i] == 0`) do not block game over.

---

## Individual Death: `scr_dead`

When a single party member reaches 0 HP:

- Their HP is set to `round(-maxhp / 2)` (negative value = downed state)
- Their battle sprite changes to the downed animation
- They are removed from the active targeting pool
- Further hits deal 25% damage

---

## `cantdie` Mechanic

Chapter 4 boss encounters can prevent Kris from dying:

| Object | Condition |
|---|---|
| `obj_dw_church_trueclimbadventure` | Always |
| `obj_titan_enemy` | Phase 8 |
| `obj_dw_churchc_darkswords` | `.cantdie == true` (all party HP clamped to min 1) |
| `obj_overworld_knight_sword_manager` | Kris HP clamped to min 1 |

---

## Chapter 4 Jackenstein Death Counter

The Jackenstein boss fight tracks how many times the player has died:

```gml
if (i_ex(obj_jackenstein_enemy))
    global.tempflag[89]++;
```

At `tempflag[89] >= 3`, `scr_tensionheal` grants 1.5x TP:

```gml
if (i_ex(obj_jackenstein_enemy) && global.tempflag[89] >= 3)
    global.tension += ceil(arg0 * 1.5);
```

This is a difficulty assist mechanic — the fight becomes easier after repeated losses.

---

## Modding Reference

| Goal | Inspect |
|---|---|
| Change game over behavior | Edit `scr_gameover` |
| Make a boss use scripted death | Set `global.flag[35] = 1` before the encounter |
| Make a boss use room restart | Set `global.flag[35] = 2` before the encounter |
| Change downed HP formula | Edit `scr_damage` — HP ≤ 0 branch |
| Add cantdie to an encounter | Check for your enemy object in `scr_damage`'s Ch4 cantdie block |