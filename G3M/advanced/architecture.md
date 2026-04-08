# Architecture

This page describes the internal architecture of G3M for contributors and plugin developers.

---

## Layer Overview

G3M is organized into distinct layers with strict boundaries:

```
┌─────────────────────────────────────┐
│  src/app          Entry Points      │
├─────────────────────────────────────┤
│  src/app_context   Composition Root │
├─────────────────────────────────────┤
│  src/bootstrap     Startup Logic    │
├─────────────────────────────────────┤
│  src/session       Runtime State    │
├─────────────────────────────────────┤
│  src/presentation  UI Orchestration │
├─────────────────────────────────────┤
│  src/controllers   UI Controllers   │
├─────────────────────────────────────┤
│  src/ui            Widgets & Views  │
├─────────────────────────────────────┤
│  src/services      App Services     │
├─────────────────────────────────────┤
│  src/adapters      External Tools   │
├─────────────────────────────────────┤
│  src/workers       Background Tasks │
├─────────────────────────────────────┤
│  src/models        Data Models      │
├─────────────────────────────────────┤
│  src/config        Configuration    │
├─────────────────────────────────────┤
│  src/utils         Pure Utilities   │
└─────────────────────────────────────┘
```

---

## src/app — Entry Points

Contains the application's entry points and thin UI composition roots.

| File | Purpose |
| --- | --- |
| `startup.py` | Process startup, splash screen, single-instance enforcement, logging configuration, command-line argument handling, and top-level crash handling. |
| `window.py` | The main `AppWindow` class — the Qt composition root for the UI. Binds the application context, initializes runtime state, creates presentation controllers, and wires signals. Does **not** create core services directly. |
| `cleanup.py` | Application cleanup tasks on exit (stopping threads, saving state). |
| `dialogs.py` | Top-level dialog factories (file pickers, confirmation dialogs). |
| `game_ui.py` | Game-specific UI helpers (chapter tab styling, Steam launch checkbox state). |
| `protocol_handler.py` | One-click install URL parsing and dispatch. |
| `localization_utils.py` | Localization helpers used within the app layer. |
| `settings_setup.py` | Settings initialization and post-load wiring. |
| `tab_handler.py` | Runtime tab-switching logic. |
| `tab_setup.py` | Tab widget construction and initial setup. |

**Boundary rules:**
- `window.py` must not create core services directly — they come from `app_context`.
- `window.py` must not own startup orchestration, network bootstrap, or presence lifecycle.

---

## src/app_context — Composition Layer

| File | Purpose |
| --- | --- |
| `application_context.py` | Builds shared state (`AppState`) and shared services. The root dependency container. |
| `service_container.py` | Owns service instances and dependency wiring. Session, localization bootstrap, config wiring, and future auth/subscription dependencies enter through this layer. |

All services are created here and injected into controllers and the window. No service creates itself.

---

## src/bootstrap — Startup Orchestration

Owns the startup flow:

- Splash screen management.
- Post-show initialization (loading settings, scanning mods, checking network).
- Network/bootstrap orchestration.
- Startup fallback flow (if initialization fails).

This logic must not be in `AppWindow`.

---

## src/session — Runtime Session State

Owns runtime session state that is not tied to the UI:

- Online presence.
- Future: auth session, account identity, entitlement/subscription cache.

No UI widget code belongs here.

---

## src/presentation — UI Orchestration

Helpers that support the presentation layer:

- Controller composition.
- Window runtime state.
- Drag-and-drop handling.
- Qt-specific wiring.

May depend on Qt and application services. Must not become a second domain layer.

---

## src/controllers — UI Controllers

Each controller owns a specific feature area of the UI:

| Controller | Responsibility |
| --- | --- |
| `game_launch_controller.py` | Game launch button state, launch operations. |
| `library_display_controller.py` | Library tab rendering and display updates. |
| `mod_import_export_controller.py` | Import/export dialogs and operations. |
| `mod_operations_controller.py` | Mod-level operations (delete, enable, etc.). |
| `plugins_controller.py` | Plugins settings tab, filters, catalog. |
| `refresh_controller.py` | Coordinating refresh of mod/game/catalog data. |
| `search_display_controller.py` | Mods browser search results display. |
| `settings_controller.py` | Settings tab interaction and persistence. |
| `shortcut_controller.py` | Shortcut creation logic. |
| `theme_controller.py` | Theme application and debounced updates. |

Controllers depend on services (via dependency injection) and emit signals that the window connects to UI updates.

---

## src/services — Application Services

The largest layer. Each service owns a distinct domain:

| Service | Domain |
| --- | --- |
| `settings_service.py` | Settings read/write, color keys, file extensions. |
| `profile_service.py` | Profile CRUD, switching, migration. |
| `mod_service.py` | Mod scanning, loading, metadata management. |
| `mod_filter_service.py` | Filtering and sorting mod lists. |
| `used_mods_service.py` | Tracking which mods are "used" per chapter. |
| `launch_service.py` | Game launching, patching, monitoring. |
| `backup_service.py` | File backup and restoration. |
| `downloads_manager.py` | Download queue and history. |
| `game_versions_manager.py` | Game version snapshots. |
| `updatecheck_service.py` | Auto-update checking and installation. |
| `chat_service.py` | Chat messaging. |
| `announce_service.py` | Announcements and polls. |
| `analytics_service.py` | Anonymous analytics collection. |
| `customization_service.py` | Theme, audio, logo, font management. |
| `blocklist_service.py` | Mod blocklist rules. |
| `game_registry_service.py` | Runtime game registry (built-in + custom). |
| `game_detection_service.py` | Game process detection and path resolution. |
| `localization_service.py` | Translation loading and the `tr()` function. |
| `migration_service.py` | Legacy data migrations. |
| `plugin_runtime_service.py` | Plugin scanning, loading, hook execution. |
| `pizza_oven_conversion_service.py` | PizzaOven mod format conversion. |
| `g3mtool_patching_service.py` | G3MTool-based patching orchestration. |
| `base_json_store.py` | Base class for JSON-backed persistent stores. |
| `downloads_store.py` | Persistent download record storage. |
| `game_versions_store.py` | Persistent game version record storage. |
| `pizza_tower_afom_service.py` | Pizza Tower AFOM/CYOP mod support. |
| `plugin_catalog_service.py` | Plugin catalog fetching and caching. |
| `plugin_install_service.py` | Plugin installation from archive. |
| `plugin_state_service.py` | Plugin enabled/disabled state management. |
| `plugin_support.py` | Plugin support utilities. |

**Boundary rules:**
- Services must not import `app.window` or manipulate widgets directly.
- If a service needs UI feedback, it emits signals or returns structured results.

---

## src/adapters — External Tool Wrappers

| Adapter | Wraps |
| --- | --- |
| `g3mtool_adapter.py` | G3MTool CLI (patch create/apply, convert, diff, info, merge). |
| `deltamod_adapter.py` | DELTAMOD format conversion. |
| `gamebanana_adapter.py` | GameBanana API HTTP requests and response parsing. |
| `gamebanana_converter.py` | GameBanana API response → internal mod model conversion. |

Adapters translate between G3M's internal model and external tools/formats.

---

## src/workers — Background Tasks

Workers run IO and long-running tasks in background threads:

| Worker | Task |
| --- | --- |
| `background_loader_worker.py` | Generic background file loading. |
| `game_monitor_worker.py` | Monitors game process until exit. |
| `plugin_hook_worker.py` | Executes plugin hooks in background thread. |
| Various download workers | Handle file download with progress. |
| Various catalog workers | Fetch mod/plugin catalogs from remote. |

**Boundary rules:**
- Workers are execution units, not business-rule owners.
- Workers must not decide product rules or UI flow.

---

## src/models — Data Models

Pure data classes and enums:

| Model | Contains |
| --- | --- |
| `app_state.py` | `AppState` — Central reactive state with signals. |
| `game_modes.py` | `GameDefinition`, `GameEntry`, `GameTab`, built-in game registry. |
| `game_version_models.py` | Game version record data classes. |
| `mod_models.py` | `LocalModInfo`, `BrowserModInfo`, `ModFileData`. |
| `plugin_models.py` | `PluginManifest`, `InstalledPluginRecord`, `PluginContext`. |
| `download_models.py` | `DownloadRecord`, `DownloadStatus`, `UseStatus`. |
| `exceptions.py` | Custom exception classes. |

Models have no dependencies on Qt widgets or services.

---

## src/config — Configuration

| File | Contains |
| --- | --- |
| `config.py` | Constants: version, URLs, file extensions, colors, API endpoints. |
| `settings_schema.py` | Default settings values, theme color key helpers. |
| `style_loader.py` | QSS stylesheet generation and caching. |
| `styles.py` | QSS string constants and style templates. |

---

## src/utils — Pure Utilities

Stateless helper functions:

| File | Functions |
| --- | --- |
| `archive_utils.py` | Archive extraction (zip, 7z, rar, tar). |
| `cache_utils.py` | Caching helpers. |
| `file_utils.py` | Safe file operations, directory creation, sanitization. |
| `game_version_utils.py` | Game version archive helpers. |
| `mod_config_parser.py` | `mod_config.json` reading/writing/normalization. |
| `mod_readme_utils.py` | Mod readme file detection and reading. |
| `mod_scan_utils.py` | Scanning directories for installed mods. |
| `mod_utils.py` | Mod ID extraction, name parsing. |
| `mod_version_utils.py` | Version snapshot creation. |
| `network_utils.py` | HTTP session creation, request helpers. |
| `path_utils.py` | Path resolution, resource path, profile roots. |
| `pizzatower_afom_utils.py` | Pizza Tower AFOM/CYOP path utilities. |
| `time_utils.py` | UTC timestamps, formatting. |
| `patching/` | Subdirectory: patch file resolution, verification, file-override and mod-content utilities. |

---

## Dependency Direction

Dependencies flow downward:

```
app → app_context → services → models
app → controllers → services → models
app → ui → models
controllers → services → models
services → adapters → (external tools)
services → workers
services → utils
```

**Forbidden directions:**
- `services` → `app.window`
- `workers` → `controllers`
- `models` → `services`
- `adapters` → `ui`

---

## Signal-Based Communication

G3M uses PyQt6 signals extensively for decoupled communication:

- `AppState` emits signals when reactive properties change (e.g., `game_mode_changed`, `is_installing_changed`).
- Services emit signals for completed operations (e.g., `update_available`, `game_launch_finished`).
- Controllers connect service signals to UI update methods.
- The window connects signals between controllers and widgets.

This pattern ensures that services never need to know about specific UI widgets.

---

## Testing Architecture

Tests are organized into three categories:

| Folder | Purpose |
| --- | --- |
| `tests/unit/` | Unit tests for individual services, models, and utilities. |
| `tests/integration/` | Integration tests that verify multi-component interactions. |
| `tests/ui/` | UI tests that require a QApplication instance. |

The test suite uses pytest with pytest-qt for Qt-related tests and pytest-mock for mocking dependencies. Tests can be run without constructing `AppWindow` — services and models are testable in isolation.

---

## Configuration Constants

Key constants defined in `src/config/config.py`:

| Constant | Value | Description |
| --- | --- | --- |
| `APP_DISPLAY_NAME` | "G3M" | Application display name. |
| `APP_VERSION` | "3.0.3stable" | Current version string. |
| `PRIMARY_URL_SCHEME` | "g3m" | Primary protocol scheme. |
| `URL_PROTOCOL_PREFIXES` | `("g3m://", "deltahub://")` | Recognized protocol prefixes. |
| `MOD_CONFIG_FILENAME` | "mod_config.json" | Standard mod config file name. |
| `MOD_VERSIONS_DIR` | "mod_versions" | Mod version snapshots directory. |
| `PLUGIN_API_VERSION` | "1.0.0" | Current plugin API version. |
| `PLUGIN_HOOKS` | see below | Recognized plugin hook names. |

Plugin hooks (from `config.py`): `app_ready`, `app_shutdown`, `before_mod_apply`, `after_mod_apply_before_launch`, `mod_apply_cancelled`, `after_game_started`, `before_restore_after_exit`, `after_restore_after_exit`, `language_changed`, `theme_changed`, `profile_changed`, `settings_view`, `main_view`, `navigation_actions`, `game_registry`, `background_task`.
