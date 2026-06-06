# Announcements & Polls

G3M can show developer announcements inside the app. Some announcements are just messages, and some are polls.

## Supported types

The current code supports three announce types:

- `post`
- `poll_single`
- `poll_multiple`

## What you see

- Regular posts show a message inside the announcement dialog.
- Polls show selectable options and a submit action.
- If the announcement includes a link, the dialog can open a details page in your browser.

## When it appears

Announcements are checked from the app's global settings payload. G3M only shows a newer announcement version that you have not already dismissed or completed.

The seen version is stored locally as `announce_version`.

## Poll voting

Poll votes are submitted through the announce service. For voting, G3M keeps a local `announce_identity`, hashes it with SHA-256, and sends the hash instead of the raw identity.

Your submitted poll choices are also stored locally in `announce_poll_votes` so the app knows that you already voted.
