# SSMS — Smart School Management System

> A modern, modular school management platform designed for Sri Lankan schools.

## 📌 Project Overview

**SSMS (Smart School Management System)** is a web-based platform for managing day-to-day academic and administrative operations from one centralized system.

### User Roles

- **Admin** — manages school settings, users, teachers, classes, subjects, timetable, attendance, examinations, reports, notices, and system permissions.
- **Secretary / Office Staff** — manages student and parent records, student admissions, student profile records, achievements, certificates, examination history, O/L and A/L results, leaving/completion records, parent accounts, and student-parent linking. This role reduces the administrative workload of managing a large student population.
- **Teacher** — manages assigned classes, attendance, assignments, marks, timetable, and permitted student information.
- **Student** — views timetable, attendance, results, assignments, notices, achievements, certificates, and permitted academic information.
- **Parent** — monitors linked students, attendance, results, timetable, assignments, notices, achievements, certificates, and permitted academic information.

---

# 🎨 Official UI Theme

This section is the **visual source of truth** for future SSMS implementation.

## Design Style

**Clean • Modern • Professional • Light Glassmorphism**

The interface should feel like a modern school-management SaaS platform: professional for administrators and teachers, simple and friendly for students and parents.

### Core Design Principles

- Clean white surfaces
- Professional blue primary color
- Soft light-blue application background
- Subtle glassmorphism
- Rounded cards and controls
- Light shadows and borders
- Strong readability
- Spacious layouts
- Responsive desktop/tablet/mobile design
- Avoid excessive neon effects
- Prioritize usability over decoration

## 🎨 Official Color Palette

| Purpose | Hex | Usage |
|---|---|---|
| **Primary Blue** | `#2563EB` | Main actions, active navigation, links |
| **Light Blue** | `#3B82F6` | Hover states and secondary blue elements |
| **Accent Cyan** | `#06B6D4` | Highlights and accents |
| **Success Green** | `#10B981` | Success/active states |
| **Warning Amber** | `#F59E0B` | Warnings/pending states |
| **Danger Red** | `#EF4444` | Errors/destructive actions |
| **Background** | `#F8FAFC` | Main application background |
| **Surface** | `#FFFFFF` | Cards, panels, modals |
| **Text Primary** | `#0F172A` | Headings and important text |
| **Text Secondary** | `#64748B` | Descriptions and secondary text |
| **Border** | `#E2E8F0` | Borders/dividers |

### CSS Theme Variables

```css
:root {
    --primary: #2563EB;
    --primary-light: #3B82F6;
    --accent: #06B6D4;
    --success: #10B981;
    --warning: #F59E0B;
    --danger: #EF4444;
    --background: #F8FAFC;
    --surface: #FFFFFF;
    --text-primary: #0F172A;
    --text-secondary: #64748B;
    --border: #E2E8F0;
    --shadow: 0 4px 20px rgba(15, 23, 42, 0.06);
    --radius-sm: 8px;
    --radius-md: 12px;
    --radius-lg: 16px;
}
```

## ✍️ Typography

- **Inter** is the primary UI font.
- **Poppins** may be used for selected headings or branding.
- Keep typography consistent and readable.

## 🧊 Glassmorphism

Glassmorphism must remain subtle and must not reduce readability.

```css
.glass {
    background: rgba(255, 255, 255, 0.72);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid rgba(255, 255, 255, 0.7);
    box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
}
```

Use glass effects mainly for floating panels, modals, headers, important dashboard widgets, login cards, and selected navigation elements.

## 🧭 Navigation Theme

Desktop uses a deep blue/navy sidebar with Dashboard, Students, Teachers, Parents, Classes, Timetable, Examinations, Attendance, Reports, and Settings as appropriate to the logged-in role. Mobile uses a compact drawer/navigation system.

## 🖥️ Dashboard Theme

```text
Background → #F8FAFC
Cards      → #FFFFFF
Primary    → #2563EB
Text       → #0F172A
Secondary  → #64748B
```

Dashboards should provide clear statistics, search, notifications, profile information, role indicators, and useful quick actions.

## 📅 Timetable Theme

The timetable must be highly readable and responsive.

### Sri Lankan School Schedule

- **8 periods per day**
- **40 minutes per period**
- School starts at **7:30 AM**
- First teaching period starts at **7:50 AM**
- Fourth period ends at **10:30 AM**
- Interval: **10:30 AM – 10:50 AM**
- School ends at **1:30 PM**

### Automatic Class–Subject–Period Matching

SSMS must support an **automatic timetable generation and matching system**. Admin should not have to manually select every Class + Subject + Teacher + Period combination.

The system should use configured academic data such as:

- Classes / sections
- Subjects
- Teacher-subject assignments
- Required periods per subject per week
- Teacher availability
- Class availability
- School days and periods
- Room/resource availability where enabled
- Teacher workload constraints
- Subject scheduling rules

The automatic generator should build a **DRAFT timetable**, validate it, and present it to the Admin for review before publication.

```text
Classes + Subjects + Teachers
             ↓
Subject Period Requirements
             ↓
Availability + Scheduling Rules
             ↓
Automatic Matching Engine
             ↓
Conflict Detection
             ↓
Generated DRAFT Timetable
             ↓
Admin Review / Manual Adjustment
             ↓
Final Conflict Check
             ↓
PUBLISH
```

### Timetable Matching Rules

The generator must prevent or minimize:

- Teacher conflicts — one teacher cannot teach two classes in the same period.
- Class conflicts — one class cannot have two subjects in the same period.
- Room/resource conflicts when rooms/resources are enabled.
- Duplicate assignments for the same class, subject, and period.
- Incorrect weekly subject-period counts.
- Invalid assignments during the school interval.
- Unavailable teacher/class periods.
- Unbalanced teacher workloads where the configured rules allow optimization.

The generator should prefer a well-balanced timetable rather than simply filling empty cells randomly.

### Double Period Support

A subject may require **double periods** (two consecutive periods treated as one longer lesson block). Double periods are a first-class timetable requirement, not an exception.

For example:

```text
Monday
Period 3 + Period 4 → Science (Double Period)
```

The automatic matching engine must reserve both consecutive periods together, ensure the teacher and class are available for both, and prevent another assignment from occupying either slot.

Admin should also be able to manually create or adjust double-period blocks after automatic generation. The system must validate double-period conflicts in the same way as normal single-period assignments.

### Timetable States

- `DRAFT` — generated or edited but not visible to normal users.
- `REVIEW` — ready for Admin review and adjustment.
- `PUBLISHED` — approved timetable visible to authorized Teachers, Students, and Parents.

Only a conflict-validated timetable should be publishable.

### Timetable Views

- Admin — automatic generator, draft review, manual adjustment, conflict display, and publish controls.
- Teacher — personal teaching timetable.
- Student — own class timetable.
- Parent — selected child's timetable.
- Desktop — weekly grid with days and periods.
- Mobile — day/card-based timetable view.
- Print — print-friendly class and teacher timetable.

## 📱 Responsive Design

SSMS must support desktop, laptop, tablet, and mobile layouts. Tables, forms, dashboards, navigation, and timetable views must adapt without becoming difficult to use.

---

# 🧩 System Modules

## Authentication & Authorization

- Login/logout
- Session management
- Password hashing
- Role-based access control
- Protected pages/actions
- Account status management

## Student Management

Students are managed by the **Secretary / Office Staff** role so the Admin does not need to manually handle thousands of student records.

### Student Registration / Admission Flow

1. Secretary opens **Students → Add Student**.
2. Secretary enters the student's school/admission information.
3. The system creates the student record and assigns the relevant academic year, grade, and class.
4. The system automatically generates a unique **Student Code** for the student.
5. The system automatically generates a unique **one-time Parent Registration Code** for that student.
6. The Secretary securely gives the Student Code and Parent Registration Code to the student's parent/guardian.
7. The parent can use those two codes during Parent Registration to claim and link the child automatically.
8. The student receives a system account/activation method according to the school's chosen student account policy.
9. The student can later log in and access only their own permitted academic information.

### Student Information

The student record can include:

- Admission / Student Number
- System-generated Student Code
- Full Name
- Date of Birth
- Gender where required by the school
- Grade
- Class / Section
- Academic Year
- Address
- Parent/Guardian relationship
- Student status
- Admission information
- Academic history
- Examination history
- O/L results
- A/L results
- Achievements and awards
- Certificates and supporting documents
- Leaving/completion information

### Student Profile & Achievement Records

Each student has a long-term profile that can preserve important school history from admission until leaving/completion.

### Achievements & Certificates

Authorized Office Staff/Secretary users can add or update permitted student achievement records, including:

- Academic achievements
- School-level achievements
- Zonal achievements
- Provincial achievements
- National achievements
- International achievements
- Sports achievements
- Arts/aesthetic achievements
- Clubs and societies
- Scouts/Cadets/Guides and similar activities
- Competitions and awards
- Positions/ranks received
- Achievement date
- Event/competition name
- Description
- Certificate/document attachment

Each achievement should record who added or updated it and when.

### Examination & Academic History

The student profile should preserve important academic results across the student's school years. Depending on the school's configuration and permissions, authorized Office Staff can maintain historical records such as:

- School examination results
- Term-test results
- Scholarship/external examination records where required
- **G.C.E. O/L results**
- **G.C.E. A/L results**
- Subject name/code
- Grade/result
- Marks where the school stores marks
- Examination year
- Attempt information where applicable
- Index/reference number where required by the school
- Result publication/verification status
- Supporting result document where permitted

Protected live marks-entry and result-publication workflows remain controlled by their designated academic permissions. Office Staff should not automatically receive unrestricted access to protected teacher/examiner workflows simply because they can maintain historical student profile records.

### Student Leaving / Completion Record

When a student completes school or leaves the school, the system should not delete the student's history. Instead, authorized staff can change the student status to an appropriate state such as **COMPLETED**, **LEFT**, or another configured status.

The system can then generate a **Student Leaving / School Completion Report** containing, where permitted:

- Student identity and Student Code
- Admission number
- Date of birth
- Date of admission
- Date of leaving/completion
- Final grade/class
- Academic years attended
- Academic/examination summary
- O/L results
- A/L results where applicable
- Attendance summary
- Achievements and awards
- Certificates recorded in the system
- School activities/organizations where permitted
- Exit/leaving reason where the school records one
- Authorized officer information
- Report/reference number
- Generated date

The original student record remains available in the **Student Records Archive** according to the school's retention policy.

### Student Management Rules

- Secretary can add, edit, search, filter, and manage permitted student records.
- Secretary can open a student profile only after server-side role/permission verification.
- Student lookup can use Student Code, Admission Number, student name, grade, or class.
- Student Code identifies the student but is not by itself a permission credential.
- Secretary can assign students to classes.
- Secretary can generate/reissue a parent one-time registration code where permitted.
- Secretary can view the status of a student's parent registration code without exposing the stored secret value.
- Secretary can maintain achievements, certificates, and permitted historical academic records.
- Secretary can generate authorized student reports and leaving/completion reports.
- Secretary can link students to parent accounts when an authorized manual correction is required.
- Admin retains system-level authority and permissions.
- Students cannot edit protected school/admission information themselves.

## Teacher Management

Teachers use a **pre-registration + self-completion** flow. A teacher cannot create an unrestricted public account.

### Teacher Pre-Registration

1. Admin opens **Teachers → Pre-Register Teacher**.
2. Admin enters the teacher's **full name**.
3. SSMS automatically generates a unique random **secret registration code**.
4. The pre-registration is stored with `PENDING` status.
5. Admin securely shares the generated code with that teacher.

### Teacher Registration

The teacher first enters:

- Pre-registered Full Name
- Secret Registration Code

SSMS verifies that both values match the **same PENDING pre-registration**. If successful, the remaining fields become available, such as email, phone, address, date of birth, qualification, username, and password. The verified pre-registered full name remains locked.

### Teacher Completion

```text
Admin Pre-Registers Teacher
          ↓
System Generates Unique Secret Code
          ↓
Admin Shares Code with Teacher
          ↓
Teacher Enters Full Name + Secret Code
          ↓
SSMS Verifies Both Against PENDING Record
          ↓
Teacher Completes Remaining Information
          ↓
Account Created
          ↓
Pre-registration → REGISTERED
          ↓
Teacher Can Login
```

The teacher secret code is one-time use, securely generated, preferably stored as a hash, and optionally expiry-controlled.

## Secretary / Office Staff Management

The **Secretary / Office Staff** role is specifically designed for schools with a large number of students, such as 3000+ students. It separates daily student/parent data entry from system administration.

### Office Staff Login & Student Verification

Office Staff use their own staff account and never log in as a student to edit a student's record.

```text
Office Staff Login
       ↓
Secretary / Office Dashboard
       ↓
Students → Search Student
       ↓
Student Code / Admission No. / Name / Grade / Class
       ↓
Open Student Profile
       ↓
Server-side role + permission check
       ↓
Authorized Profile Access
```

Student Code is a reliable student identifier, but it is **not** treated as a password or permission credential. Every profile action is authorized server-side.

### Secretary Responsibilities

- Add new students
- Edit permitted student profile information
- Search and filter students
- Open verified student profiles
- Manage admission information
- Assign students to grades/classes/sections
- Manage permitted student status fields
- Generate/reissue parent one-time registration codes where permitted
- Add parent records when manual parent management is required
- Edit parent contact information
- Link parents to students when authorized
- Support multiple children for one parent
- Maintain student achievements and awards
- Add/update certificate records and permitted certificate files
- Maintain permitted historical examination records
- Maintain **O/L results** and **A/L results** where the school assigns this permission
- Maintain other approved academic-history records
- Generate permitted student profile reports
- Generate Student Leaving / School Completion Reports
- View relevant student/parent reports
- View an audit history of changes made by Office Staff where permitted

### Secretary Restrictions

The Secretary must not have unrestricted access to:

- System settings
- Role/permission administration
- Admin account management
- Teacher pre-registration unless explicitly granted
- Timetable configuration unless explicitly permitted
- Sensitive system configuration
- Unrestricted live examination/marks workflows unless explicitly permitted
- Destructive changes to protected academic records

All Secretary actions must be checked server-side by the authorization layer and recorded in the activity/audit log where appropriate.

## Parent Management

Parent registration is designed around a **Student Code + One-Time Parent Registration Code** flow. This removes the need for the Secretary to manually create every parent account and manually link every child.

### Parent Registration — First Child

When the Secretary adds a student, SSMS automatically generates:

- A unique **Student Code** for that student.
- A unique **One-Time Parent Registration Code** for that student.

The Secretary gives both values to the student's parent/guardian through the school's approved communication method.

The Parent Registration page asks for:

- Student Code
- One-Time Parent Registration Code

The system verifies that the two values belong to the **same eligible student** and that the parent code is still unused and valid.

If verification succeeds:

1. The student identity is confirmed.
2. The parent completes their account/profile information.
3. The parent account is created.
4. SSMS automatically creates the `parent_student_links` relationship between the new parent account and that student.
5. The one-time parent code is immediately marked as used/invalidated.
6. The parent is taken to the Parent Dashboard with the child already available.

The parent must never be able to claim a student by Student Code alone.

### Parent Registration Flow

```text
Secretary Adds Student
          ↓
Student Record Created
          ↓
System Generates Student Code
          ↓
System Generates One-Time Parent Code
          ↓
Secretary Gives Both Codes to Parent
          ↓
Parent Registration
          ↓
Enter Student Code + One-Time Parent Code
          ↓
SSMS Verifies Matching Student + Unused Code
          ↓
Parent Completes Account Information
          ↓
Parent Account Created
          ↓
Child Automatically Linked
          ↓
One-Time Code Invalidated
          ↓
Parent Dashboard
```

### Add 2nd / 3rd / 4th Child

A parent must not create a new parent account for each child.

After the first registration, the Parent Dashboard provides an **Add Child** action.

```text
Parent Dashboard
       │
       ├── Child 1
       │
       ├── Child 2
       │
       ├── Child 3
       │
       └── + Add Child
```

When **Add Child** is selected, the parent enters:

- The new child's Student Code
- The new child's One-Time Parent Registration Code

SSMS verifies the pair. If valid, the new child is automatically linked to the **existing parent account**. The code is then invalidated so it cannot be reused.

The system should not impose an artificial four-child limit. It should support additional children through the same linking mechanism.

### Multi-Child Parent Dashboard

The Parent Dashboard should provide a clear child selector or child cards. After selecting a child, all child-specific information is scoped to that student:

- Attendance
- Results
- Timetable
- Assignments
- Notices
- Achievements
- Certificates
- Other permitted academic information

### Parent ↔ Student Linking Rules

- One parent account can be linked to multiple children.
- A child can have multiple parents/guardians where the school's policy requires it.
- Additional children are linked to the existing parent account; a duplicate parent account must not be created.
- A parent can see only children linked to that parent account.
- A parent cannot use a Student Code alone to claim or access a student.
- One-time parent registration codes are single-use and must be invalidated after successful linking.
- Codes should have an optional expiry period and may be reissued by authorized Secretary/Admin users when necessary.
- Code values should be generated securely and stored as hashes where practical; raw codes must not be exposed in URLs, page source, or logs.
- Linking and unlinking actions must be authorization-checked and audited.

### Parent Information

- Full Name
- Relationship to student
- Phone number
- Email where available
- Address
- Parent/guardian status
- Linked student records
- Account status

### Parent Access Rules

- Parent can view only linked children's information.
- Parent can switch between linked children.
- Parent can add another child only by providing the valid Student Code + One-Time Parent Registration Code for that child.
- Parent cannot edit protected academic records.
- Parent cannot view unrelated students.
- Multiple-child support is required.

## Class & Subject Management

- Grades/classes
- Sections
- Subjects
- Teacher-subject relationships
- Student-class relationships
- Subject weekly period requirements
- Double-period requirements where applicable

## Attendance

- Daily attendance
- Attendance records
- Teacher attendance entry
- Summaries
- Monthly/term statistics
- Attendance history

## Examinations & Results

- Examination setup
- Marks entry
- Grade calculation
- Results viewing
- Result summaries
- Academic performance reports
- Historical examination records
- G.C.E. O/L results
- G.C.E. A/L results
- Result verification/publication status

## Assignments

- Create assignments
- Assign to classes/subjects
- Due dates
- Assignment status
- Student assignment view

## Notices & Announcements

- School-wide notices
- Role/class-specific notices
- Publish/unpublish controls
- Notice history

## Student Achievements & Certificates

The Student Achievements & Certificates module keeps long-term non-academic and academic accomplishments inside the student profile.

Achievement records can include school, zonal, provincial, national, international, sports, arts, clubs, societies, Scouts/Cadets/Guides, competitions, awards, and other configured categories.

Each record can contain:

- Achievement category
- Achievement title
- Event/competition
- Level
- Position/award
- Date
- Description
- Certificate/document attachment
- Added by
- Updated by
- Created/updated timestamps

Students and authorized parents can view permitted achievement information. Office Staff/Secretary and Admin can add/update records according to permissions.

## Student Leaving & Completion Reports

SSMS should generate a formal report when a student completes school or leaves the school. The report can summarize the student's school history and, where permitted, include:

- Student identity
- Admission details
- Academic years attended
- Final grade/class
- Attendance summary
- Examination history
- O/L results
- A/L results where applicable
- Achievements and awards
- Certificates
- Activities/organizations
- Leaving/completion date and status
- Authorized officer details
- Unique report/reference number
- Generated date

The report should be printable and suitable for later PDF export. Archived student history must remain available according to the school's retention policy.

## Reports

- Student profile reports
- Attendance reports
- Examination/result reports
- O/L and A/L result summaries
- Student achievement reports
- Certificate/achievement lists
- Student leaving/completion reports
- Class reports
- Teacher reports
- Parent/student reports
- Timetable reports
- Academic summaries

---

# 🏫 Additional Approved SSMS Modules

The following modules are now part of the planned full SSMS scope. Existing modules are not duplicated; these sections define the additional capabilities approved for the system.

## 1. School Administration

SSMS should provide centralized school administration tools for authorized Admin users, including:

- School profile, name, contact information, logo, and official details
- Academic years and terms
- Grades, classes, sections, and class organization
- School calendar
- Public holidays and special school days
- Staff directory
- Staff leave management
- Staff attendance management
- Staff duty roster and assigned duties
- School-wide administrative settings
- Configurable school information used in reports and certificates

Administrative controls must remain protected by role and permission checks.

## 11. School Events & Calendar

SSMS should provide a school events system integrated with the school calendar.

Supported events can include:

- Sports meets
- Prize giving ceremonies
- Parent meetings
- School trips
- Competitions
- Workshops and seminars
- Clubs and society events
- School functions
- Examination-related dates
- Other configured school events

Events should support title, description, date/time, location, target audience, organizer, status, and optional attachments. Authorized users can publish or update events, while students, parents, teachers, and staff see only events relevant to them.

## 14. Library Management

SSMS should include a complete school library module.

Core capabilities:

- Book catalogue
- Book title, author, ISBN/reference, category, publisher, and edition information
- Multiple physical copies of the same title
- Copy/barcode/reference tracking
- Student and teacher library members
- Book issue/checkout
- Book return
- Due dates
- Renewal where permitted
- Overdue tracking
- Lost/damaged status
- Borrowing history
- Search and filtering
- Library availability status
- Library reports and statistics

Library access must be permission-controlled, and student/teacher borrowing history should be visible only to authorized users and the relevant account holder where applicable.

## 20. Advanced Dashboard & Analytics

SSMS dashboards should provide role-specific analytics rather than only static counters.

Admin analytics can include:

- Total students, teachers, parents, and classes
- Student distribution by grade/class
- Daily/monthly attendance trends
- Examination performance summaries
- Upcoming examinations and events
- Recent achievements and certificates
- Student leaving/completion statistics
- Recent system activity
- Data-quality or pending-action indicators

Secretary dashboards can focus on admissions, student records, parent links, pending data tasks, and profile updates. Teacher dashboards can focus on teaching workload, attendance, assignments, and results. Student and Parent dashboards should show useful personal/linked-child summaries.

Analytics must respect role permissions and must not expose unrelated student data.

## 22. Alumni Management

Students who complete or leave the school can optionally transition into an Alumni record without deleting their historical school data.

Alumni capabilities can include:

- Alumni profile created from the archived student record
- Leaving/completion year
- Admission and school history
- Final grade/class
- Academic history
- O/L and A/L results where permitted
- Achievements and activities
- Certificate history
- Alumni status
- Contact information where the school chooses to maintain it
- Alumni search and directory
- Alumni reports

The alumni system must preserve the original student record and follow the school's retention and privacy policies.

## 24. Global Search & Advanced Data Discovery

SSMS should provide a fast, permission-aware global search experience.

Search targets can include:

- Student Code
- Admission Number
- Student name
- Teacher name
- Parent name
- Class/section
- Subject
- Achievement title/event
- Certificate title/reference
- Examination/result records where authorized
- Library records where authorized
- School events

Search results must be filtered by the authenticated user's permissions. A search result must never become a way to bypass normal record-level authorization.

The search system should support:

- Debounced live search
- Exact and partial matching
- Filters
- Sorting
- Pagination
- No-result states
- Keyboard-friendly navigation
- Mobile-friendly search
- Fast database indexes for common search fields

---

# 🧩 Full SSMS Scope Expansion

The full planned SSMS system now includes the existing core academic, student, parent, teacher, timetable, attendance, examination, assignment, notice, achievement/certificate, reporting, security, and audit modules plus the newly approved School Administration, School Events, Library, Advanced Analytics, Alumni, and Global Search capabilities.

---

# 🏗️ Technical Architecture

SSMS will use a lightweight **PHP OOP + MVC-like architecture** without a full PHP framework.

```text
Browser
   │
   ▼
Apache / PHP
   │
   ├── Routes / Controllers
   │        │
   │        ▼
   │     Services
   │        │
   │        ▼
   │     Models / Data Access
   │        │
   │        ▼
   │      MariaDB
   │
   └── Views / CSS / JavaScript
```

### Technology Stack

| Layer | Technology |
|---|---|
| Backend | PHP 8+ |
| Architecture | OOP + MVC-like |
| Database | MySQL / MariaDB |
| Engine | InnoDB |
| Frontend | HTML5, CSS3, JavaScript |
| Dynamic Requests | AJAX / Fetch API |
| Web Server | Apache |
| Development | XAMPP / WampServer |

No frontend or PHP framework is required for the planned core system.

---

# 🔐 Security Plan

Planned protections:

- Password hashing with PHP password APIs
- Prepared statements / parameterized queries
- Server-side validation
- Output escaping
- CSRF protection
- Session security
- Server-side role/permission checks
- Secure file handling if uploads are introduced
- Login protections where appropriate
- Never expose database credentials to frontend code
- Audit important Secretary actions
- Prevent Secretary access to Admin-only functions
- Prevent students/parents from accessing unrelated records
- Prevent IDOR-style access to another student's data
- Permission-check every student-profile update
- Permission-check every certificate/document download
- Validate uploaded certificate/document MIME type, extension, and size
- Keep uploaded documents outside executable public paths where possible
- Preserve audit history for academic-history and achievement changes

Teacher registration codes must be securely generated, preferably hashed, single-use, and invalidated after successful registration.

Parent one-time registration codes must also be securely generated, preferably hashed, tied to the intended student, single-use, invalidated after successful linking, optionally expiry-controlled, and never exposed in URLs or frontend source.

---

# 🗄️ High-Level Data Model

```text
users
 ├── teachers
 ├── students
 └── parents

teacher_pre_registrations
 ├── full_name
 ├── secret_code_hash
 ├── status
 ├── expires_at
 ├── registered_at
 └── teacher_id

parent_registration_codes
 ├── student_id
 ├── code_hash
 ├── status
 ├── expires_at
 ├── used_at
 ├── created_by
 └── claimed_by_parent_id

student_achievements
 ├── student_id
 ├── category
 ├── title
 ├── level
 ├── award_position
 ├── achievement_date
 ├── description
 ├── created_by
 └── updated_by

student_certificates
 ├── student_id
 ├── achievement_id (optional)
 ├── title
 ├── file_path
 ├── file_type
 ├── file_size
 ├── uploaded_by
 └── created_at

student_academic_history
 ├── student_id
 ├── examination_type
 ├── examination_year
 ├── subject
 ├── grade/result
 ├── marks (optional)
 ├── index/reference (optional)
 ├── verification_status
 └── recorded_by

student_exit_records
 ├── student_id
 ├── status
 ├── leaving_date
 ├── final_grade/class
 ├── reason (optional)
 ├── report_reference
 ├── generated_by
 └── generated_at

classes
subjects
academic_years
terms

student_class_assignments
teacher_subject_assignments
parent_student_links

timetable
 ├── class_id
 ├── subject_id
 ├── teacher_id
 ├── day
 ├── period_start
 ├── period_end
 ├── is_double_period
 └── status

attendance
examinations
exam_results
assignments
notices

settings
activity_logs
```

The final database schema will be designed before implementation. Parent registration codes must be associated with a student and tracked independently from the parent account so the first successful registration can claim the child and later codes can add further children to the same parent account. Timetable records must support both single-period assignments and consecutive double-period blocks.

---

# 📁 Planned Project Structure

```text
ssms/
├── app/
│   ├── Controllers/
│   ├── Models/
│   ├── Services/
│   ├── Middleware/
│   └── Helpers/
├── config/
│   ├── app.php
│   └── database.php
├── database/
│   ├── migrations/
│   └── seeds/
├── public/
│   ├── index.php
│   └── assets/
│       ├── css/
│       ├── js/
│       └── images/
├── routes/
│   └── web.php
├── views/
│   ├── layouts/
│   ├── auth/
│   ├── admin/
│   ├── secretary/
│   ├── teacher/
│   ├── student/
│   └── parent/
└── storage/
    ├── logs/
    ├── cache/
    └── student-documents/
```

This structure is a plan and may evolve during implementation.

---

# 🛠️ Development Roadmap

### Phase 1 — Planning

- [x] Define project purpose
- [x] Define user roles
- [x] Define core modules
- [x] Define technology stack
- [x] Define timetable requirements
- [x] Define automatic timetable matching and double-period requirements
- [x] Define official UI theme
- [x] Confirm scalable Student/Parent management through Secretary / Office Staff
- [x] Confirm Teacher pre-registration workflow
- [x] Confirm Student Code + Parent One-Time Code registration flow
- [x] Confirm automatic parent-child linking
- [x] Confirm multi-child Parent Dashboard linking
- [x] Confirm Student Achievements & Certificates records
- [x] Confirm O/L and A/L historical result records
- [x] Confirm Student Leaving / Completion Report workflow
- [x] Confirm Office Staff student-profile management permissions
- [x] Approve School Administration module
- [x] Approve School Events & Calendar module
- [x] Approve Library Management module
- [x] Approve Advanced Dashboard & Analytics module
- [x] Approve Alumni Management module
- [x] Approve Global Search & Advanced Data Discovery module
- [ ] Finalize database ERD
- [ ] Finalize permission matrix

### Phase 2 — Foundation

- [ ] Project structure
- [ ] Configuration system
- [ ] Database connection layer
- [ ] Routing/controller foundation
- [ ] Base model/service classes
- [ ] Common UI layout

### Phase 3 — Authentication

- [ ] Login/logout
- [ ] Password hashing
- [ ] Session handling
- [ ] Role-based authorization
- [ ] Teacher registration verification flow
- [ ] Secretary authentication and permissions
- [ ] Student authentication
- [ ] Parent authentication
- [ ] Parent Student Code + One-Time Code verification flow
- [ ] Automatic parent-child linking during registration
- [ ] Add Child verification flow for existing parent accounts
- [ ] Server-side authorization for every student profile action

### Phase 4 — School Management

- [ ] Users
- [ ] Students
- [ ] Teachers
- [ ] Parents
- [ ] Secretary / Office Staff
- [ ] Classes
- [ ] Subjects
- [ ] Academic years/terms
- [ ] Student-parent linking
- [ ] Student-generated parent registration code lifecycle
- [ ] Student profile history
- [ ] Student achievements and certificates
- [ ] Historical O/L and A/L results
- [ ] Student leaving/completion records
- [ ] School Administration
- [ ] School profile and official school identity
- [ ] School calendar
- [ ] Public holiday management
- [ ] Staff directory
- [ ] Staff leave management
- [ ] Staff attendance management
- [ ] Staff duty roster

### Phase 5 — Academic Modules

- [ ] Automatic timetable generation and class-subject-period matching
- [ ] Double-period timetable support
- [ ] Timetable conflict validation and publish workflow
- [ ] Attendance
- [ ] Examinations
- [ ] Results
- [ ] Assignments
- [ ] Notices

### Phase 6 — School Services

- [ ] School Events & Calendar
- [ ] Event creation/editing/publishing
- [ ] Event audience targeting
- [ ] Event calendar view
- [ ] Library catalogue
- [ ] Library book-copy tracking
- [ ] Library issue/return
- [ ] Library overdue tracking
- [ ] Library borrowing history
- [ ] Library reports

### Phase 7 — Reports, Analytics & UX

- [ ] Student profile reports
- [ ] Achievement/certificate reports
- [ ] O/L and A/L result reports
- [ ] Student Leaving / School Completion Report
- [ ] Printable reports
- [ ] Dashboard statistics
- [ ] Advanced role-specific analytics
- [ ] Attendance/examination trend analytics
- [ ] Admissions and pending-task analytics
- [ ] Responsive improvements
- [ ] Accessibility improvements

### Phase 8 — Search & Alumni

- [ ] Global Search service
- [ ] Permission-aware search across approved modules
- [ ] Student/Teacher/Parent/Class/Subject search
- [ ] Achievement/Certificate search
- [ ] Examination/Library/Event search where authorized
- [ ] Search filters/sorting/pagination
- [ ] Debounced live search
- [ ] Alumni record lifecycle
- [ ] Alumni directory
- [ ] Alumni search/filter
- [ ] Alumni reports

### Phase 9 — Testing & Deployment

- [ ] Security testing
- [ ] Functional testing
- [ ] Database integrity testing
- [ ] Database/file upload security testing
- [ ] Performance testing with large student datasets
- [ ] Parent registration-code lifecycle testing
- [ ] Multi-child linking testing
- [ ] Achievement/certificate authorization testing
- [ ] O/L/A/L historical-result validation testing
- [ ] Student leaving/completion report testing
- [ ] Automatic timetable generation testing
- [ ] Timetable conflict and double-period testing
- [ ] School Administration permission testing
- [ ] Events/calendar visibility testing
- [ ] Library issue/return/overdue testing
- [ ] Analytics data-scope and performance testing
- [ ] Alumni archive/privacy testing
- [ ] Global Search authorization/IDOR/performance testing
- [ ] Cross-module integration testing
- [ ] Deployment documentation
- [ ] Backup/restore documentation

---

# 🌐 Deployment Concept

SSMS should work on a school local network as well as a properly configured server deployment.

```text
Users
  ↓
Apache
  ↓
PHP SSMS Application
  ↓
MariaDB/MySQL
```

---

# 📌 Project Status

**Current status: Planning / System Overview**

This repository is currently the central planning and design document for SSMS. The application itself has not been built yet.

The README defines the system scope, architecture, modules, timetable requirements, automatic timetable matching, official visual theme, role permissions, Office Staff workflows, student achievements/certificates, O/L/A/L historical results, student leaving/completion reporting, School Administration, School Events, Library, Advanced Analytics, Alumni, and Global Search.

---

# 🚀 Future Vision

Possible future capabilities:

- Advanced timetable auto-generation and optimization
- Detailed analytics
- Notification system
- Printable reports
- Digital student portfolio
- Certificate/document verification workflows
- Import/export tools
- Backup and restore
- PWA support
- Optional API layer
- Integration with other school services
- Optional dark mode using the same design language
