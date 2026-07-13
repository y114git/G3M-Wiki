# Localization

G3M ships with built-in translations and can also load external language files.

## Bundled languages

The current bundled set is:

- `en`
- `ru`
- `es`
- `ko`
- `ja`
- `zh_cn`
- `zh_tw`

## Where files live

Bundled language files are inside `src/assets/lang/`.

At runtime, G3M also syncs language files into the user data `lang/` folder so
they can be customized outside the bundle.

## Plugin support

Plugins can ship their own `lang/` folder and merge extra strings into the app
localization system.
