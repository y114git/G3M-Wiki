# Getting Started

## Install

Download the release for your platform from the project releases page, or build from source.

## Build From Source

Requires the .NET 10 SDK.

```bash
dotnet publish G3MToolCLI -c Release -r <runtime>
```

Common runtimes:

| Runtime | Platform |
| --- | --- |
| `win-x64` | Windows 64-bit |
| `linux-x64` | Linux 64-bit |
| `linux-arm64` | Linux ARM64 |
| `osx-x64` | macOS Intel |
| `osx-arm64` | macOS Apple Silicon |

## Run Commands

```bash
G3MTool patch create original.win modified.win mod.g3mpatch
G3MTool patch apply original.win mod.g3mpatch patched.win
G3MTool info data.win
G3MTool diff original.win modified.win reports
```

G3MTool returns exit code `0` on success and `1` on command failure.

## Interactive Mode

Run `G3MTool` without arguments to open the prompt.

```text
G3MTool (?.?.?) - by Y114
Type 'help' for available commands or 'exit' to quit

(G3MTool) patch create original.win modified.win mod.g3mpatch
(G3MTool) info data.win --verbose
(G3MTool) exit
```

Interactive mode accepts the same commands as command-line mode. Use quotes for paths with spaces.

## Version

```bash
G3MTool --version
G3MTool -V
```

## Global Options

| Option | Description |
| --- | --- |
| `--verbose`, `-v` | Print detailed logs, phase names, and timing breakdowns |
| `--log [path]`, `-l` | Write a log file. Without a path, writes to `logs/{command}_{timestamp}.log` next to the executable |
| `--json` | Print JSON for commands that support it |
| `--version`, `-V` | Print the version and exit |

## Optional Cache

Commands that accept `--cache <dir>` can reuse `.g3mcache` analysis files across runs. The cache helps repeated `info`, `diff`, `patch create`, `patch validate --data`, and `patch merge` scenarios. It does not replace resource payloads during `patch apply`.
