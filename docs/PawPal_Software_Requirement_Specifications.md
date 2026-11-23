**PAWPAL**

Pet Care Management App

**SOFTWARE REQUIREMENTS**  
**SPECIFICATION**

v1.0  \|  20 November 2026

CSS3344 Mobile Application Development  
CSS3453 IT Project Management

*Baselined for design and implementation*

**Table of Content:**  
[Document Control	4](#document-control)  
[Revision History	4](#heading=)  
[Review Instructions	4](#heading=)  
[1\. Introduction	4](#heading=)  
[1.1 Purpose	4](#heading=)  
[1.2 Scope	5](#heading=)  
[1.3 Assignment Context	5](#heading=)  
[1.4 Intended Users	5](#heading=)  
[1.5 Definitions	5](#heading=)  
[2\. Overall Description	6](#heading=)  
[2.1 Product Perspective	6](#heading=)  
[2.2 Main Product Functions	6](#heading=)  
[2.3 Operating Environment	6](#heading=)  
[2.4 Constraints and Assumptions	6](#heading=)  
[3\. MVP Scope and Exclusions	7](#heading=)  
[3.1 Included	7](#heading=)  
[3.2 Excluded or Future	7](#heading=)  
[4\. Functional Requirements	7](#heading=)  
[4.1 Authentication and Account Management	7](#heading=)  
[4.2 Pet Profile Management	8](#heading=)  
[4.3 Care Scheduler	9](#heading=)  
[4.4 Appointment and Vaccination Records	9](#heading=)  
[4.5 File Attachments and Submission	10](#heading=)  
[4.6 Nearby Pet Services / Explore	10](#heading=)  
[4.7 Reminders and Notification Centre	11](#heading=)  
[4.8 Dashboard, Navigation and Offline Cache	11](#heading=)  
[4.9 Web Admin Panel	12](#heading=)  
[5\. External Interface Requirements	13](#heading=)  
[5.1 UI and Accessibility	13](#heading=)  
[5.2 Software Interfaces	13](#heading=)  
[5.3 Device Permissions	14](#heading=)  
[6\. Conceptual Data Requirements	14](#heading=)  
[6.1 Ownership and Retention	14](#heading=)  
[7\. Non-Functional Requirements	15](#heading=)  
[7.1 Performance Measurement	15](#heading=)  
[8\. System Architecture	15](#heading=)  
[8.1 Security Architecture Rules	16](#heading=)  
[8.2 Conceptual Data Flow	16](#heading=)  
[9\. Key Workflows	16](#heading=)  
[9.1 Online/Offline Read	16](#heading=)  
[9.2 Explore and Location	16](#heading=)  
[9.3 Recurring Care	17](#heading=)  
[10\. Acceptance Criteria and Test Coverage	17](#heading=)  
[10.1 Test Conditions	17](#heading=)  
[11\. Risks and Mitigations	18](#heading=)  
[12\. Open Decisions and Validation Items	18](#heading=)  
[13\. Traceability to the Six MAD Essential Features	19](#heading=)  
[14\. Assignment Alignment and AI-Use Caution	19](#heading=)  
[Appendix A – MVP Checklist	20](#heading=)  
[Appendix B – Explicitly Not in MVP	20](#heading=)

# **Document Control** {#document-control}

| Field | Value |
| :---- | :---- |
| Project | PawPal – Pet Care Management App |
| Document | Software Requirements Specification |
| Version / status | 1.0 – Baselined |
| Prepared | 16 November 2026 |
| Platforms | Flutter Android application \+ React Web Admin Panel |
| Backend | Supabase: Auth, PostgreSQL, Storage and Edge Functions |
| Audience | Project team, lecturer/supervisor, testers and implementation contributors |

## **Revision History**

| Version | Date | Description |
| :---- | :---- | :---- |
| 0.1–0.8 | Nov 2026 | Requirements elicited through team decision interview. |
| 0.9 | 16 Nov 2026 | Consolidated draft; open points and validation notes included. |
| 1.0 | 20 Nov 2026 | Records scope confirmed in MVP (FR-REC-01 to 11 upgraded to MVP); FR-DASH-05/06 added; document baselined. |

## **Review Instructions**

* Review the requirements for accuracy, feasibility and agreement before treating this document as a baseline.  
* Mark corrections directly in Word, especially items in Section 12 (Open Decisions and Validation Items).  
* Do not treat Optional or Future items as compulsory MVP work.  
* Validate package compatibility, Android permissions, map tile-provider terms and Supabase quotas during implementation.

| Label | Meaning |
| :---- | :---- |
| MVP | Required for the first working version. |
| Optional | May be implemented only if time permits; not part of MVP acceptance. |
| Future | Excluded from current MVP; possible later enhancement. |
| TBD / Validate | Needs team or technical confirmation. |

# **1\. Introduction**

## **1.1 Purpose**

This SRS records the agreed PawPal requirements to guide design, implementation, testing and team coordination for CSS3344 Mobile Application Development. It distinguishes MVP requirements from optional and future work.

## **1.2 Scope**

PawPal is a pet-care organisation and local pet-service discovery application. It helps dog and cat owners maintain multiple pet profiles, organise care activities, record veterinary appointments and vaccinations, discover nearby pet-related services and receive reminders. PawPal is an organisational tool; it does not diagnose illness, prescribe treatment or replace veterinary advice.

## **1.3 Assignment Context**

* CSS3344 requires a Flutter Android application, compulsory Web Admin Backend, six essential features, technical report, public GitHub repository, installable APK and submission to the designated drive folder.  
* The six essential features are Secure Authentication System; MVVM/BLoC Dashboard; Location-Aware Feature; Interactive Data Submission; Local Offline Caching; and Asynchronous Notifications.  
* CSS3453 uses the same project topic and group but assesses project management separately through initiating, planning, executing, monitoring/controlling and closing deliverables.  
* The assigned project constraint is Hardware Limitations: PawPal should remain usable on older/lower-end devices with limited processing power and memory.

## **1.4 Intended Users**

| Role | Client and access |
| :---- | :---- |
| Pet Owner | Flutter Android app; manages own account, pets, care activities, records, reminders and service discovery. |
| Administrator | React Web Admin Panel; manages users, listings, categories, locations and reports according to admin permissions. |
| Service Provider | No provider account or portal in MVP; service information is maintained by administrators. |

## **1.5 Definitions**

| Term | Meaning |
| :---- | :---- |
| MVP | Minimum Viable Product. |
| RLS | Supabase Row Level Security, used to restrict database access. |
| OCR | Optical Character Recognition. |
| Local notification | A notification scheduled and delivered by the device. |
| Cache | Local copy of previously retrieved data for offline viewing. |
| Edge Function | Server-side function for operations requiring trusted backend execution. |

# **2\. Overall Description**

## **2.1 Product Perspective**

PawPal consists of two clients sharing a Supabase backend: a Flutter Android application for pet owners and a React Web Admin Panel for authorised administrators. Supabase provides authentication, PostgreSQL and file storage. SQLite provides read-only offline caching on the mobile device.

## **2.2 Main Product Functions**

* Pet-owner authentication and account management.  
* Multiple pet profiles and dated weight measurements.  
* One-time and recurring care activities with status tracking.  
* Appointment and vaccination records with attachments.  
* Nearby pet-service discovery through list and map views.  
* Local reminders and notification history.  
* Read-only offline access to previously loaded information.  
* Admin management of users, services, categories, locations and reports.

## **2.3 Operating Environment**

| Area | Agreed direction |
| :---- | :---- |
| Mobile | Flutter; Android 8.0 Oreo (API 26\) minimum; target minimum RAM 2 GB. |
| Architecture | MVVM \+ Riverpod; repository/data-access layer. |
| Web Admin | React \+ Material UI; responsive hybrid navigation. |
| Backend | Supabase Auth, PostgreSQL, Storage, RLS and Edge Functions where needed. |
| Offline cache | SQLite using sqflite; read-only cache. |
| Maps | OpenStreetMap-based map view using flutter\_map and a suitable tile provider. |
| Notifications | flutter\_local\_notifications; FCM excluded from MVP. |
| Connectivity | connectivity\_plus plus actual network-request error handling. |

## **2.4 Constraints and Assumptions**

* The six MAD essential features and compulsory Web Admin Panel must be demonstrated.  
* Compress images, load long lists progressively and avoid unnecessary animations/background work.  
* Load map resources only when Map View opens; no continuous location tracking.  
* Never embed the Supabase service-role key in Flutter or browser clients.  
* OpenStreetMap data does not imply unrestricted free tile hosting; select a tile provider whose terms permit the intended use.  
* Users need the internet for create, edit and delete operations; previously loaded data may be viewed offline for up to seven days.  
* Administrators manually maintain the service directory. Coverage is intended across Sarawak but is not guaranteed in every town at launch.

# **3\. MVP Scope and Exclusions**

## **3.1 Included**

* Secure pet-owner authentication: email/password and Google Sign-In; verification and password reset.  
* Dog and cat pet profiles; multiple pets; photo and weight history.  
* Care scheduler, recurrence, status tracking and reminders.  
* Appointment and vaccination records, reminders and attachments.  
* Five-category pet-service directory with GPS/manual town selection, filters, sorting, list and map views.  
* Local notification centre and SQLite read-only offline cache.  
* React Web Admin Panel with dashboard, user management, service/category/location management and CSV reports.

## **3.2 Excluded or Future**

* Pet Journal, service ratings/reviews and owner-submitted service corrections.  
* Provider accounts, provider portal, online booking or clinic integration.  
* FCM push notifications, Google Maps integration and offline write/synchronisation.  
* Mandatory OCR or AI document analysis; OCR is optional only if time permits.  
* iOS, multilingual interface, admin mobile access, AI diagnosis/treatment, telemedicine, payments, wearables and automatic health monitoring.

# **4\. Functional Requirements**

All requirements below are MVP unless marked Optional or Future. IDs should be retained when preparing test cases.

## **4.1 Authentication and Account Management**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-AUTH-01 | Allow pet owners to register with email/password. | MVP |
| FR-AUTH-02 | Support Google Sign-In for pet owners. | MVP |
| FR-AUTH-03 | Support email verification and password reset. | MVP |
| FR-AUTH-04 | Maintain secure authenticated sessions and provide logout. | MVP |
| FR-AUTH-05 | Use email as an account identifier; display name is not an identifier. | MVP |
| FR-AUTH-06 | Generate a temporary pet-themed nickname if the display name is blank; allow later editing. | MVP |
| FR-AUTH-07 | Profile supports display name, photo, phone, password change for password accounts, email viewing, logout and account deletion. | MVP |
| FR-AUTH-08 | Require confirmation and appropriate re-authentication/verification for account deletion. | MVP |
| FR-AUTH-09 | Permanently delete account, pets, weight history, schedules/history, records, attachments and associated cache. | MVP |
| FR-AUTH-10 | Admin accounts are manually created/authorised by the development team through Supabase; no public admin registration. | MVP |
| FR-AUTH-11 | Admin login supports email/password and Google; Google authentication alone does not grant admin privileges. | MVP |
| FR-AUTH-12 | Only the development team activates/deactivates admin accounts through Supabase. | MVP |

## **4.2 Pet Profile Management**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-PET-01 | Allow a pet owner to create, view, edit and delete multiple pet profiles. | MVP |
| FR-PET-02 | Require pet name and species (Dog or Cat). | MVP |
| FR-PET-03 | Optional fields: breed, birth date/estimated age, gender, one profile photo, weight and additional notes. | MVP |
| FR-PET-04 | Breed uses a predefined list plus Other/custom value; breed may be unknown. | MVP |
| FR-PET-05 | Birth information supports exact date, estimated age or unknown. | MVP |
| FR-PET-06 | Gender supports Male, Female or Unknown. | MVP |
| FR-PET-07 | Record weight in kg with dated entries; allow viewing, editing and deleting incorrect entries. | MVP |
| FR-PET-08 | Show latest weight as current weight; load weight history progressively. | MVP |
| FR-PET-09 | Allow camera/device upload, replace and remove one pet photo; compress before Supabase Storage upload. | MVP |
| FR-PET-10 | Confirm permanent pet deletion and remove associated schedules, reminders, records, documents and photos. | MVP |
| FR-PET-11 | Keep species model extensible, although Dog and Cat are the only MVP choices. | MVP |

## **4.3 Care Scheduler**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-SCH-01 | Provide Feeding, Grooming/Bathing, Medication, Exercise/Walking and General Care activity types. | MVP |
| FR-SCH-02 | Allow user-created custom activity types. | MVP |
| FR-SCH-03 | Each activity is linked to a pet and includes name, date/time and recurrence settings. | MVP |
| FR-SCH-04 | Support one-time and daily, weekly or monthly recurring activities. | MVP |
| FR-SCH-05 | Recurring schedules have no automatic end date and continue until manually deleted. | MVP |
| FR-SCH-06 | Allow each occurrence to be marked Completed, Missed or Skipped. | MVP |
| FR-SCH-07 | Do not request a status-change note in MVP. | MVP |
| FR-SCH-08 | General care activities may include optional short notes. | MVP |
| FR-SCH-09 | Medication activity includes medication name, date/time, recurrence and optional short notes; dosage, units and treatment duration are excluded. | MVP |
| FR-SCH-10 | Provide chronological list view and filters by pet and Upcoming/Completed/Missed/Skipped status. | MVP |
| FR-SCH-11 | Show care history newest first, grouped by date with expandable groups and progressive loading. | MVP |
| FR-SCH-12 | Recurring edit choices: this occurrence only; this and future; all occurrences. | MVP |
| FR-SCH-13 | Recurring delete choices: this occurrence only; this and future; all occurrences. | MVP |
| FR-SCH-14 | Reminder timing: scheduled time, 10 minutes before or 30 minutes before. | MVP |
| FR-SCH-15 | Dismissing a notification does not change activity status. | MVP |

## **4.4 Appointment and Vaccination Records**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-REC-01 | Appointments support create, view, edit, cancel and delete. | MVP |
| FR-REC-02 | Appointment fields: pet, veterinary clinic name, appointment date, appointment time and purpose. | MVP |
| FR-REC-03 | Appointment statuses: Upcoming, Confirmed, Completed, Cancelled and Missed; owner updates status. | MVP |
| FR-REC-04 | Appointment history is newest first and filterable by pet. | MVP |
| FR-REC-05 | Load the latest 20 appointments first, then older records progressively. | MVP |
| FR-REC-06 | Provide local appointment reminders. | MVP |
| FR-REC-07 | Vaccination fields: pet, vaccination name, vaccination date and optional next vaccination date. | MVP |
| FR-REC-08 | Vaccination history is newest first, progressively loaded and filterable by pet. | MVP |
| FR-REC-09 | Vaccination reminder timing: 7 days, 3 days, 1 day before or on the date; user may disable it. | MVP |
| FR-REC-10 | Changing next vaccination date reschedules reminder; deleting record cancels reminder. | MVP |
| FR-REC-11 | Appointment form excludes contact number and extra notes; vaccination form excludes clinic name and extra notes. | MVP |

## **4.5 File Attachments and Submission**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-FILE-01 | Support camera capture and selecting existing images/files. | MVP |
| FR-FILE-02 | Support JPG, JPEG, PNG and PDF attachments. | MVP |
| FR-FILE-03 | Image limit 5 MB before compression; PDF limit 10 MB. | MVP |
| FR-FILE-04 | Allow up to five attachments per record. | MVP |
| FR-FILE-05 | Validate file type/size, compress images, show upload progress and allow preview/removal. | MVP |
| FR-FILE-06 | Store files securely in Supabase Storage and associate with relevant pet record. | MVP |
| FR-FILE-07 | Google ML Kit OCR may be evaluated if time permits; users must review/correct extracted fields. | Optional |
| FR-FILE-08 | Manual pet-profile entry, photo upload and record attachments (images/documents on records) are supported; document OCR is excluded from MVP. | MVP |

## **4.6 Nearby Pet Services / Explore**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-EXP-01 | Provide veterinary clinics, pet shops, grooming centres, boarding/pet hotels and pet parks/pet-friendly facilities. | MVP |
| FR-EXP-02 | Provide both list view and map view. | MVP |
| FR-EXP-03 | Map view shows service pins; selecting a pin displays basic service information. | MVP |
| FR-EXP-04 | Request GPS permission only for location-aware functions; do not continuously track users. | MVP |
| FR-EXP-05 | If GPS is denied, allow browsing and manual Sarawak town/city selection. | MVP |
| FR-EXP-06 | Manual location selection uses a predefined town/city list; no manual address entry. | MVP |
| FR-EXP-07 | Filter by category, location and service name. | MVP |
| FR-EXP-08 | Sort by nearest, alphabetical A–Z or admin-recommended. | MVP |
| FR-EXP-09 | Nearest uses GPS when available or selected town/city as fallback. | MVP |
| FR-EXP-10 | Do not provide a separate distance-radius filter in MVP. | MVP |
| FR-EXP-11 | Listing details: name, category, address, phone, hours, map location/directions, description and website/social links where available. | MVP |
| FR-EXP-12 | Listings are text-based; no cover images or galleries in MVP. | MVP |
| FR-EXP-13 | Available actions: call, WhatsApp, website and social links; hide unavailable actions. | MVP |
| FR-EXP-14 | Directions open an external map application. | MVP |
| FR-EXP-15 | Load first 10 listings, then load more progressively on scroll. | MVP |
| FR-EXP-16 | Default sort is nearest when location is available; otherwise admin-recommended. | MVP |
| FR-EXP-17 | Administrators manually collect, maintain and publish listings; owner suggestions are future work. | MVP |
| FR-EXP-18 | Target coverage is Sarawak-wide, but full coverage in every town is not guaranteed at launch. | MVP |
| FR-EXP-19 | Do not display a verified badge or last-updated date. | MVP |
| FR-EXP-20 | Use OpenStreetMap with flutter\_map and a permitted tile provider; Google Maps is deferred. | MVP |

## **4.7 Reminders and Notification Centre**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-NOT-01 | Use flutter\_local\_notifications for scheduled local reminders. | MVP |
| FR-NOT-02 | Schedule care, appointment and vaccination reminders. | MVP |
| FR-NOT-03 | Allow independent enable/disable preferences for care, appointment and vaccination reminders. | MVP |
| FR-NOT-04 | Mobile notification history retains latest 30 days; older entries are automatically removed. | MVP |
| FR-NOT-05 | History item shows title, message and date/time and opens related activity/record. | MVP |
| FR-NOT-06 | No read/unread tracking or individual notification deletion in mobile MVP. | MVP |
| FR-NOT-07 | General care alert shows pet and activity; tapping opens in-app details with scheduled time and optional notes. | MVP |
| FR-NOT-08 | Medication alert shows pet, medication name and optional short notes. | MVP |
| FR-NOT-09 | Notification opens relevant detail in app; status changes occur in app, not via quick action. | MVP |
| FR-NOT-10 | No snooze or notification quick-action buttons. | MVP |
| FR-NOT-11 | Firebase Cloud Messaging push notifications are excluded. | Future |

## **4.8 Dashboard, Navigation and Offline Cache**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-DASH-01 | Home shows welcome/display name, upcoming activities and quick-access shortcuts. | MVP |
| FR-DASH-02 | Bottom navigation: Home, My Pets, Schedule and Explore. | MVP |
| FR-DASH-03 | Home top-right icons: Notification and Profile; Settings is inside Profile. | MVP |
| FR-DASH-04 | MVP interface language is English; BM and Chinese are future enhancements. | MVP |
| FR-DASH-05 | Home supports pull-to-refresh and shows a clear offline/read-only indicator when connectivity is unavailable. | MVP |
| FR-DASH-06 | Cached data that may be stale is visually distinguished from fresh data on Home and Scheduler. | MVP |
| FR-OFF-01 | Use SQLite via sqflite to cache previously loaded Supabase data. | MVP |
| FR-OFF-02 | Offline access is read-only; create/edit/delete require internet. | MVP |
| FR-OFF-03 | Cache previously loaded pets, weight history, schedules/history, appointments, vaccinations and service listings. | MVP |
| FR-OFF-04 | Cached data expires after seven days. | MVP |
| FR-OFF-05 | Refresh relevant cached data automatically when connectivity returns and support pull-to-refresh. | MVP |
| FR-OFF-06 | Use connectivity\_plus for connectivity changes and handle failed requests separately. | MVP |
| FR-OFF-07 | Cache is account-scoped; after logout it may remain until expiry but must not be visible to another account. | MVP |
| FR-OFF-08 | Account deletion clears associated local cache. | MVP |

## **4.9 Web Admin Panel**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| FR-ADM-01 | Build Admin Panel with React and Material UI using responsive desktop sidebar/collapsible small-screen navigation. | MVP |
| FR-ADM-02 | Use Supabase Auth and role-based access; only pre-authorised administrators may access the panel. | MVP |
| FR-ADM-03 | Dashboard summary: total users, pets, service listings and appointments. | MVP |
| FR-ADM-04 | Dashboard charts: user registration trend (line) and popular service categories (bar). | MVP |
| FR-ADM-05 | Dashboard date filters: Today, Last 7 Days, Last 30 Days, This Month and All Time. | MVP |
| FR-ADM-06 | User management: view/search users; filter by account status and registration date; activate/deactivate pet-owner accounts. | MVP |
| FR-ADM-07 | Show user registered pets and account registration date. | MVP |
| FR-ADM-08 | Admin pet access is view-only; admins cannot edit/delete pet profiles. | MVP |
| FR-ADM-09 | Service management: add, view, edit, delete and deactivate listings; inactive listings are hidden from Explore. | MVP |
| FR-ADM-10 | Required listing fields: service name, category, town/city and address. | MVP |
| FR-ADM-11 | Optional listing fields: phone, WhatsApp, hours, description, coordinates, website and social links. | MVP |
| FR-ADM-12 | Manage categories with add/view/edit/deactivate/delete; prevent deletion while listings depend on category. | MVP |
| FR-ADM-13 | Manage locations with add/view/edit/coordinates/deactivate/delete; prevent deletion while listings depend on location. | MVP |
| FR-ADM-14 | Initial categories are the five service categories defined in FR-EXP-01. | MVP |
| FR-ADM-15 | Reports cover user, pet, service and appointment statistics, registration trends, popular categories and service distribution by town/city. | MVP |
| FR-ADM-16 | Export individual or combined CSV reports; date-range filter applies where relevant. | MVP |
| FR-ADM-17 | Admin tables use pagination with 10 records per page. | MVP |
| FR-ADM-18 | Top-nav notification bell/dropdown shows new user registrations and newly added service listings. | MVP |
| FR-ADM-19 | Admin notifications retained 7 days; show title, short description and date/time; no read/unread, sound or navigation action; click previews only. | MVP |
| FR-ADM-20 | Admin session expires after 60 minutes of inactivity; manual logout available. | MVP |
| FR-ADM-21 | Admin accounts are created/activated/deactivated by development team through Supabase, not through the panel. | MVP |

# **5\. External Interface Requirements**

## **5.1 UI and Accessibility**

* Mobile bottom tabs: Home, My Pets, Schedule and Explore; Home has Notification and Profile icons.  
* Explore switches between list and map; service listings are text-based with available contact actions.  
* Admin panel uses responsive navigation, dashboard cards/charts, management tables and forms.  
* Accessibility: readable consistent text, sufficient contrast, clearly labelled buttons/icons, touch-friendly controls and status cues not relying on colour alone.

## **5.2 Software Interfaces**

| Interface | Purpose |
| :---- | :---- |
| Supabase Auth | Email/password, Google Sign-In and session/token management. |
| Supabase PostgreSQL | Primary persistent application database. |
| Supabase Storage | Pet photos and record attachments. |
| Supabase Edge Functions | Sensitive server-side operations where required. |
| SQLite / sqflite | Read-only cache for previously loaded information. |
| flutter\_local\_notifications | Scheduled local reminders. |
| connectivity\_plus | Connectivity-change detection; network failures still handled. |
| flutter\_map \+ OpenStreetMap | In-app map pins; tile provider to be selected. |
| External map app | Directions/navigation from a service listing. |
| React \+ Material UI | Web Admin Panel frontend. |

## **5.3 Device Permissions**

* Camera and media/file access for pet photos and record attachments.  
* Location permission requested contextually for GPS-based Explore.  
* Notification permission and Android scheduling behaviour handled for local reminders.  
* Target Android 8.0/API 26+ and test against 2 GB RAM target.

# **6\. Conceptual Data Requirements**

This entity inventory is conceptual; exact columns, keys, indexes, enums and normalisation must be finalised in the database design.

| Entity | Purpose and relationship |
| :---- | :---- |
| User/Profile | Supabase Auth identity and profile details; one owner has multiple pets. |
| Pet | Belongs to one owner; name, species, breed, birth, gender, notes and photo reference. |
| PetWeightEntry | Dated weight-in-kg measurements belonging to a pet. |
| CareActivity/Schedule | Pet-linked activity, date/time, recurrence and optional creation notes. |
| CareOccurrence/Status | Occurrence-level Completed/Missed/Skipped state; supports per-occurrence recurrence edits. |
| Appointment | Pet-linked clinic name, date/time, purpose and status. |
| VaccinationRecord | Pet-linked vaccination name, date and optional next date. |
| RecordAttachment | Reference to appointment/vaccination record and secure Storage object. |
| PetService | Listing details, category, town/city, address, optional contacts/hours/coordinates/links and active state. |
| ServiceCategory | Five initial service categories and admin-managed category state. |
| Location | Supported town/city values and map coordinates. |
| MobileNotificationHistory | Title/message/time and related activity or record reference. |
| AdminNotification | Admin event title/description/time with seven-day retention. |

## **6.1 Ownership and Retention**

* Each pet belongs to one owner; weight entries, schedules, appointments and vaccinations belong to a pet.  
* Attachments belong to a relevant pet record and must follow database and Storage access policies.  
* Mobile notification history: 30 days; admin notification history: 7 days; SQLite cache: 7 days.  
* Deleting a pet removes associated schedules, reminders, records, attachments and photos.  
* Deleting an account removes associated account/pet data and local cache; implement dependent record and Storage cleanup.

# **7\. Non-Functional Requirements**

| ID | Requirement | Priority |
| :---- | :---- | :---- |
| NFR-PERF-01 | Cold app launch target: within 8 seconds on the agreed lower-end test device. | Target |
| NFR-PERF-02 | Normal screen navigation target: within 3 seconds under normal test conditions. | Target |
| NFR-PERF-03 | Cached data loading target: within 3 seconds. | Target |
| NFR-PERF-04 | Compress images and load images progressively; long lists/history use progressive loading or pagination. | MVP |
| NFR-PERF-05 | Avoid unnecessary animations, continuous GPS tracking and unnecessary background work. | MVP |
| NFR-REL-01 | No frequent crashes during normal tested usage; record test conditions and defects. | MVP |
| NFR-SEC-01 | RLS enforces owner-only access to private pet-owner data. | MVP |
| NFR-SEC-02 | Admin permissions are enforced by backend/database policies, not only UI visibility. | MVP |
| NFR-SEC-03 | Never embed Supabase service-role key in Flutter or browser clients. | MVP |
| NFR-SEC-04 | Protect uploaded files using appropriate Storage policies. | MVP |
| NFR-SEC-05 | Handle sessions and account-specific local cache safely on logout/deletion. | MVP |
| NFR-PRIV-01 | Collect only necessary information and request location only when relevant. | MVP |
| NFR-USE-01 | Use English in MVP and provide readable, accessible controls. | MVP |
| NFR-MAINT-01 | Use MVVM/repository separation between UI, state/business logic and data access. | MVP |
| NFR-COMP-01 | Support Android 8.0/API 26+; 2 GB RAM is the minimum device target for testing. | Target |

## **7.1 Performance Measurement**

Timing values are initial engineering targets, not values mandated by the assignment. Record device model, Android version, RAM, network condition, cold/warm launch state, dataset size and measured results. Revise targets only with test evidence and team agreement.

# **8\. System Architecture**

| Layer | Responsibility |
| :---- | :---- |
| Flutter Views | Screens, widgets, forms, navigation and accessible UI. |
| ViewModels \+ Riverpod | Screen state, user actions, validation orchestration and dependency/state management. |
| Repositories | Abstract data access and select Supabase or SQLite cache according to connectivity and operation. |
| Supabase client | Normal authenticated data operations subject to RLS. |
| Supabase backend | Auth, PostgreSQL, Storage, RLS and Edge Functions for sensitive operations. |
| SQLite cache | Previously loaded data for read-only offline viewing. |
| React Admin Panel | Material UI admin client sharing Supabase backend and role policies. |

## **8.1 Security Architecture Rules**

* Use direct Supabase client for ordinary authenticated operations subject to RLS.  
* Use Edge Functions for sensitive server-side operations when appropriate.  
* Do not ship service-role key to either client.  
* RLS separates owner data by authenticated user identity and enforces administrator-only operations.  
* UI role checks do not replace backend authorisation.

## **8.2 Conceptual Data Flow**

Flutter Views → ViewModels/Riverpod → Repositories ↔ Supabase (Auth, PostgreSQL, Storage, Edge Functions). Repositories also read/write the SQLite cache for offline viewing. React Admin Panel ↔ the same Supabase backend, with administrator policies.

# **9\. Key Workflows**

## **9.1 Online/Offline Read**

1. User opens a supported screen.  
2. Repository checks cache and network availability.  
3. If online, fetch relevant data from Supabase and update local cache.  
4. If offline, show unexpired cached data in read-only mode.  
5. When connectivity returns, refresh relevant data automatically; pull-to-refresh is also available.

## **9.2 Explore and Location**

6. User opens Explore and chooses List View or Map View.  
7. If permission is granted, use GPS for the location-aware task.  
8. If denied/unavailable, allow town/city selection from the predefined Sarawak list.  
9. Filter by category, location and service name; sort by nearest, A–Z or admin-recommended.  
10. Map pins show service locations; selecting a pin displays basic information; directions open externally.

## **9.3 Recurring Care**

11. User creates pet-linked activity and selects one-time or daily/weekly/monthly recurrence.  
12. App schedules local reminders according to chosen reminder timing.  
13. Each occurrence can be marked Completed, Missed or Skipped.  
14. Editing/deleting a recurring activity requires choosing this occurrence, this and future, or all occurrences.

# **10\. Acceptance Criteria and Test Coverage**

| Area | Minimum evidence |
| :---- | :---- |
| Authentication | Email/password and Google login; verification/reset; owner/admin separation; logout. |
| Dashboard/architecture | Reactive dashboard using agreed MVVM/Riverpod structure. |
| Location-aware | GPS nearest sorting and map pins; manual town/city fallback; external directions. |
| Interactive submission | Validated forms; camera/gallery/file selection; file type/size checks; upload progress. |
| Offline caching | Cached data visible offline; writes blocked offline; expiry and reconnect refresh tested. |
| Notifications | Scheduled local reminders; tapping opens relevant in-app details. |
| Pet management | Multiple pets, CRUD, weight history and deletion behaviour. |
| Scheduler | One-time/recurring activities, occurrence status, recurrence edit/delete scope and history. |
| Records | Appointment/vaccination management, reminders, ordering, filters and attachments. |
| Explore | Five categories, list/map toggle, filters/sorting, GPS/manual location and contact actions. |
| Admin Panel | Authorised login, dashboard, user status, view-only pets, listing/category/location management, CSV. |
| Low-end performance | Record launch, navigation, cache loading, stability and image handling on lower-end Android. |

## **10.1 Test Conditions**

* Test Android 8.0/API 26+ and the 2 GB RAM target where feasible.  
* Test GPS permission granted and denied; online, offline and intermittent connectivity.  
* Test multiple pets and sufficient records to exercise progressive loading.  
* Test owner-to-owner isolation and administrator permissions.  
* Test attachment type/size limits and cleanup of associated Storage objects.

# **11\. Risks and Mitigations**

| Risk / constraint | Mitigation |
| :---- | :---- |
| Low-end performance | Compress images, progressive loading, minimal animations/background work, map on demand and lower-spec testing. |
| Outdated service data | Admin-maintained directory; no verification badge or last-updated date in MVP; coverage not guaranteed everywhere. |
| GPS denied/unavailable | Manual town/city selection; browsing remains available. |
| Map tile cost/policy | Select a tile provider whose terms permit the project use; OSM data is not unlimited tile hosting. |
| Privacy/access control | RLS, role policies, secure Storage, account-scoped cache and deletion handling. |
| Incorrect reminder dates | Dates are user-entered; reminders are organisational only, not veterinary advice. |
| Package compatibility | Validate package versions and Android permission behaviour early. |
| Scope creep | Keep journal, reviews, push, OCR, Google Maps and provider accounts outside MVP. |

# **12\. Open Decisions and Validation Items**

* Choose a compliant OpenStreetMap tile provider and decide how service coordinates/town locations are searched.  
* Confirm the predefined Sarawak town/city catalogue and how town-level coordinates are used for nearest sorting when GPS is unavailable.  
* Finalise Supabase schema, foreign keys, RLS policies, Storage buckets and Edge Function boundaries; test role separation.  
* Validate the shared-device privacy implications of retaining account-scoped cache for up to seven days after logout.  
* Design recurrence storage/materialisation so this-only, future and all-occurrence edits/deletions behave correctly.  
* Validate Android notification permission, exact-alarm behaviour where relevant, time zones, recurrence rescheduling and reboot behaviour.  
* Confirm exactly which appointment/vaccination record screens expose attachments; basic forms omit extra fields but record attachments are supported.  
* Confirm what event source triggers admin notifications for newly added service listings.  
* Define how deactivated pet-owner accounts are prevented from signing in/accessing data and whether existing sessions are revoked.  
* Define date fields and counting rules used by each CSV report.  
* Choose the actual lower-end Android test device and reproducible performance measurement conditions.  
* Confirm account deletion cascade, Storage cleanup, retention obligations and failure recovery.

# **13\. Traceability to the Six MAD Essential Features**

| Assignment feature | PawPal implementation |
| :---- | :---- |
| Secure Authentication System (token management, login/registration API) | FR-AUTH-01 to FR-AUTH-12; NFR-SEC-01 to NFR-SEC-05. |
| MVVM/BLoC Dashboard (reactive UI from API endpoints) | MVVM \+ Riverpod; FR-DASH-01 to FR-DASH-06; Section 8\. |
| Location-Aware Feature (GPS mapping, nearest facility locator) | FR-EXP-02 to FR-EXP-10 and FR-EXP-14; GPS/manual fallback, map pins and nearest sorting. |
| Interactive Data Submission (camera/gallery uploads, validation) | FR-FILE-01 to FR-FILE-08; validated forms and secure uploads. |
| Local Offline Caching (SQLite/local storage) | FR-OFF-01 to FR-OFF-08; SQLite read-only cache. |
| Asynchronous Notifications (push/local alerts or toast) | FR-NOT-01 to FR-NOT-11; scheduled local reminders. |

# **14\. Assignment Alignment and AI-Use Caution**

This draft is based on the team's recorded PawPal decisions, the uploaded CSS3344 Mobile Application Development brief, the uploaded CSS3453 IT Project Management brief and the PawPal Project Concept & Planning Summary.

* CSS3344 brief: Flutter Android app, compulsory Web Admin Backend, all six essential features, technical report, public GitHub repository, APK and designated-drive submission. Its marking breakdown includes UI/UX, production readiness/backend logic, technical report, Web Admin Panel, weekly progress updates and peer evaluation.  
* CSS3453 brief: group portfolio of 35–50 pages excluding appendices, including business case, literature review (8–12 sources; at least three existing solutions; maximum five pages excluding references), project management plan, execution record, control report/risk addendum and closure report/reflection. A separate individual reflective journal is also required.  
* CSS3453 AI-use restriction: the brief permits AI only for grammar checking, formatting or idea generation; it prohibits AI-generated project content, analysis, calculations, diagrams and personal reflection for submission. Any permitted AI assistance must be declared as specified by the brief. This SRS is a requirements-planning aid; ask the lecturer whether/how it may be used in assessed submissions and ensure assessed content is authored by the group in compliance with the brief.  
* CSS3453 Week 8 Risk Card: treat the assigned event as real for the project-management plan. The brief explicitly says not to change CSS3344 app requirements because of the simulated risk event.

# **Appendix A – MVP Checklist**

* ☐  Authentication and account management  
* ☐  Pet profiles and weight history  
* ☐  Care scheduler and recurring activity tracking  
* ☐  Appointment records and reminders  
* ☐  Vaccination records and reminders  
* ☐  Record attachments (manual entry; OCR optional)  
* ☐  Explore list \+ map  
* ☐  Local reminders and notification history  
* ☐  SQLite offline cache  
* ☐  React Web Admin Panel  
* ☐  Admin reports and CSV export  
* ☐  Low-end Android performance and accessibility

# **Appendix B – Explicitly Not in MVP**

* Pet Journal; ratings/reviews; owner-submitted service corrections.  
* Provider accounts/portal; online booking; clinic integrations.  
* FCM push notifications; Google Maps; mandatory OCR; AI document analysis.  
* Offline writes/synchronisation; iOS; multilingual UI; admin mobile app.  
* AI diagnosis/treatment, telemedicine, payments, wearables and automatic health monitoring.

