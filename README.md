# SSMS — Smart School Management System

> A modern, modular school management platform designed for Sri Lankan schools.

## 📌 Project Overview

**SSMS (Smart School Management System)** is a web-based platform for managing the day-to-day academic and administrative operations of a school from one centralized system.

The system is planned around four main user roles:

- **Admin** — manages the school, users, classes, subjects, timetable, academic settings, and reports.
- **Teacher** — manages teaching-related activities such as attendance, marks, classes, assignments, and student information.
- **Student** — views timetable, attendance, results, assignments, notices, and academic information.
- **Parent** — monitors linked students, attendance, results, notices, timetable, and other important school information.

The project is intended to be lightweight, maintainable, secure, responsive, and suitable for deployment on a normal Apache/PHP/MySQL server.

---

## 🎯 Main Goals

1. Centralize school management into one platform.
2. Reduce repetitive manual administration.
3. Give each user role an appropriate dashboard.
4. Provide reliable academic and attendance records.
5. Automate school timetable planning.
6. Make important information accessible from desktop and mobile devices.
7. Keep the codebase simple enough to maintain without a large framework.

---

## 👥 User Roles

### Admin

- Dashboard and school overview
- User account management
- Teacher management
- Student management
- Parent management
- Class and grade management
- Subject management
- Academic year/term management
- Timetable management
- Attendance overview
- Examination and result management
- Notices and announcements
- Reports and statistics
- System settings

### Teacher

- Personal dashboard
- Assigned classes and subjects
- Student list
- Attendance management
- Marks/results entry
- Assignment management
- Class notices
- Timetable
- Student academic overview
- Profile/settings

### Student

- Personal dashboard
- My timetable
- Attendance
- Examination results
- Assignments
- Notices/announcements
- Subjects and classes
- Profile/settings

### Parent

- Parent dashboard
- Linked student accounts
- Student attendance
- Student results
- Student timetable
- Assignments/notices
- School announcements
- Profile/settings

---

## 🧩 Core Modules

### 1. Authentication & Authorization

- Login/logout
- Session management
- Password hashing
- Role-based access control
- Protected pages and actions
- Account status management

### 2. Dashboard

Each role receives a different dashboard with relevant information, statistics, shortcuts, notifications, and recent activity.

### 3. Student Management

- Student registration
- Admission information
- Student ID/reference number
- Class assignment
- Parent linking
- Student status
- Academic history
- Search and filtering

### 4. Teacher Management

- Teacher profiles
- Teacher accounts
- Subject assignments
- Class assignments
- Timetable assignments
- Teacher status

### 5. Parent Management

- Parent profiles
- Parent accounts
- Student-parent relationships
- Multiple children support
- Contact information

### 6. Class & Subject Management

- Grades/classes
- Sections
- Subjects
- Subject assignments
- Teacher-subject relationships
- Student-class relationships

### 7. Timetable Engine

The timetable module is designed around the Sri Lankan school schedule used for this project.

Planned timetable rules:

- **8 periods per school day**
- **40 minutes per period**
- School begins at **7:30 AM**
- First teaching period begins at **7:50 AM**
- Fourth period ends at **10:30 AM**
- Interval: **10:30 AM – 10:50 AM**
- School ends at **1:30 PM**

The timetable engine should help prevent conflicts between:

- Teachers
- Classes
- Subjects
- Rooms/resources
- Periods

It should support manual editing as well as automated timetable generation in a future implementation stage.

### 8. Attendance

- Daily attendance
- Student attendance records
- Teacher attendance entry
- Attendance summaries
- Monthly/term statistics
- Attendance history

### 9. Examinations & Results

- Examination setup
- Subjects and marks
- Student marks entry
- Results viewing
- Grade calculation
- Result summaries
- Academic performance reports

### 10. Assignments

- Create assignments
- Assign to classes/subjects
- Due dates
- Assignment status
- Student assignment view
- Teacher assignment management

### 11. Notices & Announcements

- School-wide announcements
- Role/class-specific notices
- Publish/unpublish controls
- Notice history

### 12. Reports

Planned reports include:

- Student reports
- Attendance reports
- Examination/result reports
- Class reports
- Teacher reports
- Timetable reports
- Academic summaries

### 13. Search & Filtering

The system should provide fast searching and filtering for major data areas such as students, teachers, classes, subjects, attendance, and results.

---

## 🏗️ Planned Architecture

SSMS will use a lightweight **PHP OOP + MVC-like architecture** without a full-stack PHP framework.

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

### Architecture Principles

- Separation of concerns
- Reusable PHP classes
- Centralized configuration
- Secure database access
- Prepared SQL statements
- Role-based authorization
- Reusable UI components
- Minimal dependencies
- Easy local deployment

---

## 💻 Technology Stack

| Layer | Technology |
|---|---|
| Backend | PHP 8+ |
| Architecture | OOP + MVC-like |
| Database | MySQL / MariaDB |
| Database Engine | InnoDB |
| Frontend | HTML5, CSS3, JavaScript |
| Dynamic Requests | AJAX / Fetch API |
| Web Server | Apache |
| Development | XAMPP / WampServer |
| Production | Apache + PHP + MariaDB |

No frontend framework or PHP framework is required for the planned core system.

---

## 🎨 UI / UX Direction

The interface should be modern, clean, responsive, and easy to use.

Planned characteristics:

- Responsive desktop/tablet/mobile layout
- Modern dashboard cards
- Sidebar navigation
- Clear tables and forms
- Search bars and filters
- Modal dialogs where appropriate
- Notifications/toasts
- Consistent icons
- Accessible typography and spacing
- Optional dark mode
- Subtle glassmorphism where it improves the interface without reducing readability

The design should prioritize usability over excessive visual effects.

---

## 🔐 Security Plan

Security is a core requirement of SSMS.

Planned protections include:

- Password hashing with PHP's password APIs
- Prepared statements / parameterized queries
- Server-side validation
- Output escaping
- CSRF protection for state-changing forms
- Session security
- Role and permission checks on the server
- Secure file handling where uploads are introduced
- Login attempt protections where appropriate
- No database credentials inside public frontend code

---

## 🗄️ High-Level Data Model

The planned database will contain entities similar to:

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

The final database schema will be designed before implementation so relationships and constraints remain consistent.

---

## 📱 Responsive / Mobile Support

SSMS is planned as a responsive web application rather than a separate native mobile application.

The same system should work on:

- Desktop computers
- Laptops
- Tablets
- Mobile phones

Important dashboards and frequently used actions should remain practical on smaller screens.

---

## 🔄 Typical Workflows

### Admin Workflow

```text
Login
  ↓
Admin Dashboard
  ↓
Configure Academic Year
  ↓
Create Classes & Subjects
  ↓
Create Teacher/Student/Parent Accounts
  ↓
Assign Classes & Subjects
  ↓
Configure Timetable
  ↓
Monitor Attendance & Results
  ↓
Generate Reports
```

### Teacher Workflow

```text
Login
  ↓
Teacher Dashboard
  ↓
View Assigned Classes
  ↓
Take Attendance
  ↓
Manage Assignments
  ↓
Enter Examination Marks
  ↓
View Class Information
```

### Student Workflow

```text
Login
  ↓
Student Dashboard
  ↓
View Timetable
  ↓
View Attendance
  ↓
View Assignments
  ↓
View Results
  ↓
Read Notices
```

### Parent Workflow

```text
Login
  ↓
Parent Dashboard
  ↓
Select Linked Student
  ↓
View Timetable
  ↓
Check Attendance
  ↓
Check Results
  ↓
Read School Notices
```

---

## 📊 Dashboard Concept

### Admin Dashboard

Potential widgets:

- Total students
- Total teachers
- Total parents
- Total classes
- Today's attendance
- Upcoming examinations
- Recent notices
- System activity

### Teacher Dashboard

Potential widgets:

- Today's classes
- Assigned subjects
- Attendance shortcuts
- Pending assignments
- Recent notices

### Student Dashboard

Potential widgets:

- Today's timetable
- Attendance summary
- Upcoming assignments
- Latest results
- Notices

### Parent Dashboard

Potential widgets:

- Children overview
- Attendance summary
- Latest results
- Upcoming assignments
- Notices

---

## 🛠️ Development Roadmap

### Phase 1 — Planning

- [x] Define project purpose
- [x] Define user roles
- [x] Define core modules
- [x] Define technology stack
- [x] Define timetable requirements
- [ ] Finalize database ERD
- [ ] Finalize permission matrix

### Phase 2 — Foundation

- [ ] Project directory structure
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
- [ ] Advanced search/filtering
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

## 📁 Planned Project Structure

```text
ssms/
├── app/
│   ├── Controllers/
│   ├── Models/
│   ├── Services/
│   ├── Middleware/
│   └── Helpers/
│
├── config/
│   ├── app.php
│   └── database.php
│
├── database/
│   ├── migrations/
│   └── seeds/
│
├── public/
│   ├── index.php
│   ├── assets/
│   │   ├── css/
│   │   ├── js/
│   │   └── images/
│   └── uploads/
│
├── routes/
│   └── web.php
│
├── views/
│   ├── layouts/
│   ├── auth/
│   ├── admin/
│   ├── teacher/
│   ├── student/
│   └── parent/
│
├── storage/
│   ├── logs/
│   └── cache/
│
└── README.md
```

This is a planned structure; implementation may evolve as the project develops.

---

## 🌐 Deployment Concept

SSMS is intended to run on a standard PHP hosting/server environment.

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

### Server Deployment

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

The system should also be usable on a school local network if internet access is unavailable.

---

## 🧪 Testing Strategy

Testing will eventually cover:

- Authentication
- Authorization
- CRUD operations
- Database relationships
- Timetable conflict detection
- Attendance calculations
- Result calculations
- Search/filter functionality
- Responsive layouts
- Security controls

---

## 📌 Project Status

**Current status: Planning / System Overview**

This repository currently serves as the central planning document for SSMS. The goal at this stage is to define the complete system scope, architecture, modules, workflows, and technical direction before building the actual application.

---

## 🚀 Future Vision

SSMS is intended to grow into a complete school management platform where administrators, teachers, students, and parents can use one connected system for everyday school operations and academic information.

Future possibilities may include:

- Advanced timetable auto-generation
- Detailed analytics
- Notification systems
- Printable reports
- Import/export tools
- Backup and restore tools
- PWA support
- Optional API layer
- Integration with other school services

---

## 📄 License

License to be decided before the production implementation is released.

---

**SSMS — Smart School Management System**  
*Plan the system first. Build it right.*
