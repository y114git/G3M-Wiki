# One-Click Install

G3M registers custom URL protocol handlers so you can install mods with a single click from websites like GameBanana.

---

## Supported Protocols

| Scheme | Example |
| --- | --- |
| `g3m://` | `g3m://https://gamebanana.com/dl/12345` |
| `deltahub://` | `deltahub://https://gamebanana.com/dl/12345` |

Both schemes work identically. `deltahub://` is maintained for backward compatibility with the old DELTAHUB name.

---

## How It Works

### Registration

- **Windows**: On first launch, G3M registers the `g3m` and `deltahub` URL schemes in the Windows Registry under `HKEY_CURRENT_USER\Software\Classes\`. Each scheme points to the G3M executable.
- **Linux**: G3M creates a `.desktop` file at `~/.local/share/applications/g3m-url-handler.desktop` with `MimeType=x-scheme-handler/g3m;x-scheme-handler/deltahub;`. It also runs `xdg-mime` to register itself as the default handler.
- **macOS**: The URL schemes are declared in the application's `Info.plist` as `CFBundleURLSchemes`.

### Flow

1. You click a one-click install link on a website (e.g., a "1-Click Install" button on GameBanana).
2. Your browser opens the URL with the `g3m://` scheme.
3. The operating system routes the URL to G3M.
4. If G3M is already running, the URL is forwarded to the existing instance via the single-instance mechanism.
5. If G3M is not running, it starts and receives the URL as a command-line argument.
6. G3M parses the URL to extract the actual download link.
7. A **confirmation dialog** appears showing:
   - The download URL.
   - A warning to verify the source.
   - Confirm / Cancel buttons.
8. If confirmed, the mod is downloaded and imported through the Downloads system.

### URL Parsing

The protocol URL is parsed by stripping the scheme prefix and extracting the content URL. Common URL mangling is corrected:

- `https//` → `https://`
- `http//` → `http://`
- Trailing slashes and commas are stripped.

---

## Security

- A confirmation dialog always appears before downloading. The user must explicitly approve each one-click install.
- The download URL must start with `http://` or `https://`. Other schemes are rejected.
- If the game is running when a one-click install is triggered, G3M shows a warning and does not proceed.

---

## GameBanana Integration

GameBanana supports one-click install via the `g3m://` protocol. Mod pages on GameBanana can show a "1-Click Install" button that generates a `g3m://` URL pointing to the mod's download link.

For this to work, the G3M protocol handler must be registered on the user's system (which happens automatically on first launch).
