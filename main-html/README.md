# Moddest Main HTML 0.1.12

When a game is open, the existing music player docks to the right of the navigation on wide screens; narrower screens use a short second row. Closing the game restores the regular player. The header's full-screen lyric-view button has been removed to avoid confusing it with the game's fullscreen control. Game fullscreen and playback state are preserved.

## HTTP-only downloaded client

Embedded requests now use `http://paid1.daki.cc:4144` and its `ws://` endpoint only, including signed guest chat/AI/VM reservation requests, music/audio, artwork, viewer counts, update checks and lyric feeds. A Content Security Policy blocks direct embedded HTTPS/WSS loads rather than silently falling back. This affects only the downloaded HTML, not the main website. The Daki relay contacts the HTTPS backend server-side and retains scoped signatures, replay protection, normal bans and rate limits. Private signing keys remain on the device, but HTTP traffic is NOT encrypted: prompts, messages, media and session traffic can be read or altered in transit. Do not share sensitive information. Third-party games/players with dependencies that cannot use the relay may not work; external links (including GitHub and provider-hosted Firefox) open separately and are not HTTP-converted. VM reservation availability does not prove the remote browser gateway is online or compatible.

Deploy the matching `outputs/daki-paid1/moddest-paid1.mjs` relay before publishing this HTML. This release must not be advertised as verified on the school Mac; that device has not been tested here.

The file checks the public GitHub `main-html/latest.json` manifest through the HTTP Daki relay on opening, every 15 minutes while visible, and when focus/connectivity returns (at most once per minute). A confirmed newer version shows a dismissible banner linking to this GitHub folder. Offline or blocked checks are silent and never prevent use. No account or credentials are sent for version checks. Existing 0.1.9 and older downloads must be replaced once to gain this feature. Future releases must publish the built `Moddest.html` before publishing the matching `latest.json`; both are generated from `src/release.json`.

The shared library now contains 974 entries: the previous 218 plus 756 unique GN Math additions. The GN snapshot contains 849 games; 93 entries map to existing games or a duplicate title within GN itself. All new covers are embedded in this file. Select GN Math in the category controls to find the additions.

All 756 new entry documents and covers were checked, along with 1,464 declared startup-resource requests. Sixty-five entries still reference broken/missing startup resources and remain listed as Awaiting repair, with launch disabled. Passing the file checks does not prove that a game reaches gameplay; full browser verification remains incomplete. The per-game status is in the live `/games/gn-validation.json` report and the local `outputs/gn-math-import` reports. Existing game IDs and saves were not replaced.

This repair fixes Unity loaders deriving asset URLs from about:srcdoc, bootstraps catalog-game workers through scoped blobs while retaining the opaque sandbox, and keeps dynamically requested game paths on their selected endpoint. Optional service-worker registration stays disabled. Lyric lookups retain their 65-second request budget. Connection status tests the HTTP relay without sending session credentials. It cannot override network restrictions.

Spotlight rotates three games every 30 minutes, using the same selection as the main site. Returning to a backgrounded page refreshes the selection without interrupting a running game.

Version 0.1.17 removes Collections from the HTML navigation and page, leaving the remaining links and compact music player to flow into the freed space. The main website's Collections UI is unchanged. Game selection now reports its title through anonymous presence, debounced on open/switch/close and cleared on navigation away. The viewer dropdown shows `Games · title` for updated HTML clients. Older downloads still report only Niche. The shared presence backend retains the validated game name while continuing to strip cookies, discard arbitrary page URLs, deduplicate browser tabs, and avoid total-view registration for files. No Daki patch is needed for this release; its existing presence relay is unchanged.

The file retains the 0.1.16 opt-in movie/episode captions, language and release-version selection, and no-background/black-background styles below the native player. The caption background preference is saved locally. Provider WebVTT tracks are used directly; plain media-time TTML is converted server-side with XML resources and unsupported timing rejected. Tracks are relayed through Paid1 HTTP and cached briefly in bounded server memory, not movie storage. Subtitles depend on provider availability and download quotas. No subtitle download occurs merely from starting a movie.

The file retains the Firefox removal and fixes movie posters through the existing IMDb artwork relay. Movies and TV episodes use the native player and Paid1's automatic source lookup. The resolver uses the provider's public source endpoints, tries alternate results, rejects short trailer-only movie results, and preserves the owner's verified pilot source. Availability still depends on upstream coverage; catalog listings do not guarantee playback. Encrypted and byte-range sources are unsupported. Video segments are fetched only when the player requests them, with bounded in-flight memory and no movie files saved to disk. The player uses a normal short playback buffer, not the old 30-minute rolling cache. Playback position is saved locally. Video requests use Daki HTTP without a separate Cloudflare hop. The main website is unchanged. School Mac playback has not been verified from this PC.

Download `Moddest.html` and open it in Chrome. This is the main Moddest frontend in one file, not an iframe or the Lite design. Internet access is still needed for games, music, lyrics, chat and other online services.

## Username-only visits

Only chat asks for a username. Games, music, AI and browser reservations do not require a username, password, website sign-in, account linking or approval page. The file opens directly into the game library.

Guest sessions have their own IDs and profiles, expire after 12 hours, and are kept only in the open file's memory. Closing or reloading the file starts a new visit. Choosing the same name again does not recover an old profile, messages or conversations. Sent messages remain in chat history. Existing registered names and reserved staff names cannot be claimed by guests.

Game saves and the personal music library remain local to this browser; they do not reset when you choose a different guest name. A non-authorizing anonymous browser identifier may persist to enforce guest browser bans. It is not a login token. Clearing browser storage can remove local progress and that identifier.

AI and reservations use an automatically created, scoped anonymous device session, separate from the chat username. Its non-exportable signing key is saved in this file browser's IndexedDB when available, for up to seven days, so reservations can survive refresh. If browser storage is disabled, anonymous access lasts only for the open visit. Clearing storage can lose reservation access. Anonymous browser sessions are always private, and keep normal reservation hours, one-booking-per-day limits, server availability and owner protections. Anonymous AI is limited to 15 generations per browser per day, with a 120-generation shared daily cap. Real accounts, moderation, owner Spotify controls and other users' data remain protected. Main-site sign-in has not been removed.

## Games and music

- One press of More games reveals the full 974-entry library. Filtering or sorting does not collapse it again. The previously removed 150-game batch and ROM player remain removed; the GN Math import is a separate catalog addition.
- Generic cross-origin script diagnostics and the recoverable Unity downloadAsmCode duplicate-job warning remain in browser diagnostics without creating false failure banners. Other runtime errors remain visible.
- Fullscreen uses native browser fullscreen where available, with an in-page fallback, scroll locking, a visible exit control and Escape handling. The game iframe stays mounted when entering/exiting, preserving the running game.
- One shared header and expanded live-listening widget across bundled pages.
- The top player retracts while scrolling, using the main site's compact layout.
- Album covers become embedded tab icons rather than remote favicon links. Chat unread badges still take priority.
- Visible HTML visits send anonymous presence heartbeats. Tabs in the same file browser share an anonymous viewer ID; hidden/closed tabs leave, and missed leaves expire after 75 seconds. Failed reads show unavailable after 60 seconds rather than freezing an old count.
- Music-page live tab lyrics continue when no personal track is selected; personal playback uses its own lyrics.
- Music includes word-synced lyrics, albums, artist profiles, queues and the persistent mini-player.
- Public feeds, games, music, guest entry, signed chat/profile requests and private sockets use the HTTP/WS Paid1 relay. There is no automatic HTTPS/WSS fallback in the downloaded file. Rate-limit responses are not retried.
- Scoped signatures and replay checks remain enabled; HTTP transport does not provide confidentiality or protection against an active network attacker.

Collections and third-party players retain their existing online restrictions. This is not an offline game archive or a copy of the backend. Managed-browser filtering and background throttling can still affect it.

## Verification

Automated checks cover one-click full-library expansion, filters remaining expanded, username entry without passwords, local game/music storage, shared headers, live and personal tab lyrics, isolated guest IDs, expiry, revocation, browser bans, registered-name protection, owner-tool restrictions, signed request replay protection, secure CORS and endpoint fallback.

The live browser preview verified anonymous reservation availability and AI readiness without a username. The existing username chat flow, album icons, shared player and 218-game library remain covered by tests. The actual downloaded file still needs testing on the school Mac. No production chat message was posted during verification.

Build in the existing project workspace with `node build.mjs`. No server secrets or user databases are included in the HTML. Older 0.1.0-0.1.2 files used account linking; this version does not.
