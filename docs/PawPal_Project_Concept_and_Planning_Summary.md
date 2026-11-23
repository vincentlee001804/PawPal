# **PAWPAL**

**Pet Care Management App**

**Project Concept & Planning Summary**

CSS3453 IT Project Management  \|  CSS3344 Mobile Application Development

Proposed domain: T11 – Productivity & Lifestyle App

# 

**Table of Content**

[**1\. Project Overview	4**](#heading=)

[**2\. Problem Statement and Proposed Solution	4**](#heading=)

[Problem	4](#heading=)

[Proposed solution	4](#heading=)

[Value proposition	4](#heading=)

[**3\. Measurable Organisational Value (MOV)	5**](#heading=)

[Proposed MOV targets	6](#heading=)

[Rationale	6](#heading=)

[**4\. Scope Statement	7**](#heading=)

[Scope overview and in-scope deliverables	7](#heading=)

[Out of scope and constraints	7](#heading=)

[Scope rationale and control	8](#heading=)

[**5\. Related SDG and PCDS 2030	9**](#heading=)

[Rationale	9](#heading=)

[**6\. Proposed Main Modules	9**](#heading=)

[**7\. Suggested App Navigation	10**](#heading=)

[**8\. Mapping to the Six Compulsory CSS3344 Features	10**](#heading=)

[**9\. Proposed Web Admin Panel	11**](#heading=)

[**10\. Existing Solutions and Differentiation	12**](#heading=)

[Potential differentiation to validate	12](#heading=)

[**11\. Fit with CSS3453 IT Project Management	13**](#heading=)

[**12\. Hardware Limitations Constraint	13**](#heading=)

[**13\. Key Risks and Possible Responses	14**](#heading=)

[**14\. Proposed Technical Direction	15**](#heading=)

[**15\. Validation Before Finalising the Proposal	15**](#heading=)

[**16\. Short Project Summary	16**](#heading=)

[**Reference and Assignment Notes	16**](#heading=)

[**17\. SMART Project Objectives	17**](#heading=)

[**18\. Stakeholder Identification	18**](#heading=)

[**19\. Initial User Workflows and Use Cases	19**](#heading=)

[19.1 Register and access PawPal	19](#heading=)

[19.2 Create and manage a pet profile	19](#heading=)

[19.3 Record a care activity or appointment	19](#heading=)

[19.4 Discover a nearby pet service	19](#heading=)

[19.5 View essential information offline	19](#heading=)

[**20\. Initial Non-functional Requirements	20**](#heading=)

[**21\. Data Sources and Admin Management	21**](#heading=)

[21.1 Proposed initial data approach	21](#heading=)

[21.2 Suggested listing management workflow	21](#heading=)

[**22\. Initial User Validation Plan	22**](#heading=)

[22.1 Suggested approach	22](#heading=)

[22.2 Suggested interview questions	22](#heading=)

[22.3 How to use the findings	22](#heading=)

# 

# **1\. Project Overview**

PawPal is a proposed mobile application that helps pet owners organise everyday pet-care responsibilities in one convenient place. The concept focuses on pet profiles, care schedules, appointment and vaccination records, nearby pet-related services, and reminders. It is intended to support organisation and discovery; it is not a veterinary diagnosis or treatment platform.

| Item | Proposed details |
| :---- | :---- |
| Project title | PawPal — Pet Care Management App |
| Assigned domain | T11 – Productivity & Lifestyle App |
| Target users | Dog owners, cat owners, and owners of other household pets |
| Core purpose | Help pet owners manage everyday care activities and find relevant nearby services |
| Platform direction | Flutter Android application with a compulsory web admin panel |

# **2\. Problem Statement and Proposed Solution**

## **2.1 Problem**

Pet owners may keep pet profiles, vaccination details, veterinary appointments, grooming schedules, and service information across paper records, phone notes, calendars, messaging apps, or separate platforms. This can make information difficult to organise and important activities easier to overlook.

## **2.2 Proposed solution**

PawPal proposes a centralized mobile platform where users can maintain profiles for multiple pets, organise care activities, record appointments and vaccinations, discover nearby pet services, and receive reminders.

## **2.3 Value proposition**

One convenient platform for organising everyday pet ownership responsibilities and discovering local pet-related services.

# 

# **3\. Measurable Organisational Value (MOV)**

PawPal is expected to create value by making everyday pet-care information easier to organise and locate. The proposed value focuses on customer convenience for pet owners and on reducing the effort required to find and use essential pet-care information.

| Step 1\.  Area of impact | Customer \+ Operational Customer: Improve convenience for pet owners when managing pet-care information. Operational: Centralise pet profiles, health records, care schedules and reminders in one application. |  |
| :---- | :---- | ----- |
| Step 2\.  Desired value | Do it better and faster. Better: Organise pet-care information in one accessible platform. Faster: Reduce the time required to find pet records and manage care schedules. More convenient: Receive reminders for important pet-care activities. |  |
| Step 3\.  Metric |  Measurement Proposed target Successful completion of core tasks At least 60% User satisfaction At least 60% Reduction in time spent locating pet-care information At least 20%  |  |
|  | Starting point: To be established through a baseline survey and task test with participating pet owners before using PawPal. |  |
| Step 4\.  Time frame | By project completion and final user acceptance testing (ITPM Weeks 11–14). |  |
| Step 5\.  Agreement | Agreement: All five Group 1 members and the project lecturer. Beneficiaries: Participating pet owners. Responsibility: All five group members, coordinated by the group leader. |  |
| Proposed MOV Statement | To improve customer convenience and operational efficiency for pet owners by developing PawPal, a centralised pet-care management application that enables users to organise pet profiles, health records, care schedules and reminders, targeting at least 60% successful completion of core tasks, 60% user satisfaction and a 20% reduction in time spent locating pet-care information by the end of the project (Weeks 11–14). |  |

## **3.1 Proposed MOV targets**

| MOV element | Proposed target and measurement approach |
| :---- | :---- |
| User satisfaction | At least 60% of surveyed users indicate that PawPal is satisfactory or useful after a prototype demonstration or usability test. |
| Information-locating time | A 20% reduction in the time users spend locating selected pet-care information when comparing their current method with the PawPal prototype. |
| Evaluation timing | By project end, during Weeks 11-14, after core workflows are available for demonstration and testing. |
| Status of figures | These are proposed planning targets that require validation. The group must agree the survey scale, participant sample, baseline task, timing method and evidence before treating the figures as final. |

## **Rationale**

The satisfaction target tests whether the proposed features are genuinely useful to intended users rather than only technically complete. The time-reduction target addresses the project problem directly: pet owners may currently search across notes, calendars, messages and separate services. Measuring a small, repeatable set of tasks before and after using PawPal can show whether the application makes that process more efficient. These measures are proposed targets, not achieved results, and should be revised if user validation establishes a different baseline or feasible threshold.

# 

# **4\. Scope Statement**

This scope statement defines the initial PawPal release for the CSS3453 and CSS3344 group project. It is intentionally limited to a practical mobile pet-care organiser with a small, administrator-managed service directory. The scope is designed to give a five-member team a clear, demonstrable product while keeping delivery manageable within the assignment schedule. This section is kept within the maximum three-page scope-statement limit.

## **4.1 Scope overview and in-scope deliverables**

| Scope area | Included in the initial release |
| :---- | :---- |
| Access and pet management | Secure user registration and login, plus creation, viewing, editing and deletion of multiple pet profiles. |
| Care organisation | Care schedules, reminders, appointment records and vaccination records entered and managed by the user. |
| Service discovery | Nearby pet-service discovery through a map or list, GPS where permission is granted, and a manual-search fallback. Initial coverage is limited to an agreed pilot area. |
| Offline and low-end-device support | Local caching of agreed essential records, efficient loading, compressed images and testing on at least one available lower-spec Android device. |
| Web administration | A web admin panel for authorised management, verification and updating of service listings and location details. |

## **4.2 Out of scope and constraints**

| Boundary | Decision and rationale |
| :---- | :---- |
| Medical advice | AI diagnosis, treatment recommendations and online veterinary consultations are excluded. PawPal records user-entered information but does not replace professional veterinary advice. |
| Commercial transactions | Payment processing, full online booking and complete clinic-management functions are excluded because they introduce additional security, regulatory and operational complexity. |
| Advanced integrations | Wearable-device integration, automatic health monitoring, shared family access, ratings and reviews, and extensive social functions are deferred as optional future enhancements. |
| Hardware limitation | The application must remain practical on older or lower-end Android devices. This constrains image sizes, background activity, animations, data loading and map use. |

## **4.3 Scope rationale and control**

The included features directly support the stated problem: organising pet information, remembering care activities and locating relevant services. The exclusions prevent scope creep and avoid presenting PawPal as a clinical, telemedicine or payment platform. Any request that changes these boundaries should be recorded, assessed for time, skill, privacy and hardware impact, and approved by the group before it is added to the project plan.

# 

# **5\. Related SDG and PCDS 2030**

PawPal is aligned with the following broader policy directions. This alignment explains the relevance of the project; it does not claim that PawPal alone achieves the targets of either framework.

| Framework | Related direction | Alignment rationale |
| :---- | :---- | :---- |
| Sustainable Development Goal 9 (SDG 9 – Target 9.1) | Industry, Innovation and Infrastructure | PawPal has an indirect connection to SDG Target 9.1 through its focus on improving access to digital information and local pet-related services. The application provides a centralized platform where pet owners can manage pet-care records, schedules and reminders, as well as discover nearby veterinary clinics, pet shops and grooming services. Its offline caching and optimisation for lower-end Android devices aim to make essential information more accessible to users with different device capabilities. Although PawPal does not directly develop physical infrastructure, it demonstrates how digital technology can support accessibility and service discovery within local communities. |
| PCDS 2030 | Digital Transformation | The project moves fragmented, everyday pet-care information toward a more accessible digital workflow through mobile records, reminders, offline access and an administrator-managed directory. It supports the direction of digital transformation without claiming to fulfil PCDS 2030 outcomes. |

## **Rationale**

The proposed application demonstrates how a focused digital solution can improve information accessibility and everyday service discovery. The alignment is therefore framed as contribution and relevance, not as proof that national or global development targets have been achieved. The group should keep this distinction in presentations, reports and evaluation claims.

# 

# **6\. Proposed Main Modules**

| Module | Purpose and example functions |
| :---- | :---- |
| Pet Profile Management | Create and manage multiple pet profiles with name, species, breed, age, gender, photo, and basic information. |
| Pet Care Scheduler | Organise feeding, grooming, bathing, and other recurring care activities. |
| Appointment & Health Records | Store and manage veterinary appointment and vaccination records with reminders and uploaded attachments (health documents or photos). Weight tracking is a future enhancement. No diagnosis is provided. |
| Nearby Pet Services | Discover nearby veterinary clinics, pet shops, grooming centres, pet parks, and pet-friendly facilities. |
| Reminder & Notification Centre | Receive reminders for appointments, vaccinations, grooming, and recurring care activities. |
| Pet Journal (optional) | Upload photos and record activities, memories, or milestones. |

# **7\. Suggested App Navigation**

| Screen | Main content |
| :---- | :---- |
| Home Dashboard | Pet overview, upcoming appointments, and care activities due soon. |
| My Pets | Pet profiles and related records. |
| Care Schedule | Calendar or list of appointments and recurring routines. |
| Explore | Map and list of nearby pet-related services. |
| Notifications | Upcoming and previous care reminders. |

# 

# **8\. Mapping to the Six Compulsory CSS3344 Features**

The CSS3344 assignment brief requires the six features below. The following table shows one practical way to implement each feature within PawPal.

| Compulsory feature | Proposed PawPal implementation |
| :---- | :---- |
| Secure Authentication System | User registration and login, secure token handling, and logout. |
| MVVM/BLoC Dashboard | Reactive dashboard showing pet profiles, upcoming appointments, and care activities from API endpoints. |
| Location-Aware Feature | GPS/map-based discovery of nearby veterinary clinics, pet shops, groomers, and pet parks. |
| Interactive Data Submission | Validated forms for pet profiles and records; camera/gallery upload for pet photos and relevant attachments. |
| Local Offline Caching | SQLite/local storage for essential pet profiles, saved appointments, and previously retrieved service information. |
| Asynchronous Notifications | Local or push reminders for vaccinations, appointments, grooming, and recurring care. |

# **9\. Proposed Web Admin Panel**

| Admin module | Proposed functions |
| :---- | :---- |
| Admin Dashboard | Overview of registered users, pets, and service listings. |
| User Management | View and manage user accounts and review reported accounts where appropriate. |
| Pet Service Management | Add, edit, verify, or remove veterinary clinic, pet shop, grooming, and other service listings. |
| Location Management | Maintain service addresses and GPS coordinates. |
| Content Management | Manage pet-care articles, categories, and announcements **if** this feature is included. |
| Report Management | Review user-submitted corrections, inappropriate content, or inaccurate listings. |

For the initial version, a separate veterinary clinic portal and a complete online booking system are not recommended. The admin panel can manage the service directory centrally.

# 

# **10\. Existing Solutions and Differentiation**

Initial competitor research indicates that several established apps already provide pet profiles, reminders, vaccination or medical records, and appointment-related functions. Therefore, PawPal should not claim that these basic features are unique.

| Existing solution | Relevant capabilities identified in initial research | Implication for PawPal |
| :---- | :---- | :---- |
| [11pets](https://www.11pets.com/en/home) | Pet-care records, preventive-care schedules, vaccination/deworming reminders, hygiene and other care tracking, and professional-related features. | Pet profiles and care reminders are established features; investigate the exact scope of its service directory and local coverage. |
| [Pet Care Tracker \- Dog Cat App](https://www.dogcat.app/en) | Pet profiles, feeding schedules, medication reminders, vaccination tracking, vet appointment records, weight monitoring, health logs and offline access. | Demonstrates the value of combining daily pet-care activities and health tracking; PawPal can explore nearby pet-service discovery and a simple user experience. |
| [PawPulse: Pet Reminder](https://play.google.com/store/apps/details?id=com.optimalabs.petcareplus&hl=en)  | Multiple pet profiles, feeding and medication schedules, vaccination reminders, veterinary visit tracking, weight and health logs, recurring notifications and offline functionality. | Highlights the importance of timely pet-care reminders and offline accessibility; PawPal can differentiate through integrated pet-service discovery and centralised management. |

## **Potential differentiation to validate**

* Local pet-service discovery across several service types, rather than relying only on a user's existing veterinary provider.  
* A single organiser for multiple pets, everyday care schedules, appointments, and saved service information.  
* A lightweight experience designed to remain practical on older or lower-end Android devices.

These are proposed positioning points, not confirmed market gaps. The group should verify them through competitor research and feedback from local pet owners before presenting them as differentiators.

# **11\. Fit with CSS3453 IT Project Management**

| Project phase | How PawPal can be addressed |
| :---- | :---- |
| Initiating | Interview pet owners; document current ways of managing pet records and appointments; define the business case, stakeholders, feasibility, risks, and measurable organisational value. |
| Planning | Define scope, methodology, WBS, Gantt chart, budget, resources, risk register, quality plan, communication plan, and change-control approach. |
| Executing | Build the Flutter app and web admin panel; record sprint/milestone progress, task ownership, meetings, effort, and actual costs. |
| Monitoring & Controlling | Compare actual progress, effort, cost, and quality against the plan; update risks and revise schedule/budget when required by the Week 8 risk event. |
| Closing | Evaluate results against the MOV; report final schedule and cost performance, lessons learned, methodology reflection, scalability, and individual reflections. |

The CSS3453 brief requires the group to use the same app topic as CSS3344 and to demonstrate project-management evidence throughout the project. The Week 8 risk card must be treated as a real project event and reflected in the management plan; it does not change the CSS3344 app requirements.

# **12\. Hardware Limitations Constraint**

The group's assigned constraint is **Hardware Limitations**: the application should remain usable on older or lower-end devices with limited processing power and memory.

* Compress images before upload and use small thumbnails in service listings.  
* Use pagination or lazy loading for long service lists.  
* Cache essential pet profiles and appointments locally using SQLite.  
* Avoid unnecessary animations, heavy transitions, and resource-intensive screens.  
* Load map information only when the user opens the Explore feature; avoid continuous location tracking.  
* Optimise API calls and background work, and provide a manual-search fallback if GPS is unavailable.  
* Support offline access to cached information and consider queuing eligible changes for synchronisation when connectivity returns.

# **13\. Key Risks and Possible Responses**

| Risk | Possible response |
| :---- | :---- |
| Inaccurate or outdated service listings | Use admin verification, display last-updated information, and allow users to report corrections. |
| Privacy of pet and owner information | Apply access controls, secure data transmission/storage, and avoid collecting unnecessary personal information. |
| Incorrect reminder dates | Use dates entered by users, encourage checking against official veterinary records, and state that the app does not provide medical advice. |
| GPS unavailable or inaccurate | Provide manual location search and allow users to select a location on the map. |
| Limited local service coverage | Start with a defined city or service area and expand the directory gradually. |
| Poor performance on low-end devices | Compress images, limit background tasks, paginate data, and test on lower-spec Android devices. |

# 

# **14\. Proposed Technical Direction**

| Area | Possible direction |
| :---- | :---- |
| Mobile application | Flutter for Android. |
| Architecture/state management | MVVM or BLoC, selected and justified by the group. |
| Backend | REST API and cloud database. |
| Local storage | SQLite/local storage for offline caching. |
| Location | GPS and map integration, with manual search fallback. |
| Notifications | Local notifications and/or push notifications. |
| Administration | Web-based admin dashboard for users and service listings. |

These are suggested technical choices. The group should confirm the final stack based on its skills, project schedule, cost, and the assignment requirements.

# **15\. Validation Before Finalising the Proposal**

* Interview approximately 5–10 pet owners about how they currently manage appointments, vaccination dates, grooming, and service discovery.  
* Ask which parts of the process are inconvenient and whether a single app would genuinely help.  
* Compare at least three existing solutions in detail and review 8–12 relevant sources for the CSS3453 literature review.  
* Check whether local pet-service information can be collected, verified, and maintained within the group's time and budget.  
* Test the proposed features on an older or lower-end Android device to assess performance.

# 

# **16\. Short Project Summary**

PawPal is a proposed mobile application under T11 – Productivity & Lifestyle App. It aims to help pet owners organise everyday pet-care responsibilities through pet profiles, care schedules, appointment and vaccination records, nearby pet-service discovery, and reminders. By combining a personal care organisation with a local pet-service directory, PawPal seeks to provide a convenient way for users to manage multiple aspects of pet ownership. The project will be designed with offline access and performance optimisation in mind so that it can remain usable on older or lower-end Android devices.

# **Reference and Assignment Notes**

Assignment basis: CSS3344 Mobile Application Development Group Assignment Project Brief and CSS3453 IT Project Management Assignment Brief supplied in the project conversation. Confirm the exact wording, deadlines, and submission rules against the latest lecturer-provided copies before submission.

# **17\. SMART Project Objectives**

The following objectives are proposed for discussion. They should be refined after the group validates the problem with pet owners and confirms the final MVP scope. The targets below are suggested planning targets, not achieved results or lecturer-approved commitments.

| Objective area | Proposed SMART objective | How it could be measured |
| ----- | ----- | ----- |
| Pet profile management | By the end of development, deliver a feature allowing an authenticated user to create, view, update and delete pet profiles, including more than one profile per account. | Test create, view, update and delete; test multiple profiles under one account. |
| Care scheduling and reminders | Before the final demonstration, allow users to create and view care activities and receive reminders at configured times for supported schedules. | Test one-time and recurring activities and record reminder test outcomes. |
| Pet records | Before the final demonstration, allow users to save and retrieve appointment and vaccination information for their pets. | Test record creation, editing, viewing and association with the correct pet. |
| Nearby service discovery | For the agreed pilot area, provide searchable map or list results for verified pet-service listings with location details. | Count verified listings in the agreed area; test GPS and manual-search flows. |
| Low-end device usability | Before final submission, test core workflows on at least one available lower-spec Android device and resolve high-priority performance issues found. | Record device details, test scenarios, issues and retest outcomes. |

 

Recommendation: After user validation, select a small number of measurable targets that are realistic and can be evidenced. Avoid promising user counts, listing counts or performance percentages before establishing a baseline.

# **18\. Stakeholder Identification**

Stakeholders are people or groups who influence the project, use its outputs, provide information, or are affected by the application. This is an initial stakeholder register for discussion.

| Stakeholder | Interest / expectations | Potential involvement |
| :---- | :---- | :---- |
| Pet owners (primary users) | Convenient pet profiles, schedules, records, reminders and useful nearby services. | Provide interview feedback, validate workflows and participate in usability testing. |
| Project team | Clear requirements, achievable scope, manageable workload and successful delivery. | Analyse, design, develop, test, document and manage the project. |
| Course lecturers | Evidence that course requirements and assessment deliverables are met. | Provide guidance, review progress and assess submissions. |
| System administrator | Accurate, appropriate and maintainable service-directory information. | Manage listings, verify details and review reports. |
| Pet-service providers | Accurate representation of business details and contact information. | Potentially confirm business details or request corrections; participation is not assumed. |
| Other household members / caregivers | Access to relevant pet-care information where the owner chooses to share it. | Possible future users if shared access is included; not required for the MVP. |

 

Recommendation: Treat pet owners, the project team, lecturers and the administrator as core stakeholders initially. Do not assume service providers will actively use the system unless their willingness is validated.

# 

# **19\. Initial User Workflows and Use Cases**

These high-level workflows can later be converted into use-case diagrams, user stories, screen flows and acceptance criteria.

## **19.1 Register and access PawPal**

* The user opens PawPal and selects registration or login.  
* The user enters credentials and submits the form.  
* The application validates the input and communicates with the authentication API.  
* After successful authentication, the user is taken to the Home Dashboard.

## **19.2 Create and manage a pet profile**

* The user opens My Pets and selects Add Pet.  
* The user enters required pet details and optionally selects a photo.  
* The application validates and saves the profile through the backend.  
* The pet appears in the user's pet list and can be viewed or edited later.

## **19.3 Record a care activity or appointment**

* The user selects a pet and opens Care Schedule or Records.  
* The user enters the activity or appointment details, date, time and relevant notes.  
* The application validates and saves the information.  
* The activity appears on the dashboard or schedule, and a reminder is configured where applicable.

## **19.4 Discover a nearby pet service**

* The user opens Explore and grants location permission, or chooses manual location search.  
* The application retrieves relevant service listings for the selected area.  
* The user views results as a map or list and opens a listing for its address and contact details.  
* The user can report information that appears incorrect or outdated.

## **19.5 View essential information offline**

* The user opens PawPal while internet connectivity is unavailable.  
* The application displays previously cached pet profiles and supported records.  
* If offline editing is supported, changes are stored locally and marked as pending synchronisation.  
* When connectivity returns, eligible changes are synchronised and conflicts are handled safely.

Scope recommendation: Prioritise offline viewing of essential cached data. Offline editing and conflict resolution add complexity and should only be included if the team has sufficient time.

# 

# **20\. Initial Non-functional Requirements**

Non-functional requirements describe how well PawPal should operate. The following are proposed requirements to refine during planning and testing.

| Area | Proposed requirement / expected behaviour |
| :---- | :---- |
| Performance | Core screens should remain responsive on the selected lower-spec Android test device. Avoid unnecessary animations, large images and excessive API requests. |
| Usability | Use consistent navigation, readable text, clear form labels and understandable validation messages. |
| Security and privacy | Require authentication for personal records, restrict users to their own pet data, use secure network communication and avoid unnecessary personal information. |
| Offline availability | Make agreed essential cached information available without a network connection and communicate when data may be out of date. |
| Reliability | Validate dates and required fields; handle network failures and notification-permission denial gracefully. |
| Maintainability | Use a consistent architecture, reusable components, documented APIs and version-control practices. |
| Compatibility | Define and test a realistic minimum Android version and device profile based on the group's development environment. |
| Location and permissions | Request location access only when Explore is used and provide manual search when permission is denied or GPS is unavailable. |

 

Recommendation: Convert these into testable acceptance criteria during planning. Avoid exact response-time or compatibility guarantees until test devices are selected and the application is measured.

# 

# **21\. Data Sources and Admin Management**

The nearby pet-service directory is a key part of PawPal's proposed value. Its usefulness depends on the accuracy, coverage and maintenance of listing information.

## **21.1 Proposed initial data approach**

* Start with a clearly defined pilot area rather than attempting to cover all of Sarawak or Malaysia.  
* Create an initial list of relevant clinics, pet shops and grooming services using information that can be checked.  
* Record necessary listing fields such as business name, category, address, coordinates, contact details and last-verified date.  
* Have an administrator review and approve listings before they appear as verified.  
* Provide a way for users to report incorrect or outdated details.

## **21.2 Suggested listing management workflow**

| Step | Action | Responsible party |
| :---- | :---- | :---- |
| 1\. Collect | Gather a candidate listing and publicly available business details. | Admin / project team |
| 2\. Verify | Check name, category, address, contact details and map location where possible. | Admin |
| 3\. Publish | Add the verified listing to the service directory. | Admin |
| 4\. Review | Check user-submitted reports or correction requests. | Admin |
| 5\. Update | Correct, re-verify or deactivate outdated information. | Admin |

 

Recommendation: For the MVP, use admin-managed listings. User-submitted business listings, provider accounts, booking and complex review moderation can be considered later. Distinguish verified information from information not yet checked.

# 

# **22\. Initial User Validation Plan**

Before finalising the proposal, gather feedback from a small number of pet owners. This helps test whether the problem is real and whether the proposed features are useful.

## **22.1 Suggested approach**

* Interview approximately 5–10 pet owners, if feasible, using a short and consistent set of questions.  
* Ask how they currently record vaccination dates, appointments, grooming and recurring care activities.  
* Ask how they currently find veterinary clinics, pet shops and grooming services.  
* Ask which current methods are inconvenient and what information they would want in one app.  
* Show the proposed feature list or simple screen sketches and ask which features are most valuable.  
* Record feedback without collecting unnecessary personal or sensitive information.

## **22.2 Suggested interview questions**

- How do you currently keep track of your pet's vaccination dates and veterinary appointments?  
- How do you remember recurring activities such as grooming or bathing?  
- How do you usually find nearby veterinary clinics, pet shops or grooming services?  
- What is the most inconvenient part of managing your pet's care?  
- Would pet profiles, care schedules, records, reminders and nearby service listings in one app be useful? Why or why not?  
- Which proposed features would you use most often, and which would you not need?  
- Would you expect to access your pet's basic information when your phone has no internet connection?

## **22.3 How to use the findings**

* Summarise recurring problems and feature preferences rather than relying on one person's opinion.  
* Identify features users consider essential, optional or unnecessary.  
* Adjust the MVP and problem statement based on the evidence.  
* Use the findings as supporting evidence in the CSS3453 business case and stakeholder analysis.

Important: Do not invent interview results or present proposed objectives as achieved outcomes. Record the actual date, participant profile in non-identifying terms, questions, responses and the group's conclusions.

