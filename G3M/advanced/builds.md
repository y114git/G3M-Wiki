# Building & Packaging

The current project metadata comes from `pyproject.toml`, `builds/G3MExecutable.spec`, `builds/G3MWindowsInstaller.iss`, and the GitHub workflows in `.github/workflows/`.

---

## Runtime Build Base

Current top-level build facts:

- Python requirement: `>=3.14.6`
- application version: `3.2.0`
- UI stack: `PyQt6==6.7.1`
- package entry point: `src/main.py`

The executable build is driven by `builds/G3MExecutable.spec`.

---

## Windows Installer

The installer is defined by `builds/G3MWindowsInstaller.iss`.

Current values:

| Property | Value |
| --- | --- |
| App name | `G3M` |
| App version | `3.2.0` |
| Executable name | `G3M.exe` |
| Default install dir | `{autopf}\G3M` |
| Minimum Windows build | `17763` |
| Installer languages | English, Spanish, Russian |
| Output file name | `G3M_setup_3.2.0` |

The installer also creates optional shortcuts and supports post-install launch.

---

## Build Assets

The `builds/` directory currently contains:

- `G3MExecutable.spec`
- `G3MWindowsInstaller.iss`
- installer bitmap assets

The project also bundles platform-specific helper binaries under `src/assets/bin/`, including G3MTool and xdelta assets used by launcher features.

---

## CI

The repository currently includes these workflows:

- `build-g3m.yml`
- `test-g3m.yml`
