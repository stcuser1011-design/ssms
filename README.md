# SSMS — Smart School Management System

> A modern, modular school management platform for Sri Lankan schools, designed to digitize the real academic and administrative workflows schools currently manage manually.

## Project Goal

SSMS is not only a student-record website. It is a complete school management platform connecting admissions, classes, subjects, subject baskets, O/L and A/L pathways, examinations, promotion, student placement, timetable generation, attendance, assignments, notices, events, library, reports, analytics, security, and alumni history.

The system should behave like a normal school workflow while reducing repetitive manual work and preserving human approval where school policy requires it.

## User Roles

- **Admin** — system and school administration, academic configuration, users, teachers, classes, subjects, baskets, streams, timetable, examinations, reports, settings, permissions, analytics.
- **Secretary / Office Staff** — student admissions, student/parent records, class placement, permitted academic history, achievements, certificates, O/L/A/L historical records, leaving/completion records, parent linking, reports.
- **Teacher** — assigned classes/subject groups, attendance, assignments, marks, timetable, permitted student information.
- **Student** — own timetable, attendance, results, assignments, notices, achievements, certificates and permitted academic information.
- **Parent** — linked children's attendance, results, timetable, assignments, notices, achievements, certificates and permitted academic information.

## Official UI Theme

Clean, modern, professional blue + white with subtle glassmorphism. No excessive neon effects.

| Purpose | Hex |
|---|---|
| Primary Blue | `#2563EB` |
| Light Blue | `#3B82F6` |
| Accent Cyan | `#06B6D4` |
| Success | `#10B981` |
| Warning | `#F59E0B` |
| Danger | `#EF4444` |
| Background | `#F8FAFC` |
| Surface | `#FFFFFF` |
| Primary Text | `#0F172A` |
| Secondary Text | `#64748B` |
| Border | `#E2E8F0` |

- Inter is the primary UI font.
- Poppins may be used for selected branding/headings.
- Glass effects must remain subtle and readable.
- Responsive desktop/tablet/mobile layouts are required.

## Technical Direction

- PHP 8+
- OOP + lightweight MVC-like architecture
- MySQL/MariaDB with InnoDB
- HTML5, CSS3, Vanilla JavaScript
- Fetch/AJAX where useful
- Apache
- Prepared statements and secure server-side authorization
- No unnecessary frameworks

---

# 1. School Administration

Admin can configure the school without hard-coding school-specific rules:

- School profile
- Academic years and terms
- Grades
- Classes/sections
- Class capacity
- School days and periods
- Subjects and subject categories
- Subject groups
- Subject baskets
- O/L configuration
- A/L streams and subject combinations
- Optional subjects
- Teacher-subject assignments
- Rooms/resources where enabled
- Houses
- Departments
- School calendar and holidays
- Events
- Examination types
- Promotion rules
- Attendance rules
- Report settings

---

# 2. Student Lifecycle

```text
Admission
  ↓
Student Profile
  ↓
Grade/Class
  ↓
Subject Selection
  ↓
Subject Basket / Group Allocation
  ↓
Attendance + Exams + Assignments
  ↓
Promotion Analysis
  ↓
Next Grade/Class
  ↓
O/L pathway
  ↓
A/L Stream + Subjects
  ↓
A/L Results
  ↓
Completed / Left
  ↓
Alumni
```

Historical class and academic records must never be deleted simply because a student is promoted.

---

# 3. Academic Structure and Subject Configuration

## 3.1 Grades and Classes

Admin creates school grades and sections, for example:

```text
Grade 10
├── 10-A
├── 10-B
├── 10-C
└── 10-D
```

Each class can have configurable capacity, class teacher, medium, academic year and active status.

## 3.2 Subjects

Subjects are configurable records, not hard-coded pages. Each subject can have:

- Code
- Name
- Category
- Grade availability
- Medium
- Required/optional status
- Weekly period requirement
- Single/double-period requirement
- Active years/terms
- Teacher assignments
- Basket/group eligibility

## 3.3 Subject Categories

Examples:

- Core/Common
- Optional
- Basket
- O/L
- A/L
- Practical
- Language
- Religious
- School-specific

The school can create additional categories.

---

# 4. O/L Subject Basket Management

**Important requirement:** Admin must be able to configure O/L subject baskets before student placement, normally when students reach **Grade 10**, instead of hard-coding a fixed basket structure.

Admin workflow:

```text
Admin
 ↓
Academic Management
 ↓
Grade 10 / O/L Setup
 ↓
Create Basket
 ↓
Add Subjects
 ↓
Set Selection Rules
 ↓
Publish for Student Selection
```

A basket can contain configurable subjects and rules such as:

- Basket name/code
- Description
- Grade/year
- Minimum selections
- Maximum selections
- Exactly-one selection where required
- Multiple selections where allowed
- Allowed subjects
- Subject capacity
- Subject group rules
- Timetable compatibility rules
- Active/inactive status

The exact subjects are **school-configurable** and must not be assumed to be identical in every school.

### Student Basket Selection

When a Grade 10/O/L student is ready for subject selection, SSMS shows only valid configured choices. The system validates the student's selection against basket rules before saving.

The system records:

- Academic year
- Student
- Basket
- Selected subject(s)
- Selection status
- Submitted date
- Approval status where the school requires approval
- Change history

---

# 5. A/L Stream and Subject Management

Admin must be able to create and configure A/L streams and their subjects.

Example structure:

```text
A/L
├── Science
│   ├── Biology
│   ├── Chemistry
│   └── Physics
│
├── Mathematics
│   ├── Combined Mathematics
│   ├── Physics
│   └── Chemistry
│
├── Commerce
│   ├── Accounting
│   ├── Business Studies
│   └── Economics
│
└── Arts
    └── School-configured subject combinations
```

The example is illustrative. Admin controls the actual subjects and combinations used by the school.

A/L configuration supports:

- Stream name/code
- Academic year
- Allowed subjects
- Required subject count
- Optional subjects
- Subject combinations
- Capacity per stream/group
- Eligibility rules where the school uses them
- Teacher assignments
- Weekly periods
- Practical/double-period requirements
- Group creation rules

Students can select an A/L stream and valid subjects according to the school's configured rules. Invalid combinations cannot be submitted.

---

# 6. Optional Subject Management

Admin can create optional subjects for any configured grade/level.

Each optional subject can define:

- Eligible grades
- Selection window
- Minimum/maximum class size
- Teacher requirements
- Room/resource requirements
- Basket membership
- Stream membership
- Weekly periods
- Whether approval is required

---

# 7. Student Placement / Class Allocation Engine

SSMS must support the real school workflow where students are grouped based on their subject choices instead of simply being placed randomly.

## Important distinction

A **Home Class / Section** and a **Subject Group** are different concepts.

Example:

```text
Home Class: 11-A

Common lessons:
  Mathematics → 11-A
  Science → 11-A

Subject groups:
  ICT → ICT Group 01
  Business → Business Group 01
```

A student can therefore belong to one home class while joining different subject groups for optional/basket subjects.

## Automatic placement flow

```text
Students
   ↓
Promotion / Grade
   ↓
Subject and Basket Selections
   ↓
Validate combinations
   ↓
Group students by compatible selections
   ↓
Apply class/group capacity
   ↓
Apply teacher availability
   ↓
Apply room/resource constraints where enabled
   ↓
Generate placement proposal
   ↓
Conflict / capacity checks
   ↓
Admin/Secretary review
   ↓
Manual adjustments if required
   ↓
Confirm placement
```

The engine should consider:

- Student subject selections
- Basket rules
- A/L stream and combination rules
- Home class capacity
- Subject group capacity
- Teacher availability
- Teacher-subject assignments
- Rooms/resources where enabled
- Language/medium where configured
- Existing class structure
- School-specific placement rules
- Balanced distribution where the school enables it

It must prevent duplicate placement and invalid subject combinations.

### Manual school control

Automatic placement is a proposal, not an irreversible action. Authorized staff can review and move students before confirmation.

A validation screen should show:

- Capacity violations
- Invalid combinations
- Missing teacher assignment
- Missing room/resource where required
- Students without a valid placement
- Duplicate subject/group assignment
- Timetable conflicts where detectable

Only a validated allocation should be confirmed.

---

# 8. Automatic Grade Promotion

At the end of an academic year, SSMS can analyze promotion according to school-configured rules.

```text
Current Grade/Class
      ↓
Results + Attendance + Configured Rules
      ↓
Promotion Analysis
      ↓
PROMOTE / REVIEW / REPEAT
      ↓
Admin Approval
      ↓
Next Academic Year
      ↓
New Grade/Class Placement
```

The system must preserve the old class history. Promotion should not erase previous enrollment records.

The school can configure whether results, attendance, failed subjects or other factors affect automatic recommendation. Final approval remains controlled by authorized staff.

---

# 9. Examination and Results

Support:

- School exams
- Term tests
- Mid-year/final exams
- O/L results
- A/L results
- Marks
- Grades
- Result publication
- Historical results
- Result verification
- Reports

Protected live marks workflows remain controlled by appropriate academic permissions.

---

# 10. Attendance

- Student attendance
- Teacher/staff attendance where enabled
- Daily/period attendance
- Class attendance
- Attendance reports
- Parent visibility
- Attendance summaries for reports/promotion where configured

---

# 11. Timetable

Sri Lankan school schedule configuration:

- 8 periods/day
- 40 minutes/period
- School starts 7:30 AM
- Teaching starts 7:50 AM
- Period 4 ends 10:30 AM
- Interval 10:30–10:50 AM
- School ends 1:30 PM

Automatic generator uses classes, subject groups, teacher assignments, weekly period requirements, availability, rooms/resources, workload and scheduling rules.

States:

- `DRAFT`
- `REVIEW`
- `PUBLISHED`

Double periods are first-class blocks. A double period reserves two consecutive periods and cannot cross the interval.

---

# 12. Assignments, Notices and Events

Assignments:

- Teacher creates assignment
- Assign to class/subject group
- Due date
- Student submission/status where implemented
- Parent/student visibility

Notices:

- School-wide
- Grade/class
- Teacher/student/parent targeted notices
- Publish/schedule

Events/calendar:

- Exams
- Sports
- Meetings
- Competitions
- School events
- Holidays
- Academic events

---

# 13. Student Complete Profile

```text
Student
├── Personal Information
├── Admission History
├── Parent / Guardians
├── Class History
├── Subject History
├── Subject Selections
├── Basket Selections
├── A/L Stream
├── Attendance
├── Examination Results
│   ├── School Exams
│   ├── O/L
│   └── A/L
├── Promotion History
├── Achievements
├── Certificates
├── Assignments
├── Timetable
├── Discipline Records
├── Activities
├── Clubs / Societies
├── Sports
├── Documents
├── Leaving / Completion Record
└── Alumni Record
```

---

# 14. Parent Portal

Parent registration uses Student Code + One-Time Parent Registration Code. Codes are single-use and securely stored. Student Code alone is never sufficient to claim an account.

One parent account can link to multiple children. Parent access is limited to linked students.

---

# 15. Teacher Management

Admin pre-registers teacher name, system generates a one-time secret registration code, and the teacher completes the account after matching the pre-registered name + code. Code is single-use and preferably hashed.

Teachers can be assigned to subjects, classes, subject groups, O/L groups, A/L groups and timetable periods.

---

# 16. Library

- Catalogue
- Books and copies
- Members
- Borrow/return/renew
- Due dates
- Overdue
- Lost/damaged states
- History
- Reports

---

# 17. Achievements and Certificates

Track school/zonal/provincial/national/international achievements, academic, sports, arts, clubs, scouts/cadets/guides, competitions, awards, positions, dates, organizers, descriptions and certificate files.

Files are stored on the server filesystem; the database stores metadata/path rather than file BLOBs.

---

# 18. Reports and Documents

Generate configurable reports such as student profile, class list, subject group list, basket selection list, O/L/A/L results, attendance, examinations, promotion analysis, class allocation, teacher workload, timetable, achievements/certificates, leaving/completion, library, events and analytics summaries.

Leaving/completion reports receive unique reference numbers such as `SSMS-EXIT-2026-000184`.

---

# 19. Advanced Dashboard and Analytics

Role-aware analytics can include student counts, class sizes, attendance, result/pass rates, subject performance, O/L/A/L summaries, promotion statistics, teacher workload, library statistics, event statistics and placement/capacity issues.

Analytics must respect record-level permissions and should not expose sensitive individual data to unauthorized roles.

---

# 20. Global Search

Search across permitted students, teachers, parents, classes, subjects, subject groups, baskets, achievements, certificates, results, library and events.

Exact Student Code and Admission Number matches receive high priority. Search results must be permission-filtered server-side.

---

# 21. Alumni

When students complete/leave, their history is retained and can be represented in an Alumni record. Alumni access is permission-controlled and privacy-aware.

---

# 22. Security and Audit

Required security includes authentication, RBAC, server-side authorization, CSRF protection, XSS-safe output, SQL injection protection, secure sessions, secure password hashing, secure random registration codes, private document protection, safe uploads, audit logging, backup/restore planning, and permission-filtered search/analytics.

Audit records should answer:

```text
WHO → user/account
WHAT → action
TARGET → record
WHEN → timestamp
RESULT → success/failure
```

---

# 23. Architecture Principles

Keep configuration separate from code. School-specific academic structures must be database/configuration driven.

The system must not assume every school has the same O/L baskets, A/L streams, optional subjects, class names or capacities. Admin configures them.

Automatic engines should produce reviewable proposals. Authorized staff retain final approval over promotion, class placement, subject allocation and publication where school policy requires it.

All important academic history is history-aware; promotion must never destroy previous class or subject history.
