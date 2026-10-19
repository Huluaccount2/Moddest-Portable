# Moddest single-file client

Open `Moddest.html` with Google Chrome. Keep the file intact; no other files,
Terminal, Node.js, launcher or installation are required.

The interface, styles, fonts and local artwork are embedded. Home and Niche
navigation stays inside the file. Public playback, lyric timings, album art,
listening history, counters, weather, media and the radio listing use online
services. Word highlighting uses the existing playback clock and lyric renderer.

Important limits:

- This is a public/guest client, not a full account client. Sign-in, chat, AI,
  reservations, Listen Live and game links open their existing hosted pages.
  They are not silently authenticated or claimed to run inside the local file.
- Only fixed public read endpoints are exposed to the file. No account cookies,
  Spotify secrets, access keys or pairing data are embedded or transmitted.
- Internet access to Moddest's APIs is required for live data. A blocked API,
  blocked third-party site or device policy can still prevent a feature working.
- The app does not cache old playback or queue account writes offline.
- The file does not automatically update. Download a new build for UI updates.

Browser verification and remaining gaps are recorded in VERIFICATION.md.

