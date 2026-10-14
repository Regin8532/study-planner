# Banking Study Hub

A simple, responsive, offline-first banking exam productivity tracker built with HTML, CSS, and vanilla JavaScript. No backend, login, paid API, or build step is required.

## Features

- Personal dashboard, daily tasks, timer, streak calendar, mock tests, revision list, reports, and settings.
- Focus timer with 25-minute, 50-minute, custom, and break sessions.
- Productive-day and streak calculations from recorded study minutes.
- Custom subjects, editable tasks, mock-test history, revision due dates.
- Weekly/monthly summaries, subject time distribution, CSV export, JSON backup/restore.
- Light/dark mode, mobile navigation, and a basic installable PWA/offline cache.

## Run locally

For the full PWA experience, serve the folder over HTTP rather than opening `index.html` directly.

Python:
```bash
python -m http.server 8000
```
Then open `http://localhost:8000`.

## Deploy on GitHub Pages

1. Create a GitHub repository, for example `banking-study-hub`.
2. Upload `index.html`, `styles.css`, `app.js`, `manifest.webmanifest`, `icon.svg`, and `sw.js` to the repository root. Include this README.
3. Open repository **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then Save.
6. Wait for the deployment workflow to finish. Open the Pages URL shown by GitHub.
7. Test on the published URL. The service worker registers only on HTTPS/localhost. Relative asset paths are used so the app works in a repository subpath.

## Daily use

- Add tasks and set planned time.
- Use the timer to record focus sessions.
- A day qualifies as productive once saved focus-session minutes plus actual minutes from completed tasks reach the configured minimum streak goal.
- Completed tasks with 0 actual minutes add no time.
- Avoid logging the same minutes in a timer session and a task's actual-time field; the app cannot infer duplicates.
- Mock tests and revision topics are manually entered.

## Backup and privacy

- **Settings → JSON backup** downloads a complete JSON snapshot.
- **Settings → Restore backup** imports a snapshot and replaces the current local data.
- **Export CSV** exports task, session, mock test, and revision records.
- Data is stored in `localStorage` in the current browser profile. It is device- and browser-specific. Clearing browser storage can erase data.
- There is no server, account, cross-device synchronization, automatic sharing, or shared leaderboard. Aspirants on different devices share progress summaries manually.
- The app does not upload study data. The first-load Google Fonts import is optional styling; system sans-serif fallbacks are included.

## Known limitations

- This is a static personal tracker, not a synchronized group platform.
- The browser must be open for the countdown timer to tick; closing/suspending the browser may interrupt the timer.
- Streaks are calculated from the browser's local calendar date. Avoid changing your device date/time to manipulate records.
- The timer saves when the user finishes a session or the countdown completes. Resetting a session discards its unsaved elapsed time.
- The reports are based only on records entered in the app. They do not import mock test scores automatically.
- For best offline behavior, open the app online once after deployment so the service worker can cache core files.

## Feature test checklist

- [ ] Add, edit, complete, and delete tasks; refresh and verify persistence.
- [ ] Try all timer modes, pause/resume, reset, finish early, and allow a session to complete.
- [ ] Record enough minutes to meet the minimum streak goal; verify today's calendar cell turns green.
- [ ] Check current/longest streak around missed days, month boundaries, and year boundaries using test records if desired.
- [ ] Add/edit/delete mock tests and verify accuracy and totals.
- [ ] Add a revision topic, mark it revised, and test the overdue filter.
- [ ] Switch weekly/monthly reports and export CSV.
- [ ] Download a JSON backup, clear data, restore the backup, and verify records.
- [ ] Test light/dark modes and small mobile widths.
- [ ] Test GitHub Pages URL under the repository subpath and verify offline reload after the first successful visit.
