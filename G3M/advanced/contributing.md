# Contributing

This page is for people working on G3M itself rather than just using it.

## Current stack

- Python `3.14+`
- PyQt6
- pytest
- ruff

## Main folders

The current repo is centered around:

- `src/` for app code
- `tests/` for tests
- `builds/` for packaging assets and scripts
- `catalog/` for plugin catalog data

## Usual workflow

1. Create a virtual environment.
2. Install the project with dev dependencies.
3. Run the app from `src/main.py`.
4. Run `ruff` and `pytest` before shipping changes.

## Important rule

If you change real behavior, the wiki and other user-facing docs should match the new HEAD instead of describing past behavior.
