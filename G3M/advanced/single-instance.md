# Single Instance Enforcement

G3M ensures only one instance of the application runs at a time. This prevents conflicts with file operations, game monitoring, and settings management.

---

## How It Works

G3M uses Qt's `QLocalServer` / `QLocalSocket` (named local socket) as its cross-platform single-instance mechanism. The socket is identified by the key `g3m.single-instance-lock`.

1. On startup, G3M tries to connect to the named local socket.
2. If the connection succeeds, another instance is already running — the second instance sends any URL argument (e.g., `g3m://...`) over the socket, then exits immediately.
3. If the connection fails, no other instance is running — G3M removes any stale socket entry with `QLocalServer.removeServer`, then starts its own `QLocalServer` to listen for future second instances.
4. The running instance receives forwarded data and processes it (e.g., shows the one-click install confirmation dialog and brings its window to the foreground).

This mechanism works identically on Windows, macOS, and Linux.

---

## URL Forwarding

The most common reason a second instance is launched is to handle a `g3m://` or `deltahub://` URL:

1. The user clicks a one-click install link in their browser.
2. The OS launches G3M with the URL as a command-line argument.
3. If G3M is already running:
   - The new instance detects the existing one.
   - The URL is forwarded to the existing instance.
   - The new instance exits immediately.
   - The existing instance receives the URL and processes it (showing the download confirmation dialog).
4. If G3M is not running:
   - The new instance starts normally.
   - The URL is processed during initialization.

---

## Window Activation

When the second instance exits and forwards to the first:

1. The first instance's window is brought to the foreground.
2. If the window was minimized, it is restored.
3. If the window was behind other windows, it is raised to the top.
4. This ensures the user sees the download confirmation dialog when clicking a one-click install link.

---

## Error Handling

If the single-instance mechanism fails (e.g., permission errors creating the local socket):

- G3M logs a warning.
- It continues to start — better to risk two instances briefly than to fail to start.
- In practice, this is extremely rare.
