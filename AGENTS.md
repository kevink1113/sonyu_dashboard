# AGENTS.md

## Cursor Cloud specific instructions

This repository is a single-page static web app: `index.html` plus the `font/`
directory. There is no build system, package manager, dependencies, lint, or
automated tests.

- **What it is:** A German public-transit departure monitor
  ("S Plänterwald – Abfahrtsmonitor"). All logic (HTML/CSS/JS) lives inline in
  `index.html`. It fetches live data at runtime from public HTTP APIs:
  the BVG REST API (`https://v6.bvg.transport.rest`) for stops/departures and
  Google Translate (`translate.googleapis.com`) for on-demand destination
  translation. No API keys are required.
- **Run it (dev):** Serve the repo root over HTTP and open `index.html`, e.g.
  `python3 -m http.server 8000` then browse to
  `http://localhost:8000/index.html`. A static HTTP server is required (not
  `file://`) so the `@font-face` files load and `fetch()` works.
- **No install step:** There is nothing to install; `python3` (or any static
  file server) is all that is needed.
- **Lint / test / build:** None exist in this repo. Do not fabricate them.
- **Gotcha — "Keine Abfahrten" is not an error:** The default station
  "S Plänterwald" often legitimately has no departures during off-peak times, so
  the app shows "Keine Abfahrten" (no departures) with a successful HTTP 200 API
  response. To verify live data rendering, use the station picker (click the
  station name at the top) and switch to a busy station such as
  "S+U Alexanderplatz Bhf".
- **Network:** The app depends on outbound access to the two external APIs
  above; verify egress if departures never load.
