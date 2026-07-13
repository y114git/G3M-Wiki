# PizzaOven and CYOP/AFOM Conversion

G3M has built-in conversion paths for some Pizza Tower community formats.

## Supported import paths

The current code recognizes:

- normal PizzaOven-style mod imports
- CYOP or AFOM custom level imports

It also explicitly detects unsupported GMLoader-style packages and does not
treat them as normal G3M-ready content.

## What conversion does

For supported PizzaOven content, G3M prepares an equivalent local G3M mod by
turning changed game data into a form G3M can launch and restore.

For CYOP or AFOM content, G3M treats the level files as extra content that is
installed for the play session and then cleaned up afterward.

## Why this matters

Players can bring some Pizza Tower community mods into the normal G3M library
flow instead of managing them completely by hand.
