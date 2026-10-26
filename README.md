[README.md](https://github.com/user-attachments/files/33947911/README.md)
<div align="center">

# Mihrab

**A calm, installable prayer companion: prayer times, Qibla, reminders, a prayer tracker and a step-by-step guide.**

Version 1.40.9 · build 2026.10.22.87

[Live app](https://mihrab-prayer-app.vercel.app/)

</div>

---

## Overview

Mihrab is a single-page web app (PWA) for daily prayer. It works offline once installed, keeps your data on your own device, and is available in **English, Malayalam and Arabic** (with full right-to-left support).

It has no account, no backend and no build step. The whole app lives in one `index.html` file.

## Features

### Home
- A live "sky" semicircle that follows the day: **Now: Asr** during a prayer and **Next: Dhuhr** between sunrise and Dhuhr, with the Arabic name inside it.
- A countdown to the next prayer in hours, minutes and seconds.
- An **iqama counter** under the Arabic name, counting down to the iqama time you set.
- Quick chips for your **location**, the **Qibla** direction and the **nearest masjid** (opens Google Maps; for female profiles it searches for masjids with a women's prayer area).
- Messages and greetings that change with the time of day and your progress.
- **Fridays:** Dhuhr is shown as **Jumu'ah** everywhere, and the greeting becomes "Jumu'ah Mubarak" from Thursday Maghrib to Friday Maghrib.

### Prayer times
- Calculation methods including Muslim World League, with a **Shafi'i / Hanafi Asr** setting.
- Per-prayer minute adjustments to match your local mosque timetable.
- **Iqama times**, adjustable per prayer (minutes after the adhan).
- Built-in cities with a custom-location option.

### Prayer tracker
- Mark each prayer as **on time**, **late** or **missed**.
- Five-part rings per day, a streak card and a calendar view.
- **Rest days** for female profiles, with a gentle prompt to pause tracking.
- Can be **hidden completely** from Settings → Profile & data. Your tracking data is kept.

### Reminders
- Per-prayer reminders with a choice of how early to be reminded.
- **Tahajjud** reminder: start of the last third of the night, 2 hours / 1 hour / 30 minutes before Fajr, or a custom time.
- **Jumu'ah reminders** (Fridays only): Surah al-Kahf, trimming nails and tidying up, ghusl and perfume, heading to the mosque early, salawat and dua.
- Lock-screen preview that follows the app theme.

### Guide
Step-by-step guides in three languages, organised into categories:

- **Daily:** the five prayers
- **Purification:** wudu, ghusl, tayammum, wiping over socks, what breaks wudu and prayer
- **Sunnah:** rawatib, Taraweeh, Witr, Tahajjud and more
- **Special:** Jumu'ah, Eid, janazah, jama'ah, adhan and iqamah, missed prayers (qada), prayer when unwell
- **Occasion:** istikhara, tawbah, shukr, forgetful prostration (sahw), prostration of recitation
- **Travel:** shortening (qasr), combining, praying in a vehicle

### Also
- **Calendar** with Hijri and Gregorian dates.
- **Qibla** compass.
- **Widgets preview:** 4 × 1, 2 × 2 (next prayer), 4 × 2, 4 × 3 (home) and 2 × 2 (clock with sun and moon).
- **Themes:** night and day.
- Installable on Android and desktop; works offline.

## Tech

| | |
|---|---|
| App | Vanilla HTML, CSS and JavaScript in a single `index.html` |
| Offline / install | Service worker (`sw.js`) and web app manifest |
| Storage | `localStorage` on the device |
| Hosting | Vercel (static), deployed from this repo |
| Fonts | Google Fonts |

Prayer times and Qibla are calculated on the device from your location. Reminders use the browser's notifications and only fire while the browser allows the app to run.

## Project structure

```
.
├── index.html              # the whole app
├── sw.js                   # service worker (offline cache and update flow)
├── manifest.webmanifest    # install metadata, icons and shortcuts
├── vercel.json             # headers for sw.js and the manifest
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── icon-maskable-512.png
    └── apple-touch-icon.png
```

## Run locally

Service workers need `http://localhost` or HTTPS, so serve the folder instead of opening the file directly:

```bash
# any static server works
npx serve .
# or
python3 -m http.server 8080
```

Then open `http://localhost:3000` (or `:8080`).

## Deploy

The repo is connected to Vercel. Push to `main` and Vercel redeploys automatically. No build command or output directory is needed.

## Releasing an update

1. Edit `index.html`.
2. Bump the version in the `APP` object near the top of the script:
   ```js
   version:"1.40.9", build:"2026.10.22.87"
   ```
3. Commit and push to `main`.

The app registers its service worker as `sw.js?v=<version>`, so every version bump makes installed apps show **"A new version is ready" → Refresh**. You don't need to edit `sw.js` for normal updates. The version and build also appear in the footer of the home screen.

## Install

- **Android (Chrome):** open the live app, then use the menu → **Install app**.
- **Desktop (Chrome / Edge):** use the install icon in the address bar.
- **iPhone / iPad (Safari):** Share → **Add to Home Screen**.

## Privacy

- No account, no analytics code and no backend.
- Your name, settings and prayer-tracking data are stored only on your device.
- The nearest-masjid button opens Google Maps in a new tab with a search near your chosen location.
- Fonts are loaded from Google Fonts.

## Religious content

The guides are written following the Shafi'i approach, except the travel prayer (Qasr), which follows the Hanafi view cited below. Each guide is marked **"Pending scholar review"** and should be checked by a qualified scholar before wide release. Where scholars differ, the app says so and advises following a scholar you trust.

If you spot something that needs correcting, please open an issue.

## References

- Prayer time calculation: [PrayTimes.org](https://praytimes.org)
- Umm al-Qura calendar: [R.H. van Gent](https://webspace.science.uu.nl/~gent0113/islam/ummalqura_introduction.htm)
- Travel prayer (Qasr): [Jibreel](https://www.jibreel.app/islamqa/hanafi-qasar-namaz-distance)
- Intention in prayer: [Prayer in Islam](https://prayerinislam.com/verbal-intention-prayer-necessary/)
- Typefaces: [Google Fonts](https://fonts.google.com)

## Credits

Design and cared by **Basil Melepat**.

## License

Add your license here (for example MIT) before sharing the code publicly.
