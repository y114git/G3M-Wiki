# Patching Formats

G3M currently works with four main patching styles for game data:

- `g3mpatch`
- `xdelta` and `vcdiff`
- `csx`
- full raw data replacement

## Practical difference

- `g3mpatch` is G3M's native patch format
- `xdelta` and `vcdiff` are binary patch formats
- `csx` is a script-based modification flow through G3MTool
- raw replacement swaps the whole data file

## Detection

G3M detects the format automatically from the file extension or, for
archive-style patches, from the presence of `g3mpatch.json`.

## Recommendation

For sharing and combining mods, patch-based formats are usually more flexible
than shipping a full raw data file.
