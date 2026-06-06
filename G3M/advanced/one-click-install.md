# One-Click Install

G3M supports protocol-based install links so a browser can hand a mod download directly to the app.

## Supported schemes

- `g3m://`
- legacy `deltahub://`

## Safety behavior

The app does not silently download on protocol open. It shows a confirmation step first, and the forwarded target still has to be a normal `http` or `https` URL.

## Single-instance behavior

If G3M is already open, the protocol request is forwarded to the running instance instead of opening a second full app window.
