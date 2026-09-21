# Ramzan Calendar - 2027

Ramzan Calendar - 2027 is a location-aware prayer calendar for the expected 2027 Ramadan period. It helps users follow daily Suhoor and Iftar times, view local prayer times, read a daily dua, and install the calendar as an offline-capable app.

## What the app does

- Detects the user’s location, with an option to search for a city manually.
- Selects an appropriate prayer calculation method for the detected country.
- Shows Suhoor and Iftar times for all 30 expected days of Ramadan.
- Counts down to the next Suhoor or Iftar event.
- Displays Fajr, Sunrise, Dhuhr, Asr, Maghrib, and Isha times.
- Presents a daily dua in Arabic with an English meaning and reference.
- Shows a dedicated “Eid Mubarak” fireworks experience on the expected Eid date.
- Can be installed as a progressive web app (PWA).
- Keeps the calendar, daily duas, icons, and fallback schedule available offline.

## 2027 dates

The calendar uses **8 February through 9 March 2027** as the expected 30-day Ramadan period. The dedicated Eid experience appears on **10 March 2027**.

Islamic dates depend on local moon sighting and may vary by one day. Users should confirm the beginning and end of Ramadan with their local mosque or recognised religious authority.

## Prayer times and location

The app requests device location only when needed to calculate local prayer times. Users can decline location access and search for a city instead.

Location names are obtained from OpenStreetMap’s Nominatim service. Prayer times are obtained from the Aladhan prayer-time API. The calculation method is selected according to the user’s country, with methods such as Karachi, ISNA, Muslim World League, Umm Al-Qura, Moonsighting Committee, and other regional standards.

If location detection or the prayer-time service is unavailable, the app uses a built-in Chigwell, United Kingdom schedule so the interface remains functional. Prayer times can differ between calculation authorities and local mosques, so the local mosque timetable should take priority.

## Daily duas

The app contains 30 curated duas. Each card includes:

- Arabic text
- English meaning
- Quran or hadith reference where applicable

During Ramadan, each dua maps directly to its Ramadan day. Outside Ramadan, the collection rotates by local calendar date so a dua remains visible every day.

## Eid experience

On the expected Eid date, the normal calendar interface is replaced with an “Eid Mubarak” greeting and animated fireworks. The animation is disabled automatically when the user has enabled reduced-motion preferences on their device.

## Installing the app

On supported browsers, an **Install app** button appears when the browser confirms that the PWA is installable. Once installed, the calendar opens in a standalone app window.

On iPhone or iPad, installation is available through Safari’s **Share → Add to Home Screen** action.

## Offline behaviour

The service worker stores the local app shell, including the calendar page, manifest, and app icons. The built-in timetable and daily duas remain available without a network connection. Live location lookup and updated prayer-time requests require connectivity; when those services are unavailable, the app uses its fallback data.

## Privacy

Location coordinates are used to request the relevant city name and prayer times. The selected location and prayer-time response are cached in the browser’s local storage to reduce repeated requests. The app does not include its own user accounts or database.

The page includes Google AdSense, which may process data according to Google’s policies. OpenStreetMap Nominatim and Aladhan receive the information required to provide their respective location and prayer-time services.

## Project structure

| File | Purpose |
| --- | --- |
| `index.html` | Interface, calendar data, daily duas, location handling, prayer calculations, countdowns, and Eid experience |
| `manifest.json` | PWA name, appearance, install scope, and icon declarations |
| `sw.js` | Offline app-shell caching and network fallback behaviour |
| `icon-source.svg` | Editable source artwork for the app icon |
| `icon-192.png` | 192px install icon |
| `icon-512.png` | 512px install and maskable icon |
| `ads.txt` | Advertising platform declaration |

## Maintenance notes

The year, expected Ramadan dates, Eid date, API calendar months, fallback timetable, cache names, page metadata, and manifest metadata are year-specific. They should be reviewed together before preparing the calendar for another Ramadan.

When changing local assets or offline behaviour, update the cache name in `sw.js` so installed copies receive the latest files. If the app icons change, regenerate both required PNG sizes from the source artwork.

## Technology

The app is a lightweight static site built with HTML, CSS, and browser JavaScript. It uses browser geolocation, local storage, a web app manifest, Canvas fireworks, and a service worker. It can be deployed directly on Netlify without a separate application server.
