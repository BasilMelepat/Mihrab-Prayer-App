# Mihrab – prayer companion

A single-file, offline-capable prayer companion (prayer times, Qibla, calendar, guides, reminders) in English, Malayalam and Arabic. Installable as a PWA.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Service worker (offline shell, update flow) |
| `manifest.webmanifest` | Install metadata, home-screen shortcuts |
| `icons/` | App icons (192, 512, maskable, Apple touch, favicon) |
| `favicon.ico` | Browser tab icon |
| `vercel.json` | Headers (service worker, manifest, caching) |

## Deploy

1. Push this folder to a GitHub repository.
2. In Vercel: **Add New → Project → Import** the repo.
3. Framework Preset: **Other**. Leave Build Command and Output Directory empty. Deploy.

Every push to `main` redeploys automatically.

## Releasing an update

Whenever you change `index.html`, bump `CACHE_VERSION` in `sw.js` (for example `mihrab-v2`).
Installed copies will then show "A new version is ready" and update on tap.

## Notes

- Location, notifications and the service worker need HTTPS. Vercel provides this.
- User data is stored in the browser (`localStorage`, key `mihrab-v1`); nothing is sent to a server.
- Fonts load from Google Fonts and are cached after first use.
