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
4. The student receives a system account/activation method according to the school's chosen account policy.
5. The student can later log in and access only their own academic information.

### Student Information

The student record can include:

- Admission / Student Number
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
- Secretary can link students to parent accounts.
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
- Add parent records
- Edit parent contact information
- Link parents to students
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

Parent accounts are managed through the Secretary / Office Staff workflow rather than requiring the Admin to manually handle every parent.

### Parent Registration / Account Creation Flow

1. Secretary opens **Parents → Add Parent**.
2. Secretary enters the parent's basic information.
3. Secretary creates or activates the parent account according to the school's account policy.
4. Secretary links the parent to one or more existing student records.
5. The parent can log in and see only their linked children.

### Parent ↔ Student Linking

The system must support one parent linked to multiple children and, where the school requires it, multiple parents/guardians linked to the same student.

```text
Parent Account
      │
      ├── Student A — Grade 10A
      ├── Student B — Grade 7B
      └── Student C — Grade 5C
```

The relationship is stored separately so adding another child does not require creating another parent account.

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

The final database schema will be designed before implementation.

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

---

## 🎯 Official Design Keywords

```text
Clean
Modern
Professional
Academic
Trustworthy
Responsive
Light
Blue
Subtle Glassmorphism
Minimal
Readable
Organized
```

> **SSMS should look like a modern professional school platform — clean white surfaces, strong blue navigation and actions, subtle glass effects, excellent readability, and responsive layouts.**

---

**SSMS — Smart School Management System**  
*Plan the system first. Build it right.*
