# Chat

G3M includes a built-in community chat accessible from the title bar.

---

## Opening Chat

Click the **Chat** button (speech bubble icon) in the title bar. The Chat dialog opens.

---

## Channels

The chat has multiple channels, one per supported language:

- **English** (`en`)
- **Español** (`es`)
- **Русский** (`ru`)
- **中文** (`zh`)

Select a channel from the dropdown at the top of the chat dialog. Messages are loaded from the selected channel.

---

## Reading Messages

Messages are loaded from the G3M cloud server. Each message shows:

- **Author name** — The display name of the sender.
- **Message text** — The content of the message.
- **Timestamp** — When the message was sent.

Messages are cached for 5 seconds to reduce server load. Up to 100 messages are loaded per channel.

---

## Sending Messages

Type your message in the input field and press Enter or click Send. Rules:

- **Maximum length**: 100 characters.
- **No URLs**: Messages containing URLs, links, or domain names are rejected. This includes `http://`, `https://`, `www.`, shortener domains (bit.ly, t.co, etc.), and bare domain patterns.
- **No empty messages**: Whitespace-only messages are rejected.

If a rule is violated, an error message is shown (e.g., "Message too long", "Links are not allowed in chat", "Empty message").

---

## Requirements

- An active internet connection is required.
- The G3M cloud backend must be reachable.
- No account or login is needed — chat is anonymous.

---

## Error States

| Error | Meaning |
| --- | --- |
| "config_error" | The cloud server URL is not configured. |
| "empty_message" | The message is blank. |
| "message_too_long" | Message exceeds 100 characters. |
| "contains_url" | The message contains a link or domain. |
| "send_error" | The server rejected the message or the request failed. |
