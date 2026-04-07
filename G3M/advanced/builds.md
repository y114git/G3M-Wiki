# Building & Packaging

This page describes how G3M is compiled and distributed.

---

## Build System

G3M is packaged as a single executable using **PyInstaller**. The build configuration is defined in `G3MExecutable.spec`.

### Build Dependencies

- Python 3.14+
- PyInstaller 6.19.0
- All runtime dependencies listed in `pyproject.toml`

### Build Command

The build is triggered by the GitHub Actions workflow `build-g3m.yml`. It runs on a Windows runner and produces a single `.exe` file.

---

## Windows Installer

The Windows installer is built with **Inno Setup** using the script `G3MWindowsInstaller.iss`.

### Installer Details

| Property | Value |
| --- | --- |
| App Name | G3M |
| App Version | 3.0.3stable |
| Executable Name | G3M.exe |
| Default Install Path | `{autopf}\G3M` (Program Files) |
| Compression | LZMA (solid) |
| Architecture | x64 only |
| Minimum Windows | 10.0.17763 (version 1809) |
| Installer Languages | English, Spanish, Russian |
| Output File | `G3M_setup_v3.0.3stable.exe` |

### Installer Features

- Modern wizard style with custom images (SmallIcon.bmp, WizardImage.bmp).
- Optional desktop shortcut creation.
- Start Menu entry.
- Post-install launch option.
- Windows version check — blocks installation on unsupported versions with a clear error message.

---

## Build Assets

The `builds/` folder contains:

| File / Folder | Description |
| --- | --- |
| `G3MExecutable.spec` | PyInstaller spec file for creating the executable. |
| `G3MWindowsInstaller.iss` | Inno Setup script for the Windows installer. |
| `assets/icons/icon.ico` | Application icon used in the installer and executable. |
| `assets/SmallIcon.bmp` | Small icon used in the installer wizard header. |
| `assets/WizardImage.bmp` | Large image displayed on the left side of the installer wizard. |
| `assets/bin/` | Bundled binary tools (G3MTool executables for each platform). |

---

## CI/CD

Two GitHub Actions workflows automate the build and test process:

| Workflow | File | Purpose |
| --- | --- | --- |
| Build | `build-g3m.yml` | Compiles the executable and creates the installer on push/release. |
| Test | `test-g3m.yml` | Runs the test suite (pytest) on every push and pull request. |

---

## Bundled Binaries

G3M bundles platform-specific G3MTool executables:

| Platform | Path |
| --- | --- |
| Windows | `assets/bin/g3mtool_windows/G3MTool.exe` |
| macOS | `assets/bin/g3mtool_macos/G3MTool` |
| Linux | `assets/bin/g3mtool_linux/G3MTool` |

On non-Windows platforms, G3M automatically sets the executable permission (chmod 700) on first use.
