# SSMS — Complete Project Task Plan

> Master implementation checklist for the Smart School Management System.
>
> **Rule:** Complete tasks in order where dependencies exist. Do not start a later phase until its required foundation is stable.

---

## 0. Project Rules & Technical Decisions

- [ ] Confirm project name: **SSMS — Smart School Management System**
- [ ] Confirm backend: PHP 8+
- [ ] Confirm architecture: OOP + lightweight MVC-like structure
- [ ] Confirm database: MySQL/MariaDB + InnoDB
- [ ] Confirm frontend: HTML5 + CSS3 + Vanilla JavaScript
- [ ] Confirm AJAX approach: Fetch API / AJAX where useful
- [ ] Confirm web server: Apache
- [ ] Avoid unnecessary PHP/frontend frameworks
- [ ] Keep the application responsive on desktop, tablet, and mobile
- [ ] Follow the visual theme defined in `README.md`
- [ ] Keep security requirements active throughout development

---

# PHASE 1 — Planning & System Design

## 1.1 Requirements

- [ ] Define all Admin requirements
- [ ] Define all Teacher requirements
- [ ] Define all Student requirements
- [ ] Define all Parent requirements
- [ ] Define school-wide requirements
- [ ] Define academic year/term behavior
- [ ] Define class/section behavior
- [ ] Define subject behavior
- [ ] Define attendance rules
- [ ] Define examination/result rules
- [ ] Define assignment rules
- [ ] Define notice/announcement rules
- [ ] Define reporting requirements

## 1.2 Permission Matrix

- [ ] Create role/permission matrix
- [ ] Define Admin permissions
- [ ] Define Teacher permissions
- [ ] Define Student permissions
- [ ] Define Parent permissions
- [ ] Define read/write/delete permissions
- [ ] Define permissions for sensitive academic records
- [ ] Define server-side authorization rules

## 1.3 Database Design

- [ ] Design ERD
- [ ] Define primary keys
- [ ] Define foreign keys
- [ ] Define indexes
- [ ] Define unique constraints
- [ ] Define timestamps/audit fields
- [ ] Define soft-delete strategy if required
- [ ] Review database relationships
- [ ] Prepare migration SQL
- [ ] Prepare seed/demo data

## 1.4 UX Planning

- [ ] Define navigation structure
- [ ] Define Admin dashboard
- [ ] Define Teacher dashboard
- [ ] Define Student dashboard
- [ ] Define Parent dashboard
- [ ] Define mobile navigation
- [ ] Define common forms
- [ ] Define table/list patterns
- [ ] Define empty/loading/error states
- [ ] Define confirmation dialogs

---

# PHASE 2 — UI Design System

## 2.1 Color System

Use the approved SSMS blue/white visual direction.

- [ ] Primary Blue: `#2563EB`
- [ ] Light Blue: `#3B82F6`
- [ ] Accent Cyan: `#06B6D4`
- [ ] Success Green: `#10B981`
- [ ] Warning Amber: `#F59E0B`
- [ ] Danger Red: `#EF4444`
- [ ] Background: `#F8FAFC`
- [ ] Surface: `#FFFFFF`
- [ ] Primary Text: `#0F172A`
- [ ] Secondary Text: `#64748B`

## 2.2 Typography

- [ ] Use Inter as primary UI font
- [ ] Use Poppins for headings/branding where appropriate
- [ ] Define typography hierarchy and readable contrast

## 2.3 Components

- [ ] Buttons and icon buttons
- [ ] Inputs, selects, textareas
- [ ] Checkboxes, radios, toggles
- [ ] Cards, tables, badges
- [ ] Alerts, toasts, modals, dropdowns
- [ ] Tabs, pagination, breadcrumbs
- [ ] Search bars and date/time controls
- [ ] Loading indicators

## 2.4 Glassmorphism Rules

- [ ] Use subtle glass effects only where useful
- [ ] Keep text readable
- [ ] Avoid excessive blur
- [ ] Maintain strong card/input boundaries
- [ ] Use consistent shadows
- [ ] Keep the interface professional rather than overly decorative

## 2.5 Responsive Design

- [ ] Desktop layout
- [ ] Laptop layout
- [ ] Tablet layout
- [ ] Mobile layout
- [ ] Responsive sidebar/tables/forms/dashboards
- [ ] Touch-friendly controls

---

# PHASE 3 — Project Foundation

- [ ] Create planned `app/`, `config/`, `database/`, `public/`, `routes/`, `views/`, and `storage/` directories
- [ ] Create application/database configuration
- [ ] Keep secrets outside public files
- [ ] Configure timezone, URL, and error logging
- [ ] Create application entry point and autoloading
- [ ] Create request/response and routing foundation
- [ ] Create centralized error handling
- [ ] Create secure PDO/MySQLi database layer
- [ ] Enable prepared statements
- [ ] Add transactions and connection error handling
- [ ] Test database connection

---

# PHASE 4 — Routing, Controllers & Services

## 4.1 Routing

- [ ] Define GET/POST routes
- [ ] Define authentication routes
- [ ] Define Admin routes
- [ ] Define Teacher routes
- [ ] Define Student routes
- [ ] Define Parent routes
- [ ] Define API/AJAX routes if needed
- [ ] Add route protection

## 4.2 Controllers

- [ ] Base controller
- [ ] Auth controller
- [ ] Dashboard controller
- [ ] User controller
- [ ] Student controller
- [ ] Teacher controller
- [ ] Parent controller
- [ ] Class controller
- [ ] Subject controller
- [ ] Academic controller
- [ ] Timetable controller
- [ ] Attendance controller
- [ ] Examination controller
- [ ] Result controller
- [ ] Assignment controller
- [ ] Notice controller
- [ ] Report controller
- [ ] Settings controller

## 4.3 Services

- [ ] Authentication and Authorization services
- [ ] User, Student, Teacher, Parent services
- [ ] Class, Subject, Timetable services
- [ ] Attendance, Examination, Result services
- [ ] Assignment, Notice, Report services
- [ ] Notification service if required

---

# PHASE 5 — Authentication & Security

## 5.1 Authentication

- [ ] Login page and validation
- [ ] Verify credentials
- [ ] Password hashing
- [ ] Session creation and logout
- [ ] Session timeout
- [ ] Account active/inactive handling

## 5.2 Authorization

- [ ] Role middleware
- [ ] Permission checks
- [ ] Admin/Teacher/Student/Parent route protection
- [ ] Prevent IDOR-style access to other users' records

## 5.3 Security Hardening

- [ ] CSRF protection
- [ ] XSS-safe output escaping
- [ ] SQL injection protection
- [ ] Secure session cookie settings
- [ ] Login attempt protection where appropriate
- [ ] Secure password reset design if implemented
- [ ] Secure file upload validation if implemented
- [ ] Remove debug output from production
- [ ] Centralize security logging

---

# PHASE 6 — Base Layout & Navigation

- [ ] Main application shell
- [ ] Sidebar and top navigation
- [ ] User profile menu
- [ ] Notification area
- [ ] Page header/content container/footer where needed
- [ ] Dashboard, Students, Teachers, Parents, Classes, Subjects navigation
- [ ] Timetable, Examinations, Attendance, Assignments, Notices, Reports, Settings navigation
- [ ] Global search UI
- [ ] Toasts, loading states, form errors, confirmations
- [ ] Empty, 404, 403, and 500 states

---

# PHASE 7 — User & School Management

## 7.1 User Management

- [ ] User model
- [ ] User creation/editing
- [ ] User activation/deactivation
- [ ] User search/filter
- [ ] Role assignment
- [ ] Profile management

## 7.2 Student Management

- [ ] Student database table/model
- [ ] Student registration
- [ ] Student profile and ID/reference number
- [ ] Admission information
- [ ] Class assignment and status
- [ ] Student search/filter/detail page
- [ ] Academic history
- [ ] Parent linking

## 7.3 Teacher Management — Pre-Registration + Self-Completion

### Admin Pre-Registration

- [ ] Admin can open **Teachers → Pre-Register Teacher**
- [ ] Admin enters only the teacher's **full name** for pre-registration
- [ ] System automatically generates a unique random **secret registration code**
- [ ] Store the pre-registration with `PENDING` status
- [ ] Store the secret code securely, preferably as a hash
- [ ] Admin can view/copy the generated code to share with that teacher

### Teacher Registration Verification

- [ ] Teacher Registration page asks for **Pre-Registered Full Name**
- [ ] Teacher Registration page asks for **Secret Registration Code**
- [ ] Verify that the full name and secret code match the **same PENDING pre-registration**
- [ ] Do not allow registration when either value does not match
- [ ] Do not allow a code belonging to another teacher to be used
- [ ] Keep the verified pre-registered full name locked after successful verification

### Teacher Self-Completion

- [ ] Only after successful verification, show the remaining registration fields
- [ ] Allow approved profile information such as email, phone, address, date of birth, qualification, username, and password
- [ ] Validate all submitted information server-side
- [ ] Create the teacher account after successful completion
- [ ] Link the new teacher account to the original pre-registration record
- [ ] Change pre-registration status from `PENDING` to `REGISTERED`

### Secret Code Rules

- [ ] Secret registration code is single-use
- [ ] Invalidate the code immediately after successful registration
- [ ] Prevent duplicate registration with the same code
- [ ] Optional expiry time for unused codes
- [ ] Do not expose secret codes in public pages, URLs, or frontend source
- [ ] Log important registration actions without logging the raw secret code

### Teacher Management After Registration

- [ ] Teacher profile
- [ ] Teacher account/status
- [ ] Subject assignments
- [ ] Class assignments
- [ ] Teacher search/filter

## 7.4 Parent Management

- [ ] Parent table/model
- [ ] Parent profile/account
- [ ] Parent contact details
- [ ] Link parent to student
- [ ] Multiple children support
- [ ] Parent search/filter

## 7.5 Class Management

- [ ] Grade/class creation
- [ ] Section creation
- [ ] Class teacher assignment
- [ ] Student assignment
- [ ] Class details/search/filter

## 7.6 Subject Management

- [ ] Subject creation/editing
- [ ] Subject code
- [ ] Subject/class assignment
- [ ] Teacher-subject assignment
- [ ] Subject search/filter

## 7.7 Academic Year & Terms

- [ ] Academic year creation
- [ ] Term creation
- [ ] Active academic year/term
- [ ] Historical academic periods
- [ ] Prevent invalid overlapping active periods

---

# PHASE 8 — Timetable Engine

## 8.1 Timetable Configuration

- [ ] Define school days
- [ ] Define 8 periods
- [ ] Define 40-minute period duration
- [ ] Configure school start time: 7:30 AM
- [ ] Configure first teaching period: 7:50 AM
- [ ] Configure interval: 10:30–10:50 AM
- [ ] Ensure fourth period ends at 10:30 AM
- [ ] Configure school end time: 1:30 PM
- [ ] Allow timetable settings to be configurable where appropriate

## 8.2 Timetable Data

- [ ] Timetable schema
- [ ] Class-period assignments
- [ ] Teacher-period assignments
- [ ] Subject-period assignments
- [ ] Room/resource assignments if enabled

## 8.3 Conflict Detection

- [ ] Teacher conflict detection
- [ ] Class conflict detection
- [ ] Subject conflict validation
- [ ] Room/resource conflict detection
- [ ] Duplicate period prevention
- [ ] Clear conflict messages

## 8.4 Timetable UI

- [ ] Weekly timetable view
- [ ] Class timetable
- [ ] Teacher timetable
- [ ] Student timetable
- [ ] Parent timetable view
- [ ] Admin timetable editor
- [ ] Mobile timetable view
- [ ] Print-friendly timetable

## 8.5 Future Automation

- [ ] Define timetable generation constraints
- [ ] Define optimization rules
- [ ] Prototype automatic timetable generator
- [ ] Validate generated timetable
- [ ] Allow manual adjustment after generation

---

# PHASE 9 — Attendance System

- [ ] Attendance schema and statuses
- [ ] Present/Absent status
- [ ] Late/Excused status if required
- [ ] Teacher selects class/date and loads students
- [ ] Mark and save attendance
- [ ] Edit attendance with permission
- [ ] Prevent unauthorized modification
- [ ] Student attendance history
- [ ] Daily/monthly/term summaries
- [ ] Class attendance statistics
- [ ] Parent and Student attendance views

---

# PHASE 10 — Examinations & Results

- [ ] Examination creation/date/year/term
- [ ] Classes and subjects included
- [ ] Maximum marks
- [ ] Teacher marks-entry screen
- [ ] Marks validation/save/edit
- [ ] Lock/publish results if required
- [ ] Grade calculation
- [ ] Subject and overall result calculation
- [ ] Student and Parent result views
- [ ] Printable result report

---

# PHASE 11 — Assignment System

- [ ] Teacher creates assignment with class, subject, title, description, and due date
- [ ] Edit/delete/cancel assignment
- [ ] Student assignment list/filter/due/overdue views
- [ ] Parent view of linked student's assignments

---

# PHASE 12 — Notices & Announcements

- [ ] Notice database
- [ ] Create/edit/publish/unpublish/delete notices
- [ ] Target all users, roles, or classes/sections
- [ ] Notice list/detail pages
- [ ] Student, Parent, and Teacher notice views

---

# PHASE 13 — Dashboards

## Admin
- [ ] Students, Teachers, Parents, Classes statistics
- [ ] Today's attendance
- [ ] Upcoming examinations
- [ ] Recent activities/notices
- [ ] Attendance chart and quick actions

## Teacher
- [ ] Today's classes
- [ ] Assigned subjects
- [ ] Attendance shortcut
- [ ] Pending assignments
- [ ] Notices and student overview

## Student
- [ ] Today's timetable
- [ ] Attendance summary
- [ ] Assignments
- [ ] Results
- [ ] Notices

## Parent
- [ ] Linked children
- [ ] Child selector
- [ ] Attendance
- [ ] Results
- [ ] Assignments
- [ ] Notices

---

# PHASE 14 — Search, Filtering & Data UX

- [ ] Global search
- [ ] Student/Teacher/Parent/Class/Subject search
- [ ] Attendance/Result/Assignment/Notice filters
- [ ] Pagination and sorting
- [ ] AJAX/Fetch search where beneficial
- [ ] Debounced live search
- [ ] No-result states

---

# PHASE 15 — Reports

- [ ] Student profile/academic/attendance reports
- [ ] Class student/attendance/result reports
- [ ] Teacher workload/timetable/assignment reports
- [ ] Examination/subject/grade reports
- [ ] Class and Teacher timetable print views
- [ ] Printable HTML reports
- [ ] CSV export where useful
- [ ] PDF export if required later

---

# PHASE 16 — Settings & Administration

- [ ] School profile/name/logo
- [ ] Academic settings
- [ ] Timetable settings
- [ ] Attendance settings
- [ ] Result/grade settings
- [ ] User settings
- [ ] Notification settings
- [ ] Theme settings
- [ ] Dark mode if implemented
- [ ] Maintenance settings

---

# PHASE 17 — Notifications

- [ ] Notification schema
- [ ] In-app notifications
- [ ] Unread count
- [ ] Mark read/all read
- [ ] Assignment notifications
- [ ] Result publication notifications
- [ ] Notice notifications
- [ ] Attendance notifications if required

Email/SMS/push notifications are optional future extensions and should not block the core system.

---

# PHASE 18 — File & Media Handling

- [ ] Define allowed file types
- [ ] Validate MIME/type and extension
- [ ] Enforce file-size limits
- [ ] Generate safe filenames
- [ ] Store files outside executable paths where possible
- [ ] Prevent executable uploads
- [ ] Permission-check downloads
- [ ] Assignment attachments if required
- [ ] Profile images if required
- [ ] Notice attachments if required

---

# PHASE 19 — Audit & Activity Logging

- [ ] Define audit log schema
- [ ] Login activity
- [ ] User changes
- [ ] Student record changes
- [ ] Teacher registration/pre-registration activity
- [ ] Attendance changes
- [ ] Result changes
- [ ] Timetable changes
- [ ] Notice changes
- [ ] Record who performed the action
- [ ] Record timestamp
- [ ] Restrict audit log access

---

# PHASE 20 — Performance

- [ ] Add database indexes based on real queries
- [ ] Avoid N+1 queries
- [ ] Paginate large lists
- [ ] Optimize dashboard queries
- [ ] Minimize unnecessary AJAX requests
- [ ] Optimize CSS/JS assets and images
- [ ] Add caching where useful
- [ ] Test with realistic school-sized data

---

# PHASE 21 — Accessibility & UX Quality

- [ ] Keyboard navigation
- [ ] Visible focus states
- [ ] Semantic HTML
- [ ] Form labels
- [ ] Accessible error messages
- [ ] Sufficient text contrast
- [ ] Responsive text sizing
- [ ] Avoid color-only status indicators
- [ ] Screen-reader-friendly important controls

---

# PHASE 22 — Testing

## Functional Testing

- [ ] Authentication and authorization tests
- [ ] Student CRUD tests
- [ ] Teacher pre-registration tests
- [ ] Teacher name + secret-code verification tests
- [ ] Teacher wrong-code/wrong-name rejection tests
- [ ] Teacher single-use code tests
- [ ] Teacher duplicate-registration prevention tests
- [ ] Teacher account completion tests
- [ ] Parent CRUD/linking tests
- [ ] Class/Subject/Academic year tests
- [ ] Timetable tests
- [ ] Attendance tests
- [ ] Examination/Result tests
- [ ] Assignment tests
- [ ] Notice tests
- [ ] Report tests

## Security Testing

- [ ] SQL injection checks
- [ ] XSS checks
- [ ] CSRF checks
- [ ] Session security checks
- [ ] Authorization bypass checks
- [ ] Teacher registration-code security checks
- [ ] Direct URL access checks
- [ ] Sensitive data exposure checks

## UI/Data Testing

- [ ] Desktop Chrome/Edge testing
- [ ] Mobile browser testing
- [ ] Tablet testing
- [ ] Form validation testing
- [ ] Navigation testing
- [ ] Responsive layout testing
- [ ] Foreign key integrity
- [ ] Duplicate prevention
- [ ] Required-field validation
- [ ] Transaction rollback tests
- [ ] Backup/restore tests

---

# PHASE 23 — Deployment

## Local

- [ ] Apache configuration
- [ ] PHP configuration
- [ ] MariaDB/MySQL configuration
- [ ] Database creation
- [ ] Migration process
- [ ] Seed/demo data process
- [ ] Local virtual host setup

## Production

- [ ] Production server preparation
- [ ] PHP version/extensions verification
- [ ] Apache configuration
- [ ] HTTPS configuration
- [ ] Database configuration
- [ ] File permissions
- [ ] Environment configuration
- [ ] Error logging
- [ ] Disable debug mode

## Backup

- [ ] Database backup
- [ ] File backup
- [ ] Restore process
- [ ] Backup documentation
- [ ] Regular restoration tests

---

# PHASE 24 — Documentation

- [ ] Update `README.md`
- [ ] Keep `TASK.md` updated
- [ ] Installation/configuration/database guides
- [ ] User/role documentation
- [ ] Admin guide
- [ ] Teacher guide including pre-registration and registration-code flow
- [ ] Student guide
- [ ] Parent guide
- [ ] Deployment guide
- [ ] Backup/restore guide
- [ ] Troubleshooting guide
- [ ] Security documentation

---

# PHASE 25 — Final Release Checklist

- [ ] All core modules complete
- [ ] All four roles tested
- [ ] Teacher pre-registration flow tested end-to-end
- [ ] Database schema finalized
- [ ] Timetable engine validated
- [ ] Attendance validated
- [ ] Results validated
- [ ] Reports validated
- [ ] Security review complete
- [ ] Responsive review complete
- [ ] Accessibility review complete
- [ ] Performance review complete
- [ ] Backup/restore tested
- [ ] Production configuration tested
- [ ] Documentation complete
- [ ] Remove development/test accounts
- [ ] Remove debug code
- [ ] Review permissions
- [ ] Create first stable release

---

# Recommended Build Order

```text
1. Planning
   ↓
2. Database + Architecture
   ↓
3. Project Foundation
   ↓
4. Authentication + Security
   ↓
5. Shared UI + Navigation
   ↓
6. Users / Students / Teachers / Parents
   ↓
7. Classes / Subjects / Academic Years
   ↓
8. Timetable
   ↓
9. Attendance
   ↓
10. Examinations + Results
   ↓
11. Assignments
   ↓
12. Notices
   ↓
13. Dashboards
   ↓
14. Search + Reports
   ↓
15. Settings + Notifications
   ↓
16. Testing + Security Review
   ↓
17. Deployment + Documentation
   ↓
18. Stable Release
```

# Definition of Done

A task is considered complete only when:

- [ ] The feature works correctly
- [ ] The feature follows the SSMS UI theme
- [ ] Server-side validation exists where needed
- [ ] Authorization is enforced
- [ ] Database operations use safe queries
- [ ] Errors are handled cleanly
- [ ] Responsive behavior is checked
- [ ] Related workflows are tested
- [ ] Documentation is updated when behavior changes

---

## Project Status

**Current stage: Planning / Task Breakdown**

This file is the master checklist for the future SSMS implementation. Checkboxes should be updated as development progresses. The project should be implemented incrementally rather than attempting to build the entire system in one step.
