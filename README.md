# FocusFlow

A polished, responsive personal work-management dashboard built with React, Vite, Framer Motion, and Lucide icons. Tasks and activity are persisted locally in the browser so they remain after refreshes.

## Included

- Dashboard with animated statistics, upcoming deadlines, overdue tasks, and weekly insights
- Task CRUD flow with details, edit form, completion feedback, soft deletion, status/priority/category fields, and filters
- Local-time deadline status calculation and a notification center
- Browser Notification API setup, with one-time reminder / overdue tracking while the app is open
- Calendar, history timeline, dark mode, responsive sidebar, and mobile-friendly modals
- My Day: automatically ranks overdue, due-today, urgent/high-priority, in-progress, and manually chosen work
- Subtasks with persisted progress, completion state, edit/delete controls, and task activity records
- Per-task working notes with add, edit, delete, timestamps, and history integration
- Analytics page with date filters, completed-per-day chart, status/category breakdowns, insights, and streak history
- Backup and restore: export full JSON backups, export tasks as CSV, and validate then merge or replace an imported backup

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

## Using the advanced features

- Open any task to manage **Subtasks**, **Notes**, and the task-specific **Activity** timeline.
- Use **My Day** to add a future task manually; due-today, overdue, and high-priority work is included automatically.
- Open **Analytics** to switch between reporting ranges and view the current and longest productive streaks. A productive day is one on which at least one task is completed.
- In **Settings → Backup & data**, use JSON for a full portable backup, CSV for spreadsheets, and Import Backup to choose either a safe merge or an explicit full replacement.
