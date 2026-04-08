# Drag and Drop

G3M supports drag and drop for importing mods, mod versions, and files throughout the application.

---

## Main Window Drop

You can drag files or URLs directly onto the main G3M window.

### Supported Drop Types

| Drop Type | Behavior |
| --- | --- |
| **Archive files** (`.zip`, `.7z`, `.rar`, `.tar.gz`, `.lzma`) | Extracted; content detected as native G3M mod, DELTAMOD format, or theme package, and imported accordingly. |
| **Patch files** (`.g3mpatch`, `.xdelta`, `.vcdiff`, `.csx`) | Imported as single-file mods. |
| **Data files** (`.win`, `.ios`, `.unx`, `.droid`) | Imported as raw-data mods. |
| **Folders** | Scanned for `mod_config.json` (native G3M), `_deltamodInfo.json` / `meta.json` (DELTAMOD), or known theme config files. Imported accordingly. |
| **URLs** (`http://`, `https://`) | Downloaded and then imported. Text drops containing HTTP URLs are also handled. |
| **Multiple files** | Queued and processed one at a time. |

### Drop Zones

The drop zone covers the entire main window content area. When a file is dragged over the window, a visual indicator (highlighted border or overlay) appears to show that G3M is ready to accept the drop.

---

## Mod Versions Dialog Drop

In the Mod Versions dialog, you can drag archive files or URLs onto the dialog to import them as version snapshots.

---

## Game Versions Dialog Drop

The Game Versions dialog also accepts dropped files and URLs to create a new game version snapshot.

---

## Modding Tools Drop

In the Modding Tools dialog, some input fields accept file drops. For example, you can drag a `.win` file onto the "Source file" field to populate it.

---

## File Path Collection

When processing dropped files, G3M:

1. Collects all file paths from the drop event.
2. Resolves any URL drops to local files (by downloading).
3. Filters out unsupported file types.
4. Queues the remaining files for import.
5. Processes each file according to its type.

---

## Limitations

- Drag and drop is not available on all Linux desktop environments. It depends on the window manager's support for the XDnD protocol with Qt applications.
- Very large files (multiple GB) dropped for import may take time to process. A progress indicator appears during import.
- Files cannot be dropped while G3M is in the middle of a patching or launching operation.
