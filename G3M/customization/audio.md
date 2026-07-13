# Audio

G3M supports two kinds of custom audio:

- startup sound
- background music

## Supported formats

The current code looks for these extensions:

- `.mp3`
- `.wav`
- `.ogg`
- `.flac`
- `.m4a`
- `.aac`

## Startup sound

Startup sound can be muted without deleting the file through the
`disable_startup_sound` setting.

## Background music

Background music is managed by the customization service and can be paused
automatically when the app loses focus through:

- `pause_background_music_unfocused`

The same service also stops music while a game session is running.
