# Network & API

G3M mixes local features with a few online ones. Local library management keeps
working offline. Browser-style features depend on the network.

## What uses the network

- GameBanana browsing and downloads
- Discord Rich Presence handoff through the local Discord IPC pipe when
  available
- Announcements and polls
- Update checks
- Online presence count and global settings
- Plugin catalog and plugin downloads
- Community feeds

## GameBanana

G3M talks to the GameBanana API through the built-in adapter and uses the
current API base configured in the app. GameBanana-backed browsing is what
powers the Mods Browser for supported games.

The UI also has an explicit rate-limit message for the documented `250` requests
per hour limit.

## G3M cloud services

G3M uses cloud endpoints for:

- announcements and poll voting
- online presence and global settings

G3M does not collect or upload usage analytics.

## Session and availability

G3M keeps a shared network session and tracks overall connectivity with
`app_state.has_internet`.

When that flag is false, online features degrade gracefully, but local actions
such as:

- managing installed mods
- switching profiles
- importing local files
- editing mods
- launching already configured games

still remain available.
