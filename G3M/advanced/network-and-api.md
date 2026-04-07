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
- **Mod icons** — Cached in memory (LRU, up to 100 entries).
- **Description images** — Cached during the session.
- **Mod metadata** — Stored locally when a mod is downloaded, so Library mods don't need network access.

### Timeouts

- Search requests: **10 seconds** timeout.
- General API requests: **10 seconds** timeout.
- File downloads: No fixed timeout (progress-based).

---

## G3M Cloud Services

G3M has its own cloud backend for features not provided by GameBanana.

### Base URL

The cloud functions base URL is configured in `config.py`. All cloud requests use this base URL.

### Endpoints

| Endpoint | Purpose | Method |
| --- | --- | --- |
| `/chat/messages` | Fetch chat messages | GET |
| `/chat/send` | Send a chat message | POST |
| `/presence/ping` | Register/refresh online presence | POST |
| `/presence/count` | Get online player count | GET |
| `/announce/latest` | Get the latest announcement | GET |
| `/announce/vote` | Submit a poll vote | POST |
| `/ingestAnalytics` | Upload analytics batch | POST |
| `/globalSettings` | Fetch global app settings | GET |
| `/updates/latest` | Check for app updates | GET |

### Authentication

No user authentication is required. All cloud endpoints are anonymous. The only identity used is:

- **Chat**: Anonymous — no identity.
- **Polls**: A hashed UUID (`announce_identity` in settings), used solely to prevent duplicate votes.
- **Analytics**: A local UUID, never correlated to any account.
- **Presence**: A session token generated per app launch.

### Global Settings

On startup, G3M fetches global settings from the cloud. These settings include:

- Download URLs for Full Install games.
- Feature flags.
- Plugin catalog URL.
- Announcement payload.
- Any server-side configuration overrides.

The global settings are cached with a timestamp (`global_settings_loaded_at`) and refreshed periodically.

---

## GitHub API

Used for update checking:

| Purpose | Endpoint |
| --- | --- |
| Check latest release | `https://api.github.com/repos/y114git/G3M/releases/latest` |
| List all releases (beta) | `https://api.github.com/repos/y114git/G3M/releases` |

### Rate Limiting

GitHub's API has a rate limit of 60 requests per hour for unauthenticated requests. Since G3M only checks once per launch, this is rarely an issue.

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
- Ensure `https://api.github.com` is accessible (for updates).
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
