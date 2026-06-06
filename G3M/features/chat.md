# Chat

G3M has a lightweight in-app chat client. It is meant for short community messages, not for account-based messaging or file sharing.

---

## What It Does

The client can:

- load recent chat messages from the backend
- send short text messages
- refresh messages with a small cache to avoid hammering the server

There is no account flow in the client.

---

## Message Rules

Current client-side limits are strict:

- maximum message length: `100` characters
- empty messages are rejected
- messages that look like links or domains are rejected

That URL filter blocks common link patterns such as `http://`, `https://`, `www.`, shortener domains, and bare domain-like text.

---

## Networking

Chat requires:

- a reachable backend URL in global settings
- an internet connection

Message lists are cached for `5` seconds. That cache only affects how often the client re-requests the same message list.

---

## What to Expect

If chat works normally, you type a short message, send it, and the dialog refreshes the visible message list. If it does not work, the usual reasons are:

- backend configuration is missing
- the message broke one of the client rules
- the network request failed
