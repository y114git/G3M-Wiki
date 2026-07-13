# Importing Mods

Importing is how a file becomes a usable Library mod.

---

## The Usual Ways

Most imports happen through one of these:

- download from the Mods Browser
- choose a local file from disk
- drag and drop a file, folder, or URL onto G3M

All three paths end up feeding the same general import pipeline.

---

## What G3M Tries to Recognize

When a file comes in, G3M tries to answer:

- is this already a native G3M mod
- is this a supported archive with recognizable mod content
- is this a known external format that can be converted
- is this at least a raw patch or data file that can become a basic mod

If one of those answers is yes, G3M tries to build a usable mod entry for you.

---

## Best Case

The smoothest imports are:

- native G3M mod folders or archives
- `.g3mpatch`
- supported archives with clear mod structure

Supported conversion paths also exist for some external ecosystems, including
DELTAMOD, supported Pizza Tower-related flows, and strict FRICKBEARS3 addon
archives.

---

## When Import Is Not Automatic

Sometimes G3M can download or open a file but still cannot turn it into a clean
installed mod on its own.

That usually means:

- the format is unsupported
- the archive layout is too ambiguous
- the file needs a more manual conversion workflow

If the file is close to usable but not mappable automatically, G3M can hand it
off to the Manual Install dialog instead of failing as a blind import. That flow
can assign DATA files, extra files, and additional xdelta patches to explicit
game targets.

When that happens, the right next step is usually to inspect the file structure
or try the relevant modding/conversion tools instead of assuming the file is
broken.

---

## Merge vs Replace

If the incoming mod matches an existing mod ID, G3M asks whether you want to
merge or replace.

- **merge** is better when you want to preserve the current mod folder and
  update it
- **replace** is better when you want a clean reimport

If you do not specifically need to preserve local folder state, replace is often
the simpler option.
