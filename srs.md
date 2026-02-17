

# Ethiopian Exam Preparation Website: SRS Document
---
## Revision History

| Name  | Date       | Reason For Changes | Version |
| ----- | ---------- | ------------------ | ------- |
| Dagmawi | 2026-02-17 | Initial draft      | 1.0     |

## Table of Contents

- [1 Introduction](#1-introduction)
- [2. System Overview](#2-system-overview)
- [3. Functional Requirements](#3-functional-requirements)
  - [FR1. Multi-Institutional Support](#fr1-multi-institutional-support)
  - [FR2. User Registration and Authentication](#fr2-user-registration-and-authentication)
  - [FR3. Role-Based Access Control (RBAC)](#fr3-role-based-access-control-rbac)
  - [FR4. Exam and Question Management](#fr4-exam-and-question-management)
  - [FR5. Exam Delivery and Simulation](#fr5-exam-delivery-and-simulation)
  - [FR6. Automatic Grading and Results](#fr6-automatic-grading-and-results)
  - [FR7. Performance Analytics and Reporting](#fr7-performance-analytics-and-reporting)
  - [FR8. Admin Features](#fr8-admin-features)
  - [FR9. Notifications and Communication](#fr9-notifications-and-communication)
- [4. Use Cases](#4-use-cases)
  - [Student Registration](#student-registration)
  - [Admin Assigns Teacher](#admin-assigns-teacher)
  - [Teacher Creates Exam](#teacher-creates-exam)
  - [Student Takes Exam](#student-takes-exam)
  - [View Results and Analytics (Teacher)](#view-results-and-analytics-teacher)
  - [Administrator Reviews System Usage](#administrator-reviews-system-usage)

## 1 Introduction
---
The (SRS) for this Ethiopian web based Exam Preparation and Management website is for use by Ethiopian high school and college students to prepare for the National Exam (TAT), University Entrance exam and Exit exam. The exam preparation website should allow Ethiopian students to prepare in a realistic simulated testing environment that closely represents an official government exam. This is a multi-institutional website that allows many schools, colleges, and exam preparation centres throughout Ethiopia to operate on a single platform. Students are able to self-register for an account and school administrators can manage their schools and assign teachers. All users will be interacting with an interface that mimics the look and feel of an official government exam user interface (UI) and associated workflows. The major objectives of the exam preparation website include automated scoring of multiple choice exams, automated real-time reporting of results, and comprehensive reporting, analysis and performance for students and teachers. The automated



## 2. System Overview

This platform is a cloud-based SaaS platform utilising a multi-tenant architecture. Institutions (such as schools or preparatory centres) in the system act as individual “tenants”, but they share the core application and infrastructure of the system while keeping their data in private and segregated partitions. This structure makes it easy to add additional institutions and provides resources for institutions to be added or scaled up easily (e.g. adding more servers during peak exam times). The platform is accessed via a browser and all of the screens are dynamically responsive to device and platform specifications.

Users of the platform fall into specific defined roles and have security access controls set at a high level. The primary user groups are as follows:

Central Administrators (Admins) – The central administrators have complete control over creating new institutions, assigning teachers to those institutions, creating and managing system-wide settings, determining which schools are able to be created in the system, and creating and managing global exam templates.


Institution Admins/Managers (optional): Optionally, each institution may have one or more local admins (e.g., a school principal or exam coordinator) who liaise with the central system admin, monitor their institution’s usage, and approve teacher accounts.

Teachers: Authorized by admins, teachers can create/edit question banks and exams for their assigned institution, view student rosters, monitor exam results, and run reports on student performance.

Students: Any student can self-register with valid ID or credentials. Students can take mock tests, model exams, or simulated official exams on the platform. After each exam, students see immediate results.

An efficient and easy user interface (UI) design was developed to be helpful and lessen stress for students taking online exams through the exam interface on the platform. Utilizing proven practices for user experience (UX), the exam interface has been designed to include clear navigation, feedback per step and status indicator showing students the current location on the exam. An example of this is a constant timer and easily accessed “Next/Back” button will be visible to students while taking an online exam similar to what they will see when taking a national exam. If a system is calculating a score or has not completed loading, it will notify the student so that they do not have to worry about what to expect. The students will focus only on demonstrating their knowledge during the exam and the exam interface (UI) will not be a distraction.

All exam questions are multiple-choice. The system automatically grades them immediately upon test submission. An example SRS for online exams notes that such systems allow candidates to take tests “anywhere at any time” and automatically grade them with instant results. Likewise, our platform will instantly compute each student’s score and show pass/fail status, along with detailed analytics. Teachers and admins will have dashboards  that summarize student scores by subject and over time. For instance, a modern result-management solution highlights “subject-wise analysis” and real-time dashboards for performance insights. The platform will generate reports (marksheets, progress charts, ranking lists) dynamically for any exam.

All test items consist of multiple-choice answers and will be graded by the system within seconds after the test has been finished. An example of a student's record system (SRS) for internet testing states that the system gives students the ability to test "anywhere" and "at any time," and that it grades each test with instant results. Similarly, the SRS will also calculate the student's score and indicate if they passed or failed, as well as provide additional details about their performance through various statistics (e.g., subject areas). In addition, teachers and administrators will have access to a dashboard that will display all students' subject-area scores for a specified period of time. For example, an updated results-management system includes the ability to provide "subject-wise analysis" and "real time" performance information displayed on a dashboard. Finally, the SRS system will produce all required reporting documentation for every examination, including scorecards, progress graphs, and rankings, using information generated dynamically.

## 3. Functional Requirements

### FR1. Multi-Institutional Support:

The solution must be capable of managing multiple institutions (schools, colleges, assistive prep centers). The data for each institution (users, tests, scores) must be kept separate and logically separate (or "multi-tenant") from each other (i.e., each user can only see users from his/her institution). As one vendor has stated regarding education software, "the central station has central management capabilities for multi-location and multi-division institutions." An administrator may add; modify; or deactivate an institution by adding the institution name; address; exam calendar; and any other applicable data to its profile.

### FR2. User Registration and Authentication:

Student Self-Registration: Anyone can register themselves as a student using a valid email and phone. The registration page asks for personal details (name, ID number, contact), and a verification email is sent. After verification, the student’s account is activated.

Teacher Accounts: Teachers cannot register themselves; only an Admin can create or approve teacher accounts and assign teachers to one or more institutions.

Admin Accounts: Super-admins are automatically created during the system deployment and can create new admins. Institution admins (if used) are created/assigned by super-admins.

Login/Logout: All users log in using a username/email and password. After successful login, they are redirected to a role-specific dashboard. Normal security practices (password hashing, timeouts) are mandatory.

### FR3. Role-Based Access Control (RBAC):

The RBAC structures are established for each user role within the platform. Therefore, students may only have access to their own examination results and take their examinations, teachers may manage their students’ examinations and exam questions, while the administrator will manage users and institutions. The method employed adheres to best industry practice: “Only authorized personnel have access to sensitive examination materials according to RBAC”. As stated in one source, implementing RBAC within the examination system is imperative to maintaining the system’s integrity and security.

### FR4. Exam and Question Management:

Question Bank: Teachers (and admins) can create a pool of multiple-choice questions. Each question has one correct answer and several distractors. Questions can be categorized by subject (e.g., Math, Physics) and difficulty.

Exam Creation: Users with permission (teachers or admins) can assemble exams from the question bank. For each exam, they set metadata (title, subject, date, time limit, number of questions, pass marks). The exam can be marked as a Mock Test, Model Exam, or Final Exam. It should closely replicate the national exam pattern (same number of questions, time per subject, etc.).

Scheduling: Exams can be scheduled at specific times or made available on-demand. Once scheduled or activated, students of the respective institution will be able to see the exam on their dashboard.

### FR5. Exam Delivery and Simulation: 
The exam body must emulate the experience of an official test, meaning that during an examination students will have access to limited options  and each examination will display a countdown timer together with limited means of navigation. The features of the exam interface will be clean and distraction free, resembling those of other national examination software applications. For example, “An effective Examination UI will have clear prompts…that will show a Test-Taker what is happening; and what will happen next,” thus helping to eliminate or reduce the amount of confusion and/or to deal with crashes caused by user error.

Once an examination begins, the system will enforce the time limit by displaying the remaining time and will automatically submit the examination when the allotted time has elapsed. Once an examination has been completed or has expired, the student will not be able to return to the examination.

An answer will be recorded for each question regardless of whether the user was in a valid examination timeframe or not, and therefore it will be impossible for the user to perform any actions (e.g., logging in multiple times) which might compromise the integrity of the examination.
### FR6. Automatic Grading and Results:

The system automatically grades the MCQ exam as soon as the student submits or when time is up. The grading and results are done automatically without any human intervention. the automatic grading system allows students to get their results “the moment the student submits their test”.

The student will then be able to view their result summary (correct, wrong, percentage, pass/fail) and, if desired, a review of each question (selected answer vs. correct answer).

The results will be stored in the student’s record and in the central result database. A distinct result report (such as a PDF marksheet) will be created for each student for each exam.

### FR7. Performance Analytics and Reporting:

The solution must offer performance analytics and reporting capabilities to teachers and admins. Teachers can use the system to analyze performance data in terms of subject-wise performance analysis, performance analysis over multiple exams, class average performance analysis, and individual student performance analysis. The importance of performance analytics is highlighted by one solution, which stresses “subject-wise analysis” and “real-time dashboards” for performance analysis.

Performance data can be analyzed based on exam, subject, date range, or student group. For instance, teachers can use the system to create a report on the top 10 students in a mock exam or an item analysis chart to identify the questions that most students have answered incorrectly in an exam.

School admins (and teachers) can use the system to analyze school performance over time to assess the effectiveness of the curriculum. The system must also enable the creation of traditional reports such as rank lists, certificates for high performers, and student transcripts.

### FR8. Admin Features:

Institution Administration: Admin will be able to create/update school (institution) details (e.g. name, location, number of student enrolments, contact information, etc.). Each institution can have its own separate list of subjects/exams. 

Teacher Assignment: Admin will assign teacher accounts to each institution. Teachers may belong to one or multiple institutions depending on the number of schools they work at.

User Administration: Admins are able to view and manage all accounts created within the application, can reset passwords for accounts, can disable the accounts of users who no longer require access, and can monitor the logins of all accounts.

Audit Logging: The system will maintain a record of relevant events (user logins, start times of exams, actions completed by admin) for accuracy of the audit process.

### FR9. Notifications and Communication:

When important events occur (e.g., a new exam is scheduled, results are released), the system can optionally send email notifications to relevant users (students and/or teachers). This ensures students know when practice exams are available.

## 4. Use Cases

### Student Registration:

Actor: Prospective Student

Preconditions: Internet access; a valid email or student ID.

Main Flow: Student accesses the “Register” page, enters his/her personal information and a new password. The system checks the entered information (for example, checks for a unique email), and then sends a confirmation email. Student clicks on the email link to confirm, and the account is activated.

Postconditions: A student account exists, and the student is prompted to log in.

### Admin Assigns Teacher:

Actor: System Admin

Preconditions: Admin is logged in; teacher user account exists or will be created.

Main Flow: Admin chooses an institution and a teacher’s user account, then assigns the teacher to the institution.

Postconditions: The teacher can now create exams and view reports for that institution’s students.

### Teacher Creates Exam:

Actor: Teacher

Preconditions:The teacher is logged in and assigned to an institution. There are existing questions in the question bank (or the teacher can create new ones).

Main Flow: The teacher selects “Create New Exam”, enters metadata (title, subjects, time limit, etc.), and selects questions from the pool. The teacher saves the exam as a draft or publishes it (makes it available to students).

Postconditions: The exam appears on the dashboard for appropriate students, and is stored in the system’s exam schedule.

### Student Takes Exam:

Actor: Student

Preconditions: Student is logged in and has one or more scheduled exams available. Student has not already taken this exam (or is allowed multiple attempts per rules).

Main Flow: Student clicks “Start Exam” next to a scheduled test. The system displays instructions, then begins the timed exam. Student answers each multiple-choice question (navigating with Next/Back). When time expires or the student submits, the system automatically grades the exam. The result summary is shown immediately.

Postconditions: The student sees their score and passes if above threshold. The result is saved.

### View Results and Analytics (Teacher):

Actor: Teacher

Preconditions: Teacher is logged in and at least one student has completed an exam.

Main Flow: Teacher opens the “Analytics” or “Results” section and selects an exam or date range. The system displays charts and tables (e.g. class average, item analysis, student breakdown). Teacher can drill down to individual student results.

Postconditions: Teacher gains insights (e.g. identifies weak topics) and may export the report as PDF.

### Administrator Reviews System Usage:

Actor: System Admin

Preconditions: Admin is logged in. Some usage data exists.

Main Flow: Admin navigates to an “Institution Summary” dashboard. The system shows totals (number of registered students, number of exams taken, success rates per school, etc.). The admin can filter by institution or time period.

Postconditions: Admin can monitor platform adoption and plan support.
