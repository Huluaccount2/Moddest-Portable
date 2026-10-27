# Moddest Main HTML

Version 0.1.2 adds one persistent navigation header and the same expanded live-listening widget across every bundled page. The widget retains its cover, centered lyrics, progress bar and source label during navigation. Music no longer claims the tab title when no personal track is selected; live lyrics continue there, while a selected personal track uses its own audio-clock lyrics. The shared header is measured so the music and chat workspaces fit the remaining viewport height.

Version 0.1.1 restores Lite's connection routing: public feeds and games prefer Paid1, while music prefers the HTTPS Worker service. Public requests can fall back to the other known endpoints if one is unreachable. Game asset paths and audio URLs follow the service that actually succeeded. HTTP mirrors carry anonymous data only; account linking, signed requests, and private sockets use HTTPS/WSS exclusively. Rate-limit responses are not retried across mirrors.

This is the current main Moddest frontend packaged as one downloaded HTML file, not the Lite interface or a Daki mirror. Download `Moddest.html` using GitHub's Download raw file button, then open it in Chrome.

Included: the real game library with 218 embedded thumbnails, public live listening and recent history, the personal music player with word-synced lyrics and mini-player, community chat, AI interface, cloud-browser reservations, Spotify remote interface, and the existing Movies & TV view. Collections open their main-site links separately. Games, media, and other online services still require the main Moddest backend; this is not an offline game archive or an embedded copy of the server.

## Account linking

1. In the downloaded file, choose Sign in, then Start account linking.
2. Open the provided `https://moddest.uk/portable/connect` approval page.
3. Sign in on the main site if necessary. Check that the displayed code matches the file and approve it.
4. Return to the file. Its chat, library and game-save requests now use the linked account.

The file never receives your website password or login cookies. It creates a non-exportable P-256 signing key saved in IndexedDB. Requests include short-lived, one-use signed proofs. A separate server session is encrypted at rest, limited to approved features, and expires after 30 days. Remove a link from the file or the main site's linked-files page. Unlinking does not end your normal website session.

Password changes, account deletion, moderation, new Spotify authorization, and browser-profile reset must be done on the main site. Account linking requires access to the main site for approval. Clearing browser storage or browser policies that prevent key storage may require relinking. Never approve a code from an untrusted file.

## Verification

Type checking and the production site build pass. Six security/integration tests cover the real chat service, session isolation, library saving, CSRF rejection, signature binding, replay rejection, scope restrictions, credential-free CORS, one-use socket tickets, and revocation.

Browser preview checks: all 218 thumbnail records are embedded; the original games and music interfaces render; 2048 launches and saves locally; personal audio plays; the word-synced lyrics popup opens; the mini-player survives navigation; the linking key persists across reload; a pending live link can be revoked. The live approval page and CORS preflight return the expected responses.

The actual downloaded file has not been tested on the school Mac. Managed-browser policies and background-tab throttling can still affect it. No live owner-account approval was performed during these tests. Cloud-browser availability and third-party collection/player restrictions are unchanged.

Build: `node build.mjs` from this project workspace. Backend account-linking source lives in the main site's `lib/school-chat/portable.ts`; no server secrets or user data are included in this download.

