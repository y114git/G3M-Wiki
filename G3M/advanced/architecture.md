# Architecture

G3M is a PyQt6 desktop application organized around injected services, Qt
controllers, background workers, and a runtime app state model.

---

## Main Layers

The current source tree is centered around these directories:

- `src/app` for startup, top-level window wiring, tab setup, protocol handling,
  and shutdown
- `src/app_context` for dependency construction
- `src/bootstrap` for startup orchestration
- `src/controllers` for UI-facing feature controllers
- `src/ui` for widgets, builders, and dialogs
- `src/services` for most application logic
- `src/adapters` for external tool and API bridges
- `src/workers` for threaded background jobs
- `src/models` for typed runtime data
- `src/config` for constants and settings defaults
- `src/utils` for filesystem, archive, patching, and other helpers

---

## Core Runtime Pieces

Important current components are:

- `AppState` in `models/app_state.py`
- `ProfileService` for profile switching and migration
- `GameRegistryService` for built-in and custom game entries
- `ModService` and related patching services for mod scan and apply flows
- `ModDiagnosticsService` for read-only preflight analysis of selected mods
- `SettingsService` for settings persistence
- `PluginRuntimeService` for plugin loading and hook execution
- `DiscordRichPresenceService` for Discord activity publishing
- `Frickbears3AddonsService` for strict FRICKBEARS3 addon conversion
- `UpdateCheckService`, `AnalyticsService`, `AnnounceService`, and the
  presence/session workers for network-backed features

---

## Configuration Constants

Current key values from `src/config/config.py`:

| Constant              | Value             |
| --------------------- | ----------------- |
| `APP_DISPLAY_NAME`    | `G3M`             |
| `APP_VERSION`         | `3.2.0`           |
| `PRIMARY_URL_SCHEME`  | `g3m`             |
| `LEGACY_URL_SCHEME`   | `deltahub`        |
| `PLUGIN_API_VERSION`  | `1.1.0`           |
| `DEFAULT_PROFILE`     | `Default`         |
| `MOD_CONFIG_FILENAME` | `mod_config.json` |
| `MOD_VERSIONS_DIR`    | `mod_versions`    |

Current plugin hooks are:

- `app_ready`
- `app_shutdown`
- `before_mod_apply`
- `after_mod_apply_before_launch`
- `mod_apply_cancelled`
- `after_game_started`
- `before_restore_after_exit`
- `after_restore_after_exit`
- `shortcut_dialog`
- `before_mod_apply_shortcut`
- `after_mod_apply_before_launch_shortcut`
- `before_restore_after_exit_shortcut`
- `after_restore_after_exit_shortcut`
- `language_changed`
- `theme_changed`
- `profile_changed`
- `settings_view`
- `main_view`
- `navigation_actions`
- `game_registry`
- `background_task`

---

## Testing Layout

The repository currently contains:

- `tests/unit`
- `tests/integration`
- `tests/ui`

This matches the service-heavy architecture: most logic is outside widgets and
can be exercised without booting the full application window.
