# xpatch

Create or apply xdelta patches. xdelta stores byte-level differences and expects
the matching original file when applying.

G3MTool bundles xdelta for supported platforms, and xpatch also honors the
global `--xdelta-path <path>` override.

## xpatch create

```bash
G3MTool xpatch create <original> <modified> [output] [--xdelta-path <path>]
```

- **Argument:** `original`
  - **Required:** Yes
  - **Description:** Source file

- **Argument:** `modified`
  - **Required:** Yes
  - **Description:** Modified file

- **Argument:** `output`
  - **Required:** No
  - **Description:** Output `.xdelta`. Default: `<modified_name>.xdelta` next to
    the executable

## xpatch apply

```bash
G3MTool xpatch apply <original> <patch> [output] [--xdelta-path <path>]
```

- **Argument:** `original`
  - **Required:** Yes
  - **Description:** Source file expected by the xdelta patch

- **Argument:** `patch`
  - **Required:** Yes
  - **Description:** `.xdelta` file

- **Argument:** `output`
  - **Required:** No
  - **Description:** Output file. Default: `<original_name>_patched.<ext>` next
    to the executable

## Notes

- xdelta is exact only when applied to the expected source file.
- xdelta does not carry resource-level metadata for merge-aware workflows.
- Use `patch create` when you need inspectable or mergeable `.g3mpatch` output.
