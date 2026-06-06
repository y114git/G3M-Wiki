# Modding Tools

Modding Tools is G3M's built-in utility dialog for working with GameMaker data files and patch files.

## Tabs

The current dialog has these tabs:

- Convert DATA
- Patch
- Merge
- Info
- Diff

## Supported formats

The tool flow currently recognizes:

- `.win`
- `.ios`
- `.unx`
- `.droid`
- `.g3mpatch`
- `.zip` archives that contain `g3mpatch.json`
- `.xdelta`
- `.vcdiff`
- `.csx`

## What it is for

- turn modified data into patch files
- apply patch files back onto original data
- compare two data files
- inspect data files
- merge multiple changesets

## G3MTool dependency

The dialog is a front end for the bundled `G3MTool` binaries. If you care about exact command behavior or patch format details, see the `G3MTool` section of the wiki.
