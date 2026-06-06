# Migration

G3M still contains migration logic for older local data layouts and for the legacy DELTAHUB naming era.

## What it covers

- DELTAHUB data import into the G3M data directory
- settings key migrations
- profile and state normalization
- theme-color key renames

## Why it matters

This code exists so an existing user data folder can be brought forward into the current layout instead of forcing a manual reset.
