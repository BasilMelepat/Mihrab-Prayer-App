[README.md](https://github.com/user-attachments/files/34005424/README.md)
<div align="center">

# Mihrab

**A calm, installable prayer companion: prayer times, Qibla, reminders, a prayer tracker and a step-by-step guide.**

Version 1.41.2 · build 2026.10.22.91

[Live app](https://mihrab-prayer-app.vercel.app/)

</div>

---

## Overview

Mihrab is a single-page web app (PWA) for daily prayer. It works offline once installed, keeps your data on your own device, and is available in **English, Malayalam and Arabic** (with full right-to-left support).

It has no account, no backend and no build step. The whole app lives in one `index.html` file.

## Features

### Home
- A live "sky" semicircle that follows the day, with the prayer name in Arabic inside it: **Now: Asr** during a prayer and **Next: Dhuhr** between sunrise and Dhuhr.
- A countdown to the next prayer in hours, minutes and seconds.
- An **iqama counter** under the Arabic name, counting down to the iqama time you set. The text only shifts while the counter is showing.
- Quick chips for your **location**, the **Qibla** direction and the **nearest masjid** (opens Google Maps; for female profiles the search is for masjids with a women's prayer area).
- Messages that follow the time of day and your progress, including prompts when a prayer time has passed, a prayer was missed, or prayers were excused after rest days.
- A footer with the logo, version, build and credit.
- The semicircle switches to a quieter look (soft dots instead of checkmarks) when the tracker is hidden or rest days are on.

### Fridays
- **Male profiles:** Dhuhr is shown as **Jumu'ah** everywhere (home, lists, widgets, reminders, past Fridays in the tracker).
- **Female profiles:** Friday stays **Dhuhr**, with an **Attended Jumu'ah** option in the prayer sheet and in the day sheet of past Fridays. It counts as prayed and appears as a stat in the prayer tracker.
- The greeting becomes "Jumu'ah Mubarak" from Thursday Maghrib to Friday Maghrib.

### Prayer times
- Calculation methods including Muslim World League, with a **Shafi'i / Hanafi Asr** setting.
- Per-prayer minute adjustments to match your local mosque timetable.
- **Iqama times**, adjustable per prayer (minutes after the adhan, or off).
- Built-in cities with a custom-location option.

### Prayer tracker
- Mark each prayer as **on time**, **late** or **missed**, with extras for Jama'ah and first row.
- Five-part rings per day (late shown in red; missed is not drawn), a streak card and a calendar view.
- **Rest days** for female profiles, with a gentle prompt to pause tracking. When rest days end partway through the day, prayers whose time already passed are marked **Not required**: their checkbox is hidden and the messages adjust.
- Can be **hidden completely** from Settings → Profile & data. The home screen, the desktop layout and the messages adapt, and your tracking data is kept.

### Reminders
- Per-prayer reminders, with a **How early** setting directly under them.
- **Tahajjud** reminder in its own section: start of the last third of the night, 2 hours / 1 hour / 30 minutes before Fajr, or a custom time.
- **Jumu'ah reminders** (Fridays only): Surah al-Kahf, trimming nails and tidying up, ghusl and perfume, heading to the mosque early, salawat and dua, plus a short note on preparing for Friday.
- Lock-screen preview that follows the app theme.

### Guide
Step-by-step guides in three languages, organised into categories:

- **Daily:** the five prayers
- **Purification:** wudu (with the prayer after it), ghusl, tayammum, wiping over socks, what breaks wudu and prayer
- **Sunnah:** rawatib, Taraweeh (11 rak'ahs), Witr, Tahajjud and more
- **Special:** Jumu'ah, Eid, janazah, jama'ah, adhan and iqamah, missed prayers (qada), prayer when unwell
- **Occasion:** istikhara, tawbah, shukr, forgetful prostration (sahw), prostration of recitation
- **Travel:** shortening (qasr), combining, praying in a vehicle

### Also
- **Calendar** with Hijri and Gregorian dates.
- **Qibla** compass.
- **Widgets preview:** 4 × 1, 2 × 2 (next prayer), 4 × 2, 4 × 3 (home, with sun and moon on the arc) and 2 × 2 (clock with sun and moon around the ring).
- **Themes:** night and day.
- Animated toggle switches (respects "reduce motion").
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

The guides are written following the Shafi'i approach, except the travel prayer (Qasr), which follows the Hanafi view cited below, and Taraweeh, which is given as 11 rak'ahs following the report from the Prophet ﷺ. Each guide is marked **"Pending scholar review"** and should be checked by a qualified scholar before wide release. Where scholars differ, the app says so and advises following a scholar you trust.

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
