# Announcements & Polls

G3M displays in-app announcements and polls from the developer.

---

## How Announcements Work

On launch (after initialization), G3M checks the cloud server for the latest announcement. If a new announcement is available (one that hasn't been dismissed yet), a dialog appears.

---

## Announcement Types

### Post

A simple text announcement. The dialog shows:

- **Title / heading** — The announcement title.
- **Body text** — The full announcement content, rendered as rich text/HTML.
- **Dismiss button** — Closes the dialog and marks the announcement as seen.

### Single-Choice Poll

A poll where you can select **exactly one** option. The dialog shows:

- **Question / body text** — The poll question.
- **Options** — Radio buttons or a list of choices.
- **Submit button** — Sends your vote to the server.
- **Skip / Dismiss** — Closes without voting.

### Multiple-Choice Poll

A poll where you can select **one or more** options. Same as above, but with checkboxes instead of radio buttons.

---

## Poll Options

Poll options can be defined as:

- A simple list of strings.
- A list of objects with a `name` field.
- A dictionary with option names as keys (optionally with an `_order` key to specify display order).

Options starting with `_` (underscore) are hidden/internal and not shown to the user.

---

## Voting

When you submit a poll vote:

1. G3M sends your selection(s) to the cloud server along with:
   - The announcement version number.
   - The announcement type (single or multiple).
   - A hashed anonymous client ID (SHA-256 of a locally generated UUID, stored in settings as `announce_identity`).
   - A Unix timestamp.
2. The server records the vote.
3. G3M saves the vote locally in `announce_poll_votes` in your settings, so it knows you already voted for this version.

### Validation

- **Single poll**: You must select exactly one option.
- **Multiple poll**: You must select at least one option.
- The announcement must have a valid version number (> 0).

---

## Anonymous Identity

The first time a poll is encountered, G3M generates a random UUID and stores it in your local settings under `announce_identity`. This UUID is hashed (SHA-256) before being sent to the server, so the server never sees your raw ID. The identity is used only to prevent duplicate votes.

---

## Persistence

Dismissed announcements and submitted votes are tracked by version number in `announce_poll_votes` in the settings file. Each entry includes the selected options and a timestamp. If the developer publishes a new announcement with a higher version, the dialog appears again.
