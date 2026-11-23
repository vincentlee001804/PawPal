# AGENTS.md — PawPal MVP

Guidance for AI agents and contributors working in this repository.

## Project overview

PawPal is a pet-care management app for the CSS3344 Mobile Application Development / CSS3453 IT Project Management group assignment (T11 – Productivity & Lifestyle App). It helps pet owners manage pet profiles, care schedules, appointment/vaccination records, reminders, and nearby pet-service discovery. It is an organisational tool — never veterinary advice.

Authoritative documents in `docs/`:

- `docs/PawPal_Software_Requirement_Specifications.md` (**authoritative**, v0.9) — fixed stack, functional requirements (FR-XXX), non-functional requirements (NFR-XXX), MVP scope. Where other docs disagree, the SRS wins.
- `docs/PawPal_Project_Concept_and_Planning_Summary.md` — concept, MOV, stakeholder and risk rationale (planning context only).
- `docs/MAD Group Assignment 2026.docx` — the assignment brief from the lecturer.

## Tech stack (fixed decisions — do not change without group agreement)

| Area | Decision |
| :---- | :---- |
| Mobile app | Flutter, Android 8.0 / API 26 minimum, 2 GB RAM target device |
| Mobile architecture | MVVM + Riverpod, with a repository/data-access layer |
| Backend | Supabase: Auth, PostgreSQL, Storage, RLS, Edge Functions |
| Offline cache | SQLite via `sqflite`, **read-only** cache of previously loaded data |
| Maps | `flutter_map` + OpenStreetMap with a tile provider whose terms permit this use (Google Maps is out of scope) |
| Notifications | `flutter_local_notifications` (local only; FCM/push is out of scope) |
| Connectivity | `connectivity_plus` plus real network-error handling |
| Web admin panel | React + Material UI, responsive sidebar/collapsible navigation |
| Language | English only in MVP |

## Hard rules

1. **Never embed the Supabase service-role key** in the Flutter app or the browser admin client. Ordinary operations go through the Supabase client subject to RLS; sensitive server-side work goes in Edge Functions.
2. **Backend authorisation is enforced by RLS/policies**, never by UI visibility alone. Admin permissions and owner-only data access must hold at the database level.
3. **Hardware-limitations constraint** (assigned project constraint): compress images before upload, use thumbnails/progressive loading/pagination for long lists, avoid unnecessary animations and background work, no continuous GPS tracking, and load map resources only when the Explore map opens.
4. **Offline behaviour is read-only.** Create/edit/delete require internet. Cached data expires after 7 days, is account-scoped (never visible to another account after logout), and is cleared on account deletion. When connectivity returns, refresh relevant data automatically and support pull-to-refresh.
5. **The six compulsory CSS3344 features must all be demonstrable**: secure authentication; MVVM/BLoC reactive dashboard; location-aware feature; interactive data submission with camera/gallery upload; local offline caching (SQLite); asynchronous notifications. See SRS Section 13 for traceability.
6. **Stay inside MVP scope.** Do not build: Pet Journal, ratings/reviews, provider accounts or portal, online booking, FCM push, Google Maps, mandatory OCR (OCR is optional only), offline write/sync, iOS, multilingual UI, payments, AI diagnosis/treatment, telemedicine, wearables. See SRS Appendix B.
7. **Admin accounts are created/activated/deactivated only by the development team through Supabase** — there is no public or in-panel admin registration. Google sign-in alone never grants admin privileges.
8. **Deletion cascades are required**: deleting a pet removes its schedules, reminders, records, attachments and photos; deleting an account removes all associated data and local cache, including Storage cleanup.
9. **Retention limits**: mobile notification history 30 days; admin notification history 7 days; SQLite cache 7 days.
10. **No verified badge or last-updated date** on Explore listings, and listings are text-based (no cover images/galleries) in MVP.
11. **Location permission is requested contextually** only for Explore; if denied, fall back to manual selection from the predefined Sarawak town/city list (no free-text address entry).

## Working conventions

- Keep requirement IDs (FR-AUTH-01, NFR-SEC-03, etc.) traceable: reference them in code comments, tests and commit messages where relevant.
- Validate package versions and Android permission behaviour early; the SRS flags package compatibility as a risk.
- Record database schema, RLS policy and Edge Function changes in a migration/change note so the team stays in sync.
- Performance targets (8s cold launch, 3s navigation/cache loading) are engineering targets on the agreed lower-end test device — measure with recorded device model, Android version, RAM and network conditions before claiming them.
- **AI-use caution**: the CSS3453 brief restricts AI use in assessed submissions. Keep AI assistance to implementation support and follow the group's declared-use obligations; assessed written content must be authored by the group.

## Definition of done (per feature)

- Matches the SRS requirement and priority label (MVP vs Optional vs Future).
- RLS/permissions verified at the backend, not just the UI.
- Offline and permission-denied paths handled gracefully.
- Works within the hardware-limitations constraints (no heavy images/animations/background work).
- Tested on an Android 8.0+/2 GB-class device where feasible, with conditions recorded.
