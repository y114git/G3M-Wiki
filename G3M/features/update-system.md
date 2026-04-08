# Update System

G3M includes an automatic update checker that notifies you when a new version is available.

---

## How Update Checking Works

### Automatic Check

On every launch (after initialization), G3M fetches global settings from the G3M cloud backend, which includes update information. The check runs in the background and does not block the UI.

### Manual Check

You can manually trigger an update check from Settings → General → **Check for updates** button.

---

## Version Comparison

G3M compares version strings by splitting them into numeric components (e.g., "3.0.3" → [3, 0, 3]) and comparing from left to right. The current version is defined in `pyproject.toml` and compiled into the application.

---

## Beta Updates

If **Enable beta updates** is checked in Settings → General, G3M also considers pre-release versions (tagged as beta, alpha, rc, or similar) as valid updates. With this setting off, only stable releases trigger the update notification.

---

## Update Dialog

When an update is found, a dialog appears with:

- **Current version** — Your installed version (e.g., "3.0.3stable").
- **New version** — The available version.
- **Release notes** — The changelog/notes provided by the cloud settings payload.
- **Install** button — Downloads and installs the update.
- **Skip** button — Dismisses the dialog. The update is not installed but may be shown again on the next launch.

---

## Update Installation

### Windows

1. G3M downloads the update archive from the URL provided in the cloud settings.
2. Saves it to a temporary directory.
3. Extracts and launches the InnoSetup installer.
4. Requests the application to quit so the installer can proceed.
5. After updating, G3M restarts.

### macOS

1. G3M downloads the new `.dmg` or `.zip` release.
2. Extracts the new `G3M.app`.
3. On macOS, a Python symlink fix may be applied to ensure the app bundle is valid.
4. Replaces the current installation.
5. Restarts.

### Linux

1. G3M downloads the new release archive.
2. Extracts it alongside the current installation.
3. Restarts.

---

## Update Analytics

If analytics opt-in is enabled, the outcome of each update check is recorded:

- **up_to_date** — No update available.
- **update_available** — A newer version exists.
- **update_installed** — The user installed the update.
- **update_skipped** — The user dismissed the update.
- **check_failed** — The update check failed (network error, etc.).

---

## Network Requirements

Update checks require an internet connection and access to the G3M cloud backend. If the network is unavailable, the check silently fails and no notification is shown.

The request timeout is 5 seconds (`NETWORK_TIMEOUT_SHORT`). If the cloud server is slow to respond, the check may be skipped.

---

## Signals

The update system emits these events internally:

- **update_available** — New version found.
- **status_changed** — Progress messages during download.
- **progress_updated** — Download percentage.
- **update_finished** — Update process completed.
- **update_error** — An error occurred during the update.
- **quit_requested** — The application should quit for the updater to proceed.
