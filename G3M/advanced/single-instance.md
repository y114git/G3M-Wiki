# Single Instance

G3M is designed to keep one primary running instance.

## Current mechanism

The current startup flow uses Qt local-server and local-socket primitives to detect an already running copy and hand work over to it.

## Why this matters

This avoids duplicate launch-state tracking, duplicate patching work, and awkward conflicts with protocol handling.

## One-click install tie-in

Second launches caused by `g3m://` or `deltahub://` links are forwarded to the running instance so the existing window can handle the request.
