# CSX Scripting

G3MTool can execute `.csx` C# scripts against a loaded GameMaker data file. Scripts are compiled and run at runtime through the Roslyn scripting engine and receive a `ScriptGlobals` instance as their global context.

Scripts are used by [`execute`](commands/execute.md). G3MTool also embeds import and export scripts for UndertaleModTool-style workflows.

## Running a script

```bash
G3MTool execute my_script.csx --data data.win --output patched.win
G3MTool execute my_export.csx --data data.win --output output_dir/
G3MTool execute my_import.csx --data data.win --input sprites/ --output patched.win
```

Current behavior:

- `--data` loads the data file before the script runs.
- `--input` becomes the first script argument and is also exposed as `ScriptGlobals.InputDir`.
- `--output` is converted into `ScriptGlobals.OutputDir` as a directory path.
- If `--data` is omitted, scripts still run, but data-dependent code must call `EnsureDataLoaded()` first and handle the failure.

## ScriptGlobals surface

### Properties

| Member | Type | Description |
| --- | --- | --- |
| `Data` | `UndertaleData` | Loaded GameMaker data file |
| `FilePath` | `string` | Data-file path when data is loaded; otherwise script or fallback path |
| `DataFilePath` | `string` | Absolute path to the loaded data file, or empty string |
| `ScriptPath` | `string?` | Absolute path to the `.csx` script |
| `OutputDir` | `string` | Output directory derived from `--output` |
| `InputDir` | `string` | Input directory derived from `--input`, or empty string |
| `Verbose` | `bool` | Mirrors G3MTool verbose mode |

### Validation and messaging

| Method | Description |
| --- | --- |
| `EnsureDataLoaded()` | Throws `ScriptException` if no data file is loaded |
| `ScriptError(string message, string? title = null)` | Throws `ScriptException` |
| `ScriptMessage(string message)` | Writes a script log message |
| `ScriptQuestion(string message)` | Logs the question and returns `true` |
| `ScriptInputDialog(...)` | Logs the prompt and returns the default input |
| `SimpleTextInput(...)` | Same behavior as `ScriptInputDialog(...)` |
| `PromptLoadFile(...)` | Logs and returns `null` |
| `PromptSaveFile(...)` | Logs and returns `null` |
| `PromptChooseDirectory()` | Logs and returns `null` |

### Progress helpers

| Method | Description |
| --- | --- |
| `SetProgressBar(...)` | Set progress state |
| `UpdateProgressBar(...)` | Alias for `SetProgressBar(...)` |
| `AddProgress(int amount)` | Increment progress by an amount |
| `IncrementProgress()` | Increment progress by one |
| `IncrementProgressParallel()` | Thread-safe increment |
| `StartProgressBarUpdater()` | Start periodic console progress output in verbose mode |
| `StopProgressBarUpdater()` | Stop the background progress updater |
| `HideProgressBar()` | Reset progress state |
| `GetProgress()` | Return the current progress value |

### Compatibility stubs

These methods exist for compatibility with GUI-oriented scripts and are no-ops in G3MTool:

- `SetFinishedMessage(bool enabled)`
- `ChangeSelection(object obj, bool isRecursive = false)`
- `SyncBinding(string name, bool value)`
- `SyncBinding(bool condition, bool value)`
- `DisableAllSyncBindings()`

## Built-in scripts

The current embedded scripts are the files under `G3MToolCLI/Assets/scripts/`, including import and export helpers for:

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
