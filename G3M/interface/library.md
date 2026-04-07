# Library

The **Library** tab shows all mods you have installed locally. This is where you select which mods to use, manage mod files, and organize your collection.

---

## Layout

1. **Filter Bar** (top) — Search, tag filters, sort options.
2. **Game Selector** — Dropdown to switch which game's mods are displayed. Same games as listed in the Game Manager.
3. **Chapter Tabs** (DELTARUNE only) — For DELTARUNE, multiple chapter tabs appear: **Main Menu**, **Chapter 1**, **Chapter 2**, **Chapter 3**, **Chapter 4**. Each tab shows mods that include data for that specific chapter.
4. **Mod List** — Cards showing installed mods with their details and action buttons.
5. **Add Mod Button** — Opens a dialog to import or create a new mod.

---

## Filter Bar

### Search

A text input to filter mods by name, description, author, tags, added date, and updated date. Case-insensitive, matches all space-separated terms. Press the "×" button or clear the text to reset the filter.

### Tag Filters

Same tag buttons as in Mods Browser: **Text Edit**, **Customization**, **Gameplay**, **Other**. Select one or more to show only mods with matching tags.

### Hide Library Filters

In Settings → General, there is a **Hide Library filters** checkbox. When enabled, the filter bar in the Library tab is completely hidden for a cleaner look.

---

## Mod Cards (Library)

Each installed mod card shows:

- **Icon** — The mod's icon image if available, otherwise a placeholder.
- **Name** — The mod's display name. Bold if the mod is currently selected ("used").
- **Author** — The mod author.
- **Version** — The installed version number.
- **Description** — A brief description.
- **Tags** — Colored tag badges.
- **Added Date** — When the mod was first imported.
- **Last Updated** — When the mod was last modified.
- **Selected indicator** — A visual highlight or badge if the mod is currently selected for use in the active chapter.

### Mod Card Actions

Each mod card has action buttons:

- **Use / Unuse** — Toggles whether this mod is selected for the current chapter/game section. Multiple mods can be selected simultaneously for a chapter.
- **Edit** — Opens the Mod Editor dialog to modify metadata, files, and chapter assignments.
- **Delete** — Removes the mod from the library. A confirmation dialog appears. The mod folder and all its files are permanently deleted.
- **Export** — Exports the mod as a `.zip` archive.
- **Versions** — Opens the Mod Versions dialog (see [Mod Versions](../mods/mod-versions.md)).
- **Open Folder** — Opens the mod's folder in the system file explorer.

### Context Menu

Right-clicking a mod card opens a context menu with additional options depending on the mod:

- Open mod homepage (if the mod has a homepage URL).
- Open GameBanana page (if it's a GameBanana mod).
- Copy mod ID.
- Add to Blocklist.

---

## Chapter Tabs (DELTARUNE)

For DELTARUNE, the library splits mods into chapter tabs:

| Tab | Content |
| --- | --- |
| **Main Menu** | Mods with data for the title screen and menu (chapter 0). |
| **Chapter 1** | Mods with data for Chapter 1. |
| **Chapter 2** | Mods with data for Chapter 2. |
| **Chapter 3** | Mods with data for Chapter 3. |
| **Chapter 4** | Mods with data for Chapter 4. |

A single mod can appear in multiple chapter tabs if it contains data for multiple chapters.

The active tab determines which chapter you are selecting mods for. Selecting "Use" on a mod in Chapter 1 assigns it to Chapter 1 specifically.

### Chapter Mode vs Normal Mode

G3M has two launch modes for multi-chapter games:

- **Chapter Mode** — Each chapter has its own independent mod selection. When launching, G3M patches each chapter's data with its assigned mod. Enabled by toggling Chapter Mode in Settings → General or via the chapter tabs UI.
- **Normal Mode** — A single mod selection applies to all chapters. The mod is applied to the game's default data section.

---

## Mod Selection ("Used Mods")

When you click **Use** on a mod, it becomes the "used mod" for that chapter/game section. The used mods are what G3M patches into the game when you click **Launch**.

- You can select **multiple mods** per chapter. They will be applied in order — the first mod is patched first, then the second, and so on.
- Selecting a mod that is already selected will **deselect** it.
- Used mods are saved per-profile. Switching profiles changes which mods are selected.
- The current used mods are displayed in the status area and on the action button tooltip.

### Updates Available

If a mod has a newer version available on GameBanana than the locally installed version, a badge or indicator appears on the mod card. The action button changes from "Launch" to "Update" to indicate that one or more selected mods can be updated before launching.

---

## Add Mod Dialog

Clicking the **Add Mod** button (plus icon) opens a small dialog with two options:

- **Import Mod** — Opens a file picker to import a mod from a `.zip`, `.7z`, `.rar`, `.g3mtool`, `.g3mpatch`, `.deltamod`, or raw folder. See [Importing Mods](../mods/importing.md) for details.
- **Create Mod** — Opens the Mod Editor in creation mode. See [Mod Editor](../mods/mod-editor.md).

---

## Empty State

If no mods are installed for the current game and profile, the library shows a message: "No mods installed. Get started by browsing mods or importing a local mod." (Translated text depends on language.)
