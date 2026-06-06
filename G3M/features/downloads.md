# Downloads

The Downloads page is the place to watch anything G3M fetched for you: browser downloads, one-click installs, direct URLs, and optionally local imports.

---

## What You See

Each record tells you three things:

- where the file came from
- whether the file finished downloading
- whether G3M already turned it into an installed mod or plugin

That matters because a download can succeed, but still need your attention before it becomes usable.

---

## Most Common States

Use this quick mental model:

- `Queued` or `Downloading`: still in progress
- `Downloaded`: file is on disk
- `Pending Auto` or `Using`: G3M is trying to install it
- `Ready`: file is waiting for you because auto-use is off
- `Overwrite Pending`: G3M found an existing mod with the same ID and needs your decision
- `Needs Manual Install`: the file was downloaded, but G3M could not confidently map it to a supported import flow
- `Failed` or `Cancelled`: the flow stopped before completion

---

## Typical Flow

For a normal mod download, the flow is:

1. G3M creates a download record
2. the file is downloaded into the downloads area
3. G3M tries to auto-use it unless you disabled that behavior
4. the file is either installed, left ready for manual use, or flagged for manual attention

Auto-use goes through the same import pipeline as manual mod import, including conversion paths for supported external mod formats.

---

## Settings That Matter

The three download settings are:

- `No auto-use`: keep finished downloads in a ready state instead of importing them immediately
- `Delete after use`: remove the downloaded archive after a successful install
- `Save local imports`: create download history records for files you imported manually from disk

If you want a cleaner, more manual workflow, turn on `No auto-use`. If you want the smoothest browser-to-library flow, leave it off.

---

## Where Files Live

Downloads use the user data directory:

- records: `downloads/downloads_history.json`
- downloaded files: `downloads/`

The records survive restarts. On startup, G3M checks whether the physical file still exists and updates the record accordingly.

---

## When You Need to Act

Usually you only need to touch this page when:

- a mod wants to overwrite an existing install
- a file needs manual install
- you want to retry or inspect a failed download
- you disabled auto-use and want to process the file later
