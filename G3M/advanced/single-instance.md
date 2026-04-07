# Single Instance Enforcement

G3M ensures only one instance of the application runs at a time. This prevents conflicts with file operations, game monitoring, and settings management.

---

## How It Works

### Windows

G3M uses a named mutex (`G3M_SingleInstance_Mutex`) to detect if another instance is running:

1. On startup, G3M attempts to create the mutex.
2. If the mutex already exists, another instance is running.
3. The second instance sends its command-line arguments to the first instance (via a local socket or shared file).
4. The first instance receives the arguments (which may include a `g3m://` URL).
5. The second instance exits.
6. The first instance brings its window to the foreground.

### macOS

G3M uses a combination of process name checking and file-based locking:

1. On startup, G3M checks for other processes with the same name.
2. A lock file is created in the user data directory.
3. If the lock file is already held by another process, the second instance forwards its arguments and exits.

### Linux

G3M uses a similar lock file mechanism:

1. A lock file is created at a known path.
2. The file contains the PID of the running instance.
3. On startup, G3M checks if the PID in the lock file corresponds to a running G3M process.
4. If so, arguments are forwarded and the second instance exits.

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

## Lock File Cleanup

The lock file (on macOS/Linux) is cleaned up when G3M exits normally. If G3M crashes:

1. The lock file may remain on disk.
2. On the next launch, G3M checks if the PID in the lock file is still running.
3. If the PID is not running (stale lock), the lock file is removed and G3M starts normally.
4. If the PID is running but is a different process (PID reuse), G3M may incorrectly detect a running instance. In this rare case, manually deleting the lock file resolves the issue.

---

## Error Handling

If the single-instance mechanism fails (e.g., permission errors creating the mutex/lock):

- G3M logs a warning.
- It continues to start — better to risk two instances briefly than to fail to start.
- In practice, this is extremely rare.
