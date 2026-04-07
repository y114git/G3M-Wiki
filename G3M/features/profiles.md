# Profiles

Profiles let you maintain completely separate mod collections, mod selections, and game path overrides. Each profile has its own mods folder and its own set of "used mods" per game and chapter.

---

## Default Profile

G3M always has a profile named **Default**. It cannot be deleted or renamed. When you first launch G3M, all your mods and settings are stored under the Default profile.

---

## Creating a Profile

1. Open the Profile selector (visible in the Library tab or Settings).
2. Click **New Profile** (or the "+" button).
3. Enter a name. The name is sanitized: special characters are replaced with underscores, and the name is truncated to 80 characters.
4. Click **Create**.

A new profile folder is created in the `profiles/` directory of your user data folder. It starts empty — no mods are installed, and no mods are selected.

---

## Switching Profiles

Select a different profile from the dropdown. When you switch:

1. The current profile's used-mods state is saved.
2. The new profile's settings and mods are loaded.
3. The Library refreshes to show only the mods belonging to the new profile.
4. All mod selections (used mods) switch to the new profile's selections.

Switching profiles does **not** change global settings (language, colors, game paths, etc.). Only profile-specific data changes:

- Which mods are installed (each profile has its own `mods/` subfolder).
- Which mods are selected for each chapter.
- The active game and chapter state.

---

## Profile Data Storage

Each profile is stored as a folder under `{user_data_root}/profiles/<profile_name>/`:

| Path | Content |
| --- | --- |
| `profile.json` | Used mods state and profile-specific settings. |
| `mods/` | All installed mod folders for this profile. |

---

## Importing / Exporting Profiles

### Export

Profiles can be exported as `.zip` archives. The export includes the `profile.json` and the entire `mods/` folder.

### Import

You can import a profile by selecting a `.zip` archive. G3M extracts it into the `profiles/` directory, creating a new profile with the imported data.

If an imported profile has the same name as an existing profile, G3M prompts you to rename or overwrite.

---

## Deleting a Profile

Select a profile and click **Delete**. A confirmation dialog appears. Deleting a profile:

- Removes the entire profile folder from disk (including all mods in that profile's `mods/` subfolder).
- Switches to the Default profile.

The Default profile cannot be deleted.

---

## Renaming a Profile

Profiles can be renamed. The folder on disk is renamed accordingly. The same name sanitization rules apply.

If the profile named **Unnamed** is created (via an empty name input), it gets the internal name "Unnamed".

---

## Migration from Legacy Settings

If you upgrade from an older version of G3M (or DELTAHUB) that stored mod selections directly in the main settings file instead of profiles, G3M automatically migrates that data into the Default profile on first launch. The old keys are removed from the main settings.
