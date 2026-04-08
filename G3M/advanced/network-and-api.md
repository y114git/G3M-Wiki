# Network & API

G3M communicates with several external services. This page documents all network interactions.

---

## GameBanana API

G3M fetches mod data from the GameBanana REST API.

### Endpoints Used

| Purpose | Endpoint Pattern |
| --- | --- |
| List mods for a game | `https://gamebanana.com/apiv11/Game/<game_id>/Subfeed?...` |
| Search mods | `https://gamebanana.com/apiv11/Util/Search/Results?...` |
| Get mod details | `https://gamebanana.com/apiv11/Mod/<mod_id>/ProfilePage` |
| Get mod description | Loaded from the mod's description URL field. |
| Get mod files | `https://gamebanana.com/apiv11/Mod/<mod_id>/DownloadPage` |
| Download mod file | Direct download URL provided by GameBanana (e.g., `https://files.gamebanana.com/...`). |

### Pagination

The GameBanana API returns mods in pages of 15 items. G3M tracks which pages have been loaded per game and loads the next page on scroll.

### Rate Limiting

GameBanana enforces a limit of **250 requests per hour**. When this limit is reached:

- G3M receives a 429 (Too Many Requests) response.
- The status bar shows: "GameBanana API rate limit reached (250 requests/hour). Please wait and try again."
- A `gb_rate_limit_error` signal is emitted.
- No further requests are made until the rate limit resets.

### Caching

- **Mod list pages** — Cached in memory per game. Refreshing the game clears the cache.
- **Mod icons** — Cached in memory as rendered `QPixmap` objects (plain dict, unbounded during session).
- **Description images** — Cached during the session.
- **Mod metadata** — Stored locally when a mod is downloaded, so Library mods don't need network access.

### Timeouts

- Search requests: **10 seconds** timeout.
- General API requests: **10 seconds** timeout.
- File downloads: No fixed timeout (progress-based).

---

## G3M Cloud Services

G3M has its own cloud backend for features not provided by GameBanana. The following features communicate with it:

- **Chat** — Fetches and sends messages. Anonymous, no account required.
- **Online Presence** — Registers the current session and retrieves the live online user count.
- **Announcements & Polls** — Fetches developer announcements and submits poll votes. Poll votes use a locally generated anonymous identifier to prevent duplicates.
- **Analytics** — Uploads anonymous usage data when opted in.
- **Global Settings** — Fetches configuration on startup (update info, Full Install URLs, announcement payload). Cached in memory and re-fetched periodically.

---

## HTTP Session

G3M creates a shared `requests.Session` with:

- A custom User-Agent header identifying the app and version.
- Connection pooling for efficiency.
- Retry logic for transient failures.

The session is stored in `AppState.network_session` and reused across all services.

---

## Network Availability

G3M tracks network availability via the `AppState.has_internet` flag:

- On startup, G3M attempts a lightweight network request.
- If it succeeds, `has_internet` is set to `True`.
- If it fails, `has_internet` is set to `False`.
- Certain features (Mods Browser, Chat, Online Presence, Updates) are disabled or degraded when offline.
- The flag may be updated during the session if network conditions change.

---

## Proxy and Firewall

G3M uses the system's default proxy settings via the `requests` library. If you are behind a corporate proxy or firewall:

- Ensure `https://gamebanana.com` is accessible.
- Ensure the G3M cloud functions URL is accessible.
- If these are blocked, the corresponding features will not work, but local mod management remains fully functional.

---

## SSL/TLS

All network communication uses HTTPS. G3M uses the `urllib3` library (bundled with `requests`) for TLS support. Certificate verification is enabled by default.

---

## Offline Mode

G3M works offline for local operations:

- Importing local mods from files.
- Managing installed mods in the Library.
- Launching games with mods.
- Creating/applying patches in Modding Tools.
- Editing mod metadata.
- Profile management.
- Theme customization.

Online-only features:

- Mods Browser (GameBanana browsing).
- Downloads from GameBanana.
- One-Click Install.
- Chat.
- Announcements and Polls.
- Online Presence counter.
- Update checking.
- Analytics upload.
- Plugin catalog browsing.
