# Online Presence

G3M displays an online player counter in the title bar, showing how many people are currently playing games through G3M.

---

## What It Shows

In the title bar, next to the app title, an "Online: N" counter appears. The tooltip reads: "This counter shows the number of players playing the game via the launcher."

The number represents users who have G3M open and have launched a game in the current session.

---

## How It Works

1. When G3M launches, it registers a "presence" with the G3M cloud server.
2. The server maintains a count of active sessions.
3. G3M periodically refreshes the presence (approximately every 30 minutes) to keep the session alive.
4. When G3M closes, the session eventually expires on the server side.
5. The counter is fetched from the server and displayed in the title bar.

---

## Privacy

- No personal information is sent with the presence ping.
- The server only sees an anonymous session token.
- The counter is aggregate — it shows a total count, not individual user information.

---

## Network Dependency

The online counter requires an active internet connection. If the network is unavailable:

- The counter may show "Online: 0" or not appear at all.
- G3M continues to function normally; the counter is purely informational.
- When the network becomes available again, the counter updates on the next refresh cycle.
