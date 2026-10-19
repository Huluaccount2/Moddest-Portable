# Moddest Portable Client 0.1.0 Beta

This is a local React build of the Moddest interface, not an iframe of the main
website and not a copy of the backend. It connects to the existing Moddest
services. No Spotify credentials, AI access keys, account databases, pairing
files or server environment settings are distributed.

## Open

Extract the complete ZIP first. Open `index.html` for a limited local preview.
For full online connections, install Node.js 22 or newer from https://nodejs.org/
and double-click `Start-Moddest.cmd` on Windows. On macOS/Linux run
`node server.mjs --open` in the extracted folder. Open http://127.0.0.1:19192/.
Keep the launcher running. Ctrl+C stops it. No npm install is needed to run.

The launcher binds only to 127.0.0.1. Do not expose it using port forwarding or a
public tunnel. It only relays the fixed https://moddest.uk API origin, validates
the local request origin and Host, and keeps account cookies HttpOnly. Cookies
belong to the local client, not the browser's existing Moddest login. Sign in
normally; never import cookies or paste server keys. As with any local app,
other software running as your Windows user can access its traffic/storage.

## Included

Home/music, lyric view, Niche, local accounts/sign-in interface, chat, message
editing and notifications, schedule review/OCR, Listen Live interface, browser
reservations, achievements, dynamic weather, AI interface and bundled artwork.
AI remains restricted by the live server's account permissions. The disabled
Panye game stays disabled. Dihlyrics authentication opens the online service.

Niche games are embedded from their online URLs in separate-origin sandboxed
frames, not copied or served in the same local origin as account cookies.
Some sites reject embedding or require opening the provided online link.
Third-party games, videos, radio, live audio peers, AI, lyric search, account
storage and cloud-browser hosts all still require online services. Browser
capture and desktop notifications remain subject to browser permissions.
Closing the launcher does not stop the online services. A blocked or offline
backend cannot be repaired or bypassed by this package.

## Build from source

The source archive contains a snapshot of only the frontend modules used by the
client, plus permitted frontend assets. Run `npm ci` then `npm run build`.
Maintainers can refresh the snapshot with `node build.mjs PATH_TO_MODDEST_SITE`.
Generated output is in `release/Moddest`. Do not publish `.build`, `.env`, API
keys, browser profiles, account exports or the original backend repository.
Third-party licenses are in `licenses` and `app.js.LEGAL.txt` when emitted.

This beta is not a promise that every hosted-site feature works locally. See
VERIFICATION.md for what was actually tested and remaining limitations.

