# ScholarQueue

ScholarQueue is a responsive React/Next.js prototype for digital token distribution and queue management in a college scholarship office. It is designed as a reliable end-to-end demo: students issue and look up tokens, staff operate the queue, and administrators can inspect capacity, history, and analytics.

## Run locally

```bash
pnpm install
pnpm dev
```

Open the local preview shown by Next.js. The current starter uses the existing Next.js runtime in this workspace; the UI is client-side React and can be moved behind a Vite entry point later if needed.

## Features

- Student Portal with validation, duplicate active-token protection, category and counter selection, lookup, and live estimates.
- Live Display with now-serving, next-in-line, current queue, and proceed messaging.
- Staff Dashboard with Call Next, Start Serving, Mark Served, Skip, Cancel, and counter selection.
- Daily office-wide capacity with sequential IDs such as `SQ-20261028-001`; cancelled or skipped numbers are never reused on that date.
- Historical date views, category distribution, peak-hour summary, service duration analytics, empty states, and responsive mobile layouts.
- Fictional demo dataset loader that adds sample records without overwriting existing records, plus a confirmed reset action.
- Visible Demo Mode indicator: records are stored in this browser with `localStorage`.

## Queue and estimates

Waiting tokens are sorted by creation timestamp. The default estimate is the number of active people ahead multiplied by the configurable average service duration (5 minutes by default). Completed records contribute actual service durations when staff has both called and completed timestamps; otherwise the configured default is used. Estimates are labelled as estimates and are not guarantees. This prototype uses transparent queue calculations and historical averages, not a trained machine-learning model.

The daily limit is shared across the whole office, not per category. Tokens may only be issued for the current local calendar date. A new date naturally starts a new sequence while previous records remain available in History.

## Demo-mode limitations

Local browser storage is not shared between staff or student devices and can be cleared by browser settings. No official college system is connected. Use fictional IDs only; the app does not collect bank account details, Aadhaar numbers, scholarship documents, or other sensitive information. A future production version should replace the storage adapter with a shared authenticated database, add server-side token allocation/locking, and enforce role-based access.
