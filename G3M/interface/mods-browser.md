# Mods Browser

The Mods Browser is the discovery tab. Its job is simple: help you find a mod,
inspect it, and get it into your library with as little friction as possible.

---

## What It Searches

The browser only shows games that currently have a GameBanana ID in the runtime
registry.

That means:

- supported built-in games with GameBanana IDs appear automatically
- custom games can appear if you gave them a GameBanana ID
- games without a GameBanana ID do not show up here

So if a game is supported by G3M but missing from the browser, the usual reason
is that there is no GameBanana mapping for it.

---

## How Most People Use It

The common flow is:

1. pick a game
2. narrow results with search, tags, sort, or NSFW filter
3. open a mod card
4. inspect the details and screenshots
5. download it
6. let Downloads import it into your Library

That makes the Browser and Downloads work as a pair.

---

## Filters That Matter

The filter bar answers different kinds of questions:

- game selector: "show me mods for this game"
- search: "find this mod or keyword"
- tags: "show only a certain kind of mod"
- sort: "show popular, newer, or recently updated items first"
- NSFW toggle: "hide or include adult-marked content"

The browser uses the same broad tag family the rest of G3M uses, with extra
special cases such as `CYOP/AFOM` where relevant.

---

## Mod Details

Opening a mod gives you the richer view:

- description
- screenshots
- tags
- version-related metadata
- homepage or mod-page links when available
- download and library-related actions

If the mod has multiple downloadable files, G3M asks which file you want instead
of guessing.

---

## Compatibility Reality

Not every GameBanana upload is something G3M can auto-install cleanly.

When a file is compatible, the Browser-to-Downloads-to-Library flow is smooth.
When it is not, G3M can still tell you that the mod exists, but it may need a
manual install path or an external format conversion first.
