# Modpacks (Multiple Mods)

G3M supports selecting and applying multiple mods simultaneously for a single game chapter. This section explains how multi-mod configurations work.

---

## Selecting Multiple Mods

In the Library, for any chapter tab:

1. Click **Use** on the first mod you want to apply.
2. Click **Use** on the second mod.
3. Click **Use** on the third mod.
4. Continue for as many mods as you want.

All selected mods appear in the "used mods" list for that chapter. Their order in the list determines the application order.

---

## Application Order

When launching with multiple mods selected for a chapter:

1. **First mod** is applied to the original game data file.
2. **Second mod** is applied on top of the result from step 1.
3. **Third mod** is applied on top of the result from step 2.
4. And so on.

This sequential application means:

- **Non-overlapping mods** — Mods that change different parts of the game data coexist perfectly. For example, a sprite replacement mod and a music replacement mod will both work.
- **Overlapping mods** — If two mods change the same resource, the **last mod** in the list wins for that resource. The earlier mod's changes to that specific resource are overwritten.

---

## Merge Options

Two settings in Settings → Library affect how overlapping changes are handled:

### Merge Properties

When **enabled**, game object properties from each mod are merged with existing properties rather than replacing the entire property set. This means:

- If Mod A changes property X and Mod B changes property Y on the same object, both changes are preserved.
- If both Mod A and Mod B change property X, Mod B's value wins (last mod wins).

When **disabled** (default), properties are replaced wholesale — if Mod B touches an object, all of Mod A's property changes to that object are lost.

### Merge Code

When **enabled**, code blocks from each mod are merged rather than replaced. This allows:

- Two mods that modify different code sections of the same script to coexist.
- Insertions from both mods to be preserved.

When **disabled** (default), if Mod B modifies a code block that Mod A also modified, Mod A's changes to that block are lost.

---

## Compatibility Considerations

Not all mods are designed to work together. Common compatibility issues:

| Scenario | Result |
| --- | --- |
| Two sprite replacement mods changing different sprites | Works perfectly. |
| Two sprite replacement mods changing the same sprite | Last mod's sprite is used. |
| A gameplay mod and a text translation mod | Usually works (different resource types). |
| Two gameplay mods changing the same game logic | Likely conflicts — last mod's logic overwrites the first. |
| A raw data replacement mod and any other mod | Raw data replaces everything — the other mod's changes are lost. |
| Two g3mpatch mods with non-overlapping chunks | Works perfectly. |

**Recommendation**: Use patch-based mods (g3mpatch, xdelta, csx) rather than raw data mods when combining multiple mods. Patches only modify specific parts of the data, leaving the rest untouched for other mods.

---

## Reordering Mods

To change the application order of selected mods:

1. In the Library, look at the used mods list for the chapter.
2. Deselect all mods.
3. Re-select them in the desired order.

The first mod you select becomes the first to be applied. Think of it as a "stack" — the bottom mod is applied first, and the top mod is applied last (and has the highest priority).

---

## Deselecting Mods

To remove a mod from the multi-mod selection:

- Click **Unuse** on the mod card.
- Or click **Use** again on an already-selected mod (toggles it off).

---

## Limitations

- There is no automatic conflict detection. G3M does not analyze whether two mods modify the same resources. You need to know your mods and their compatibility.
- Performance decreases with many mods. Each mod requires a separate patching pass, so 10 mods take approximately 10× the patching time of a single mod.
- Raw data replacement mods should generally be placed **first** in the order (if used at all), since they replace the entire data file and subsequent patch mods can then modify on top of it.

---

## Shortcuts and Multiple Mods

Desktop shortcuts support only **one mod per chapter**. If you have multiple mods selected for a chapter, shortcut creation shows a warning message. You must reduce to one mod per chapter to create a shortcut.

For multi-mod configurations, launch from the GUI instead of using shortcuts.

---

## Saving Multi-Mod Selections

Your multi-mod selection is saved automatically to the current profile. When you switch profiles and come back, the selection is restored. When you close and reopen G3M, the selection persists.
