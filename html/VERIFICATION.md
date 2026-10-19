# Verification - 2026-10-19

- Single HTML build passed; approximately 8.3 MB including fonts, images, code,
  styles and third-party license notices. No external application script or CSS
  files and no meta-refresh redirect.
- Four direct-client tests passed: credential-free fixed public routes, blocked
  account/write/query requests, external-request behavior and embedded assets.
- Four public-gateway tests passed: exact read allowlist, method checks,
  filtering private response headers, error handling, HEAD and Retry-After.
- Four existing local-server regression tests passed; the original portable
  launcher and packages were not replaced by this HTML build.
- Production Vinext build and Worker deployment passed. Worker version:
  60a4b8c4-d9ee-436d-9ce3-e37e5b578aca.
- Live API requests with Origin: null returned JSON and Access-Control-Allow-Origin:
  * for playback, Dihlyrics, history, statistics, weather and icon metadata.
  No Set-Cookie was returned; an account-like unknown route returned 404.
- Browser preview used the exact HTML bytes at http://127.0.0.1:19194/ solely for
  verification. Home/Niche hash navigation, live counters, history and release
  artwork worked. Embedded thumbnails rendered without broken images. No
  horizontal overflow at 1280px or 390px widths. No console errors on the final
  Niche page.

Not verified or not implemented:

- Direct file:// opening on actual Mac hardware was not tested. The browser
  tool's local-file policy prevented that earlier; the localhost preview is not
  proof of identical file:// behavior or school-device access.
- Active music/word timing alignment was not tested because playback was paused
  or offline. The existing timing renderer is bundled, not newly validated here.
- In-file sign-in, chat, AI, uploads, browser reservations and Listen Live are
  not implemented. Their links open the normal hosted secure pages.
- The YouTube embed returned configuration Error 153 in preview. External
  video/profile links remain available; embedded media may require the hosted
  page or an allowed referrer and is not promised to work from a local file.
- Account authentication and cross-origin cookie protections remain unchanged.

