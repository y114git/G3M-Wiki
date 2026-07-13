# Analytics

G3M keeps a small amount of anonymous aggregated usage data so the project can
see which parts of the app are actually being used.

## How it works

There are two layers:

- A minimal baseline layer that records broad app activity such as launches and
  general feature usage.
- An extra opt-in layer controlled by the **Anonymous analytics** setting in
  Settings.

The opt-in layer is **off by default**.

## What the opt-in setting changes

When you enable the setting, G3M can send more detailed aggregated usage buckets
such as dialog opens, downloads, searches, plugin actions, and launch outcome
categories. The setting is stored as `analytics_opt_in_enabled`.

When you disable it again, G3M stops sending the opt-in-only events.

## Storage and delivery

- Pending batches are stored locally in `analytics_pending.json`.
- Uploads go to the G3M cloud endpoint `/sendAnalytics`.
- If the app is offline, pending data waits locally and is retried later.

## Privacy boundaries

The current code is written to avoid sending direct personal data such as raw
file paths or exact search text. The user-facing tooltip also explicitly
describes the analytics as anonymous and aggregated.
