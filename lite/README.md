# Moddest Lite 0.3.0

[Download Moddest-Lite.html](https://github.com/Huluaccount2/Moddest-Portable/raw/refs/heads/main/lite/Moddest-Lite.html)

Open the downloaded HTML in Chrome. No installation, Terminal, Node.js, or
companion files are required. The file is approximately 556 KB.

## Included

- All 218 entries from the current Moddest game catalog, with search,
  categories, local saves, fullscreen controls and credits.
- The actual Moddest music page, audio player and lyrics components, bundled
  into the HTML rather than an iframe or a second simplified implementation.
- Song search, album and artist views, library, likes, playlists, queue,
  shuffle/repeat, seeking, volume and the word-synced lyrics popup.
- Live public Moddest playback and the ten latest public history entries.
- Personal tab-title lyrics while your own music is active, public live lyrics
  otherwise. Pausing or a lyric gap returns the title to Moddest after 10 seconds.
- Long line-only tab titles scroll forward at the same fixed speed as the main
  site, then stop at the ending instead of wrapping or replaying missed steps.
- The existing public playback WebSocket, with polling fallback. Personal
  lyrics use the audio clock directly and schedule the next word boundary.

## Online Features

This is an online-connected client, not a fully offline game or music archive.
Application code, styles, icons and the original 25 thumbnails are embedded.
The additional artwork, game programs and audio still load from online services.
Skribbl.io opens its original site in another tab.

Music uses the existing HTTPS public services, with the selected paid1 service
as a network-failure fallback. It never streams Spotify account audio or changes
anyone else's playback. Public Spotify metadata remains read-only.

Connections selects the public live/history and preferred game service.
Games missing from the reduced Daki catalog retry against the complete existing
HTTPS catalog. An unavailable or blocked backend can still prevent playback.

## Local Data and Limits

Music libraries, likes and playlists save to this browser/file, not a Moddest
account. Existing local game saves are preserved. Keep the file location stable;
managed-browser storage policies may prevent persistence or change it when moved.

There are no account logins, proxy-site launchers, chat, AI, reservations or
private account exports in this package. Requests omit account credentials.
Game documents remain sandboxed; accepted saves are source/nonce validated.

Word-by-word lyrics depend on available timings. Background updates remain
subject to browser/OS throttling; a local HTML file cannot remove that restriction
or make a blocked service accessible. Direct testing on the school Mac is still
needed. See VERIFICATION.md for the tests and remaining limits.

The full hosted site and original portable client are not replaced.
