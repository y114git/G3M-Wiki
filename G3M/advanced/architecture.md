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
| `mod_import_export_controller.py` | Import/export dialogs and operations. |
| `plugins_controller.py` | Plugins settings tab, filters, catalog. |
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

**Boundary rules:**
- Services must not import `app.window` or manipulate widgets directly.
- If a service needs UI feedback, it emits signals or returns structured results.

---

## src/adapters — External Tool Wrappers

| Adapter | Wraps |
| --- | --- |
| `g3mtool_adapter.py` | G3MTool CLI (patch create/apply, convert, diff, info, merge). |
| `deltamod_adapter.py` | DELTAMOD format conversion. |
| `theme_adapter.py` | Theme file import/export. |
| `mod_adapter.py` | Mod file processing and normalization. |

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

---

## src/utils — Pure Utilities

Stateless helper functions:

| File | Functions |
| --- | --- |
| `file_utils.py` | Safe file operations, directory creation, sanitization. |
| `path_utils.py` | Path resolution, resource path, profile roots. |
| `network_utils.py` | HTTP session creation, request helpers. |
| `mod_utils.py` | Mod ID extraction, name parsing. |
| `mod_config_parser.py` | `mod_config.json` reading/writing/normalization. |
| `mod_version_utils.py` | Version snapshot creation. |
| `time_utils.py` | UTC timestamps, formatting. |

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
| `APP_VERSION` | "3.0.3" | Current version string. |
| `PRIMARY_URL_SCHEME` | "g3m" | Primary protocol scheme. |
| `URL_PROTOCOL_PREFIXES` | ["g3m://", "deltahub://"] | Recognized protocol prefixes. |
| `MOD_CONFIG_FILENAME` | "mod_config.json" | Standard mod config file name. |
| `MOD_VERSIONS_DIR` | "mod_versions" | Mod version snapshots directory. |
| `PLUGIN_API_VERSION` | 1 | Current plugin API version. |
| `PLUGIN_HOOKS` | ["pre_launch", "post_launch", ...] | Recognized plugin hook names. |
