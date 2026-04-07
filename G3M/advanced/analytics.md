# Analytics

G3M includes an optional anonymous analytics system to help the developer understand how the application is used.

---

## Opt-In

Analytics are **disabled by default**. To enable:

1. Go to Settings → General (or the Analytics section).
2. Check **Anonymous analytics opt-in**.
3. Analytics collection begins.

You can disable analytics at any time by unchecking the box. When disabled, no data is collected or sent.

---

## What Is Collected

All data is anonymous — no personal information, usernames, email addresses, or IP addresses are stored. The collected events include:

| Event | Data |
| --- | --- |
| **App launch** | App version, platform (Windows/macOS/Linux), architecture, language, screen resolution. |
| **Game launch** | Game ID, mod count, launch mode (normal/chapter), used mod IDs (hashed), playtime duration. |
| **Mod install** | Source (GameBanana/local/protocol), outcome (success/failure), file extension, merge/manual flags. |
| **Mod download** | Source kind, target kind, outcome. |
| **Update check** | Outcome (up-to-date, update available, error). |
| **Profile switch** | Profile count (not profile names). |
| **Plugin usage** | Plugin IDs of enabled plugins. |

---

## How It Works

1. Events are collected in a local buffer as they occur.
2. Periodically (or when the buffer is large enough), events are batched and sent to the G3M cloud server.
3. The batch is compressed (gzip) and base64-encoded before transmission for efficiency.
4. The server endpoint is `{CLOUD_FUNCTIONS_BASE_URL}/ingestAnalytics`.
5. If the upload fails, events are retained and retried later.
6. No event is ever sent if analytics are disabled.

---

## Privacy

- No personally identifiable information is collected.
- Mod IDs from GameBanana are included as-is (they are public information). Local mod IDs are hashed.
- The analytics identity is a local UUID, never correlated to any account or device fingerprint.
- All data is processed in aggregate for usage statistics only.
