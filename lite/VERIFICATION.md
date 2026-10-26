# Moddest Lite 0.3.1 Verification, 2026-10-26

## Game Loading Repair

- All 218 thumbnails are embedded: 214 optimized WebP images and four original
  ICO files. The package build fails if a thumbnail is missing; it no longer
  silently substitutes remote artwork URLs.
- Added a catalog-validated, read-only /api/portable/games/{id}/ route. It
  serves all 218 catalog entries through paid1 without restoring the disabled
  batch in Daki's main page.
- Nested HTML/JS/CSS/JSON asset paths stay on that same per-game route.
- Scoped known publisher splash assets and the copied /main.min.js SDK to the
  game root; removed missing optional Paper.io ad-loader references.
- Already-rewritten scripts stream through the HTTP mirrors using a recognized
  JavaScript MIME type, avoiding the paid1 relay's 18 MiB text rewrite limit.
- Added actionable game startup errors while retaining the opaque iframe
  sandbox and source/nonce-checked local saves.
- Fixed stream cancellation/error handling in the live Daki proxy and gateway.
  Unchanged rollback copies were saved before the patches and the backend was
  restarted. No settings, account data or allocation sizes were changed.

## Passed

- Art verification: 218 / 218 images cached and embedded.
- HTTP check: 217 / 217 in-panel game entry routes and their checked first
  startup scripts/styles passed through paid1. Skribbl.io is external.
  Transient failures during deployment were retried after service restoration.
- Eight automated Lite tests, including the new-game paid1 route and embedded
  artwork, existing music behavior, ordered pushes and tab scrolling.
- Five portable-game backend tests: known-ID/path validation, credentials
  stripping, binary integrity, scoped vendor rewriting and SDK/ad-loader fixes.
- A real HTTP stream-cancellation regression test leaves the proxy healthy.
- Penrose reached its title screen. Tetris reached its menu, started a round
  and responded to controls. Vex 8 passed the publisher splash and rendered its
  game stage. These checks go beyond a successful HTML response.
- Paid1 proxy health returned HTTP 200 after the cancellation regression check.
- Existing music UI, libraries, playlists, queue, lyrics and title scheduling
  remain bundled from Moddest as in 0.3.0.

## Limits

- HTTP startup-file checks are not complete gameplay tests of all 218 games.
- Browser tools permit HTTP/HTTPS only. The UI preview serves the exact generated
  HTML bytes through localhost; direct file use on the school Mac still needs
  a device test. No browser security policies were changed.
- Game programs/audio require working online services. Embedded thumbnails do
  not depend on any remote host, but a local file is not a fully offline archive.
- Background title updates remain subject to browser/OS throttling. Word timing
  depends on the recording's available lyric data.
