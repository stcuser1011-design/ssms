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
- [ ] Define all Secretary / Office Staff requirements
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
- [ ] Define Student Code generation rules
- [ ] Define Parent One-Time Registration Code generation, expiry, and claim rules
- [ ] Define first-child parent registration flow
- [ ] Define additional-child linking flow from the Parent Dashboard

## 1.2 Permission Matrix

- [ ] Create role/permission matrix
- [ ] Define Admin permissions
- [ ] Define Secretary / Office Staff permissions
- [ ] Define Teacher permissions
- [ ] Define Student permissions
- [ ] Define Parent permissions
- [ ] Define read/write/delete permissions
- [ ] Define permissions for sensitive academic records
- [ ] Define server-side authorization rules
- [ ] Ensure Secretary cannot access Admin-only system settings or permission management
- [ ] Ensure Student/Parent access is limited to authorized records
- [ ] Define who can generate/reissue Parent One-Time Registration Codes
- [ ] Define who can manually correct parent ↔ student links

## 1.3 Database Design

- [ ] Design ERD
- [ ] Define primary keys
- [ ] Define foreign keys
- [ ] Define indexes
- [ ] Define unique constraints
- [ ] Define timestamps/audit fields
- [ ] Define soft-delete strategy if required
- [ ] Review database relationships
- [ ] Design `users`, `students`, `parents`, and `parent_student_links`
- [ ] Design `parent_registration_codes`
- [ ] Store parent registration code hashes rather than raw codes where practical
- [ ] Store code status such as `PENDING` / `USED` / `EXPIRED`
- [ ] Store code `expires_at` and `used_at` where required
- [ ] Track which student a Parent One-Time Registration Code belongs to
- [ ] Track which parent account successfully claimed/used a code
- [ ] Design student class/academic-year relationships
- [ ] Design Secretary role/permission relationships
- [ ] Prepare migration SQL
- [ ] Prepare seed/demo data

## 1.4 UX Planning

- [ ] Define navigation structure for each role
- [ ] Define Admin dashboard
- [ ] Define Secretary / Office Staff dashboard
- [ ] Define Teacher dashboard
- [ ] Define Student dashboard
- [ ] Define Parent dashboard
- [ ] Define mobile navigation
- [ ] Define common forms
- [ ] Define student admission form
- [ ] Define parent management form
- [ ] Define Parent Registration page with Student Code + One-Time Parent Code
- [ ] Define parent ↔ student linking UI
- [ ] Define Parent Dashboard child selector/cards
- [ ] Define Parent Dashboard **Add Child** flow
- [ ] Define code verification success/error/expired states
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
- [ ] Define Secretary / Office Staff routes
- [ ] Define Teacher routes
- [ ] Define Student routes
- [ ] Define Parent routes
- [ ] Define Parent Registration routes
- [ ] Define Parent Add Child / linking routes
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
- [ ] Parent Registration controller/actions
- [ ] Parent Child Linking controller/actions
- [ ] Secretary / Office Staff controller or dedicated office controllers
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
- [ ] Secretary / Office Staff service layer
- [ ] Student Code generation service
- [ ] Parent Registration Code generation/verification service
- [ ] Parent-child linking service
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
- [ ] Parent Registration verification page
- [ ] Parent first-child account creation after successful code verification
- [ ] Parent Add Child verification for already authenticated parents

## 5.2 Authorization

- [ ] Role middleware
- [ ] Permission checks
- [ ] Admin/Secretary/Teacher/Student/Parent route protection
- [ ] Prevent IDOR-style access to other users' records
- [ ] Restrict Secretary to approved student/parent management permissions
- [ ] Ensure parent child-switching is limited to linked students
- [ ] Ensure Parent Add Child can only claim a student using a valid Student Code + matching unused One-Time Parent Code

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
- [ ] Generate Student/Parent codes using a cryptographically secure random source
- [ ] Store Parent One-Time Registration Codes securely, preferably as hashes
- [ ] Never place raw Parent One-Time Registration Codes in URLs, page source, or client-side JavaScript
- [ ] Invalidate a Parent One-Time Registration Code immediately after successful use
- [ ] Prevent reuse of used/expired codes
- [ ] Prevent a Student Code from being sufficient for account creation by itself

---

# PHASE 6 — Base Layout & Navigation

- [ ] Main application shell
- [ ] Sidebar and top navigation
- [ ] Role-aware navigation
- [ ] User profile menu
- [ ] Notification area
- [ ] Page header/content container/footer where needed
- [ ] Dashboard navigation
- [ ] Students navigation
- [ ] Teachers navigation
- [ ] Parents navigation
- [ ] Classes/Subjects navigation
- [ ] Timetable/Examinations/Attendance/Assignments/Notices/Reports/Settings navigation
- [ ] Secretary-specific Students and Parents navigation
- [ ] Global search UI
- [ ] Parent Dashboard child selector
- [ ] Parent Dashboard **Add Child** action
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

## 7.2 Secretary / Office Staff Management

### Role Definition

- [ ] Create `SECRETARY` / `OFFICE_STAFF` role
- [ ] Allow Admin to create/activate Secretary accounts
- [ ] Allow multiple Secretary / Office Staff accounts
- [ ] Define granular permissions for student and parent management
- [ ] Record Secretary actions in activity/audit logs

### Secretary Responsibilities

- [ ] Add new students
- [ ] Edit student records
- [ ] Search/filter students
- [ ] Manage admission information
- [ ] Assign students to grade/class/section
- [ ] Manage student status
- [ ] Generate a unique Student Code when a student is created
- [ ] Generate a unique Parent One-Time Registration Code for the new student
- [ ] Provide the Student Code and Parent Code to the student's parent/guardian through an approved channel
- [ ] View code status without exposing stored raw code
- [ ] Reissue a new Parent One-Time Registration Code when authorized and necessary
- [ ] Add parent records when manual parent management is required
- [ ] Edit parent contact information
- [ ] Link parents to students when authorized
- [ ] Support one parent with multiple children
- [ ] Support multiple parents/guardians for one student where required
- [ ] View permitted student/parent reports

### Secretary Restrictions

- [ ] Cannot manage Admin accounts
- [ ] Cannot change system-wide permissions
- [ ] Cannot manage security settings
- [ ] Cannot access Admin-only configuration
- [ ] Cannot manage Teacher pre-registration unless explicitly granted by Admin
- [ ] Cannot modify protected academic records without explicit permission

## 7.3 Student Management — Secretary Managed

### Student Registration / Admission

- [ ] Secretary can open **Students → Add Student**
- [ ] Enter Admission / Student Number
- [ ] Enter Full Name
- [ ] Enter Date of Birth
- [ ] Enter required demographic information
- [ ] Select Academic Year
- [ ] Select Grade
- [ ] Select Class / Section
- [ ] Enter address/contact information where required
- [ ] Enter admission information
- [ ] Set student status
- [ ] Validate all information server-side
- [ ] Prevent duplicate Student/Admission Number
- [ ] Create the student record
- [ ] Automatically generate a unique Student Code
- [ ] Automatically generate a unique One-Time Parent Registration Code for that student
- [ ] Store only the secure representation of the Parent Code where practical
- [ ] Show the newly generated code to the authorized Secretary only when appropriate for delivery
- [ ] Never expose stored raw codes after initial generation

### Student Account

- [ ] Define school policy for student login/account activation
- [ ] Create or activate student account when required
- [ ] Keep protected school/admission fields controlled by authorized staff
- [ ] Student can access only their own information

### Student Management

- [ ] Student database table/model
- [ ] Student profile and ID/reference number
- [ ] System-generated Student Code
- [ ] Class assignment and status
- [ ] Student search/filter/detail page
- [ ] Academic history
- [ ] Parent linking
- [ ] Parent registration-code status display
- [ ] Parent registration-code reissue flow for authorized staff
- [ ] Student record change audit trail

## 7.4 Teacher Management — Pre-Registration + Self-Completion

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

## 7.5 Parent Management — Student Code + One-Time Code

### Parent Registration — First Child

- [ ] Parent Registration page asks for **Student Code**
- [ ] Parent Registration page asks for **One-Time Parent Registration Code**
- [ ] Do not allow registration using Student Code alone
- [ ] Verify that the Student Code identifies an eligible student
- [ ] Verify that the Parent Code belongs to the same student
- [ ] Verify that the Parent Code is `PENDING` and not expired
- [ ] Show parent profile/account fields only after successful verification
- [ ] Allow Parent Full Name, relationship, phone, email, address, username, and password to be completed as appropriate
- [ ] Keep verified student identity clear during account creation
- [ ] Create the parent account after successful completion
- [ ] Automatically create the `parent_student_links` relationship
- [ ] Mark the Parent One-Time Registration Code as `USED`
- [ ] Record `used_at` and the claiming parent account
- [ ] Prevent the same code from being used again
- [ ] Send the parent to the Parent Dashboard after successful registration

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

### Parent ↔ Student Linking

- [ ] Use `parent_student_links` as the relationship table
- [ ] Support one parent account → multiple children
- [ ] Support multiple parents/guardians → one student where required
- [ ] Do not create a duplicate parent account for an additional child
- [ ] Allow authorized Secretary/Admin users to perform manual link corrections when necessary
- [ ] Audit all manual link/unlink changes

### Add 2nd / 3rd / 4th Child

- [ ] Parent Dashboard displays all currently linked children
- [ ] Parent Dashboard provides **+ Add Child**
- [ ] Add Child form asks for the new child's **Student Code**
- [ ] Add Child form asks for the new child's **One-Time Parent Registration Code**
- [ ] Verify the Student Code + Parent Code pair belongs to the same student
- [ ] Verify the code is unused and not expired
- [ ] Verify the authenticated parent account is allowed to claim/link the child
- [ ] Automatically create a new `parent_student_links` record
- [ ] Keep the existing parent account unchanged
- [ ] Mark the new child's code as `USED`
- [ ] Prevent reuse of the code
- [ ] Refresh the Parent Dashboard child selector/cards after successful linking
- [ ] Do not impose an artificial 2/3/4-child limit; support additional children using the same mechanism

### Multi-Child Parent Dashboard

- [ ] Show child cards or a child selector
- [ ] Clearly identify each child's name, grade, and class
- [ ] Allow parent to switch active child
- [ ] Scope attendance to the selected child
- [ ] Scope results to the selected child
- [ ] Scope timetable to the selected child
- [ ] Scope assignments to the selected child
- [ ] Scope notices to the selected child where applicable
- [ ] Ensure switching children never exposes another student's data

Example:

```text
Parent Account
      │
      ├── Student A — Grade 10A
      ├── Student B — Grade 7B
      ├── Student C — Grade 5C
      └── Student D — Grade 3A
```

### Parent Code Rules

- [ ] Generate Parent Codes with a cryptographically secure random source
- [ ] Make each code unique enough to prevent guessing/collision
- [ ] Tie each code to exactly one intended student before it is claimed
- [ ] Store a secure hash rather than the raw code where practical
- [ ] Use `PENDING`, `USED`, and `EXPIRED` lifecycle states as appropriate
- [ ] Support optional expiry time
- [ ] Invalidate immediately after successful first-child registration or Add Child linking
- [ ] Never expose raw codes in URLs, frontend source, or logs
- [ ] Do not allow Student Code alone to claim a student
- [ ] Allow authorized Secretary/Admin users to reissue a new code when necessary
- [ ] Audit generation, reissue, successful claim, expiry, and relevant invalidation events without storing the raw secret code

### Parent Information

- [ ] Full Name
- [ ] Relationship to student
- [ ] Phone number
- [ ] Email where available
- [ ] Address
- [ ] Parent/guardian status
- [ ] Linked student records
- [ ] Account status

### Parent Access

- [ ] Parent sees only linked children
- [ ] Parent can switch between linked children
- [ ] Parent can add another child only by providing the valid Student Code + One-Time Parent Registration Code for that child
- [ ] Parent cannot edit protected academic records
- [ ] Parent cannot view unrelated students
- [ ] Multiple-child support is required

## 7.6 Class Management

- [ ] Grade/class creation
- [ ] Section creation
- [ ] Class teacher assignment
- [ ] Student assignment
- [ ] Class details/search/filter

## 7.7 Subject Management

- [ ] Subject creation/editing
- [ ] Subject code
- [ ] Subject/class assignment
- [ ] Teacher-subject assignment
- [ ] Subject search/filter

## 7.8 Academic Year & Terms

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
- [ ] Student, Parent, Teacher, and Secretary notice views where permitted

---

# PHASE 13 — Dashboards

## Admin
- [ ] Students, Teachers, Parents, Classes statistics
- [ ] Today's attendance
- [ ] Upcoming examinations
- [ ] Recent activities/notices
- [ ] Attendance chart and quick actions

## Secretary / Office Staff
- [ ] Total students
- [ ] New admissions
- [ ] Students by grade/class
- [ ] Parent records
- [ ] Parent-linking requests/tasks where used
- [ ] Parent registration-code status overview where permitted
- [ ] Quick Add Student
- [ ] Quick Add Parent
- [ ] Recent student/parent changes

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
- [ ] Child cards showing basic class/grade information
- [ ] **Add Child** action
- [ ] Add Child Student Code + One-Time Code form
- [ ] Attendance for selected child
- [ ] Results for selected child
- [ ] Timetable for selected child
- [ ] Assignments for selected child
- [ ] Notices for selected child where applicable
- [ ] Clear success/error feedback when adding a child

---

# PHASE 14 — Search, Filtering & Data UX

- [ ] Global search
- [ ] Student/Teacher/Parent/Class/Subject search
- [ ] Secretary student/parent search
- [ ] Attendance/Result/Assignment/Notice filters
- [ ] Pagination and sorting
- [ ] AJAX/Fetch search where beneficial
- [ ] Debounced live search
- [ ] No-result states
- [ ] Parent child selector/search behavior where needed

---

# PHASE 15 — Reports

- [ ] Student profile/academic/attendance reports
- [ ] Class student/attendance/result reports
- [ ] Teacher workload/timetable/assignment reports
- [ ] Parent/student relationship reports
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
- [ ] Role/permission settings
- [ ] Notification settings
- [ ] Theme settings
- [ ] Dark mode if implemented
- [ ] Maintenance settings
- [ ] Parent registration-code expiry/reissue settings if configurable

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
- [ ] Optional notification when a parent successfully links a new child

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
- [ ] Secretary student/parent changes
- [ ] Student record changes
- [ ] Student Code generation events
- [ ] Parent One-Time Registration Code generation events
- [ ] Parent Code reissue events
- [ ] Parent Code successful claim/use events without storing the raw code
- [ ] Teacher registration/pre-registration activity
- [ ] Attendance changes
- [ ] Result changes
- [ ] Timetable changes
- [ ] Notice changes
- [ ] Parent ↔ student relationship changes
- [ ] Record who performed the action
- [ ] Record timestamp
- [ ] Restrict audit log access

---

# PHASE 20 — Performance

- [ ] Add database indexes based on real queries
- [ ] Avoid N+1 queries
- [ ] Paginate large student/parent lists
- [ ] Optimize search/filter queries
- [ ] Test with 3000+ student records
- [ ] Test with large parent/student relationship datasets
- [ ] Test parent dashboard with multiple linked children
- [ ] Cache appropriate read-heavy data if required
- [ ] Optimize dashboard statistics

---

# PHASE 21 — Accessibility & UX Quality

- [ ] Keyboard navigation
- [ ] Visible focus states
- [ ] Accessible form labels
- [ ] Good text/background contrast
- [ ] Error messages understandable without color alone
- [ ] Touch-friendly mobile controls
- [ ] Responsive student/parent/Secretary workflows
- [ ] Accessible Parent Registration form
- [ ] Accessible Add Child flow

---

# PHASE 22 — Testing

## Authentication & Roles

- [ ] Test Admin login/permissions
- [ ] Test Secretary login/permissions
- [ ] Test Teacher login/permissions
- [ ] Test Student login/permissions
- [ ] Test Parent login/permissions
- [ ] Verify unauthorized routes are blocked

## Student Management

- [ ] Student creation tests
- [ ] Duplicate Student/Admission Number tests
- [ ] Student editing tests
- [ ] Class assignment tests
- [ ] Search/filter tests
- [ ] Student Code generation tests
- [ ] Parent One-Time Registration Code generation tests
- [ ] Large dataset tests with 3000+ students

## Parent Management

- [ ] Parent creation tests
- [ ] Parent editing tests
- [ ] Parent Registration Student Code + One-Time Code verification tests
- [ ] Matching Student Code + Code success tests
- [ ] Wrong Student Code tests
- [ ] Wrong Parent Code tests
- [ ] Student Code + code mismatch tests
- [ ] Used-code rejection tests
- [ ] Expired-code rejection tests
- [ ] First-child automatic linking tests
- [ ] Parent Dashboard child selector tests
- [ ] Add 2nd child tests
- [ ] Add 3rd child tests
- [ ] Add 4th child tests
- [ ] Additional-child tests beyond four children
- [ ] Verify no duplicate parent account is created for additional children
- [ ] Multiple guardians tests where enabled
- [ ] Verify parent cannot see unrelated students
- [ ] Verify linked-child data is correctly scoped after switching children

## Teacher Registration

- [ ] Teacher pre-registration tests
- [ ] Teacher name + secret-code verification tests
- [ ] Wrong-code/wrong-name rejection tests
- [ ] Single-use code tests
- [ ] Duplicate-registration prevention tests
- [ ] Teacher account completion tests
- [ ] Teacher registration-code security checks

## Secretary Role

- [ ] Secretary can add/edit students
- [ ] Secretary can add/edit parents
- [ ] Secretary can generate Student Codes
- [ ] Secretary can generate/reissue Parent One-Time Registration Codes where permitted
- [ ] Secretary can view code status without exposing stored raw codes
- [ ] Secretary can link parents and students when authorized
- [ ] Secretary cannot access Admin-only settings
- [ ] Secretary cannot change unauthorized roles/permissions
- [ ] Secretary actions appear in audit logs

## System Testing

- [ ] Timetable conflict tests
- [ ] Attendance tests
- [ ] Examination/result tests
- [ ] Assignment tests
- [ ] Notice tests
- [ ] Report tests
- [ ] Security regression tests
- [ ] Responsive/mobile tests

---

# PHASE 23 — Deployment

- [ ] Apache configuration
- [ ] PHP configuration
- [ ] MariaDB/MySQL configuration
- [ ] Production environment configuration
- [ ] HTTPS where deployed publicly
- [ ] Secure secrets/configuration
- [ ] Database migrations
- [ ] Initial admin account setup
- [ ] Initial Secretary / Office Staff account setup
- [ ] Backup strategy
- [ ] Restore procedure
- [ ] Production error logging

---

# PHASE 24 — Documentation

- [ ] Installation guide
- [ ] Configuration guide
- [ ] Database setup guide
- [ ] Admin guide
- [ ] Secretary / Office Staff guide
- [ ] Teacher guide
- [ ] Student guide
- [ ] Parent guide
- [ ] Parent Registration guide
- [ ] Add Child guide
- [ ] Parent Code reissue guide for authorized staff
- [ ] Timetable guide
- [ ] Attendance guide
- [ ] Examination/result guide
- [ ] Backup/restore guide
- [ ] Security notes

---

# PHASE 25 — Final Release Checklist

- [ ] All core roles implemented
- [ ] Admin permissions verified
- [ ] Secretary / Office Staff permissions verified
- [ ] Teacher pre-registration flow verified end-to-end
- [ ] Student admission/registration flow verified end-to-end
- [ ] Student Code generation verified end-to-end
- [ ] Parent One-Time Registration Code generation verified end-to-end
- [ ] Parent first-child registration and automatic linking verified end-to-end
- [ ] Parent account creation flow verified end-to-end
- [ ] Parent ↔ student linking verified
- [ ] Parent Dashboard Add Child flow verified
- [ ] Multiple-child parent accounts verified
- [ ] 2nd/3rd/4th child linking verified
- [ ] Additional-child linking beyond four children verified
- [ ] One-time codes cannot be reused
- [ ] Parent cannot claim a student using Student Code alone
- [ ] Parent can only access linked children
- [ ] 3000+ student performance verified
- [ ] Timetable requirements verified
- [ ] Attendance verified
- [ ] Examinations/results verified
- [ ] Assignments verified
- [ ] Notices verified
- [ ] Reports verified
- [ ] Security checks passed
- [ ] Mobile/responsive checks passed
- [ ] Documentation completed
- [ ] Backup/restore tested

---

# Recommended Build Order

```text
PLAN
  ↓
DATABASE + ARCHITECTURE
  ↓
PROJECT FOUNDATION
  ↓
AUTH + SECURITY + ROLES
  ↓
SHARED UI + NAVIGATION
  ↓
ADMIN + SECRETARY/OFFICE STAFF
  ↓
STUDENTS + STUDENT CODES
  ↓
PARENT REGISTRATION + ONE-TIME CODES
  ↓
AUTOMATIC FIRST-CHILD LINKING
  ↓
PARENT DASHBOARD + ADD CHILD
  ↓
TEACHERS + TEACHER REGISTRATION
  ↓
CLASSES + SUBJECTS + ACADEMIC YEARS
  ↓
TIMETABLE
  ↓
ATTENDANCE
  ↓
EXAMS + RESULTS
  ↓
ASSIGNMENTS
  ↓
NOTICES
  ↓
DASHBOARDS
  ↓
SEARCH + REPORTS
  ↓
SETTINGS + NOTIFICATIONS
  ↓
TESTING + SECURITY
  ↓
DEPLOYMENT + DOCUMENTATION
  ↓
RELEASE
```

# Definition of Done

A module is considered complete only when:

- [ ] UI is implemented according to the official theme
- [ ] Backend logic is implemented
- [ ] Database schema/queries are implemented
- [ ] Validation is implemented
- [ ] Authorization is implemented
- [ ] Error states are handled
- [ ] Responsive behavior is implemented
- [ ] Security checks are implemented
- [ ] Audit logging is added where appropriate
- [ ] Tests are completed
- [ ] Documentation is updated

---

# 📌 Current Status

**Planning / Task Breakdown**

The task file is the master implementation checklist. Student and Parent management is explicitly designed around the **Secretary / Office Staff role** so the system can scale to schools with 3000+ students without requiring the Admin to manually handle every student and parent record.

The confirmed Parent registration architecture uses a **Student Code + One-Time Parent Registration Code**. The first successful parent registration automatically links the child to the newly created parent account. After login, the Parent Dashboard provides **+ Add Child**, where the parent enters the next child's Student Code + One-Time Parent Registration Code and the system automatically adds that child to the same parent account. The design supports 2nd, 3rd, 4th, and additional children without creating duplicate parent accounts or imposing an artificial child-count limit.
