# Logging

G3M maintains detailed log files for debugging and troubleshooting.

---

## Log Location

| Platform | Path |
| --- | --- |
| Windows | `%LOCALAPPDATA%\G3M\logs\` |
| macOS | `~/Library/Application Support/G3M/logs/` |
| Linux | `~/.local/share/G3M/logs/` |

---

## Log Files

### Main Log

- **File**: `g3m.log`
- **Content**: All application activity — startup, service initialization, mod operations, network requests, errors, warnings.
- **Created**: On every launch. The previous session's log is archived before being overwritten.
- **Format**: `%(asctime)s %(levelname)s %(name)s: %(message)s`

### Shortcut Runner Log

- **File**: `shortcut.log`
- **Content**: Activity from headless shortcut launches — config loading, mod resolution, patching, game launch, restoration.
- **Created**: Each time a desktop shortcut is executed.
- **Format**: Same as the main log.

### Archived Logs

- **Directory**: `logs/g3m/`
- **Content**: Timestamped copies of previous sessions' main log files.
- **Purpose**: Allows reviewing past sessions if the current log has been overwritten.

---

## Log Levels

G3M uses standard Python logging levels:

| Level | Usage |
| --- | --- |
| **DEBUG** | Detailed diagnostic information. Verbose. Includes variable values, internal state transitions, and detailed flow tracing. |
| **INFO** | Confirmation that operations work as expected. Mod loaded, game launched, file backed up, etc. |
| **WARNING** | Something unexpected happened but the operation can continue. Missing optional files, fallback behavior triggered, deprecated features used. |
| **ERROR** | A specific operation failed. Patching error, download failure, file I/O error. The application continues but the operation did not succeed. |
| **CRITICAL** | A fatal error that may prevent the application from functioning. Extremely rare — usually only at the top-level crash handler. |

### Default Log Level

The main log file captures **INFO** and above by default. The console (stderr) captures **WARNING** and above.

---

## Log Configuration

Logging is configured in `src/app/startup.py` during application initialization:

1. A root logger is set up with the INFO level.
2. A file handler writes to `g3m.log`.
3. A console handler writes to stderr (WARNING level).
4. The log format includes timestamps, level, logger name, and message.

### Log Archival

Before creating a new `g3m.log`, the startup routine:

1. Checks if a previous `g3m.log` exists.
2. If it does, copies it to `logs/g3m/` with a timestamp in the filename (e.g., `g3m_2024-03-20_14-30-00.log`).
3. Creates a fresh `g3m.log` for the new session.

Old archived logs are not automatically cleaned up. If disk space is a concern, you can manually delete old files from `logs/g3m/`.

---

## What Gets Logged

### Startup

- Application version and platform.
- Data directory paths.
- Settings loading result.
- Migration steps (if any).
- Game path detection results.
- Plugin scanning results.
- Network connectivity check.
- Global settings fetch result.

### Mod Operations

- Mod scanning and loading.
- Import operations (source, format detected, result).
- Patching operations (mod name, patch type, file paths, duration, result).
- Backup operations (file backed up, path).
- Restoration operations (file restored, path).

### Downloads

- Download started (URL, source, target type).
- Download progress (percentage milestones).
- Download completed (file path, size).
- Download failed (error message).
- Auto-use operations.

### Network

- API requests (URL, response status).
- Rate limit hits.
- Timeout and connection errors.

### Errors

All errors include the exception type, message, and stack trace (via `exc_info=True`).

---

## Using Logs for Bug Reports

When reporting a bug:

1. Reproduce the issue.
2. Close G3M.
3. Open `g3m.log` from the logs directory.
4. Look for ERROR or WARNING entries near the end of the file.
5. Include the relevant log sections in your bug report.

If the issue occurred in a previous session, check the `logs/g3m/` archive directory for older logs.

---

## Privacy

Logs may contain:

- File paths on your system (including your username in the path).
- Mod names and IDs.
- Game paths.

Logs do **not** contain:

- Chat messages.
- Password or authentication data (G3M has no auth).
- Analytics data.
- Full network response bodies (only status codes and error messages).

When sharing logs for bug reports, review them for any file paths you may want to redact.
