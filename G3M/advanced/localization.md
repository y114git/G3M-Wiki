# Localization

G3M has a full localization system that supports multiple languages and is extensible by users and plugins.

---

## Bundled Languages

| Language | File | Code |
| --- | --- | --- |
| English | `lang_en.json` | `en` |
| Spanish | `lang_es.json` | `es` |
| Russian | `lang_ru.json` | `ru` |
| Chinese Simplified | `lang_zh_cn.json` | `zh_cn` |
| Chinese Traditional | `lang_zh_tw.json` | `zh_tw` |

English is the fallback language. If a translation key is missing in the selected language, the English text is used.

---

## Language Files

Each language file is a JSON file with nested keys. The structure follows a dot-separated naming convention:

```json
{
  "ui": {
    "launch_button": "Launch",
    "cancel_button": "Cancel",
    "close_game": "Close Game"
  },
  "buttons": {
    "change_path": "Change DELTARUNE Path",
    "install": "Install"
  },
  "status": {
    "ready": "Ready",
    "please_wait": "Please wait..."
  }
}
```

Keys are referenced in the application as flat dot-paths like `ui.launch_button`, `buttons.change_path`, `status.ready`.

---

## Key Categories

The English language file contains keys organized into these groups:

| Prefix | Content |
| --- | --- |
| `ui.*` | Main UI labels (buttons, tabs, titles, common elements). |
| `buttons.*` | Action button labels (change path, install, export, etc.). |
| `status.*` | Status bar messages (ready, loading, errors, progress). |
| `dialogs.*` | Dialog titles and body text. |
| `errors.*` | Error messages. |
| `tabs.*` | Tab labels (chapters, demo, settings sub-tabs). |
| `settings.*` | Settings labels and descriptions. |
| `tooltips.*` | Tooltip text for buttons and controls. |
| `defaults.*` | Default/fallback values ("Unknown", "Not specified"). |
| `library.*` | Library-specific labels. |
| `search.*` | Search-related text. |
| `filters.*` | Filter labels and options. |
| `blocklist.*` | Blocklist manager text. |
| `modding_tools.*` | Modding Tools dialog text. |
| `chat.*` | Chat dialog text. |
| `profiles.*` | Profile management text. |
| `plugins.*` | Plugin system text. |
| `about.*` | About dialog text. |
| `downloads.*` | Downloads system text. |
| `game_versions.*` | Game Versions dialog text. |
| `mod_versions.*` | Mod Versions dialog text. |
| `game_manager.*` | Game Manager dialog text. |
| `analytics.*` | Analytics-related text. |
| `announce.*` | Announcement/poll dialog text. |

---

## Changing Language

1. Go to Settings → General.
2. Select a language from the **Language** dropdown.
3. A restart is required for the change to fully take effect.

On restart, G3M:
1. Loads the selected language file.
2. Falls back to English for any missing keys.
3. Updates the Qt translator for system dialog translations.
4. Loads any language-specific font if needed (e.g., CJK fonts for Chinese).

---

## Language Detection

On first launch, if no language is explicitly set, G3M detects the system locale and selects the closest matching language. The mapping:

| System Locale Prefix | G3M Language |
| --- | --- |
| `ru` | Russian |
| `es` | Spanish |
| `zh_cn`, `zh_hans` | Chinese Simplified |
| `zh_tw`, `zh_hant`, `zh_hk` | Chinese Traditional |
| Everything else | English |

---

## External Language Files

G3M syncs bundled language files to the `lang/` folder in the user data directory. You can edit these external copies to customize translations. On each launch, G3M merges the bundled file with the external one — new keys added in updates are injected, but your custom changes are preserved.

---

## Plugin Localization

Plugins can provide their own language files in a `lang/` subfolder within the plugin directory. These strings are loaded and merged into the main localization system when the plugin is scanned. Plugin strings are accessed with the same `tr("key")` function and follow the same dot-key convention.

Plugin strings are cleared and reloaded each time plugins are rescanned.

---

## Missing Keys

If a translation key is not found in the current language or the English fallback, the key is displayed wrapped in brackets: `[missing.key.name]`. This makes it easy to spot untranslated content.
