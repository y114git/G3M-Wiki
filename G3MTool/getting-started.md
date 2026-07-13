# Getting Started

## Requirements

G3MTool currently targets **.NET 10**.

To build from source:

```bash
dotnet publish G3MToolCLI -c Release -r <runtime>
```

Common publish runtimes used by the project:

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
G3MTool patch apply original.win mod.g3mpatch patched.win
G3MTool patch batch apply original.win mod1.g3mpatch mod2.xdelta \
  --out-dir patched
G3MTool patch batch merge original.win "mod1.g3mpatch,mod2.xdelta" \
  "mod3.win,mod4.g3mpatch" --apply merged --out merged-patches
G3MTool info data.win
G3MTool diff original.win modified.win reports
```

## Interactive mode

Run `G3MTool` without arguments to open the interactive prompt.

```text
G3MTool (1.2.0) - by Y114
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

- **Option:** `--verbose`, `-v`
  - **Description:** Enable verbose output

- **Option:** `--log <path>`, `-l <path>`
  - **Description:** Enable file logging; use `default` to write into
    `logs/{command}_{timestamp}.log` next to the executable

- **Option:** `--json`
  - **Description:** Print JSON for commands that support it

- **Option:** `--xdelta-path <path>`
  - **Description:** Override the bundled xdelta binary

- **Option:** `--version`, `-V`
  - **Description:** Print the version and exit

## Optional cache

Commands that accept `--cache <dir>` can reuse `.g3mcache` analysis files across
runs. In the current codebase those cache files are used for repeated data-file
analysis and identity checks; they do not replace resource payloads.

Batch commands also keep a per-run hash cache. If the same input file or same
merge set appears more than once, G3MTool performs the expensive job once and
copies the resulting output for later duplicates.
