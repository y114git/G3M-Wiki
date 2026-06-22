# Modding Tools

Modding Tools is G3M's built-in utility dialog for working with GameMaker data files and patch files.

## Where to find it

1. Open G3M.
2. Use the title bar or tools/menu area to open **Modding Tools**.
3. Choose the tab for the job you want: **Convert DATA**, **Patch**, **Merge**, **Info**, or **Diff**.

The dialog is non-modal, so you can keep it open while looking at the rest of G3M.

Preflight mod-conflict analysis is now a separate **Mod Diagnostics** dialog from the Library tab rather than another tab inside Modding Tools.

## Tabs

The current dialog has these tabs:

- Convert DATA
- Patch
- Merge
- Info
- Diff

## Convert DATA

Use **Convert DATA** when an installed mod already contains a patch/data file and you want to save another format as a new mod version.

Typical flow:

1. Select the active profile at the top of the tab.
2. Pick the output format from the format dropdown.
3. Check one or more mods from the list.
4. Click **Run**.

The output format can be:

- `g3mpatch`
- `xdelta`
- `data.win`
- `game.ios`
- `game.win`

G3M scans the selected profile's installed mod folders, converts eligible DATA patch files, and creates a new version archive under each selected mod's own `mod_versions` folder. If several selected mods target the same game, G3M reuses the resolved game path during the run instead of resolving it again for every mod.

For a mod in the `Default` profile, version archives are stored like this on Windows:

`%LOCALAPPDATA%\G3M\profiles\Default\<mod id>\mod_versions\`

The current mod files are not overwritten directly. A new mod version is created so you can switch versions from the Mod Versions dialog.

## Patch

Use **Patch** when you have two files and want to create, apply, or convert a patch manually.

Create patch:

1. Set the action to **Create**.
2. Pick the original DATA file.
3. Pick the modified DATA file.
4. Choose an output path ending in `.g3mpatch` or `.xdelta`.
5. Click **Run**.

Apply patch:

1. Set the action to **Apply**.
2. Pick the original DATA file.
3. Pick the patch file.
4. Choose where to write the patched DATA output.
5. Click **Run**.

Convert patch:

1. Set the action to **Convert**.
2. Pick the original DATA file.
3. Pick the source patch.
4. Choose the output patch format.
5. Click **Run**.

For `.g3mpatch` create/apply jobs, enable **Batch mode** when you want to process many modified DATA files or many patch files against the same original. Add every input file to the batch list, choose an output folder, then click **Run**. Shared options apply to the whole queue:

- **Continue on error** keeps later items running if one item fails.
- **Embed xdelta fallback** stores a fallback binary patch when creating `.g3mpatch` files and allows fallback use when applying them.

This tab writes only to the output file or output folder you choose. It does not automatically install the result as a mod unless you later import or add that file yourself.

## Merge

Use **Merge** when you have multiple patch files that should be combined against the same original DATA file.

1. Pick the original DATA file.
2. Add two or more patch files.
3. Choose the output DATA file.
4. Optionally choose a `.g3mpatch` output if you want to keep the merged patch package too.
5. Click **Run**.

For repeated merges, enable **Batch mode**. Build one merge set in the file list, click **Add set**, then build the next set. Choose the DATA output folder, optionally choose a merged patch output folder, and click **Run** to merge every set through one G3MTool batch command.

Merge options apply to every set in the batch:

- **Code** enables code-aware merge logic.
- **Properties** enables property-aware merge logic.
- **Report** writes merge report files when supported.
- **Continue on error** keeps later sets running if one set fails.

If two patches change the same content, the result depends on what the underlying merge can safely combine.

## Info

Use **Info** to inspect a DATA file or patch package. Select a file and click **Run**. G3MTool prints metadata and detected details into the output area.

## Diff

Use **Diff** to compare two DATA files and generate a report.

1. Pick the first DATA file.
2. Pick the second DATA file.
3. Click **Run**.

G3M creates a temporary report folder and opens the generated report when possible.

## Supported formats

The tool flow currently recognizes:

- `.win`
- `.ios`
- `.unx`
- `.droid`
- `.g3mpatch`
- `.zip` archives that contain `g3mpatch.json`
- `.xdelta`
- `.vcdiff`
- `.csx`

Supported ready DATA filenames include `data.win`, `game.ios`, `game.win`, `game.unx`, and `game.droid`. For manual file selection, the extension is usually what matters: a file named `BOSSRUSH.win` is still a `.win` DATA file.

## What it is for

- turn modified data into patch files
- apply patch files back onto original data
- compare two data files
- inspect data files
- merge one or many changeset sets

## G3MTool dependency

The dialog is a front end for the bundled `G3MTool` binaries. If you care about exact command behavior or patch format details, see the `G3MTool` section of the wiki.

G3MTool cache files, when used by these workflows, are stored under:

`%LOCALAPPDATA%\G3M\cache\G3MTool\`

Bundled G3MTool 1.2.0 also supports CLI batch operations:

- `patch batch apply` for applying many patches independently to the same original
- `patch batch create` for creating many `.g3mpatch` files from one original
- `patch batch merge` for running multiple independent merge sets from one command

The **Convert DATA** tab uses a checkbox batch flow for installed mods. The **Patch** and **Merge** tabs expose supported batch apply/create/merge flows in the UI, and the same commands remain available through the bundled executable for scripted or advanced workflows.
