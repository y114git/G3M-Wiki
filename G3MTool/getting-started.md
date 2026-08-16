# Getting Started

G3MTool targets .NET 10.

To build from source:

```bash
dotnet publish G3MToolCLI -c Release -r <runtime>
```

Common publish runtimes:

| Runtime       | Platform            |
| ------------- | ------------------- |
| `win-x64`     | Windows 64-bit      |
| `linux-x64`   | Linux 64-bit        |
| `linux-arm64` | Linux ARM64         |
| `osx-x64`     | macOS Intel         |
| `osx-arm64`   | macOS Apple Silicon |

## Basic usage

```bash
G3MTool patch create original.win modified.win mod.g3mpatch
G3MTool patch create original.win script.csx mod.xdelta --xdelta
G3MTool patch apply original.win mod.g3mpatch patched.win
G3MTool patch batch apply original.win mod1.g3mpatch mod2.xdelta \
  --out-dir patched
G3MTool patch batch merge original.win "mod1.g3mpatch,mod2.xdelta" \
  "mod3.win,mod4.csx" --apply merged --out merged-patches
G3MTool info data.win
G3MTool diff original.win modified.win reports
```

Run `G3MTool` without arguments for interactive prompt.

```text
G3MTool (1.2.8) - by Y114
Type 'help' for available commands or 'exit' to quit
```

Inside the prompt:

- `help` is translated to `--help`
- `exit` and `quit` close the prompt
- `clear` and `cls` clear the console
- quoted paths are supported by the built-in argument splitter

## Version

```bash
G3MTool --version
G3MTool -V
```

## Global options

- `--verbose`, `-v`: verbose output.
- `--log <path>`, `-l <path>`: log file; `default` writes beside executable.
- `--json`: JSON output where supported.
- `--xdelta-path <path>`: override bundled xdelta.
- `--version`, `-V`: print version and exit.

## Optional cache

Commands that accept `--cache <dir>` can reuse `.g3mcache` analysis files across
runs. In the current codebase those cache files are used for repeated data-file
analysis and identity checks; they do not replace resource payloads.

Batch commands also keep a per-run hash cache. If the same input file or same
merge set appears more than once, G3MTool performs the expensive job once and
copies the resulting output for later duplicates.
