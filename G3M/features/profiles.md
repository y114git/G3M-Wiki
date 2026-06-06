# Profiles

Profiles are separate library states stored under `{user_data_root}/profiles/`. Each profile has its own mod folder, its own `mods_data.json`, and its own profile JSON with launch and selection state.

---

## What Is Profile-Specific

G3M stores these values inside the active profile instead of the shared settings file:

- selected game
- chapter mode state
- full install toggle state
- direct launch chapter
- used-mod selections per game

Installed mods are also profile-local because G3M switches `app_state.mods_dir` to the active profile folder.

---

## Storage Layout

Each profile uses this layout:

| Path | Purpose |
| --- | --- |
| `profiles/<ProfileName>/` | Root folder for the profile's installed mods and metadata |
| `profiles/<ProfileName>/<ProfileName>.json` | Profile settings and per-game selection data |
| `profiles/<ProfileName>/mods_data.json` | Library metadata such as timestamps and playtime |
| `profiles/<ProfileName>/<mod id>/...` | Installed mod folders |

The active profile name is also written to the shared settings as `active_profile`.

---

## Default Profile

G3M always keeps a `Default` profile. It is created automatically if missing and becomes the fallback when the saved active profile no longer exists.

---

## Name Rules

Profile names are sanitized before being used on disk:

- unsupported characters are replaced with `_`
- names are trimmed
- names are limited to 80 characters
- reserved Windows device names are adjusted
- an empty result falls back to `Default`

---

## Operations

The profile manager can:

- create profiles
- duplicate profiles
- rename profiles
- delete non-default profiles
- reorder profiles
- export profiles to `.zip`
- import profiles from `.zip`

Deleting a profile removes its folder from `profiles/`. If the deleted profile was active, G3M switches back to `Default`.

---

## Migration

On startup, G3M migrates legacy profile keys from the shared settings file into `Default` and also migrates legacy mods from the old shared `mods/` directory into the default profile folder.
