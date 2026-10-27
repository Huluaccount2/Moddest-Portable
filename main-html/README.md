# Moddest Main HTML 0.1.3

Download `Moddest.html` and open it in Chrome. This is the main Moddest frontend in one file, not an iframe or the Lite design. Internet access is still needed for games, music, lyrics, chat and other online services.

## Username-only visits

Each time the file opens, choose a username to join as a temporary guest. There is no password, website sign-in, account linking or approval page. You can also browse games and music without entering chat.

Guest sessions have their own IDs and profiles, expire after 12 hours, and are kept only in the open file's memory. Closing or reloading the file starts a new visit. Choosing the same name again does not recover an old profile, messages or conversations. Sent messages remain in chat history. Existing registered names and reserved staff names cannot be claimed by guests.

Game saves and the personal music library remain local to this browser; they do not reset when you choose a different guest name. A non-authorizing anonymous browser identifier may persist to enforce guest browser bans. It is not a login token. Clearing browser storage can remove local progress and that identifier.

Regular website accounts and owner tools remain protected. The HTML guest mode does not unlock owner Spotify controls, owner-only AI, cloud-browser reservations, moderation, or somebody else's private data. Use the main website for those account-only tools. Main-site sign-in has not been removed. Guest chat messages and uploads are rate-limited; guest uploads have additional daily limits.

## Games and music

- One press of More games reveals the entire 218-game library. Filtering or sorting does not collapse it again.
- One shared header and expanded live-listening widget across bundled pages.
- Music-page live tab lyrics continue when no personal track is selected; personal playback uses its own lyrics.
- Music includes word-synced lyrics, albums, artist profiles, queues and the persistent mini-player.
- Public feeds and games prefer the same Paid1 route as Lite, while music prefers the HTTPS Worker. Known endpoints can be used as fallbacks; game assets and audio follow the successful endpoint.
- Guest entry, signed chat/profile requests and private sockets use HTTPS/WSS only. HTTP mirrors carry anonymous public reads, never session credentials. Rate-limit responses are not retried across mirrors.

Collections and third-party players retain their existing online restrictions. This is not an offline game archive or a copy of the backend. Managed-browser filtering and background throttling can still affect it.

## Verification

Automated checks cover one-click full-library expansion, filters remaining expanded, username entry without passwords, local game/music storage, shared headers, live and personal tab lyrics, isolated guest IDs, expiry, revocation, browser bans, registered-name protection, owner-tool restrictions, signed request replay protection, secure CORS and endpoint fallback.

The live browser preview joined chat as a temporary guest, connected its socket, revealed all 218 games with one click, and ended the visit successfully. The actual downloaded file still needs testing on the school Mac. No production chat message was posted during verification.

Build in the existing project workspace with `node build.mjs`. No server secrets or user databases are included in the HTML. Older 0.1.0-0.1.2 files used account linking; this version does not.

