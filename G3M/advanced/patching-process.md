# Patching Process

This page explains in detail how G3M applies mods to game files when you click **Launch**.

---

## Overview

When you launch a game with mods selected, G3M performs a multi-step patching pipeline:

1. **Pre-flight checks** — Validate game path, check mods exist, ensure game is not already running.
2. **Backup** — Back up original game data files.
3. **Plugin pre-launch hooks** — Execute any plugin `before_mod_apply` hooks.
4. **Patching** — Apply each mod's data to the game files.
5. **Plugin post-patch hooks** — Execute any plugin `after_mod_apply_before_launch` hooks.
6. **Extra files** — Copy any additional files from mods into the game directory.
7. **Launch** — Start the game process.
8. **Plugin after-launch hooks** — Execute any plugin `after_game_started` hooks.
9. **Monitoring** — Watch the game process until it exits.
10. **Pre-restore hooks** — Execute any plugin `before_restore_after_exit` hooks.
11. **Restoration** — Restore all original files from backups.
12. **Plugin post-restore hooks** — Execute any plugin `after_restore_after_exit` hooks.
13. **Cleanup** — Remove temporary files and backups.

---

## Step 1: Pre-Flight Checks

Before any files are modified:

- G3M verifies the game path is set and the folder exists.
- G3M checks that the game executable exists at the configured path (or the custom executable, if configured).
- G3M checks that the game is not already running by scanning process names.
- G3M verifies that all selected mods exist on disk and have valid data files.
- If any check fails, the launch is aborted with a descriptive error message.

---

## Step 2: Backup

For each chapter/section that has a mod selected:

1. G3M identifies the game's main data file path (e.g., `<game_path>/data.win`).
2. The data file is copied to a temporary backup directory.
3. The backup path is recorded in the backup manager for later restoration.
4. If the data file does not exist (e.g., a new file will be created by the mod), this is recorded as a "file did not exist" entry — meaning it will be deleted during restoration.

If any backup operation fails (disk full, permission denied), the entire launch is aborted.

---

## Step 3: Plugin Pre-Patch Hooks

If any enabled plugins implement the `before_mod_apply` hook:

1. A background thread is created.
2. Each plugin's `before_mod_apply` function is called with a `PluginTaskRuntime` context.
3. Plugins can modify files, report progress, check cancellation, or use the host's backup manager.
4. If a plugin raises an error or signals cancellation, the launch may be aborted.

---

## Step 4: Patching

For each mod in the selected order:

### Determining the Patch Method

G3M examines the mod's data file to determine how to apply it:

| Data File Type | Method |
| --- | --- |
| `.g3mpatch` or `.zip` with `g3mpatch.json` | **G3M patch** — G3MTool applies the g3mpatch to the original data file. |
| `.xdelta` or `.vcdiff` | **xdelta patch** — G3MTool applies the binary diff to the original data file. |
| `.csx` | **CSX script** — G3MTool executes the script against the data file. |
| `.win`, `.ios`, `.unx`, `.droid` | **Raw replacement** — The mod's data file directly replaces the game's data file. |

### G3M Patch Application

1. G3MTool receives the original data file path and the patch file path.
2. It reads the `g3mpatch.json` manifest to determine which chunks to modify.
3. It applies the modifications in order, producing a patched data file.
4. The patched file replaces the original at the game's data file location.
5. Progress is reported as a percentage and displayed in the status bar.

### xdelta Patch Application

1. G3MTool receives the original data file and the `.xdelta`/`.vcdiff` patch.
2. It applies the binary diff, producing the patched data file.
3. The result replaces the game's data file.

### CSX Script Execution

1. G3MTool loads the `.csx` script.
2. The script is executed against the data file (passed as `data_file` parameter).
3. The modified data is written to the output location.
4. The result replaces the game's data file.

### Raw Data Replacement

1. The mod's data file is copied directly over the game's data file.
2. No diffing or patching is involved — the entire file is replaced.

### Multiple Mods

If multiple mods are selected for the same chapter:

1. The first mod's patch is applied to the original game data.
2. The second mod's patch is applied on top of the result from step 1.
3. And so on, in the order the mods appear in the used mods list.

This means later mods may override changes from earlier mods if they modify the same resources.

### Merge Options

When patching, two merge options (from Settings → Library) affect behavior:

- **Merge Properties** — If enabled, game object properties from the mod are merged with existing properties instead of replacing them entirely. This preserves properties that the mod didn't modify.
- **Merge Code** — If enabled, code blocks are merged rather than replaced. This can allow two mods that modify different code sections to coexist.

---

## Step 5: Extra Files

After the main data file is patched, G3M processes each mod's extra files:

1. For each file listed in the mod's `extra_files` array:
2. The file path is resolved relative to the mod folder.
3. The file is copied into the game directory, preserving its relative path structure.
4. If the file would overwrite an existing game file, that existing file is backed up first.
5. If the file would create a new file (not overwriting anything), it is recorded as "added" so it can be removed during restoration.

Extra files typically include: DLLs, audio bank files (.bank), font files, texture packs, configuration files, etc.

---

## Step 6: Launch

After patching:

1. G3M determines the launch method:
   - **Direct launch** — Runs the game executable directly (possibly with arguments for chapter selection).
   - **Steam launch** — Opens `steam://rungameid/<app_id>` via the system's default handler.
   - **PortProton launch** — Uses PortProton to run the executable (Linux).
2. The game process is started.
3. The status bar updates to show the game name and "Running...".
4. The action button changes to "Close Game".
5. Background music may continue or pause depending on settings.

### Direct Launch for DELTARUNE

When Direct Launch is configured for a specific DELTARUNE chapter:

1. G3M modifies the game's launch arguments or configuration to skip the title screen.
2. The game starts directly in the specified chapter.
3. This is handled by modifying the game's data or passing command-line arguments, depending on the game version.

### Steam Blocking

For DELTARUNE, when launching directly (not through Steam), G3M can prevent Steam from opening alongside the game. This avoids Steam overlay conflicts with certain mods.

---

## Step 7: Monitoring

G3M starts a game monitor thread that:

1. Periodically checks if the game process is still running (by name).
2. While running, tracks playtime.
3. When the game exits, signals G3M to begin restoration.
4. If the game crashes, the same restoration process occurs.

The monitor is separate from the main UI thread — G3M remains responsive while the game runs.

---

## Step 8: Restoration

After the game exits:

1. G3M reads the backup manager's records.
2. For each backed-up file:
   - If the backup exists, the modded file is replaced with the backup (original) file.
   - If the backup is `null` (file did not exist before), the file is deleted.
3. For each "added" file (from extra files that created new files):
   - The file is deleted.
4. The backup directory is cleaned up.
5. The status bar updates to confirm restoration (e.g., "Original files restored").

If any individual file restoration fails, an error is logged, but the process continues for remaining files.

---

## Step 10–12: Plugin Exit Hooks

On game exit, three additional hooks fire in sequence:

1. `before_restore_after_exit` — called after the game exits, before file restoration begins.
2. File restoration completes.
3. `after_restore_after_exit` — called after restoration completes.

These allow plugins to perform cleanup, recording, or other post-game operations.

Note: `after_game_started` fires immediately after the game process is launched (Step 8) and `mod_apply_cancelled` fires if patching is cancelled.

---

## Step 13: Cleanup

Final cleanup:

1. Temporary backup directory is deleted.
2. Any temporary files created during patching are removed.
3. The game monitor thread is stopped and cleaned up.
4. The action button reverts to "Launch".
5. Playtime is recorded (analytics, if enabled).
6. The window is restored if it was hidden during the game session.

---

## Cancellation

At any point during patching (before the game starts), you can click **Cancel**:

1. The current operation is interrupted.
2. All backed-up files are restored.
3. All added files are removed.
4. The launch is aborted.
5. The status bar shows "Cancelled".

Once the game is running, cancellation is not available — you can only use "Close Game" to terminate the game process, which triggers normal restoration.

---

## Error Handling

If patching fails at any step:

1. The error is logged with details.
2. The status bar shows an error message (red text).
3. All backed-up files are restored from backups.
4. The game is not launched.
5. The progress bar is reset.

Common patching errors:

- **G3MTool not available** — The bundled G3MTool executable was not found. Reinstall G3M.
- **Data file not found** — The game's data file is missing. Verify the game path.
- **Patch failed** — The patch could not be applied (corrupted patch, incompatible game version). Check that the mod is compatible with your game version.
- **Permission denied** — G3M cannot write to the game directory. Run as administrator or change the game's install location.
- **Disk full** — Not enough space for temporary files or backups.
