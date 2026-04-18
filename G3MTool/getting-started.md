# Getting Started

## Installation

Download the latest release binary for your platform from the [GitHub Releases](https://github.com/y114git/G3MTool/releases) page. The binary is self-contained — no .NET runtime or dependencies need to be installed separately.

| Platform | Binary name |
| --- | --- |
| Windows | `G3MTool.exe` |
| Linux | `G3MTool` |
| macOS | `G3MTool` |

### Build from Source

Requires .NET 10 SDK.

```bash
dotnet publish G3MToolCLI -c Release -r <platform>
```

Replace `<platform>` with one of: `win-x64`, `linux-x64`, `linux-arm64`, `osx-x64`, `osx-arm64`.

---

## Usage Modes

### Command-line (non-interactive)

Pass a command and its arguments directly:

```
G3MTool patch create original.win modified.win
G3MTool info data.win
G3MTool xpatch apply original.win mod.xdelta patched.win
```

Exit code `0` on success, `1` on error. Errors are written to stderr.

### Interactive mode

Run G3MTool with no arguments to enter the REPL prompt:

```
G3MTool
```

```
G3MTool (?.?.?) - by Y114
Type 'help' for available commands or 'exit' to quit

(G3MTool) patch create original.win modified.win
(G3MTool) info data.win --verbose
(G3MTool) exit
```

Interactive mode supports the same commands as non-interactive. Type `help` to list them, `exit` or `quit` to leave, `clear` or `cls` to clear the screen. Arguments with spaces can be quoted (`"path with spaces/file.win"`).

To print only the version without entering interactive mode:

```bash
G3MTool --version
G3MTool -V
```

---

## Output Location

When no output path is specified, G3MTool saves output files **next to the G3MTool executable**. This applies to `patch create`, `xpatch create`, `xpatch apply`, and `patch apply`.

The `diff` command defaults to a `diff/` subdirectory next to the executable.

---

## Global Options

Apply to any command:

```
G3MTool patch create original.win modified.win --verbose
G3MTool info data.win --json
G3MTool patch validate mod.g3mpatch --log
```

| Option | Description |
| --- | --- |
| `--verbose` / `-v` | Print timing breakdowns, per-phase progress, and detailed logs to stdout |
| `--log [path]` / `-l` | Write a log file. If path is omitted, defaults to `logs/{command}_{timestamp}.log` |
| `--json` | Output structured JSON (supported for `info` and `patch validate`) |
| `--version` / `-V` | Print only the application version and exit |
