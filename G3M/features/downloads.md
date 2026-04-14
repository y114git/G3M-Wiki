# Downloads

The Downloads system manages all file downloads in G3M — from GameBanana mods to one-click protocol installs to local file imports.

---

## Downloads Panel

The Downloads panel is accessible from Settings → Downloads sub-tab. It shows:

- **Active downloads** — Currently downloading files with progress bars.
- **Completed downloads** — Successfully downloaded and (optionally) installed mods.
- **Failed / Cancelled downloads** — Downloads that encountered errors or were cancelled by the user.

Each download record shows:

| Field | Description |
| --- | --- |
| **Name** | The display name of the download (mod name or file name). |
| **Source** | Where the download came from: GameBanana, G3M Protocol, External URL, or Local File. |
| **Target** | What type of artifact: Mod or Plugin. |
| **Status** | Current download phase: Queued, Downloading, Downloaded, Failed, Cancelled. |
| **Use Status** | Install phase: Not Started, Pending Auto, Overwrite Pending, Ready, Using, Needs Manual, Failed, Cancelled. |
| **Progress** | Percentage and bytes received/total during download. |
| **Date** | When the download was created and last updated. |

---

## Download Flow

1. **Enqueue** — A download is created with status "Queued". It enters the download queue.
2. **Download** — The file is downloaded from the source URL. Progress is updated in real time. Status becomes "Downloading".
3. **Downloaded** — The file is saved to disk in the `downloads/` folder. Status becomes "Downloaded".
4. **Auto-Use** — If auto-use is enabled (default), G3M automatically extracts and imports the mod into the library. This uses the same detection pipeline as manual import: native G3M mods install directly, DELTAMOD archives are converted automatically, eligible PizzaOven Pizza Tower mods go through PizzaOven conversion, and AFOM/CYOP tower archives use their dedicated import path. Status moves through "Pending Auto" → "Using" → complete.
5. **Ready** — If auto-use is disabled, the download stays as "Ready" until you manually trigger the install.

---

## Download Settings

| Setting | Default | Description |
| --- | --- | --- |
| **No auto-use** | Off | When on, downloaded files are not automatically installed. They stay as "Ready" in the Downloads panel. |
| **Delete after use** | Off | When on, the downloaded archive file is deleted after the mod is successfully installed. |
| **Save local imports** | Off | When on, files imported from the local file system are also saved as download records. |

---

## Download Sources

| Source | Description |
| --- | --- |
| **GameBanana** | Mods downloaded from the Mods Browser. |
| **G3M Protocol** | Mods received via `g3m://` or `deltahub://` one-click install links. |
| **External URL** | Direct URL downloads triggered programmatically. |
| **Local File** | Files imported from the local file system (only recorded if "Save local imports" is enabled). |

---

## Download Targets

| Target | Description |
| --- | --- |
| **Mod** | A game mod. Installed into the current profile's mods folder. |
| **Plugin** | A G3M plugin. Installed into the plugins folder. |

---

## Overwrite Handling

If a downloaded mod has the same ID as an existing mod in the library, the download enters "Overwrite Pending" status. You must decide:

- **Merge** — Update the existing mod with the new files.
- **Replace** — Delete the old mod and install the new one.
- **Skip** — Cancel the installation and leave the existing mod untouched.

---

## Manual Install

Downloads with "Needs Manual Install" status contain files that G3M could not automatically map to a supported import structure. This usually means the archive was not a native G3M mod, not a supported DELTAMOD package, not an eligible PizzaOven/AFOM conversion case, and not a raw patch/data layout G3M can assign automatically. You can manually use them by selecting the download and clicking **Use**, which opens the import dialog with the downloaded file pre-selected.

---

## Badges

The Downloads tab shows a notification badge with the count of downloads that need attention (overwrite pending, needs manual install). The badge disappears when all downloads are resolved.

---

## Persistence

All download records are persisted in `downloads/downloads_history.json`. The actual downloaded files are stored in the `downloads/` folder. Records survive application restarts. On startup, G3M checks which downloaded files still exist on disk and updates the `file_exists` flag accordingly.

---

## Cancellation

Active downloads can be cancelled by clicking the **Cancel** button on the download record. The partial file is removed.
