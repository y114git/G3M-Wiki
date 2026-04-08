# Playtime Tracking

G3M tracks how long you play each game and each mod, providing playtime statistics in the Library.

---

## How It Works

### Timer Start

When a game is launched:

1. G3M records the launch timestamp.
2. The game monitor thread starts watching the game process.
3. The status bar shows a running playtime counter: "Game is running: DELTARUNE (0:00:00)".

### Timer Running

While the game is running:

- The timer counts up in real-time (hours:minutes:seconds format).
- The timer updates every second in the status bar.
- The action button also shows the elapsed time.

### Timer Stop

When the game process exits:

1. G3M records the exit timestamp.
2. The session duration is calculated (exit time minus launch time).
3. The duration is added to the mod's cumulative playtime.
4. If analytics opt-in is enabled, the session duration is recorded.

---

## Per-Mod Playtime

Each mod in the Library has a `playtime_hours` entry in the profile's `mods_data.json` file. This field accumulates playtime across all play sessions with that mod selected.

### Display

In the Library, each mod card can display the total playtime. The format is:

- **Under 1 hour**: "45m" (minutes).
- **1+ hours**: "2.5h" (hours with one decimal).
- **No playtime**: Not displayed (or "0m").

### Multiple Mods

When multiple mods are selected for a play session, the session's playtime is attributed to all selected mods. Each mod's `playtime_hours` increases by the same session duration.

### No Mods

If the game is launched without mods, the playtime is not attributed to any mod. It is only recorded in analytics (if enabled).

---

## Persistence

Playtime data is stored in the profile's `mods_data.json` (`{user_data_root}/profiles/<profile_name>/mods_data.json`) as a per-mod metadata entry:

```json
{
  "my_mod_id": {
    "playtime_hours": 12.5,
    "added_date": "2024-01-01 12:00:00"
  }
}
```

The value is a float representing total hours (rounded to 4 decimal places). It is updated after each play session and saved immediately.

---

## Analytics Integration

If anonymous analytics are enabled, each game launch event includes:

- **Game ID** — Which game was played.
- **Duration** — How long the session lasted.
- **Mod count** — How many mods were selected.
- **Mod IDs** — Which mods were used (hashed for local mods).

This helps the developer understand usage patterns without identifying individual users.

---

## Limitations

- Playtime tracking requires G3M to be running. If you launch the game via a shortcut and G3M crashes or is closed during the game, playtime may not be recorded for that session.
- Playtime is approximate — if the game process name changes or the monitor thread cannot detect the process, the timer may stop prematurely.
- If you minimize G3M to the system tray while the game runs, the timer continues normally.
- AFK time is included — G3M cannot distinguish between active play and idle time.
