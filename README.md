# SSMS — Smart School Management System

> A modern, modular school management platform designed for Sri Lankan schools.

## 📌 Project Overview

**SSMS (Smart School Management System)** is a web-based platform for managing day-to-day academic and administrative operations from one centralized system.

### User Roles

- **Admin** — manages school settings, users, classes, subjects, timetable, attendance, examinations, reports, and notices.
- **Teacher** — manages classes, attendance, assignments, marks, timetable, and student information.
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

---

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

---

## ✍️ Typography

### Primary Font

**Inter** is the primary UI font for dashboards, tables, forms, navigation, and mobile interfaces.

### Heading Option

**Poppins** may be used for selected large headings or branding elements.

### Recommended Hierarchy

```text
Page Title       → Inter / Poppins, SemiBold
Section Heading  → Inter, SemiBold
Card Heading     → Inter, SemiBold
Body Text        → Inter, Regular
UI Text          → Inter, Medium
Small Text       → Inter, Regular
```

Keep typography consistent and avoid unnecessary font families.

---

## 🧊 Glassmorphism

Glassmorphism must remain **subtle** and should not reduce readability.

Recommended style:

```css
.glass {
    background: rgba(255, 255, 255, 0.72);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    border: 1px solid rgba(255, 255, 255, 0.7);
    box-shadow: 0 8px 30px rgba(15, 23, 42, 0.06);
}
```

Use glass effects mainly for:

- Floating panels
- Modals
- Header elements
- Important dashboard widgets
- Login card
- Selected navigation elements

Do not apply heavy blur to every component.

---

## 🧭 Navigation Theme

### Desktop Sidebar

The desktop sidebar uses a **deep blue/navy visual treatment** to separate navigation from the light workspace.

Navigation items:

- Dashboard
- Students
- Teachers
- Classes
- Timetable
- Examinations
- Attendance
- Reports
- Settings

The SSMS logo and school branding should appear at the top, with school identity information optionally displayed at the bottom.

### Active Navigation

Use the primary blue treatment with strong contrast and rounded corners for the active item.

### Mobile Navigation

On small screens, transform the sidebar into a compact drawer or mobile navigation system.

---

## 🖥️ Dashboard Theme

The main dashboard uses:

```text
Background → #F8FAFC
Cards      → #FFFFFF
Primary    → #2563EB
Text       → #0F172A
Secondary  → #64748B
```

### Header

Recommended elements:

- Search bar
- Notifications
- User profile
- Role indicator
- Date/time where useful

### Welcome Area

Example:

```text
Good Morning, Admin!
Here's what's happening at your school today.
```

### Statistics Cards

Recommended cards:

- Total Students
- Total Teachers
- Total Classes
- Today's Attendance

Cards should use white surfaces, rounded corners, soft shadows, clear number hierarchy, and small colored icon circles.

---

## 📊 Charts & Data Visualization

Charts should be clean, simple, and readable.

Use them for:

- Attendance trends
- Student statistics
- Examination performance
- Class distribution
- Academic summaries

Use the primary blue and status colors consistently. Avoid excessive gradients and unnecessary colors.

---

## 📅 Timetable Theme

The timetable is a major SSMS interface and should be highly readable.

### Visual Rules

- Clear time column
- Day columns
- Compact subject cards
- Teacher/room information where necessary
- Subtle subject indicators
- Strong visual distinction for breaks
- Responsive horizontal scrolling on small screens

### Sri Lankan School Schedule

The project timetable engine follows these requirements:

- **8 periods per day**
- **40 minutes per period**
- School starts at **7:30 AM**
- First teaching period starts at **7:50 AM**
- Fourth period ends at **10:30 AM**
- Interval: **10:30 AM – 10:50 AM**
- School ends at **1:30 PM**

The timetable system should prevent conflicts between teachers, classes, subjects, rooms/resources, and periods.

---

## 🔐 Login Page Theme

The login page should use a professional school-oriented design with a school/SSMS visual area and a clean login card.

Recommended composition:

```text
┌─────────────────────────────────────────────┐
│                                             │
│  School Branding       ┌─────────────────┐  │
│  / Background          │   Welcome Back  │  │
│                        │                 │  │
│                        │ Username/Email  │  │
│                        │ Password        │  │
│                        │                 │  │
│                        │     Login       │  │
│                        └─────────────────┘  │
│                                             │
└─────────────────────────────────────────────┘
```

The login card should use a white/glass surface, rounded corners, and a soft shadow.

Primary login button: `#2563EB`.

---

## 🧩 Component System

### Buttons

**Primary**
- Background: `#2563EB`
- Text: white
- Hover: `#3B82F6`

**Secondary**
- White/light surface
- Blue border/text
- Subtle hover background

**Success**
- Background: `#10B981`

**Warning**
- Background: `#F59E0B`

**Danger**
- Background: `#EF4444`

All buttons should have consistent height, spacing, typography, and rounded corners.

### Form Controls

Inputs/selects/textareas should use:

- White background
- `#E2E8F0` border
- Rounded corners
- Comfortable height
- Clear labels
- Primary blue focus state

Recommended focus state:

```css
input:focus,
select:focus,
textarea:focus {
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.12);
}
```

### Status Badges

| Status | Color |
|---|---|
| Active / Success | `#10B981` |
| Pending | `#F59E0B` |
| Inactive | `#64748B` |
| Error | `#EF4444` |

Status should not rely on color alone; use text or icons too.

---

## 🪟 Cards & Surfaces

Standard cards:

```text
Background: #FFFFFF
Border:     #E2E8F0
Radius:     12–16px
Shadow:     Soft / low contrast
Padding:    20–24px
```

Cards should have enough spacing to prevent a crowded interface.

---

## 📱 Responsive Design

SSMS must be responsive from the beginning.

### Desktop

- Full sidebar
- Multi-column dashboard
- Full data tables
- Full timetable view

### Tablet

- Compact sidebar
- Reduced dashboard columns
- Scrollable tables where necessary

### Mobile

- Collapsible navigation
- Single-column cards
- Mobile-friendly forms
- Responsive timetable
- Large touch targets
- Compact header

The mobile interface should feel like an application rather than a desktop page squeezed onto a phone.

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

- Student registration
- Admission information
- Student ID/reference number
- Class assignment
- Parent linking
- Student status
- Academic history
- Search/filtering

## Teacher Management

- Teacher profiles/accounts
- Subject assignments
- Class assignments
- Timetable assignments
- Teacher status

## Parent Management

- Parent profiles/accounts
- Student-parent relationships
- Multiple children support
- Contact information

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

No frontend framework or PHP framework is required for the planned core system.

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

---

# 🗄️ High-Level Data Model

```text
users
 ├── teachers
 ├── students
 └── parents

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

- [ ] Login
- [ ] Logout
- [ ] Password hashing
- [ ] Session handling
- [ ] Role-based authorization

### Phase 4 — School Management

- [ ] Users
- [ ] Students
- [ ] Teachers
- [ ] Parents
- [ ] Classes
- [ ] Subjects
- [ ] Academic years/terms

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
- [ ] Performance testing
- [ ] Deployment documentation
- [ ] Backup/restore documentation

---

# 🌐 Deployment Concept

### Local Development

```text
Windows
  ↓
XAMPP / WampServer
  ↓
Apache + PHP + MariaDB
  ↓
SSMS
```

### Server

```text
Internet / LAN
      ↓
    Apache
      ↓
     PHP
      ↓
   SSMS App
      ↓
 MariaDB/MySQL
```

SSMS should also be usable on a school local network when internet access is unavailable.

---

# 📌 Project Status

**Current status: Planning / System Overview**

This repository is currently the central planning and design document for SSMS. The application itself has not been built yet.

The README defines the system scope, architecture, modules, timetable requirements, and official visual theme that should guide future development.

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
