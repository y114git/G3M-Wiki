# G3M Patch Format

`.g3mpatch` is G3MTool's patch format. It stores a manifest plus exported resource payloads and helper data needed for apply and merge workflows. Optional xdelta fallback data can also be embedded.

G3MTool is the reference implementation for this format.

## Manifest

The current manifest model includes these top-level fields:

| Field | Description |
| --- | --- |
| `createdAt` | Patch creation timestamp |
| `tool` | Tool name and version |
| `original` | Source data-file metadata |
| `modified` | Modified data-file metadata |
| `resources` | Changed, new, and deleted resources by type |
| `statistics` | Resource and file counts |
| `applyPlan` | Apply hints used by G3MTool |

The current example tool version in this repository is `1.2.0`.

## Data-file metadata

The `original` and `modified` entries can include:

- `filename`
- `size`
- `md5`
- `bytecodeVersion`
- `gmsVersion`
- `generalInfo`

`generalInfo` maps to the current `GeneralInfoData` model and may include fields such as:

- `displayName`
- `name`
- `fileName`
- `config`
- `gameID`
- `directPlayGuid`
- `major`
- `minor`
- `release`
- `build`
- `defaultWindowWidth`
- `defaultWindowHeight`
- `infoFlags`
- `licenseCRC32`
- `timestamp`
- `activeTargets`
- `functionClassifications`
- `steamAppID`
- `debuggerPort`
- `gms2FPS`
- `gms2AllowStatistics`
- `roomOrderCount`

## Resource changes

Each resource type can contain:

| Field | Description |
| --- | --- |
| `changed` | Resources present in both original and modified data with different content |
| `new` | Resources present only in the modified data |
| `deleted` | Resource names present only in the original data |

Each changed or new resource entry stores its resource name plus a `files` map of logical file names to paths inside the archive.

## Statistics

The current statistics model contains:

- `totalChanged`
- `totalNew`
- `totalDeleted`
- `totalChangedFiles`
- `totalNewFiles`

## Apply plan

The current apply-plan model contains:

- `mode`
- `requiresCodePipeline`
- `requiresTexturePipeline`
- `requiresAssetReorder`
- `requiresHeavyFinalize`
- `supportsDirectResourceApply`
- `simpleResourceTypes`
- `heavyResourceTypes`

These flags tell G3MTool which expensive import or finalize stages can be skipped safely.

## Xdelta fallback

`patch create --xdelta-fallback` stores an embedded xdelta fallback built from the original and modified data files.

`patch apply` behavior:

| Mode | Behavior |
| --- | --- |
| Default | Try normal `.g3mpatch` apply first, then try embedded xdelta if normal apply fails |
| `--xdelta-fallback` | Try embedded xdelta first, then continue with normal `.g3mpatch` apply if xdelta fails |

## `.g3mcache`

`.g3mcache` is not part of `.g3mpatch`. It is a separate reusable analysis cache used only when the caller passes `--cache <dir>`.

Batch commands add a second, temporary layer of caching for the current process. They hash the original and inputs before processing, deduplicate identical jobs, and copy the first output to later duplicate output names. This batch cache is not stored inside `.g3mpatch`.
