# G3MTool

G3MTool is command-line reference implementation for `.g3mpatch`. It works
with GameMaker DATA files and supports patch creation, application, merging,
inspection, diff reports, `.csx`, and xdelta.

Version: 1.2.9

Supported DATA extensions: `.win`, `.ios`, `.droid`, and `.unx`.

## Commands

- [`patch`](commands/patch.md): create, apply, validate, merge, and batch jobs.
- [`xpatch`](commands/xpatch.md): create or apply xdelta patches.
- [`execute`](commands/execute.md): run `.csx`, xdelta, or another program.
- [`info`](commands/info.md): inspect a DATA file or `.g3mpatch`.
- [`diff`](commands/diff.md): write a comparison report.
- [`--version`](commands/version.md): print version.

## Global options

- `-v`, `--verbose`: verbose output.
- `-l`, `--log <path>`: write a log. `--log default` writes beside executable.
- `--json`: JSON output for supported commands.
- `--xdelta-path <path>`: use an xdelta executable at `path`.
- `--version`, `-V`: print version and exit.

## Runtime behavior

- Running `G3MTool` with no arguments starts the interactive prompt.
- The executable name is `G3MTool`.
- The project targets **.NET 10** and is configured for self-contained
  single-file publish output.
- Platform-specific bundled xdelta binaries are embedded for Windows, Linux, and
  macOS publish targets. macOS builds use the matching Intel or Apple Silicon
  xdelta binary.

## Output defaults

When an output path is optional and omitted, commands generally write next to
the executable unless a command page states a different default. `diff` writes
into `<executable>/diff/` by default.

Batch apply and batch create require `--out-dir` and write generated files into
that directory. Batch merge writes patched data files to the current directory
by default, can redirect them with `--apply`, and can additionally keep merged
`.g3mpatch` files with `--out`.

`patch create` writes `.g3mpatch` by default. Add `--xdelta` to write an xdelta
patch. `--xdelta` and `--xdelta-fallback` cannot be used together.
