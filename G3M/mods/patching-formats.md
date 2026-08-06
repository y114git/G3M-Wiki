# Patching Formats

G3M currently works with four main patching styles for game data:

- `g3mpatch`
- `xdelta` and `vcdiff`
- `csx`
- full raw data replacement

## Practical difference

- `g3mpatch` is G3M's native patch format
- `xdelta` and `vcdiff` are binary patch formats
- `csx` runs against the original data through G3MTool; the saved result must
  reopen as valid GameMaker data before G3MTool uses it
- raw replacement swaps the whole data file

## Detection

G3M detects the format automatically from the file extension or, for
archive-style patches, from the presence of `g3mpatch.json`.

## Recommendation

G3M passes every format to G3MTool. Mixed-format merge uses the user-defined
priority order.
