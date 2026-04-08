# G3MTool

G3MTool is a cross-platform command-line tool for working with GameMaker data files (`data.win`, `.ios`, `.unx`, `.droid`). It is the backend engine that G3M (the mod manager) calls to create and apply patches, execute scripts, and inspect game data.

---

## What G3MTool Does

| Command | Purpose |
| --- | --- |
| [`patch`](commands/patch.md) | Create, apply, validate, or merge G3M-native resource patches (`.g3mpatch`) |
| [`xpatch`](commands/xpatch.md) | Create or apply binary xdelta patches |
| [`execute`](commands/execute.md) | Run `.csx` C# scripts against a data file, or passthrough to external programs |
| [`info`](commands/info.md) | Inspect a data file or `.g3mpatch` — resource counts, GeneralInfo, detailed listings |
| [`diff`](commands/diff.md) | Compare two data files or patches and produce a Markdown diff report |

---

## Key Concepts

- **G3M patch (`.g3mpatch`)** — G3MTool's native patch format. A ZIP archive containing a `g3mpatch.json` manifest with per-resource changes (sprites, sounds, code, rooms, etc.) and an embedded xdelta fallback. More precise and merge-friendly than a raw xdelta. See [G3M Patch Format](patch-format.md).
- **xdelta patch** — A standard binary diff format supported by G3MTool for compatibility. Less merge-friendly than `.g3mpatch` but simpler and smaller.
- **CSX scripts** — C# scripts (Roslyn-compiled at runtime) that receive a `ScriptGlobals` object with access to the loaded `UndertaleData`. Used to programmatically modify game data. See [CSX Scripting](csx-scripting.md).
- **Interactive mode** — When launched with no arguments, G3MTool enters a `(G3MTool)` REPL prompt where you can type commands interactively.

---

## Platform Support

G3MTool is a self-contained single-file binary built on .NET 10. No runtime installation required.

| Platform | Identifier |
| --- | --- |
| Windows 64-bit | `win-x64` |
| Linux 64-bit | `linux-x64` |
| Linux ARM64 | `linux-arm64` |
| macOS Intel | `osx-x64` |
| macOS Apple Silicon | `osx-arm64` |

---

## Global Options

These options apply to all commands:

| Option | Alias | Description |
| --- | --- | --- |
| `--verbose` | `-v` | Enable verbose output: timing breakdowns, progress, per-phase logs |
| `--log [path]` | `-l` | Write log to file. Default path: `logs/{command}_{timestamp}.log` |
| `--json` | | Output in JSON format (supported by `info` and `patch validate`) |
