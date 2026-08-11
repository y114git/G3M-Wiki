# Importing Mods

Import adds a mod to Library.

## Sources

Import from Mods Browser, a local file or folder, a URL, or drag and drop. All
sources use the same import pipeline.

G3M recognizes native G3M mods, `.g3mpatch`, raw DATA files, supported patch
files, and supported archives. It also converts current TOML and legacy JSON
DELTAMOD packages when their paths stay inside the package.

For a converted DELTAMOD mod, G3M keeps script dependencies in the mod folder.
It does not copy dependency-only files into the game installation. A CSX DATA
entry can therefore use relative `#load` imports and resource paths.

## Manual Install

Open Manual Install when G3M cannot map an archive to game targets. Assign DATA
files, Extra files, and xdelta patches to explicit targets there.

## Existing mods

When an import matches an installed mod ID, choose **Merge** to retain the
existing folder or **Replace** to install the imported folder as-is.
