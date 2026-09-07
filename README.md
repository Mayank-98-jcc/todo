# FocusFlow

A polished, responsive personal work-management dashboard built with React, Vite, Framer Motion, and Lucide icons. Tasks and activity are persisted locally in the browser so they remain after refreshes.

## Included

- Dashboard with animated statistics, upcoming deadlines, overdue tasks, and weekly insights
- Task CRUD flow with details, edit form, completion feedback, soft deletion, status/priority/category fields, and filters
- Local-time deadline status calculation and a notification center
- Browser Notification API setup, with one-time reminder / overdue tracking while the app is open
- Calendar, history timeline, dark mode, responsive sidebar, and mobile-friendly modals

## Run locally

```bash
npm install
npm run dev
```

Open the local URL printed by Vite. For a production check:

```bash
npm run build
npm run preview
```

## Notifications

Go to **Settings → Enable notifications** and approve the browser prompt. FocusFlow checks deadlines every minute while its tab is open. It sends one alert per configured reminder and one alert when a task becomes overdue; alerts are also retained in the in-app notification center.

Browsers do not reliably deliver ordinary JavaScript notifications once the browser or tab is completely closed. For guaranteed closed-browser alerts, add a service worker plus Web Push server (or a backend scheduler) in a future API-backed version.

## Data and future backend

This implementation intentionally uses `localStorage` for zero-config persistence and a working local demo. The task objects include the fields expected by a REST/MongoDB API, and the state layer can be swapped for `GET/POST/PUT/DELETE /api/tasks`, history, and notification endpoints when server-backed multi-device data is needed.
