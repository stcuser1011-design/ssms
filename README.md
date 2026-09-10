# SSMS — Smart School Management System

> A modern, modular school management platform designed for Sri Lankan schools.

## 📌 Project Overview

**SSMS (Smart School Management System)** is a web-based platform for managing day-to-day academic and administrative operations from one centralized system.

### User Roles

- **Admin** — manages school settings, users, teachers, classes, subjects, timetable, attendance, examinations, reports, notices, and system permissions.
- **Secretary / Office Staff** — manages student and parent records, student admissions, parent accounts, and student-parent linking. This role reduces the administrative workload of managing a large student population.
- **Teacher** — manages assigned classes, attendance, assignments, marks, timetable, and student information.
- **Student** — views timetable, attendance, results, assignments, notices, and academic information.
- **Parent** — monitors linked students, attendance, results, timetable, assignments, and notices.

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
| **Accent Cyan** | `#06B6DA` | Highlights and accents |
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
    --accent: #06B6DA;
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

The timetable system should prevent teacher, class, subject, room/resource, and period conflicts.

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
9. The student can later log in and access only their own academic information.

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

### Student Management Rules

- Secretary can add, edit, search, filter, and manage student records.
- Secretary can assign students to classes.
- Secretary can generate/reissue a parent one-time registration code where permitted.
- Secretary can view the status of a student's parent registration code without exposing the stored secret value.
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

### Secretary Responsibilities

- Add new students
- Edit student records
- Search and filter students
- Assign students to grades/classes/sections
- Manage admission information
- Generate/reissue parent one-time registration codes where permitted
- Add parent records when manual parent management is required
- Edit parent contact information
- Link parents to students when authorized
- Support multiple children for one parent
- View relevant student/parent reports

### Secretary Restrictions

The Secretary must not have unrestricted access to:

- System settings
- Role/permission administration
- Admin account management
- Teacher pre-registration
- Timetable configuration unless explicitly permitted
- Sensitive system configuration
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
- Other permitted academic information

Example:

```text
Parent Account
      │
      ├── Student A — Grade 10A
      ├── Student B — Grade 7B
      ├── Student C — Grade 5C
      └── Student D — Grade 3A
```

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

## Reports

- Student reports
- Attendance reports
- Examination/result reports
- Class reports
- Teacher reports
- Parent/student reports
- Timetable reports
- Academic summaries

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

classes
subjects
academic_years
terms

student_class_assignments
teacher_subject_assignments
parent_student_links

timetable
attendance
examinations
exam_results
assignments
notices

settings
activity_logs
```

The final database schema will be designed before implementation. Parent registration codes must be associated with a student and tracked independently from the parent account so the first successful registration can claim the child and later codes can add further children to the same parent account.

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
│   ├── teacher/
│   ├── student/
│   └── parent/
└── storage/
    ├── logs/
    └── cache/
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
- [x] Define official UI theme
- [x] Confirm scalable Student/Parent management through Secretary / Office Staff
- [x] Confirm Teacher pre-registration workflow
- [x] Confirm Student Code + Parent One-Time Code registration flow
- [x] Confirm automatic parent-child linking
- [x] Confirm multi-child Parent Dashboard linking
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

### Phase 5 — Academic Modules

- [ ] Timetable
- [ ] Attendance
- [ ] Examinations
- [ ] Results
- [ ] Assignments
- [ ] Notices

### Phase 6 — Reports & UX

- [ ] Reports
- [ ] Search/filtering
- [ ] Dashboard statistics
- [ ] Responsive improvements
- [ ] Accessibility improvements

### Phase 7 — Testing & Deployment

- [ ] Security testing
- [ ] Functional testing
- [ ] Database integrity testing
- [ ] Performance testing with large student datasets
- [ ] Parent registration-code lifecycle testing
- [ ] Multi-child linking testing
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

The README defines the system scope, architecture, modules, timetable requirements, official visual theme, role permissions, and registration/management workflows.

---

# 🚀 Future Vision

Possible future capabilities:

- Advanced timetable auto-generation
- Detailed analytics
- Notification system
- Printable reports
- Import/export tools
- Backup and restore
- PWA support
- Optional API layer
- Integration with other school services
- Optional dark mode using the same design language
