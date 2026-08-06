# CSX Scripting

G3MTool can execute `.csx` C# scripts against a loaded GameMaker data file.
Scripts are compiled and run at runtime through the Roslyn scripting engine and
receive a `ScriptGlobals` instance as their global context.

Scripts are used by [`execute`](commands/execute.md) and can be supplied directly
to `patch create`, `patch apply`, `patch merge`, and their batch variants.
G3MTool also embeds import and export scripts for UndertaleModTool-style
workflows.

## Using a script as a patch input

```bash
G3MTool patch apply original.win mod.csx patched.win
G3MTool patch create original.win mod.csx mod.g3mpatch
G3MTool patch merge original.win base.xdelta mod.csx --apply merged.win
```

For patch commands, G3MTool loads the current DATA into the script globals,
runs the script, saves its result to a temporary DATA file, and verifies that
the file can be reopened before continuing. A script failure or invalid saved
DATA stops the operation with an error.

## Running a script

```bash
G3MTool execute my_script.csx --data data.win --output patched.win
G3MTool execute my_export.csx --data data.win --output output_dir/
G3MTool execute my_import.csx --data data.win --input sprites/ --output patched.win
```

Current behavior:

- `--data` loads the data file before the script runs.
- `--input` becomes the first script argument and is also exposed as
  `ScriptGlobals.InputDir`.
- `--output` is converted into `ScriptGlobals.OutputDir` as a directory path.
- If `--data` is omitted, scripts still run, but data-dependent code must call
  `EnsureDataLoaded()` first and handle the failure.

## ScriptGlobals surface

### Properties

- **Member:** `Data`
  - **Type:** `UndertaleData`
  - **Description:** Loaded GameMaker data file

- **Member:** `FilePath`
  - **Type:** `string`
  - **Description:** Data-file path when data is loaded; otherwise script or
    fallback path

- **Member:** `DataFilePath`
  - **Type:** `string`
  - **Description:** Absolute path to the loaded data file, or empty string

- **Member:** `ScriptPath`
  - **Type:** `string?`
  - **Description:** Absolute path to the `.csx` script

- **Member:** `OutputDir`
  - **Type:** `string`
  - **Description:** Output directory derived from `--output`

- **Member:** `InputDir`
  - **Type:** `string`
  - **Description:** Input directory derived from `--input`, or empty string

- **Member:** `Verbose`
  - **Type:** `bool`
  - **Description:** Mirrors G3MTool verbose mode

- **Member:** `ExePath`
  - **Type:** `string`
  - **Description:** Directory that contains the current script

### Validation and messaging

- **Method:** `EnsureDataLoaded()`
  - **Description:** Throws `ScriptException` if no data file is loaded

- **Method:** `ScriptError(string message, string? title = null)`
  - **Description:** Throws `ScriptException`

- **Method:** `ScriptMessage(string message)`
  - **Description:** Writes a script log message

- **Method:** `ScriptWarning(string message)`
  - **Description:** Writes a script warning

- **Method:** `RunUMTScript(string path)`
  - **Description:** Runs another CSX file with the same loaded DATA and globals

## Relative scripts and resources

G3MTool resolves `#load`, metadata references, and `RunUMTScript()` paths from
the script directory. Nested scripts can call other scripts under the main
script's directory tree. G3MTool rejects a nested path that escapes that tree.

Keep helper scripts and resource folders beside the entry script. In a G3M mod,
mark those folders as dependency-only extra entries so G3M keeps them in the mod
folder without copying them into the game.

- **Method:** `ScriptQuestion(string message)`
  - **Description:** Logs the question and returns `true`

- **Method:** `ScriptInputDialog(...)`
  - **Description:** Logs the prompt and returns the default input

- **Method:** `SimpleTextInput(...)`
  - **Description:** Same behavior as `ScriptInputDialog(...)`

- **Method:** `PromptLoadFile(...)`
  - **Description:** Logs and returns `null`

- **Method:** `PromptSaveFile(...)`
  - **Description:** Logs and returns `null`

- **Method:** `PromptChooseDirectory()`
  - **Description:** Logs and returns `null`

### Progress helpers

- **Method:** `SetProgressBar(...)`
  - **Description:** Set progress state

- **Method:** `UpdateProgressBar(...)`
  - **Description:** Alias for `SetProgressBar(...)`

- **Method:** `AddProgress(int amount)`
  - **Description:** Increment progress by an amount

- **Method:** `IncrementProgress()`
  - **Description:** Increment progress by one

- **Method:** `IncrementProgressParallel()`
  - **Description:** Thread-safe increment

- **Method:** `StartProgressBarUpdater()`
  - **Description:** Start periodic console progress output in verbose mode

- **Method:** `StopProgressBarUpdater()`
  - **Description:** Stop the background progress updater

- **Method:** `HideProgressBar()`
  - **Description:** Reset progress state

- **Method:** `GetProgress()`
  - **Description:** Return the current progress value

### Compatibility stubs

These methods exist for compatibility with GUI-oriented scripts and are no-ops
in G3MTool:

- `SetFinishedMessage(bool enabled)`
- `ChangeSelection(object obj, bool isRecursive = false)`
- `SyncBinding(string name, bool value)`
- `SyncBinding(bool condition, bool value)`
- `DisableAllSyncBindings()`

## Built-in scripts

The current embedded scripts are the files under `G3MToolCLI/Assets/scripts/`,
including import and export helpers for:

- asset order
- audio groups
- backgrounds
- code entries
- embedded textures
- extensions
- fonts
- game objects
- GeneralInfo
- paths
- rooms
- shaders
- sounds
- sprites
- texture group info
- texture page items
- tilesets
- timelines
