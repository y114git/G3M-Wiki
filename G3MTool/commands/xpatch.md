# xpatch

Create or apply xdelta patches. xdelta stores byte-level differences and expects the matching original file when applying.

G3MTool bundles xdelta for supported platforms.

## xpatch create

```bash
G3MTool xpatch create <original> <modified> [output]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Source file |
| `modified` | Yes | Modified file |
| `output` | No | Output `.xdelta`. Default: `<modified_name>.xdelta` next to the executable |

Example:

```bash
G3MTool xpatch create data.win data_modded.win mod.xdelta
```

## xpatch apply

```bash
G3MTool xpatch apply <original> <patch> [output]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Source file expected by the xdelta patch |
| `patch` | Yes | `.xdelta` file |
| `output` | No | Output file. Default: `<original_name>_patched.<ext>` next to the executable |

Example:

```bash
G3MTool xpatch apply data.win mod.xdelta patched.win
```

## Notes

- xdelta is exact when applied to the expected source file.
- xdelta does not provide resource-level merge information.
- For mergeable GameMaker mods, use `patch create` to produce `.g3mpatch`.
- Use `patch create --xdelta-fallback` only when a `.g3mpatch` should also carry an exact xdelta fallback.
