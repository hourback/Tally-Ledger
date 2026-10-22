# Tally Ledger

An offline-first phone app for tracking daily behaviors, mostly yes/no, tagged positive (build) or negative (avoid).

- **Fully offline.** It's a static PWA. A service worker caches the app, and all data stays in the browser's storage on your device.
- **Your raw data.** Export to CSV (one row per day per behavior) or a full JSON backup. Import either format, or any CSV with `date` and `behavior` columns.
- **Reporting.** Daily balance chart, per-behavior rates with change from the previous period, streaks, a 26-week calendar and a weekday breakdown.

## Install on your phone

1. Open the GitHub Pages URL in Safari (iOS) or Chrome (Android).
2. Choose Share → Add to Home Screen (iOS), or Install app (Android).
3. Open it once while online so it caches. After that it works with no network.

Export a JSON backup from the Data tab now and then. Browser storage is tied to the device, and clearing site data erases it.

## Data format

CSV columns: `date,behavior,polarity,value,logged_at,behavior_id`

JSON backup: `{ app, version, exported_at, behaviors: [{id,name,polarity,created,archived}], entries: [{id,b,d,t}] }`, where `b` is the behavior id, `d` is the local date (YYYY-MM-DD) and `t` is the time it was logged.

## Development

No build step. Serve the folder over HTTP (`python3 -m http.server`) and open it. When you change cached files, bump `CACHE` in `sw.js` so installed copies update.
