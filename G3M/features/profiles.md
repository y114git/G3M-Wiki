# Profiles

Profiles are separate library states. Use them when you want different installed
mod sets, different selected mods, or separate setups for testing and normal
play.

On Windows, profiles are stored under:

`%LOCALAPPDATA%\G3M\profiles\`

On Linux the same folder is `~/.local/share/G3M/profiles/`. On macOS it is
`~/Library/Application Support/G3M/profiles/`.

Each profile has its own mod folders, its own `mods_data.json`, and its own
profile JSON with launch and selection state.

---

## Where to find it

1. Open G3M.
2. Use the profile selector in the main window to switch profiles quickly.
3. Open **Profile Manager** from the profile controls when you need create,
   duplicate, rename, delete, import, export, or reorder actions.

Changing the active profile refreshes the Library. It does not delete mods from
other profiles.

---

## What Is Profile-Specific

G3M stores these values inside the active profile instead of the shared settings
file:

- selected game
- chapter mode state
- full install toggle state
- direct launch chapter
- used-mod selections per game

Installed mods are also profile-local because G3M switches `app_state.mods_dir`
to the active profile folder.

---

## Storage Layout

Each profile uses this layout:

- **Path:** `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\`
  - **Purpose:** Root folder for the profile's installed mods and metadata

- **Path:** `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\<ProfileName>.json`
  - **Purpose:** Profile settings and per-game selection data

- **Path:** `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\mods_data.json`
  - **Purpose:** Library metadata such as timestamps and playtime

- **Path:** `%LOCALAPPDATA%\G3M\profiles\<ProfileName>\<mod id>\...`
  - **Purpose:** Installed mod folders

The active profile name is also written to:

`%LOCALAPPDATA%\G3M\settings\settings.json`

inside the `active_profile` setting.

---

## Default Profile

G3M always keeps a `Default` profile. It is created automatically if missing and
becomes the fallback when the saved active profile no longer exists.

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

Deleting a profile removes its folder from `%LOCALAPPDATA%\G3M\profiles\` on
Windows. If the deleted profile was active, G3M switches back to `Default`.

---

## Common actions

### Create a clean testing profile

1. Open **Profile Manager**.
2. Click **Create**.
3. Name it something like `Testing`.
4. Switch to it from the profile selector.
5. Install or import mods while that profile is active.

Those mods go into `%LOCALAPPDATA%\G3M\profiles\Testing\`, not into the
`Default` profile.

### Duplicate a working setup

1. Open **Profile Manager**.
2. Select the profile you want to copy.
3. Click **Duplicate**.
4. Give the copy a clear name.

This is useful before trying a large modpack because the copy keeps the same
installed mods and profile state.

### Export or import a profile

Export creates a `.zip` copy of the selected profile. Import reads a profile
`.zip` and adds it back as a profile folder.

Export/import affects profile data and installed mods inside that profile. It
does not export the full G3M settings folder, plugins, logs, or saved Game
Versions.

---

## Migration

On startup, G3M migrates legacy profile keys from the shared settings file into
`Default` and also migrates legacy mods from the old shared `mods/` directory
into the default profile folder.
