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
- [ ] Define empty states
- [ ] Define loading states
- [ ] Define error states
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

- [ ] Use Inter as primary UI font where available
- [ ] Use Poppins for headings/branding where appropriate
- [ ] Define heading sizes
- [ ] Define body text sizes
- [ ] Define label/helper text sizes
- [ ] Define font weights
- [ ] Ensure readable contrast

## 2.3 Components

- [ ] Buttons
- [ ] Icon buttons
- [ ] Inputs
- [ ] Textareas
- [ ] Selects
- [ ] Checkboxes
- [ ] Radio buttons
- [ ] Toggles
- [ ] Cards
- [ ] Tables
- [ ] Badges
- [ ] Alerts
- [ ] Toasts
- [ ] Modals
- [ ] Dropdowns
- [ ] Tabs
- [ ] Pagination
- [ ] Breadcrumbs
- [ ] Search bars
- [ ] Date/time controls
- [ ] Loading indicators

## 2.4 Glassmorphism Rules

- [ ] Use subtle glass effects only where useful
- [ ] Keep text readable
- [ ] Avoid excessive blur
- [ ] Maintain strong card/input boundaries
- [ ] Use shadows consistently
- [ ] Keep the interface professional rather than overly decorative

## 2.5 Responsive Design

- [ ] Desktop layout
- [ ] Laptop layout
- [ ] Tablet layout
- [ ] Mobile layout
- [ ] Responsive sidebar
- [ ] Responsive tables
- [ ] Mobile-friendly forms
- [ ] Mobile-friendly dashboards
- [ ] Touch-friendly controls

---

# PHASE 3 — Project Foundation

## 3.1 Directory Structure

- [ ] Create `app/`
- [ ] Create `app/Controllers/`
- [ ] Create `app/Models/`
- [ ] Create `app/Services/`
- [ ] Create `app/Middleware/`
- [ ] Create `app/Helpers/`
- [ ] Create `config/`
- [ ] Create `database/migrations/`
- [ ] Create `database/seeds/`
- [ ] Create `public/`
- [ ] Create `public/assets/css/`
- [ ] Create `public/assets/js/`
- [ ] Create `public/assets/images/`
- [ ] Create `routes/`
- [ ] Create `views/layouts/`
- [ ] Create `views/auth/`
- [ ] Create `views/admin/`
- [ ] Create `views/teacher/`
- [ ] Create `views/student/`
- [ ] Create `views/parent/`
- [ ] Create `storage/logs/`
- [ ] Create `storage/cache/`

## 3.2 Configuration

- [ ] Create application configuration
- [ ] Create database configuration
- [ ] Configure environment-specific settings
- [ ] Keep secrets outside public files
- [ ] Configure timezone
- [ ] Configure error logging
- [ ] Configure application URL

## 3.3 Bootstrap

- [ ] Create application entry point
- [ ] Create autoloading strategy
- [ ] Create request/response foundation
- [ ] Create route loading
- [ ] Create global helper loading
- [ ] Create centralized error handling

## 3.4 Database Layer

- [ ] Create PDO/MySQLi database connection layer
- [ ] Prefer PDO or a consistent secure database abstraction
- [ ] Enable prepared statements
- [ ] Create transaction helper
- [ ] Create query/data-access conventions
- [ ] Add connection error handling
- [ ] Test database connection

---

# PHASE 4 — Routing, Controllers & Services

## 4.1 Routing

- [ ] Define GET routes
- [ ] Define POST routes
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

- [ ] Authentication service
- [ ] Authorization service
- [ ] User service
- [ ] Student service
- [ ] Teacher service
- [ ] Parent service
- [ ] Class service
- [ ] Subject service
- [ ] Timetable service
- [ ] Attendance service
- [ ] Examination service
- [ ] Result service
- [ ] Assignment service
- [ ] Notice service
- [ ] Report service
- [ ] Notification service if required

---

# PHASE 5 — Authentication & Security

## 5.1 Authentication

- [ ] Login page
- [ ] Login form validation
- [ ] Verify credentials
- [ ] Password hashing
- [ ] Session creation
- [ ] Logout
- [ ] Session timeout behavior
- [ ] Remember-me behavior if required
- [ ] Account active/inactive handling

## 5.2 Authorization

- [ ] Role middleware
- [ ] Permission checks
- [ ] Admin route protection
- [ ] Teacher route protection
- [ ] Student route protection
- [ ] Parent route protection
- [ ] Prevent IDOR-style access to other users' records

## 5.3 Security Hardening

- [ ] CSRF protection
- [ ] XSS-safe output escaping
- [ ] SQL injection protection
- [ ] Secure session cookie settings
- [ ] Login rate/attempt protection where appropriate
- [ ] Secure password reset design if implemented
- [ ] Secure file upload validation if implemented
- [ ] Remove debug output from production
- [ ] Centralize security logging

---

# PHASE 6 — Base Layout & Navigation

## 6.1 Shared Layout

- [ ] Create main application shell
- [ ] Create sidebar
- [ ] Create top navigation
- [ ] Create user profile menu
- [ ] Create notification area
- [ ] Create page header
- [ ] Create content container
- [ ] Create footer where needed

## 6.2 Navigation

- [ ] Dashboard
- [ ] Students
- [ ] Teachers
- [ ] Parents
- [ ] Classes
- [ ] Subjects
- [ ] Timetable
- [ ] Examinations
- [ ] Attendance
- [ ] Assignments
- [ ] Notices
- [ ] Reports
- [ ] Settings

## 6.3 Shared UX

- [ ] Global search UI
- [ ] Toast notifications
- [ ] Loading states
- [ ] Form error messages
- [ ] Confirmation dialogs
- [ ] Empty states
- [ ] 404 page
- [ ] 403 page
- [ ] 500 page

---

# PHASE 7 — User & School Management

## 7.1 User Management

- [ ] User model
- [ ] User creation
- [ ] User editing
- [ ] User activation/deactivation
- [ ] User search
- [ ] User filtering
- [ ] Role assignment
- [ ] Profile management

## 7.2 Student Management

- [ ] Student database table
- [ ] Student model
- [ ] Student registration
- [ ] Student profile
- [ ] Student ID/reference number
- [ ] Admission information
- [ ] Class assignment
- [ ] Student status
- [ ] Student search
- [ ] Student filtering
- [ ] Student detail page
- [ ] Academic history
- [ ] Parent linking

## 7.3 Teacher Management

- [ ] Teacher table
- [ ] Teacher profile
- [ ] Teacher account
- [ ] Teacher status
- [ ] Subject assignments
- [ ] Class assignments
- [ ] Teacher search/filter

## 7.4 Parent Management

- [ ] Parent table
- [ ] Parent profile
- [ ] Parent account
- [ ] Parent contact details
- [ ] Link parent to student
- [ ] Multiple children support
- [ ] Parent search/filter

## 7.5 Class Management

- [ ] Grade/class creation
- [ ] Section creation
- [ ] Class teacher assignment
- [ ] Student assignment
- [ ] Class details
- [ ] Class search/filter

## 7.6 Subject Management

- [ ] Subject creation
- [ ] Subject editing
- [ ] Subject code
- [ ] Subject/class assignment
- [ ] Teacher-subject assignment
- [ ] Subject search/filter

## 7.7 Academic Year & Terms

- [ ] Academic year creation
- [ ] Term creation
- [ ] Active academic year
- [ ] Active term
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

- [ ] Timetable table/schema
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

## 9.1 Attendance Setup

- [ ] Attendance schema
- [ ] Attendance statuses
- [ ] Present status
- [ ] Absent status
- [ ] Late status if required
- [ ] Excused status if required

## 9.2 Teacher Attendance Workflow

- [ ] Select class
- [ ] Select date
- [ ] Load students
- [ ] Mark attendance
- [ ] Save attendance
- [ ] Edit attendance with permission
- [ ] Prevent unauthorized modification

## 9.3 Attendance Reports

- [ ] Student attendance history
- [ ] Daily summary
- [ ] Monthly summary
- [ ] Term summary
- [ ] Class attendance statistics
- [ ] Parent attendance view
- [ ] Student attendance view

---

# PHASE 10 — Examinations & Results

## 10.1 Examination Setup

- [ ] Examination creation
- [ ] Examination date
- [ ] Academic year/term association
- [ ] Classes included
- [ ] Subjects included
- [ ] Maximum marks

## 10.2 Marks Entry

- [ ] Teacher marks-entry screen
- [ ] Student list
- [ ] Marks validation
- [ ] Save marks
- [ ] Edit marks with permission
- [ ] Lock/publish results if required

## 10.3 Result Processing

- [ ] Grade calculation rules
- [ ] Subject result calculation
- [ ] Overall result calculation
- [ ] Result summaries
- [ ] Student result view
- [ ] Parent result view
- [ ] Printable result report

---

# PHASE 11 — Assignment System

## 11.1 Teacher Features

- [ ] Create assignment
- [ ] Select class
- [ ] Select subject
- [ ] Set title
- [ ] Set description
- [ ] Set due date
- [ ] Edit assignment
- [ ] Delete/cancel assignment
- [ ] View assignment status

## 11.2 Student Features

- [ ] View assignments
- [ ] Filter assignments
- [ ] View due dates
- [ ] Mark/view assignment status
- [ ] Show overdue assignments

## 11.3 Parent Features

- [ ] View linked student's assignments
- [ ] Show upcoming due dates

---

# PHASE 12 — Notices & Announcements

- [ ] Notice database
- [ ] Create notice
- [ ] Edit notice
- [ ] Publish/unpublish notice
- [ ] Delete notice
- [ ] Target all users
- [ ] Target specific role
- [ ] Target specific class/section
- [ ] Notice list
- [ ] Notice detail page
- [ ] Student notice view
- [ ] Parent notice view
- [ ] Teacher notice view

---

# PHASE 13 — Dashboards

## 13.1 Admin Dashboard

- [ ] Total students card
- [ ] Total teachers card
- [ ] Total parents card
- [ ] Total classes card
- [ ] Today's attendance card
- [ ] Upcoming examinations
- [ ] Recent activities
- [ ] Recent notices
- [ ] Attendance chart
- [ ] Quick actions

## 13.2 Teacher Dashboard

- [ ] Today's classes
- [ ] Assigned subjects
- [ ] Attendance shortcut
- [ ] Pending assignments
- [ ] Recent notices
- [ ] Student overview

## 13.3 Student Dashboard

- [ ] Today's timetable
- [ ] Attendance summary
- [ ] Upcoming assignments
- [ ] Latest results
- [ ] Notices

## 13.4 Parent Dashboard

- [ ] Linked children
- [ ] Child selector
- [ ] Attendance summary
- [ ] Latest results
- [ ] Upcoming assignments
- [ ] Notices

---

# PHASE 14 — Search, Filtering & Data UX

- [ ] Global search foundation
- [ ] Student search
- [ ] Teacher search
- [ ] Parent search
- [ ] Class search
- [ ] Subject search
- [ ] Attendance filters
- [ ] Result filters
- [ ] Assignment filters
- [ ] Notice filters
- [ ] Pagination
- [ ] Sorting
- [ ] AJAX/Fetch search where beneficial
- [ ] Debounce live search requests
- [ ] Handle no-result states

---

# PHASE 15 — Reports

## 15.1 Student Reports

- [ ] Student profile report
- [ ] Student academic history
- [ ] Student attendance report

## 15.2 Class Reports

- [ ] Class student list
- [ ] Class attendance report
- [ ] Class results summary

## 15.3 Teacher Reports

- [ ] Teacher workload/timetable report
- [ ] Assigned classes report
- [ ] Assigned subjects report

## 15.4 Examination Reports

- [ ] Examination result report
- [ ] Subject performance report
- [ ] Grade distribution

## 15.5 Timetable Reports

- [ ] Class timetable print view
- [ ] Teacher timetable print view
- [ ] School timetable overview

## 15.6 Export

- [ ] Printable HTML reports
- [ ] CSV export where useful
- [ ] PDF export if required later

---

# PHASE 16 — Settings & Administration

- [ ] School profile
- [ ] School name/logo
- [ ] Academic settings
- [ ] Timetable settings
- [ ] Attendance settings
- [ ] Result/grade settings
- [ ] User settings
- [ ] Notification settings
- [ ] Theme settings
- [ ] Dark mode setting if implemented
- [ ] System maintenance settings

---

# PHASE 17 — Notifications

- [ ] Notification database/schema
- [ ] In-app notifications
- [ ] Unread count
- [ ] Mark as read
- [ ] Mark all as read
- [ ] Assignment notifications
- [ ] Result publication notifications
- [ ] Notice notifications
- [ ] Attendance-related notifications if required

Email/SMS/push notifications are optional future extensions and should not block the core system.

---

# PHASE 18 — File & Media Handling

Only implement this where a module genuinely needs files.

- [ ] Define allowed file types
- [ ] Validate MIME/type and extension
- [ ] Enforce file-size limits
- [ ] Generate safe filenames
- [ ] Store files outside executable paths where possible
- [ ] Prevent executable uploads
- [ ] Permission-check downloads
- [ ] Assignment attachment support if required
- [ ] Profile image support if required
- [ ] Notice attachment support if required

---

# PHASE 19 — Audit & Activity Logging

- [ ] Define audit log schema
- [ ] Login activity
- [ ] User changes
- [ ] Student record changes
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
- [ ] Avoid N+1 database queries
- [ ] Paginate large lists
- [ ] Optimize dashboard queries
- [ ] Minimize unnecessary AJAX requests
- [ ] Optimize CSS/JS assets
- [ ] Optimize images
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

## 22.1 Functional Testing

- [ ] Authentication tests
- [ ] Authorization tests
- [ ] Student CRUD tests
- [ ] Teacher CRUD tests
- [ ] Parent CRUD tests
- [ ] Class CRUD tests
- [ ] Subject CRUD tests
- [ ] Academic year/term tests
- [ ] Timetable tests
- [ ] Attendance tests
- [ ] Examination tests
- [ ] Result tests
- [ ] Assignment tests
- [ ] Notice tests
- [ ] Report tests

## 22.2 Security Testing

- [ ] SQL injection checks
- [ ] XSS checks
- [ ] CSRF checks
- [ ] Session security checks
- [ ] Authorization bypass checks
- [ ] File upload security checks
- [ ] Direct URL access checks
- [ ] Sensitive data exposure checks

## 22.3 UI Testing

- [ ] Desktop Chrome/Edge testing
- [ ] Mobile browser testing
- [ ] Tablet testing
- [ ] Form validation testing
- [ ] Navigation testing
- [ ] Responsive layout testing
- [ ] Dark mode testing if enabled

## 22.4 Data Testing

- [ ] Foreign key integrity
- [ ] Duplicate prevention
- [ ] Required-field validation
- [ ] Transaction rollback tests
- [ ] Backup/restore tests

---

# PHASE 23 — Deployment

## 23.1 Local Deployment

- [ ] Apache configuration
- [ ] PHP configuration
- [ ] MariaDB/MySQL configuration
- [ ] Database creation
- [ ] Database migration process
- [ ] Seed/demo data process
- [ ] Local virtual host setup

## 23.2 Production Deployment

- [ ] Production server preparation
- [ ] PHP version verification
- [ ] Required PHP extensions
- [ ] Apache configuration
- [ ] HTTPS configuration
- [ ] Database configuration
- [ ] File permissions
- [ ] Environment configuration
- [ ] Error logging
- [ ] Disable debug mode

## 23.3 Backup

- [ ] Database backup process
- [ ] File backup process
- [ ] Restore process
- [ ] Backup documentation
- [ ] Test restoration regularly

---

# PHASE 24 — Documentation

- [ ] Update `README.md`
- [ ] Keep `TASK.md` updated
- [ ] Installation guide
- [ ] Configuration guide
- [ ] Database setup guide
- [ ] User/role documentation
- [ ] Admin guide
- [ ] Teacher guide
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

For implementation, follow this order:

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

---

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
