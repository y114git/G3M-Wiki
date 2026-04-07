# Audio

G3M supports two types of custom audio: a startup sound and looping background music.

---

## Startup Sound

A short audio clip that plays once when G3M opens.

### Setting a Startup Sound

1. Go to Settings → Appearance.
2. Click **Select startup sound**.
3. Choose an audio file.
4. The file is copied to the data folder as `custom_startup_sound.<ext>`.
5. The sound plays on the next launch.

### Supported Formats

`.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, `.aac`

### Removing the Startup Sound

If a sound is set, the button changes to **Remove startup sound**. Click it to delete the file.

### Disabling the Startup Sound

The **Disable startup sound** checkbox silences the startup sound without deleting the file. Useful for keeping the file but muting it temporarily.

---

## Background Music

A looping audio track that plays continuously while G3M is open.

### Setting Background Music

1. Go to Settings → Appearance.
2. Click **Select background music**.
3. Choose an audio file.
4. The file is copied to the data folder as `custom_background_music.<ext>`.
5. Music starts playing immediately and loops.

### Supported Formats

`.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, `.aac`

### Removing Background Music

If music is set, the button changes to **Remove background music**. Click it to stop the music and delete the file.

### Pause When Unfocused

The **Pause when unfocused** checkbox pauses background music when G3M loses window focus (e.g., you switch to another application). Music resumes when G3M is focused again.

### Music Monitor

G3M continuously monitors the background music playback process. If the music stops unexpectedly (e.g., the playback process crashes), it is restarted automatically within 1 second.

### Implementation

Background music runs in a separate system process to avoid blocking the UI thread. This means it continues playing even if the main UI is busy with operations.

---

## Audio and Game Launch

Background music continues playing while a game is running (unless paused by the unfocused setting). If you want silence during gameplay, pause or remove the background music before launching.
