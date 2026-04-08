# Contributing

This page describes how to contribute to G3M development.

---

## Repository Structure

```
G3M/
├── src/                    # Application source code
│   ├── app/                # Entry points and composition roots
│   ├── app_context/        # Dependency injection and service wiring
│   ├── bootstrap/          # Startup orchestration
│   ├── session/            # Runtime session state
│   ├── presentation/       # UI orchestration helpers
│   ├── controllers/        # UI controllers
│   ├── ui/                 # Widgets, dialogs, and views
│   ├── services/           # Application services
│   ├── adapters/           # External tool wrappers
│   ├── workers/            # Background task runners
│   ├── models/             # Data models and enums
│   ├── config/             # Configuration and constants
│   ├── utils/              # Pure utility functions
│   ├── assets/             # Bundled assets (icons, audio, fonts, binaries)
│   └── main.py             # Python entry point
├── tests/                  # Test suite
│   ├── unit/               # Unit tests
│   ├── integration/        # Integration tests
│   ├── ui/                 # UI tests (require QApplication)
│   ├── fixtures/           # Test data and fixtures
│   └── conftest.py         # Shared pytest fixtures
├── builds/                 # Build scripts and assets
│   ├── G3MExecutable.spec  # PyInstaller spec
│   ├── G3MWindowsInstaller.iss # Inno Setup script
│   └── assets/             # Installer icons and images
├── catalog/                # Plugin catalog data
├── .github/                # GitHub Actions workflows
├── pyproject.toml          # Project metadata and dependencies
├── CHANGELOG.md            # Version history
├── LICENSE                 # GPL-3.0 license
├── README.md               # Project readme
├── SECURITY.md             # Security policy
└── THIRD_PARTY_NOTICES.md  # Third-party license notices
```

---

## Development Setup

### Prerequisites

- Python 3.14+
- Git

### Steps

1. Clone the repository:
   ```
   git clone https://github.com/y114git/G3M.git
   cd G3M
   ```

2. Create a virtual environment:
   ```
   python -m venv .venv
   ```

3. Activate the virtual environment:
   - Windows: `.venv\Scripts\activate`
   - macOS/Linux: `source .venv/bin/activate`

4. Install dependencies:
   ```
   pip install -e ".[dev]"
   ```

5. Run the application:
   ```
   python src/main.py
   ```

---

## Running Tests

```
pytest tests/
```

### Specific test categories

```
pytest tests/unit/          # Unit tests only
pytest tests/integration/   # Integration tests only
pytest tests/ui/            # UI tests only (require display)
```

### Test coverage

```
pytest --cov=src tests/
```

---

## Code Style

G3M uses:

- **ruff** for linting and formatting.
- **Type hints** throughout the codebase.
- **Docstrings** for public functions and classes (single-line where possible).

### Running the Linter

```
ruff check src/
ruff format src/
```

---

## Architecture Rules

See [Architecture](architecture.md) for the full architecture constitution. Key rules for contributors:

### Layer Boundaries

- `app/window.py` must not create services directly — use `app_context`.
- Services must not import `app.window` or manipulate widgets.
- Workers must not decide business rules or UI flow.
- Models must not depend on services or Qt widgets.

### Dependency Direction

```
app → app_context → services → models
app → controllers → services → models
services → adapters → (external tools)
services → workers
```

Never add imports in the opposite direction.

### Forbidden Patterns

- Reintroducing service construction inside `AppWindow`.
- Import-only wrapper functions that just forward to another function.
- "Temporary", "legacy", or dead compatibility code left after refactors.
- Service code that imports `app.window`.
- Worker code that decides product rules.

### Clean Code Rules

- Remove unused imports, functions, variables, language keys, and config entries immediately.
- Don't leave `# TODO remove later`, `# deprecated`, or `# legacy` comments — if it's unused, delete it.
- Before adding a new function, check if a similar one already exists.
- Prefer modifying existing code over adding new abstractions.
- Leave the code cleaner than you found it (Boy Scout Rule).

---

## Making Changes

### Workflow

1. Create a feature branch from `main`.
2. Make your changes.
3. Write or update tests.
4. Run `ruff check` and `ruff format`.
5. Run `pytest tests/`.
6. Commit with clear, descriptive commit messages.
7. Open a Pull Request.

### Pull Request Requirements

- All tests must pass.
- No ruff errors.
- New features must include tests.
- Existing tests must not be weakened without explanation.
- Update relevant documentation (language files, docstrings, wiki) if behavior changes.
- Remove any unused code, imports, or language keys your change makes obsolete.

---

## Localization Contributions

To contribute a new language translation:

1. Copy `src/assets/lang/lang_en.json` to `lang_<code>.json` (e.g., `lang_fr.json` for French).
2. Translate all JSON values (keep the JSON keys unchanged).
3. Register the new language in the localization service's language list.
4. Test the translation in-app.
5. Submit a Pull Request.

### Updating Existing Translations

If you find missing or incorrect translations:

1. Edit the appropriate `lang_<code>.json` file.
2. Ensure the key structure matches `lang_en.json` (don't add or remove keys).
3. Submit a Pull Request with the changes.

---

## Plugin Contributions

To contribute a plugin to the official catalog:

1. Develop the plugin following the [Plugin Development Guide](../features/plugins-development.md).
2. Test it thoroughly.
3. Package it as a `.zip` archive.
4. Contact the G3M developer with:
   - The plugin package.
   - A description of what it does.
   - Source code (preferably a GitHub repository).

The catalog is curated — plugins are reviewed before being listed.

---

## Reporting Issues

### Bug Reports

Open a GitHub Issue with:

1. **G3M version** (e.g., "3.0.3stable").
2. **Operating system** (e.g., "Windows 11 23H2").
3. **Steps to reproduce** — Clear, numbered steps.
4. **Expected behavior** vs **Actual behavior**.
5. **Log file** — Attach `g3m.log` from the `logs/` directory.
6. **Screenshots** (if applicable).

### Feature Requests

Open a GitHub Issue with the "feature request" label. Describe:

1. What you want to accomplish.
2. Why the current functionality doesn't meet the need.
3. How you envision the feature working.

---

## Community

- **Discord**: [discord.gg/2MFdvFfD9a](https://discord.gg/2MFdvFfD9a) — General discussion, support, mod sharing.
- **Telegram**: [t.me/y_maintg](https://t.me/y_maintg) — Updates and announcements.
- **GitHub**: [github.com/y114git/G3M](https://github.com/y114git/G3M) — Source code, issues, pull requests.

---

## License

G3M is licensed under the **GNU General Public License v3.0** (GPL-3.0). By contributing code, you agree that your contributions will be licensed under the same terms.

Third-party dependencies and their licenses are listed in `THIRD_PARTY_NOTICES.md`.
