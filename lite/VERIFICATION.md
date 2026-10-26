# Moddest Lite 25-game test, 2026-10-26

- Built one approximately 213 KB HTML with inline application code, styles, Lucide
  icons, and all 25 optimized WebP thumbnails. No frontend library CDN is needed.
- Six automated tests passed: packaging, catalog/search, live/word-timed
  playback and recent history, sandboxed launch/save validation, failures,
  and personal audio/lyrics/tab titles including pause, seek and track changes.
- 22 focused backend and title tests passed; TypeScript checks passed after
  regenerating stale Next route types. Worker deployment completed.
- All 24 in-panel game entry routes returned HTTP 200 on paid1. Skribbl.io
  is the remaining game and opens externally rather than claiming to run locally.
- Browser preview showed 25 games, 25 loaded thumbnails, connected live music,
  current album art/progress/lyrics, and 10 recent listening-history entries.
- The 2048 board rendered inside its sandboxed frame; save/close controls and
  navigation were checked. This is not a full gameplay test of all 25 games.
- Desktop and 390px phone-width checks had no horizontal overflow. The preview
  had no browser console errors during these checks.
- Added narrowly allowlisted public read endpoints for catalog search, lyrics
  and audio, with anonymous CORS, existing rate limits, byte-range support and
  no forwarding of account credentials or private response headers.
- Live paid1 search returned real song results. Polkas on 45 returned word
  timings and audio bytes; lyric seeking and tab-title rendering were checked.

Limits:
- The browser tool permits HTTP/HTTPS only and rejected opening a file URL.
  Browser checks used the exact HTML bytes via a read-only localhost preview.
  This does not establish direct file behavior on the actual school Mac.
- Direct opening from Chrome and browser storage under managed-device rules
  still need the user's device test. No browser policies were changed.
- Internet access to game assets and public music services is still required.
  This is not a full offline game archive or a guarantee of school-filter access.
- Word-timing behavior was covered by fixtures and existing shared clock logic;
  audible alignment and complete gameplay coverage were not established.
- Background tab-title refreshes remain subject to browser/OS throttling.
- No credentials, account cookies, local browser profiles, server keys or private
  history exports were included. Requests use only fixed public read services.
