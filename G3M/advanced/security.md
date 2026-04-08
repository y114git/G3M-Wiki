# Security

G3M handles user data, downloads files from the internet, and executes patches against game files. This page documents the security measures in place.

---

## File Downloads

### Source Verification

When downloading from GameBanana:

- Files are fetched from GameBanana's official file servers (e.g., `files.gamebanana.com`).
- GameBanana performs automated file scanning on uploaded mods.
- The file picker dialog shows each file's security scan status (Scanned, Pending, etc.) and MD5 hash.
- G3M does not perform its own antivirus scanning — it relies on GameBanana's and the user's system-level protection.

### One-Click Install Confirmation

One-click install (`g3m://` protocol) always shows a confirmation dialog before downloading. The dialog displays:

- The full download URL.
- A warning to verify the source.
- The option to cancel.

No file is downloaded without explicit user approval.

### HTTPS

All network communication uses HTTPS (TLS encrypted). This includes:

- GameBanana API requests.
- File downloads from GameBanana.
- G3M cloud service requests (including update info).

Certificate verification is enabled by default via the `urllib3`/`requests` libraries.

---

## XML Processing

G3M processes XML files when importing DELTAMOD format mods (which use `modding.xml` files). To prevent XML-based attacks (XXE — XML External Entity injection), G3M uses the **defusedxml** library instead of Python's built-in `xml.etree.ElementTree`.

The `defusedxml` library:

- Blocks external entity resolution.
- Blocks DTD processing.
- Prevents billion-laughs attacks.
- Prevents other XML bomb patterns.

---

## File System Operations

### Sandboxing

G3M only operates within:

- Its own user data directory (`%LOCALAPPDATA%\G3M` on Windows, or equivalent on other platforms).
- The game's installation directory (for patching and restoration).
- User-selected directories (for imports, exports, Full Install).

G3M does not access or modify files outside these locations.

### Backup and Restore

Before modifying any game file, G3M creates a backup. After the game exits, originals are restored. This ensures game files are never permanently altered by G3M operations. See [Backup & Restore](backup-and-restore.md).

### Executable Protection

During restoration, G3M does not overwrite game executables. Protected files include:

- The game's main executable (e.g., `DELTARUNE.exe`).
- Any custom executable configured in settings.

This prevents a malicious mod from replacing the game executable with harmful code.

### Safe File Deletion

G3M uses safe delete operations that check paths before removal. Files are deleted directly (not moved to recycle bin).

---

## Plugin Security

### API Sandbox

Plugins run in the same Python process as G3M. They have access to:

- G3M's service APIs (via the `PluginContext`).
- The file system.
- The network.

Plugins are **not sandboxed** — they can do anything a Python script can do. This is similar to how browser extensions or IDE plugins work.

### Trust Model

Because plugins have full access, users should:

- Only install plugins from trusted sources.
- Review the plugin catalog (curated by the G3M developer).
- Be cautious with manually installed plugins from unknown sources.
- Check the plugin's source code if available.

### Hook Isolation

Plugin hooks run in a background thread with exception handling:

- If a plugin hook throws an exception, it is caught and logged.
- Other plugins continue to function.
- G3M does not crash.

### Disabled by Default

All installed plugins are disabled by default. Users must explicitly enable them. This prevents accidental code execution from newly installed plugins.

---

## CSX Script Security

CSX scripts (`.csx` files) are C# code executed by G3MTool against game data. They have the same security considerations as plugins:

- Scripts can potentially do anything the G3MTool runtime allows.
- Only use CSX scripts from trusted mod authors.
- G3M does not analyze or sandbox CSX scripts.

---

## Settings File Integrity

### Corrupted Settings Recovery

If `settings.json` becomes corrupted (invalid JSON):

1. G3M detects the corruption.
2. Creates a backup as `settings.json.invalid.bak`.
3. Shows a warning notification.
4. Creates fresh default settings.

This prevents a corrupted settings file from crashing the application.

### No Sensitive Data

G3M does not store any sensitive data (passwords, tokens, API keys) in its settings files. The most "sensitive" data is:

- File paths (which may contain the username in the path).
- The `announce_identity` UUID (used only for poll deduplication, hashed before transmission).

---

## Analytics Privacy

The anonymous analytics system (when opted in):

- Does not collect IP addresses, usernames, account identifiers, or file paths.
- Collects only non-personal, non-identifying usage signals.
- Data is sent securely to the G3M server over HTTPS.

---

## Update Security

When downloading app updates:

- Update availability and download URLs are fetched from the G3M cloud backend.
- The download itself uses HTTPS.
- G3M does not verify release signatures (GPG/code signing) at this time.
- On Windows, the downloaded installer is an InnoSetup executable — Windows SmartScreen and antivirus apply their usual checks.

---

## Reporting Security Issues

If you discover a security vulnerability in G3M:

1. **Do not** open a public GitHub issue.
2. See the `SECURITY.md` file in the repository for responsible disclosure instructions.
3. Contact the developer privately through the channels listed in `SECURITY.md`.
