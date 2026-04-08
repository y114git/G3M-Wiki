# xpatch

Create or apply binary xdelta3 patches. xdelta is a generic binary diff format — it stores the byte-level difference between two files and requires the original file to reconstruct the modified one. The xdelta binary is bundled inside G3MTool; no separate installation is needed.

---

## Subcommands

### xpatch create

Compute the xdelta diff between `original` and `modified` and write the patch to `output`.

```
G3MTool xpatch create <original> <modified> [output]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Path to the original (unmodified) file |
| `modified` | Yes | Path to the modified file |
| `output` | No | Output `.xdelta` path. Default: `<modified_name>.xdelta` next to executable |

**Example:**

```bash
G3MTool xpatch create data.win data_modded.win my_mod.xdelta
```

---

### xpatch apply

Apply an xdelta patch to `original` and write the result to `output`.

```
G3MTool xpatch apply <original> <patch> [output]
```

| Argument | Required | Description |
| --- | --- | --- |
| `original` | Yes | Path to the original (unmodified) file |
| `patch` | Yes | Path to the `.xdelta` patch file |
| `output` | No | Output file path. Default: `<original_name>_patched.<ext>` next to executable |

**Example:**

```bash
G3MTool xpatch apply data.win my_mod.xdelta patched.win
```

---

## Notes

- xdelta patches are binary and non-mergeable: if two xdelta patches modify different regions of the same file, they cannot be combined. Use [`patch create`](patch.md) to produce merge-friendly `.g3mpatch` files instead.
- xdelta patches are tied to a specific version of the original file. Applying a patch to a different version of `data.win` will produce corrupt output.
- `.g3mpatch` files embed an xdelta fallback automatically — you rarely need to create standalone xdelta patches unless distributing to non-G3M users.
- The bundled xdelta binary is platform-specific (`win`, `linux`, `osx`) and extracted from the embedded resources at runtime.
