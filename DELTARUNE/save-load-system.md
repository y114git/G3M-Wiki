# Save and Load System

Each numbered payload owns `scr_saveprocess` and `scr_load`. The launcher reads
file presence and compact metadata, but it does not deserialize chapter state.
All five chapters route file operations through `ossafe_*` wrappers.

## Names and Slots

|     Suffix | Meaning                                            |
| ---------: | -------------------------------------------------- |
| `0` to `2` | Three player-visible slots                         |
| `3` to `5` | Completed copies corresponding to slots `0` to `2` |
|        `9` | Rolling temporary or recovery image                |

Chapters 1 through 4 use `filech<chapter>_<slot>`. Chapter 1 constructs its name
directly; later chapters use `global.chapter`. Chapter 5 normally uses the same
name, but `scr_saveprocess` appends `global.filechoice_route`.
`scr_complete_save_file_b()` temporarily sets that suffix to `_b`, producing a
route-specific completed file. The main Chapter 5 `scr_load` still opens the
unsuffixed name, so that save and load path are intentionally asymmetric.

`scr_save()` writes the selected slot and then slot `9`. `scr_tempsave()` and
`scr_tempload()` temporarily select slot `9`. A normal successful load refreshes
that recovery image. Slots `3` to `5` are written by completion helpers using
`filechoice + 3` in Chapters 3 through 5; earlier payloads already recognize the
same completion family.

## Serialization Families

Chapter 1 has the oldest and smallest layout. Chapters 2 through 4 share the
expanded family: five character records, equipment modifiers, spell loadouts,
larger inventory arrays, Light World state, flags, plot, room, and elapsed time.
The loader mirrors the writer in strict order.

Chapter 5 remains in that later family and adds serialized state. Its writer and
loader must be treated as a Chapter 5 pair rather than assumed byte-for-byte
compatible with Chapter 4. PC writes scalar values as text lines. Console
branches group the same logical arrays through `scr_ds_list_write` and
`scr_ds_list_read`, so physical representation differs even when field order is
conceptually equivalent.

## Cross-Chapter Transfer

Later payloads contain dedicated import functions rather than loading an older
file through the current chapter loader:

- Chapter 2 has `scr_load_chapter1`;
- Chapter 3 adds `scr_load_chapter2`;
- Chapter 4 adds `scr_load_chapter3`;
- Chapter 5 includes loaders for Chapters 1 through 4 and dispatches through
  `scr_load_prev_chapter_file`.

The device menu invokes the previous-chapter importer for the selected slot.
This is a conversion boundary: defaults and chapter-specific state are applied
by the receiving payload.

## Metadata and Configuration

| File                 | Purpose                                     |
| -------------------- | ------------------------------------------- |
| `filech*`            | Numbered payload's serialized game state    |
| `dr.ini`             | Launcher metadata and Chapter 5 video state |
| `true_config.ini`    | Language and display settings               |
| `options.ini`        | GameMaker runner configuration              |
| `parity_session.ini` | Present in Windows Chapters 1 through 4     |

Chapter 5 reads and writes `[video_ch5] watched` in `dr.ini` around its
localized intro-video sequence. The helpers are defined with the Chapter 5
completion and metadata functions, not the language/display configuration.

## Repair and Failure Handling

Loaders remap legacy room indices through room-ID helpers and apply
chapter-specific post-load corrections. Chapters 1, 2, and 4 bypass part of
normal room repair for slot `9`; Chapter 3 differs. Later loaders also normalize
some arrays, such as removing empty or sentinel item entries.

The examined GML checks existence before selection or transfer and relies on the
OS-safe layer for backend operations. No general checksum or transactional
rollback format is visible in the shipped chapter scripts. Therefore a
malformed, truncated file should not be described as automatically repaired;
established recovery is limited to the independently maintained slot `9` and the
explicit post-load fixups.

## Modding Contract

When adding persistent state, update the active chapter's defaults, writer,
loader, console list grouping, older-chapter importer if relevant, and any room
or inventory repair. Never insert a field on only one side of the ordered
format.
