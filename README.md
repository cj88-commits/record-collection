# Record Collection

A self-hosted music player for Android, built for [Subsonic](http://www.subsonic.org/)-compatible servers (Navidrome, Airsonic, Subsonic, etc.).

---

## What it is

Record Collection is a minimal, album-first Android client for your self-hosted music library. It connects to any Subsonic-compatible server, syncs your album catalogue locally, and lets you stream or download your music — no streaming service required.

---

## Features

- **Album grid** — browse your library sorted A–Z, by decade, recently played, starred, or downloaded
- **Artist view** — collapsing hero with per-artist album grid
- **Streaming** — configurable quality per network type (WiFi / mobile); original or Opus transcoding
- **Offline playback** — download albums for playback without a connection
- **Now Playing** — full-screen player with seek bar, buffered position, and track list
- **Persistent playback** — Media3 `MediaSessionService`; resumes after restart
- **Scrobbling** — last.fm-compatible scrobbling via the Subsonic API
- **ReplayGain** — normalise loudness across tracks
- **Image caching** — configurable on-device cover art cache (250 MB – 2 GB)
- **Offline cover art** — cover art is cached with a stable key so it displays correctly in flight mode

---

## Requirements

- Android 8.0 (API 26) or later
- A running Subsonic-compatible server:
  - [Navidrome](https://www.navidrome.org/) (recommended)
  - [Airsonic-Advanced](https://github.com/airsonic-advanced/airsonic-advanced)
  - [Subsonic](http://www.subsonic.org/) 6.0+
  - Any server that implements the Subsonic REST API v1.16.1

---

## Installation

1. Download the latest APK from the [Releases](https://github.com/cj88-commits/record-collection/releases) page.
2. On your Android device, enable **Install unknown apps** for your browser or file manager.
3. Open the APK and follow the on-screen prompts.
4. Launch Record Collection, enter your server URL, username, and password, then tap **Test connection**.

---

## Building from source

**Prerequisites**

- Android Studio Ladybug (2024.2) or later
- JDK 17
- Android SDK with API 35 platform installed

**Steps**

```bash
git clone https://github.com/cj88-commits/record-collection.git
cd record-collection
./gradlew assembleDebug
```

The debug APK is written to `app/build/outputs/apk/debug/app-debug.apk`.

To produce a release build, create `keystore.properties` in the project root:

```properties
storeFile=/path/to/your.keystore
storePassword=your-store-password
keyAlias=your-key-alias
keyPassword=your-key-password
```

Then run:

```bash
./gradlew assembleRelease
```

---

## Compatibility

| Server | Status |
|--------|--------|
| Navidrome | Tested |
| Airsonic-Advanced | Should work |
| Subsonic | Should work |
| Jellyfin (Subsonic API) | Should work |

Connections over Tailscale (including self-signed certificates on private IP ranges) are supported.

---

## Known limitations

- **No podcast support** — the app is music-only
- **No playlist management** — playlists cannot be created or edited from the app
- **Cover art cache changes require restart** — adjusting the image cache size limit takes effect on the next app launch
- **Transcoding depends on server** — format and bitrate options are only available if your server supports transcoding

---

## Screenshots

See [recordcollection.netlify.app](https://recordcollection.netlify.app) for screenshots.

---

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.
