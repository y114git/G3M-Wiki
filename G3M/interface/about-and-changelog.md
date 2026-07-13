# About & Changelog

G3M exposes both dialogs from the title bar help menu.

---

## About Dialog

The About dialog shows runtime information from the current installation:

- app display name
- app version
- plugin API version
- current language name
- current OS string
- current Python version
- resolved user data folder

It also provides buttons for:

- Releases
- Wiki
- Issues
- Open G3M folder
- Telegram
- Discord

The Releases and Issues links are fixed GitHub URLs. The Wiki button uses
`global_settings["wiki_url"]` when present and otherwise falls back to
`https://github.com/y114git/G3M/`.

---

## Changelog Dialog

The changelog dialog is a `QTextBrowser` that loads markdown content from the
changelog URL stored in global settings.

Current behavior:

- shows a loading message first
- fetches asynchronously on a worker thread
- renders markdown
- allows external links
- shows a failure message when no source is available or loading fails
