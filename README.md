# PawPal

**Pet Care Scheduler & Nearby Pet Service Finder** — a pet-care management app.

PawPal helps pet owners manage pet profiles, care schedules, appointment and vaccination records, reminders, and discover nearby pet services. It is an organisational tool — never veterinary advice.

## Tech stack

| Area | Decision |
| :--- | :--- |
| Mobile app | Flutter (Android 8.0 / API 26 minimum) |
| Architecture | MVVM + Riverpod, with a repository layer |
| Backend | Supabase (Auth, PostgreSQL, Storage, RLS, Edge Functions) |
| Offline cache | SQLite via `sqflite` (read-only cache, 7-day expiry) |
| Maps | `flutter_map` + OpenStreetMap |
| Notifications | `flutter_local_notifications` (local only) |
| Web admin panel | React + Material UI |

## Repository

- `AGENTS.md` — guidance for AI agents and contributors (stack, hard rules, conventions)
- `docs/GitHub_Team_Workflow.md` — how the team branches, pushes, and merges

The authoritative SRS and project concept documents are maintained in the team's shared Google Drive, not in this repo.

## Team workflow

All changes go through a branch → pull request → squash merge by the maintainer. Direct pushes to `main` are blocked. See `docs/GitHub_Team_Workflow.md` for the full guide.
