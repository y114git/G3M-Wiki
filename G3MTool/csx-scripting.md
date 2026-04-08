# CSX Scripting

G3MTool can execute `.csx` C# scripts against a loaded GameMaker data file. Scripts are compiled and run at runtime using the Roslyn scripting engine (`Microsoft.CodeAnalysis.CSharp.Scripting`). They receive a `ScriptGlobals` instance as their global context, which exposes the parsed `UndertaleData` and the G3MTool API surface.

Scripts are used by [`execute`](commands/execute.md) and are the internal mechanism behind all built-in Export/Import operations.

---

## Running a Script

```bash
G3MTool execute my_script.csx --data data.win --output patched.win
G3MTool execute my_export.csx --data data.win --output output_dir/
G3MTool execute my_import.csx --data data.win --input sprites/ --output patched.win
```

- `--data` loads the data file into `ScriptGlobals.Data` before the script runs.
- `--output` sets `ScriptGlobals.OutputDir`.
- `--input` sets `ScriptGlobals.InputDir`.
- If `--data` is omitted, `Data` is null — call `EnsureDataLoaded()` at the top of scripts that require it.

---

## ScriptGlobals API

The following properties and methods are available in every `.csx` script as top-level globals.

### Data Access

| Member | Type | Description |
| --- | --- | --- |
| `Data` | `UndertaleData` | The parsed GameMaker data file. Null if `--data` was not provided. |
| `FilePath` | `string` | Absolute path to the data file. Same as `DataFilePath`. |
| `DataFilePath` | `string` | Absolute path to the data file. |
| `ScriptPath` | `string?` | Absolute path to the `.csx` script itself. |
| `OutputDir` | `string` | Output directory path (set by `--output`). |
| `InputDir` | `string` | Input directory path (set by `--input`). Empty string if not provided. |
| `Verbose` | `bool` | True if G3MTool was launched with `--verbose`. |

### Validation

| Method | Description |
| --- | --- |
| `EnsureDataLoaded()` | Throws `ScriptException` if `Data` is null. Call at the top of scripts that require a loaded data file. |

### Messaging

| Method | Description |
| --- | --- |
| `ScriptMessage(string message)` | Logs a `[Script]` message to the console (and log file if `--log` is active). |
| `ScriptError(string message, string? title = null)` | Throws `ScriptException` with the given message, halting execution. |
| `ScriptQuestion(string message)` | Logs the question and always returns `true` (G3MTool runs headless — no interactive dialogs). |
| `ScriptInputDialog(string title, string label, string defaultInput, bool allowMultiline, bool showDialog)` | Logs the prompt and returns `defaultInput`. |
| `SimpleTextInput(string title, string label, string defaultInput, bool allowMultiline)` | Same as `ScriptInputDialog`. |
| `PromptLoadFile(string filter, string defaultPath)` | Logs the prompt and returns `null`. |
| `PromptSaveFile(string filter, string defaultName)` | Logs the prompt and returns `null`. |
| `PromptChooseDirectory()` | Logs the prompt and returns `null`. |

> Dialog and prompt methods always return their default values or null — G3MTool has no GUI. Design scripts to work without user input, or check the return value and handle null.

### Progress Tracking

Progress output is only printed when `--verbose` is active.

| Method | Description |
| --- | --- |
| `SetProgressBar(string? label, string status, int current, int max)` | Set the current progress state. |
| `UpdateProgressBar(string? label, string status, int current, int max)` | Alias for `SetProgressBar`. |
| `AddProgress(int amount)` | Increment the progress counter by `amount`. |
| `IncrementProgress()` | Increment the progress counter by 1. |
| `IncrementProgressParallel()` | Thread-safe version of `IncrementProgress()`. |
| `StartProgressBarUpdater()` | Start a background task that prints progress to stdout every 500ms (verbose mode only). |
| `StopProgressBarUpdater()` | Stop and dispose the progress updater task. |
| `HideProgressBar()` | Reset progress state to zero. |
| `GetProgress()` | Returns the current progress counter value. |

### Stub Methods (no-op)

These methods exist for compatibility with UndertaleModTool scripts that target a GUI environment. In G3MTool they do nothing.

| Method | Notes |
| --- | --- |
| `SetFinishedMessage(bool enabled)` | No-op. |
| `ChangeSelection(object obj, bool isRecursive = false)` | No-op. |
| `SyncBinding(string name, bool value)` | No-op. |
| `SyncBinding(bool condition, bool value)` | No-op. |
| `DisableAllSyncBindings()` | No-op. |

---

## Script Structure

A minimal script that modifies a data file:

```csharp
EnsureDataLoaded();

// Access resources directly through Data
var player = Data.GameObjects.First(o => o.Name.Content == "obj_player");
ScriptMessage($"Found player object at index {Data.GameObjects.IndexOf(player)}");

// Modify something
foreach (var str in Data.Strings)
{
    if (str.Content == "Press Z to continue")
        str.Content = "Press ENTER to continue";
}

ScriptMessage("Done.");
```

A minimal export script:

```csharp
EnsureDataLoaded();

// OutputDir is set by --output
Directory.CreateDirectory(OutputDir);

foreach (var room in Data.Rooms)
{
    var path = Path.Combine(OutputDir, room.Name.Content + ".txt");
    File.WriteAllText(path, $"{room.Name.Content}: {room.Width}x{room.Height}");
}
```

A minimal import script that uses `InputDir`:

```csharp
EnsureDataLoaded();

// InputDir is set by --input
foreach (var file in Directory.GetFiles(InputDir, "*.txt"))
{
    var name = Path.GetFileNameWithoutExtension(file);
    // ... import logic
    IncrementProgress();
}
```

---

## UndertaleData Collections

The `Data` object exposes all resource collections as lists. Common ones:

| Property | Type | Contents |
| --- | --- | --- |
| `Data.Sprites` | `IList<UndertaleSprite>` | All sprites |
| `Data.Sounds` | `IList<UndertaleSound>` | All sounds |
| `Data.Code` | `IList<UndertaleCode>` | All code entries (GML) |
| `Data.GameObjects` | `IList<UndertaleGameObject>` | All game objects |
| `Data.Rooms` | `IList<UndertaleRoom>` | All rooms |
| `Data.Backgrounds` | `IList<UndertaleBackground>` | All backgrounds/tilesets |
| `Data.Fonts` | `IList<UndertaleFont>` | All fonts |
| `Data.Scripts` | `IList<UndertaleScript>` | All scripts |
| `Data.Shaders` | `IList<UndertaleShader>` | All shaders |
| `Data.Strings` | `IList<UndertaleString>` | The string table |
| `Data.AudioGroups` | `IList<UndertaleAudioGroup>` | Audio groups |
| `Data.EmbeddedTextures` | `IList<UndertaleEmbeddedTexture>` | Embedded texture atlases |
| `Data.TexturePageItems` | `IList<UndertaleTexturePageItem>` | Texture page UV entries |
| `Data.GeneralInfo` | `UndertaleGeneralInfo` | Game metadata |

These are the same types used by [UndertaleModTool](https://github.com/UnderminersTeam/UndertaleModTool). Scripts written for UndertaleModTool are largely compatible with G3MTool, with the exception that dialog/prompt methods return defaults instead of showing GUI dialogs.

---

## Error Handling

If a script throws any exception (including `ScriptException` from `ScriptError`), G3MTool prints the error message to stderr and exits with code `1`. No partial output is guaranteed to be valid.

---

## Built-in Scripts Reference

The built-in scripts are embedded in the G3MTool binary and are the canonical source for how each resource type is exported and imported. The full source is available in the repository under [`G3MToolCLI/Assets/scripts/`](https://github.com/y114git/G3MTool/tree/main/G3MToolCLI/Assets/scripts).
