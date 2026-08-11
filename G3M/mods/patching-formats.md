# Patching Formats

G3M accepts four DATA patch styles:

- `g3mpatch`
- `xdelta` and `vcdiff`
- `csx`
- full raw data replacement

## Format behavior

- `g3mpatch` stores resource-level changes.
- `xdelta` and `vcdiff` require matching original files.
- `csx` runs through G3MTool. It must save valid GameMaker data.
- A raw DATA file replaces target DATA.

## Detection

G3M detects the format automatically from the file extension or, for
archive-style patches, from the presence of `g3mpatch.json`.

G3M sends DATA inputs to G3MTool. Mixed merges follow mod priority.
