# About & Changelog

G3M includes an About dialog and a Changelog dialog accessible from Settings → General.

---

## About Dialog

Clicking the **About** button (or clicking the logo in the title bar) opens the About dialog.

### Content

The About dialog shows:

- **App logo** — The G3M icon (or custom logo if set).
- **App name** — "G3M".
- **Version** — The current version string (e.g., "3.0.3stable").
- **Author** — "Y114".
- **Description** — "GameMaker Mod Manager" (or the localized equivalent).
- **Links** — Clickable buttons for:
  - **Discord** — Opens the Discord invite link in your browser.
  - **Telegram** — Opens the Telegram group link.
  - **GitHub** — Opens the GitHub repository.
  - **GameBanana** — Opens the G3M GameBanana page (if applicable).
- **Changelog** button — Opens the Changelog dialog.
- **License** — "GPL-3.0".
- **Copyright** — Copyright notice.

### Third-Party Notices

The About dialog may reference third-party libraries and their licenses. A full list of dependencies is in `THIRD_PARTY_NOTICES.md` in the repository root.

---

## Changelog Dialog

The Changelog dialog shows a scrollable list of version entries, each with:

- **Version number** — e.g., "3.0.3stable".
- **Release date** — When this version was released.
- **Changes** — A bullet-point list of additions, fixes, and improvements.

The changelog is loaded from the `CHANGELOG.md` file bundled with the application. It is rendered as rich text.

### Accessing the Changelog

- From the About dialog → **Changelog** button.
- From Settings → General → **Changelog** button.
- The changelog may also appear automatically after an update, showing what changed in the new version.

---

## Version Numbering

G3M uses a version format: `<major>.<minor>.<patch><suffix>`

- **Major** — Incremented for significant architectural changes or breaking updates.
- **Minor** — Incremented for new features.
- **Patch** — Incremented for bug fixes and small improvements.
- **Suffix** — `stable` for stable releases, `beta` or `alpha` for pre-release versions.

Examples: `3.0.3stable`, `3.1.0beta`, `2.5.1stable`.

---

## Community Links

| Platform | URL |
| --- | --- |
| Discord | [discord.gg/2MFdvFfD9a](https://discord.gg/2MFdvFfD9a) |
| Telegram | [t.me/y_maintg](https://t.me/y_maintg) |
| GitHub | [github.com/y114git/G3M](https://github.com/y114git/G3M) |

These links are also shown in the title bar as small icon buttons (Telegram and Discord).
