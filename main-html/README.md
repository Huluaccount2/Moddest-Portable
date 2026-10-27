# Moddest Main HTML 0.1.7

Spotlight rotates three games every 30 minutes, using the same selection as the main site. Returning to a backgrounded page refreshes the selection without interrupting a running game.

The browser page now offers a provider-hosted Firefox beta, running locally on the visitor's device in a separate tab without using a VM slot. The launch notice explains that Puter handles the browser and networking, including its profile-storage behavior. This is not a Moddest-hosted browser or a guaranteed private/incognito session. The self-hosted Firefox engine remains disabled because its networking relay refused access. Existing VM reservations are still available under Backup. Browser support, provider availability and network filtering still apply.

Download `Moddest.html` and open it in Chrome. This is the main Moddest frontend in one file, not an iframe or the Lite design. Internet access is still needed for games, music, lyrics, chat and other online services.

## Username-only visits

Only chat asks for a username. Games, music, AI and browser reservations do not require a username, password, website sign-in, account linking or approval page. The file opens directly into the game library.

Guest sessions have their own IDs and profiles, expire after 12 hours, and are kept only in the open file's memory. Closing or reloading the file starts a new visit. Choosing the same name again does not recover an old profile, messages or conversations. Sent messages remain in chat history. Existing registered names and reserved staff names cannot be claimed by guests.

Game saves and the personal music library remain local to this browser; they do not reset when you choose a different guest name. A non-authorizing anonymous browser identifier may persist to enforce guest browser bans. It is not a login token. Clearing browser storage can remove local progress and that identifier.

AI and reservations use an automatically created, scoped anonymous device session, separate from the chat username. Its non-exportable signing key is saved in this file browser's IndexedDB when available, for up to seven days, so reservations can survive refresh. If browser storage is disabled, anonymous access lasts only for the open visit. Clearing storage can lose reservation access. Anonymous browser sessions are always private, and keep normal reservation hours, one-booking-per-day limits, server availability and owner protections. Anonymous AI is limited to 15 generations per browser per day, with a 120-generation shared daily cap. Real accounts, moderation, owner Spotify controls and other users' data remain protected. Main-site sign-in has not been removed.

## Games and music

- One press of More games reveals the existing 218-game library. Filtering or sorting does not collapse it again. The unwanted 150-game expansion and ROM player have been removed; no replacement batch was added.
- Generic cross-origin script diagnostics and the recoverable Unity downloadAsmCode duplicate-job warning remain in browser diagnostics without creating false failure banners. Other runtime errors remain visible.
- Fullscreen uses native browser fullscreen where available, with an in-page fallback, scroll locking, a visible exit control and Escape handling. The game iframe stays mounted when entering/exiting, preserving the running game.
- One shared header and expanded live-listening widget across bundled pages.
- The top player retracts while scrolling, using the main site's compact layout.
- Album covers become embedded tab icons rather than remote favicon links. Chat unread badges still take priority.
- Visible HTML visits send anonymous presence heartbeats. Tabs in the same file browser share an anonymous viewer ID; hidden/closed tabs leave, and missed leaves expire after 75 seconds. Failed reads show unavailable after 60 seconds rather than freezing an old count.
- Music-page live tab lyrics continue when no personal track is selected; personal playback uses its own lyrics.
- Music includes word-synced lyrics, albums, artist profiles, queues and the persistent mini-player.
- Public feeds and games prefer the same Paid1 route as Lite, while music prefers the HTTPS Worker. Known endpoints can be used as fallbacks; game assets and audio follow the successful endpoint.
- Guest entry, signed chat/profile requests and private sockets use HTTPS/WSS only. HTTP mirrors carry anonymous public reads, never session credentials. Rate-limit responses are not retried across mirrors.

Collections and third-party players retain their existing online restrictions. This is not an offline game archive or a copy of the backend. Managed-browser filtering and background throttling can still affect it.

## Verification

Automated checks cover one-click full-library expansion, filters remaining expanded, username entry without passwords, local game/music storage, shared headers, live and personal tab lyrics, isolated guest IDs, expiry, revocation, browser bans, registered-name protection, owner-tool restrictions, signed request replay protection, secure CORS and endpoint fallback.

The live browser preview verified anonymous reservation availability and AI readiness without a username. The existing username chat flow, album icons, shared player and 218-game library remain covered by tests. The actual downloaded file still needs testing on the school Mac. No production chat message was posted during verification.

Build in the existing project workspace with `node build.mjs`. No server secrets or user databases are included in the HTML. Older 0.1.0-0.1.2 files used account linking; this version does not.
