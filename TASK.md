# SSMS — Complete Project Task Plan

> Master implementation checklist for Smart School Management System. Build in dependency order and keep school-specific academic rules configurable rather than hard-coded.

## 0. Project Rules

- [ ] PHP 8+
- [ ] OOP + lightweight MVC-like architecture
- [ ] MySQL/MariaDB + InnoDB
- [ ] HTML5 + CSS3 + Vanilla JavaScript
- [ ] Fetch/AJAX where useful
- [ ] Apache
- [ ] Responsive desktop/tablet/mobile UI
- [ ] Blue/white subtle-glassmorphism design from README
- [ ] Server-side authorization for every protected action
- [ ] Preserve academic history when students move between years/classes

# PHASE 1 — Planning & Database

## 1.1 School Configuration

- [ ] School profile/settings
- [ ] Academic years
- [ ] Terms
- [ ] Grades
- [ ] Classes/sections
- [ ] Class capacities
- [ ] School days/periods
- [ ] Subjects
- [ ] Subject categories
- [ ] Subject groups
- [ ] Optional subjects
- [ ] O/L configuration
- [ ] A/L streams
- [ ] A/L subject combinations
- [ ] Houses/departments
- [ ] Rooms/resources
- [ ] Examination types
- [ ] Promotion rules
- [ ] Attendance rules
- [ ] School calendar/events

## 1.2 Subject Basket Requirements — IMPORTANT

- [ ] Create configurable `subject_baskets`
- [ ] Allow Admin to create O/L baskets for the relevant Grade 10/O/L stage
- [ ] Basket name/code/description
- [ ] Academic year/grade linkage
- [ ] Add/remove allowed subjects
- [ ] Minimum selections
- [ ] Maximum selections
- [ ] Exactly-one selection rules where required
- [ ] Multiple-selection rules where required
- [ ] Subject capacity
- [ ] Basket active/inactive state
- [ ] Selection open/close dates where needed
- [ ] Approval requirement where needed
- [ ] Basket history by academic year
- [ ] Prevent invalid subject combinations
- [ ] Never hard-code one universal basket structure

## 1.3 O/L Subject Selection

- [ ] Create student subject-selection records
- [ ] Show only valid baskets to eligible students/staff
- [ ] Validate basket rules before save
- [ ] Save student + basket + selected subject(s) + academic year
- [ ] Support selection status such as DRAFT/SUBMITTED/APPROVED
- [ ] Record selection/change history
- [ ] Allow authorized correction without destroying history
- [ ] Generate basket selection reports

## 1.4 A/L Stream and Subject Configuration

- [ ] Create configurable A/L streams
- [ ] Stream name/code
- [ ] Academic year
- [ ] Allowed subjects
- [ ] Required subject count
- [ ] Optional subjects
- [ ] Valid subject combinations
- [ ] Stream/group capacity
- [ ] Eligibility rules where school policy requires them
- [ ] Teacher assignments
- [ ] Weekly periods
- [ ] Practical/double-period requirements
- [ ] Group creation rules
- [ ] Student A/L stream selection
- [ ] Student A/L subject selection
- [ ] Validate combinations before submission
- [ ] Preserve A/L selection history

## 1.5 Database / ERD

- [ ] Design ERD
- [ ] `users`
- [ ] `students`
- [ ] `parents`
- [ ] `parent_student_links`
- [ ] `parent_registration_codes`
- [ ] `academic_years`
- [ ] `terms`
- [ ] `grades`
- [ ] `classes`
- [ ] `student_class_history`
- [ ] `subjects`
- [ ] `subject_categories`
- [ ] `subject_groups`
- [ ] `subject_baskets`
- [ ] `subject_basket_items`
- [ ] `student_subject_selections`
- [ ] `student_subject_history`
- [ ] `al_streams`
- [ ] `al_stream_subjects`
- [ ] `al_subject_combinations`
- [ ] `student_al_selections`
- [ ] `promotion_rules`
- [ ] `promotion_runs`
- [ ] `promotion_results`
- [ ] `student_placement_runs`
- [ ] `student_placements`
- [ ] `placement_conflicts`
- [ ] `teachers`
- [ ] `teacher_subject_assignments`
- [ ] `teacher_availability`
- [ ] `rooms/resources`
- [ ] `examinations`
- [ ] `results`
- [ ] `attendance`
- [ ] `assignments`
- [ ] `notices`
- [ ] `events`
- [ ] `library_books`
- [ ] `library_copies`
- [ ] `library_transactions`
- [ ] `achievements`
- [ ] `certificates`
- [ ] `student_documents`
- [ ] `student_exit_records`
- [ ] `alumni`
- [ ] `audit_logs`
- [ ] Add primary/foreign keys
- [ ] Add unique constraints
- [ ] Add indexes for Student Code, Admission Number, class, subject, basket and academic year
- [ ] Prepare migrations/SQL
- [ ] Prepare seed/demo data

# PHASE 2 — Architecture & Security

- [ ] Application config
- [ ] Database layer with prepared statements
- [ ] Routing
- [ ] Controllers
- [ ] Services
- [ ] Repositories/models
- [ ] Views/layouts
- [ ] Validation layer
- [ ] Authentication
- [ ] RBAC
- [ ] Granular permissions
- [ ] CSRF protection
- [ ] XSS-safe output
- [ ] SQL injection protection
- [ ] Secure sessions
- [ ] Secure password hashing
- [ ] Audit logging
- [ ] Secure file uploads
- [ ] Private document authorization

# PHASE 3 — School Administration

- [ ] Admin school profile
- [ ] Academic year/term manager
- [ ] Grade manager
- [ ] Class/section manager
- [ ] Class capacity configuration
- [ ] Subject manager
- [ ] Subject category manager
- [ ] Subject group manager
- [ ] Optional subject manager
- [ ] O/L basket manager
- [ ] A/L stream manager
- [ ] A/L combination manager
- [ ] Teacher-subject manager
- [ ] Room/resource manager
- [ ] Promotion rule manager
- [ ] Attendance rule manager
- [ ] School calendar
- [ ] Event manager

# PHASE 4 — Users and Student Lifecycle

## 4.1 Teacher

- [ ] Admin teacher pre-registration
- [ ] Generate secure one-time registration code
- [ ] Teacher name + code verification
- [ ] Lock verified full name
- [ ] Complete profile
- [ ] Create account
- [ ] Mark pre-registration REGISTERED
- [ ] Invalidate code
- [ ] Assign subjects/classes/groups

## 4.2 Secretary / Office Staff

- [ ] Create Secretary/Office Staff accounts
- [ ] Student admission
- [ ] Student search/filter
- [ ] Student profile
- [ ] Admission history
- [ ] Parent records
- [ ] Parent-child linking
- [ ] Class assignment
- [ ] Subject selection management
- [ ] Basket selection management
- [ ] O/L historical results
- [ ] A/L historical results
- [ ] Achievements
- [ ] Certificates
- [ ] Documents
- [ ] Leaving/completion
- [ ] Authorized reports
- [ ] Audit actions

## 4.3 Parent

- [ ] Student Code + one-time Parent Registration Code flow
- [ ] First child claim
- [ ] Parent account creation
- [ ] Add Child flow
- [ ] Multiple children per parent
- [ ] Permission-filtered child access

# PHASE 5 — Academic Structure & Student Subject Selection

## 5.1 Common/Core Subjects

- [ ] Configure common subjects by grade/year
- [ ] Assign teachers
- [ ] Configure weekly periods
- [ ] Configure double periods where required

## 5.2 Optional Subjects

- [ ] Configure optional subjects by grade/year
- [ ] Eligibility
- [ ] Capacity
- [ ] Teacher/resource requirements
- [ ] Selection window
- [ ] Approval rules

## 5.3 Grade 10 / O/L Basket Selection

- [ ] Admin creates O/L baskets
- [ ] Admin adds valid subjects to each basket
- [ ] Admin configures selection rules
- [ ] Publish basket choices
- [ ] Student/authorized staff selects subjects
- [ ] Validate selection
- [ ] Save selection
- [ ] Allow authorized review/approval
- [ ] Lock selection after finalization where required
- [ ] Preserve changes in history

## 5.4 A/L Selection

- [ ] Admin creates streams
- [ ] Admin creates allowed subject combinations
- [ ] Configure optional subjects
- [ ] Publish stream choices
- [ ] Student selects stream
- [ ] Student selects valid subjects
- [ ] Validate required count
- [ ] Validate combination
- [ ] Validate capacity
- [ ] Review/approve where configured
- [ ] Finalize selection

# PHASE 6 — Student Placement / Class Splitting Engine

## 6.1 Placement Inputs

- [ ] Current grade
- [ ] Academic year
- [ ] Student promotion result
- [ ] Current/home class
- [ ] Student subject selections
- [ ] O/L basket selections
- [ ] A/L stream
- [ ] A/L subject combination
- [ ] Optional subject selections
- [ ] Class capacities
- [ ] Subject group capacities
- [ ] Teacher-subject assignments
- [ ] Teacher availability
- [ ] Room/resource availability
- [ ] School-specific placement rules

## 6.2 Home Class Allocation

- [ ] Calculate required number of classes from student count/capacity
- [ ] Generate proposed sections
- [ ] Distribute students according to configured rules
- [ ] Avoid duplicate students
- [ ] Detect capacity violations
- [ ] Support manual movement
- [ ] Preserve class history

## 6.3 Subject Group Allocation

- [ ] Group students by compatible subject combinations
- [ ] Create required subject groups
- [ ] Apply group capacity
- [ ] Assign teacher where available
- [ ] Assign room/resource where required
- [ ] Detect students with no valid group
- [ ] Detect invalid combinations
- [ ] Support manual adjustment

## 6.4 Placement Review

- [ ] Generate DRAFT placement
- [ ] Show class/group counts
- [ ] Show unplaced students
- [ ] Show capacity violations
- [ ] Show missing teacher/resource assignments
- [ ] Show subject conflicts
- [ ] Allow authorized staff to move students
- [ ] Revalidate after changes
- [ ] Confirm placement
- [ ] Lock finalized placement according to school policy
- [ ] Record placement run/audit history

# PHASE 7 — Automatic Grade Promotion

- [ ] Configure promotion rules
- [ ] Analyze yearly results
- [ ] Include attendance where configured
- [ ] Identify PROMOTE
- [ ] Identify REVIEW
- [ ] Identify REPEAT
- [ ] Generate promotion proposal
- [ ] Allow authorized review
- [ ] Approve promotion run
- [ ] Create next-year class history
- [ ] Trigger next-stage subject selection when appropriate
- [ ] Never delete previous class history

# PHASE 8 — Examination, Results and Academic History

- [ ] Examination types
- [ ] Exam scheduling
- [ ] Marks entry
- [ ] Grade calculation
- [ ] Result verification
- [ ] Result publication
- [ ] Term/school exam history
- [ ] G.C.E. O/L history
- [ ] G.C.E. A/L history
- [ ] Result documents
- [ ] Result reports
- [ ] Permission-protected live marks workflows

# PHASE 9 — Timetable Engine

- [ ] 8 periods/day
- [ ] 40 minutes/period
- [ ] 7:30 school start
- [ ] 7:50 teaching start
- [ ] 10:30 interval start
- [ ] 10:30–10:50 interval
- [ ] 1:30 school end
- [ ] Use home classes and subject groups
- [ ] Use teacher assignments
- [ ] Use weekly subject periods
- [ ] Use availability
- [ ] Use rooms/resources where enabled
- [ ] Teacher conflict detection
- [ ] Class conflict detection
- [ ] Subject/group conflict detection
- [ ] Double periods
- [ ] No double period across interval
- [ ] DRAFT → REVIEW → PUBLISHED
- [ ] Manual adjustments
- [ ] Final conflict validation

# PHASE 10 — Daily School Management

- [ ] Student attendance
- [ ] Staff/teacher attendance where enabled
- [ ] Assignments
- [ ] Notices
- [ ] School calendar
- [ ] Events
- [ ] Notifications where needed

# PHASE 11 — Student Development & Records

- [ ] Achievements
- [ ] Certificates
- [ ] Activities
- [ ] Clubs/societies
- [ ] Sports
- [ ] Discipline records with restricted permissions
- [ ] Student documents
- [ ] Student profile timeline
- [ ] Leaving/completion record
- [ ] Automatic leaving/completion report
- [ ] Unique report reference number
- [ ] Archive history
- [ ] Alumni record

# PHASE 12 — Library

- [ ] Catalogue
- [ ] Book copies
- [ ] Members
- [ ] Issue
- [ ] Return
- [ ] Renew
- [ ] Due dates
- [ ] Overdue
- [ ] Lost/damaged
- [ ] Borrowing history
- [ ] Library reports

# PHASE 13 — Reports & Documents

- [ ] Student profile reports
- [ ] Class lists
- [ ] Subject group lists
- [ ] Basket selection lists
- [ ] Promotion reports
- [ ] Placement reports
- [ ] Attendance reports
- [ ] Examination/result reports
- [ ] O/L reports
- [ ] A/L reports
- [ ] Teacher workload reports
- [ ] Timetables
- [ ] Achievement/certificate reports
- [ ] Leaving/completion reports
- [ ] Library reports
- [ ] Event reports
- [ ] PDF/print-friendly output

# PHASE 14 — Dashboards & Analytics

- [ ] Admin dashboard
- [ ] Secretary dashboard
- [ ] Teacher dashboard
- [ ] Student dashboard
- [ ] Parent dashboard
- [ ] Student/class counts
- [ ] Attendance analytics
- [ ] Result/pass analytics
- [ ] Subject performance
- [ ] O/L/A/L analytics
- [ ] Promotion analytics
- [ ] Placement/capacity analytics
- [ ] Teacher workload analytics
- [ ] Library analytics
- [ ] Event analytics
- [ ] Role-based data visibility
- [ ] Performance optimization for large schools

# PHASE 15 — Global Search

- [ ] Search students
- [ ] Search Student Code exactly
- [ ] Search Admission Number exactly
- [ ] Search teachers
- [ ] Search parents
- [ ] Search classes
- [ ] Search subjects
- [ ] Search subject groups
- [ ] Search baskets
- [ ] Search achievements
- [ ] Search certificates
- [ ] Search results
- [ ] Search library
- [ ] Search events
- [ ] Permission-filter every result
- [ ] Do not expose unauthorized records through autocomplete
- [ ] Index high-use fields

# PHASE 16 — Security, Audit, Backup

- [ ] Full RBAC matrix
- [ ] Server-side permission checks
- [ ] Record-level authorization
- [ ] Audit every important academic/admin change
- [ ] Log promotion runs
- [ ] Log placement runs
- [ ] Log subject/basket changes
- [ ] Log O/L/A/L historical changes
- [ ] Log certificate/document changes
- [ ] Log leaving/completion changes
- [ ] Secure one-time codes
- [ ] Prevent code reuse
- [ ] Prevent IDOR
- [ ] Backup plan
- [ ] Restore testing
- [ ] Production error logging

# PHASE 17 — UX / Responsive / Accessibility

- [ ] Admin navigation
- [ ] Secretary navigation
- [ ] Teacher navigation
- [ ] Student navigation
- [ ] Parent navigation
- [ ] Mobile drawer
- [ ] Responsive tables
- [ ] Responsive forms
- [ ] Responsive timetable
- [ ] Responsive subject/basket selection
- [ ] Responsive placement review
- [ ] Loading/empty/error states
- [ ] Confirmation dialogs
- [ ] Keyboard-friendly controls
- [ ] Readable contrast

# PHASE 18 — Testing

## Academic Logic Tests

- [ ] Basket rule validation
- [ ] Invalid O/L combination rejection
- [ ] Valid O/L combination acceptance
- [ ] A/L stream validation
- [ ] A/L subject combination validation
- [ ] Optional subject validation
- [ ] Capacity calculations
- [ ] Automatic class splitting
- [ ] Subject group allocation
- [ ] Unplaced student detection
- [ ] Promotion calculations
- [ ] Historical class preservation
- [ ] Timetable conflicts
- [ ] Double-period conflicts

## Security Tests

- [ ] Authentication
- [ ] Authorization
- [ ] IDOR prevention
- [ ] CSRF
- [ ] XSS
- [ ] SQL injection
- [ ] File upload validation
- [ ] Private document access
- [ ] Audit log integrity

## Scale Tests

- [ ] 1,000+ students
- [ ] 3,000+ students
- [ ] Large class lists
- [ ] Large subject-group lists
- [ ] Large search index
- [ ] Promotion run performance
- [ ] Placement run performance
- [ ] Timetable generation performance

# PHASE 19 — Production Readiness

- [ ] Remove debug output
- [ ] Configure production environment
- [ ] Secure secrets
- [ ] Configure HTTPS when deployed
- [ ] Configure backups
- [ ] Test restore
- [ ] Review permissions
- [ ] Review audit logging
- [ ] Review database indexes
- [ ] Review upload/storage security
- [ ] Final UI review
- [ ] Final mobile review
- [ ] Final academic workflow review with real school rules

# Definition of Done

A feature is complete only when:

1. Database structure exists.
2. Backend validation exists.
3. Server-side authorization exists.
4. UI is implemented.
5. Mobile/responsive behavior is checked.
6. Audit requirements are implemented where applicable.
7. Error/empty/loading states exist.
8. Tests cover important rules.
9. Documentation is updated.
10. Existing academic history is preserved.

# Recommended Build Order

```text
Foundation
  ↓
Authentication + RBAC
  ↓
School Administration
  ↓
Academic Years / Grades / Classes
  ↓
Subjects + Optional Subjects
  ↓
O/L Baskets + Student Selection
  ↓
A/L Streams + Subject Combinations
  ↓
Students + Teachers + Parents
  ↓
Promotion Engine
  ↓
Class Splitting + Subject Group Placement
  ↓
Exams + Results
  ↓
Timetable Engine
  ↓
Attendance + Assignments + Notices
  ↓
Events + Library
  ↓
Achievements + Certificates + Documents
  ↓
Reports + Leaving + Alumni
  ↓
Analytics + Global Search
  ↓
Security/Audit/Backup
  ↓
Testing + Production
```

# Current Scope

The approved SSMS scope includes school administration, Secretary/Office Staff management, complete student academic history, examinations, achievements/certificates, attendance, automatic timetable generation with double periods, assignments, notices, events, library, teacher management, parent portal, advanced analytics, document/report generation, alumni, security/audit, and global search.

The newly confirmed academic placement scope additionally requires **Admin-configurable O/L subject baskets at Grade 10/O/L stage, configurable A/L streams and subject combinations, optional subjects, student subject selection, automatic class splitting and subject-group allocation based on those selections, manual review, validation, and permanent placement/class history**.
