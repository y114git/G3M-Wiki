# Full Install

Full Install is the launcher flow that downloads a clean game package into a
folder you choose and then sets that folder as the active game path.

---

## Supported Games

Games with `supports_full_install = True` are:

- `deltarunedemo`
- `undertaleyellow`
- `sugaryspire`
- `frickbears3`

Built-in games without that flag and all custom games do not expose the feature.

---

## UI Behavior

When the selected game supports Full Install, G3M shows the `Full Install`
checkbox in the main window. If the checkbox is enabled, the primary action
becomes install instead of launch.

The setting is stored in profile state as `full_install_enabled`.

---

## Install Flow

The current flow is:

1. choose a parent folder
2. let G3M create or reuse the target game folder inside it
3. resolve the game-specific download URL from global settings
4. download the archive
5. extract the files
6. set the installed folder as the active path for that game
7. clear the Full Install checkbox

The worker uses different global setting keys depending on the selected game:

- `demo_full_install_url`
- `undertaleyellow_full_install_url`
- `sugaryspire_full_install_url`
- `full_install_url` for `frickbears3`

---

## Platform Notes

On macOS, turning the checkbox on is rejected immediately and the UI turns it
back off. The code path does not allow Full Install to proceed there.

On other platforms, behavior depends on whether the configured download URL is
available and whether the downloaded package matches the current platform's
launch requirements.
