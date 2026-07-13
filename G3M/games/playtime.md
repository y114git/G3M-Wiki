# Playtime

G3M tracks playtime for installed mods that were active during a launch.

## How it is recorded

When a launch finishes, G3M calculates the session length and adds that time to
the active mod IDs from that session.

The stored field is:

- `playtime_hours`

It is saved in the current profile's mod metadata.

## Where you see it

Playtime is shown in the Library UI through the mod summary panel. The value is
formatted as hours for display.

## Important limitation

This is G3M-side tracking. It reflects sessions launched and monitored through
G3M, not every possible way the game might have been started outside the
launcher.
