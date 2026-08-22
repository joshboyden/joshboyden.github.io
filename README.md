# Small Apps

A handful of small, single-purpose web apps. Each one is a self-contained
HTML file in its own folder: no build step, no dependencies, no network
calls, and nothing leaves the device. Served as static files from GitHub
Pages.

| App | Folder | What it is |
| --- | --- | --- |
| [Swingtime](swingtime/) | `swingtime/` | Kettlebell circuit timer — 15 exercises, 40s on / 20s off, editable weights. |
| [Silver Falls](silverfalls/) | `silverfalls/` | Nine-week training tracker for the Silver Falls trail half marathon. |

The root `index.html` is a launcher listing them.

## Adding an app

1. Create a folder with an `index.html` that stands on its own.
2. Add an entry to the `APPS` array in the root `index.html`.
3. Add a row to the table above.

## Conventions

These are shared by habit rather than enforced by tooling, but they are what
make the apps feel like one family:

- Vanilla HTML, CSS and JS in a single file. No frameworks, no CDN requests.
- Dark theme, mobile-first, 44px minimum tap targets, safe-area insets
  respected, system font stack.
- `apple-mobile-web-app` meta tags so the app behaves when added to an iOS
  home screen, plus a `180×180` touch icon and a `32×32` favicon.
- State, where there is any, lives in `localStorage` under one key.
- All date math on locally-parsed dates — never `new Date("YYYY-MM-DD")`,
  which parses as UTC and shifts the day.

Silver Falls additionally ships a service worker and a web manifest, so it
works with no signal at all. Swingtime relies on the browser cache.
