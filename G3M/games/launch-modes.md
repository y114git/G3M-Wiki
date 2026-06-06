# Launch Modes

`Launch` in G3M can mean a few different things depending on your current game, selected mods, and launch settings.

---

## The Simple Mental Model

There are four launch situations most users care about:

- launch the game with no mods
- launch with selected mods
- launch DELTARUNE in chapter mode
- launch through Steam or another platform helper

Everything else is a variation of those.

---

## Vanilla vs Modded Launch

If nothing is selected, G3M mostly just resolves the executable and starts the game.

If mods are selected, G3M does more work:

1. prepares backups
2. applies patch or replacement data
3. copies any extra files a mod needs
4. launches the game
5. restores the original state after exit

So the important rule is simple: selected mods turn launch into a patch-and-restore session.

---

## Chapter Mode

Chapter mode matters mainly for DELTARUNE.

With chapter mode on:

- chapter selections can differ from each other
- chapter tabs become the place where you decide what is active
- launch uses those per-chapter choices instead of one shared selection

If chapter mode is off, the setup is simpler and behaves more like one shared mod stack.

---

## Direct Launch

Direct launch is the shortcut-style DELTARUNE flow that tries to jump straight into a chosen chapter instead of starting at the normal title flow.

For most users, the only thing to remember is:

- it is DELTARUNE-specific
- it is tied to chapter choice
- if you do not need it, you can ignore it completely

---

## Steam and Platform Helpers

If a game has a Steam App ID and you enabled Steam launch, G3M can patch first and then ask Steam to start the game.

On Linux, PortProton can also be part of the launch path when you configured it.

Those options change how the executable is started, but they do not change the basic idea that selected mods are applied before the game begins.

---

## Mod Order Still Matters

When you selected multiple mods for the same target, G3M applies them in sequence. That means later mods can override changes from earlier ones.

If two mods touch the same thing and the result looks wrong, order is one of the first things to check.
