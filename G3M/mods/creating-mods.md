# Creating Mods

This guide covers the full process of creating a mod for G3M from scratch, including both the simple approach (data file replacement) and the advanced approach (patch-based mods).

---

## Prerequisites

Before creating a mod, you need:

- **G3M** installed and configured with the game you want to mod.
- The **original, unmodified game data file** (e.g., `data.win`). You can get this by keeping a clean copy of the game before any mods are applied.
- A **modified game data file** — the result of your changes. This comes from a GameMaker modding tool, hex editor, or scripting workflow.
- (Optional) G3M's built-in **Modding Tools** for creating patches and converting formats.

---

## Method 1: Simple Data File Replacement

The simplest way to create a mod.

### Steps

1. Make a copy of the game's `data.win` (or equivalent).
2. Modify the copy using your preferred tool (e.g., UndertaleModTool, GameMaker decompiler, hex editor, etc.).
3. Open G3M → Library → **Add Mod** → **Create Mod**.
4. Fill in the metadata:
   - **Name**: Your mod's name.
   - **Author**: Your name.
   - **Version**: A version number (e.g., "1.0.0").
   - **Description**: What your mod does.
   - **Game**: Select the target game.
   - **Tags**: Choose relevant tags (`customization`, `gameplay`, `textedit`, `other`).
5. Under the chapter file assignments, select your modified `data.win` as the data file for the appropriate chapter.
6. Optionally add an icon image.
7. Click **Create**.

The mod appears in the Library immediately. You can select it and launch the game to test.

### Drawbacks

- The mod file is very large (entire data file).
- Incompatible with other mods — this mod replaces everything.
- Breaks if the game updates.

---

## Method 2: Creating a g3mpatch

The recommended approach for distributing mods. A g3mpatch stores only the differences between the original and modified data.

### Steps

1. Start with the original game data file (`data.win`).
2. Create your modified version using your preferred modding tool.
3. Open G3M → **Modding Tools** (wrench icon).
4. Go to the **Convert DATA** tab.
5. Set:
   - **Source file**: Your modified `data.win`.
   - **Original data file**: The unmodified `data.win`.
   - **Target format**: `g3mpatch`.
6. Click **Convert**.
7. G3M creates a `.g3mpatch` file. Choose where to save it.
8. Now create the mod: Library → **Add Mod** → **Create Mod**.
9. Fill in metadata as before.
10. Under file assignments, select the `.g3mpatch` as the data file.
11. Click **Create**.

### Advantages

- Small file size (typically 1–10% of the original data file).
- Compatible with other mods that modify different parts of the data.
- Easy to distribute.

### Verification

After creating the g3mpatch, you can verify it:

1. In Modding Tools → **Patch** tab.
2. Apply the g3mpatch to the original data file.
3. Compare the result with your modified file (Modding Tools → **Diff** tab).
4. If they match, the patch is correct.

---

## Method 3: Creating an xdelta Patch

An alternative patch format popular in the modding community.

### Steps

1. Same starting point: original and modified data files.
2. Open Modding Tools → **Convert DATA**.
3. Set target format to `xdelta`.
4. Click **Convert**.
5. Save the `.xdelta` file.
6. Create the mod using this file as the data file.

---

## Method 4: CSX Script Mod

For advanced users who want programmatic modifications.

### Steps

1. Write a C# script (`.csx` file) that modifies the game data.
2. Test it in Modding Tools → **Patch** tab (apply the script to the original data and verify the result).
3. Create the mod using the `.csx` file as the data file.

### Script Structure

CSX scripts have access to the game data's internal structure. They can:

- Add, modify, or remove sprites.
- Change script code.
- Modify room layouts.
- Alter game objects and their properties.
- Manipulate sound, font, and background resources.

### Example (Conceptual)

```csharp
// Replace the text of a specific string resource
var stringTable = Data.Strings;
for (int i = 0; i < stringTable.Count; i++) {
    if (stringTable[i].Content == "Hello World") {
        stringTable[i].Content = "Modded World";
    }
}
```

(Actual API depends on the G3MTool CSX runtime.)

---

## Multi-Chapter Mods

For games with multiple chapters (like DELTARUNE), your mod can include data for multiple chapters:

1. In the Mod Editor, each chapter has its own file assignment row.
2. Create separate modified data / patches for each chapter you want to modify.
3. Assign each chapter's patch to its respective row.
4. The mod will appear in all chapter tabs that have data assigned.

You don't need to modify all chapters. A mod can target just Chapter 1 and Chapter 2, for example. Chapters without assigned data are left unmodified.

---

## Extra Files

If your mod needs additional files beyond the main data file (e.g., custom DLLs, audio banks, font files, texture packs):

1. In the Mod Editor, use the **Extra Files** button for the relevant chapter.
2. Select the additional files.
3. These files are copied into the game directory alongside the data file during patching.
4. They are removed during restoration after the game exits.

### Extra File Path Structure

Extra files maintain their relative path structure. If you add `sounds/custom_music.bank`, it will be placed at `<game_path>/sounds/custom_music.bank`.

---

## Mod Icon

Add an icon image to make your mod visually recognizable in the Library:

1. Prepare a square image (recommended: 256×256 px, PNG format).
2. In the Mod Editor, click the **Icon** button.
3. Select the image file.
4. The icon is copied into the mod folder and referenced in `mod_config.json`.

---

## Testing Your Mod

After creating the mod:

1. Select it in the Library (**Use** button).
2. Click **Launch**.
3. Verify the changes are applied in-game.
4. After exiting the game, verify the original files are restored correctly.
5. Check the log file for any errors during patching.

### Testing Tips

- Always test with a clean game installation first.
- Test each chapter separately for multi-chapter mods.
- Test with the "Merge Properties" and "Merge Code" settings both on and off.
- Test alongside another mod to verify compatibility.

---

## Distributing Your Mod

Once your mod is ready:

### Export as ZIP

1. In the Library, click **Export** on your mod card.
2. Save the `.zip` file.
3. Share the `.zip` — other G3M users can import it directly.

### Upload to GameBanana

1. Create an account on [GameBanana](https://gamebanana.com).
2. Navigate to the appropriate game page.
3. Upload your mod's `.zip` file.
4. Fill in the mod page details (name, description, screenshots, tags).
5. G3M users can then find and download your mod from the Mods Browser.

### Share the Patch File

Alternatively, share just the `.g3mpatch` or `.xdelta` file. Users can import it via G3M's Library → Add Mod → Import Mod.

---

## Best Practices

- **Use patches instead of raw data files.** Smaller size, better compatibility, easier updates.
- **Include a clear description.** Explain what your mod changes and any known compatibility issues.
- **Tag your mod appropriately.** Use the correct game and category tags.
- **Version your mod.** Use semantic versioning (1.0.0, 1.1.0, etc.). G3M can detect updates based on version numbers.
- **Include screenshots.** Visual mods especially benefit from before/after screenshots.
- **Test thoroughly.** Test on a clean game installation, test with popular mods, test on different game versions if possible.
- **Save versions.** Use G3M's Mod Versions feature to save snapshots of your mod as you develop it.
