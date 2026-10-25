# SmartAttend AI

### Smart Student Attendance Management System

> A responsive, browser-based attendance management dashboard for
> organizing departments, classes, students, subjects, attendance
> records, and attendance analytics.

**Project credit:** Designed by **Bharathraj**\
**Project type:** Front-end web application\
**Main file:** `index.html`\
**Storage:** Browser Local Storage\
**Interface:** Responsive layout with light and dark themes

------------------------------------------------------------------------

## Table of Contents

-   [Project Overview](#project-overview)
-   [Objectives](#objectives)
-   [Features](#features)
-   [Application Structure](#application-structure)
-   [Technology Stack](#technology-stack)
-   [Getting Started](#getting-started)
-   [How to Use the Application](#how-to-use-the-application)
-   [Attendance Rules and
    Calculations](#attendance-rules-and-calculations)
-   [Admin Dashboard](#admin-dashboard)
-   [Reports and Exports](#reports-and-exports)
-   [Data Storage and Privacy](#data-storage-and-privacy)
-   [Important Limitations](#important-limitations)
-   [Troubleshooting](#troubleshooting)
-   [Customization](#customization)
-   [Future Enhancements](#future-enhancements)
-   [Project Author](#project-author)
-   [License](#license)

------------------------------------------------------------------------

## Project Overview

SmartAttend AI is a student attendance management web application
designed to help faculty organize academic information and maintain
attendance records through a single interface.

The application supports a hierarchy of **departments → classes →
students and subjects → attendance records**. Faculty can mark
attendance by date and subject, review student attendance percentages,
identify students below a configurable attendance threshold, explore
trends, and export selected records.

The current project is implemented as a client-side web application. It
runs in a modern browser and stores its records in that browser's Local
Storage. It does not require a server or database for basic local use.

**Important naming note:** The project name includes "AI", but the
current attendance alerts and classifications use explicit percentage
rules. The application does not implement a machine-learning model or AI
prediction service.

## Objectives

1.  Make routine attendance entry easier to manage.
2.  Organize student records by department and class.
3.  Maintain subject-wise attendance history by date.
4.  Calculate attendance percentages consistently.
5.  Highlight attendance levels using configurable thresholds.
6.  Provide an administrative overview across classes and departments.
7.  Support filtering and downloadable reports.
8.  Offer a responsive interface with light and dark modes.
9.  Keep the initial installation simple for demonstration and academic
    project use.

## Features

### 1. Dashboard and academic organization

-   Create and view departments.
-   Create classes within a department.
-   View student and subject totals for departments and classes.
-   Navigate between the main dashboard, departments, and class
    workspaces.
-   The interface currently allows up to **10 departments** and **3
    classes per department**.
-   The app starts with empty data when no saved records are present.

### 2. Student management

-   Add student records to a class.
-   Store a student's name and register number.
-   Edit student names and register numbers.
-   Review student attendance information.
-   Search and filter student records in the administrative directory.
-   Validate user-entered text and escape displayed values to reduce
    unsafe HTML injection risks.

### 3. Subject management

-   Create subjects for a class.
-   Keep subjects associated with their class.
-   Mark attendance against a selected subject.
-   Review subject-specific attendance and reports.

### 4. Attendance marking

-   Record attendance for a selected date and subject.
-   Supported attendance statuses:
    -   **Present**
    -   **On Duty**
    -   **Absent**
-   Present and On Duty count as attended records in percentage
    calculations.
-   The app validates dates and prevents future attendance dates in the
    relevant date controls.
-   The data-cleanup logic keeps at most one record for each student,
    date, and subject combination.
-   Attendance history is associated with the selected student and
    subject.

### 5. Attendance monitoring

-   Calculate cumulative and subject-wise attendance percentages.
-   Show attendance status using configurable thresholds.
-   Identify students below the required percentage.
-   Show critical and warning categories.
-   Display a class overview and attendance visualizations.
-   Review attendance history and calendar-oriented views.

### 6. Analytics and reporting

-   Review attendance summaries and trends.
-   Compare attendance across subjects and classes.
-   Use the Admin Dashboard to inspect a wider set of records.
-   Filter student data by department, class, attendance status, or
    search text.
-   Export filtered student data as CSV.
-   Download the recorded absent-student list for the selected date as
    CSV where available.
-   Generate the reports offered by the class workspace.

### 7. Admin Dashboard

The Admin Page provides a read-only overview of attendance and student
records across the available departments and classes.

Depending on the selected filters, it can show:

-   Department, class, student, and subject totals.
-   Attendance completion information for a selected date.
-   Present, absent, partially marked, and not-marked student lists.
-   Overall attendance rate for the selected scope.
-   Department or class rankings based on recorded attendance.
-   A seven-day attendance trend.
-   Students below the configured attendance threshold.
-   A searchable student directory.
-   CSV export for the filtered student list.

**The Admin Page is an overview screen, not a secure login-protected
administrator account.** The current code does not provide
authentication or server-side access control.

### 8. Appearance and usability

-   Responsive layout for desktop and mobile-sized screens.
-   Sidebar navigation on larger screens and a menu control on smaller
    screens.
-   Light and dark themes.
-   Theme preference stored in browser Local Storage.
-   Modal dialogs for relevant data-entry and settings tasks.
-   Toast messages for feedback.
-   Charts and summary cards where supported by the current page.
-   Keyboard Escape handling for closing relevant dialogs and the
    sidebar.

------------------------------------------------------------------------

## Application Structure

The uploaded project is a **single-file application**:

``` text
SmartAttend-AI/
└── index.html
```

The `index.html` file contains:

-   HTML markup for the page layout and dialogs.
-   CSS for layout, cards, tables, themes, and interface states.
-   JavaScript for application state, navigation, validation, attendance
    calculations, rendering, data persistence, and exports.

The project does not require separate `style.css` or `script.js` files
in its current form. These can be extracted later if a multi-file
project structure is desired.

## Technology Stack

  -----------------------------------------------------------------------
  Technology / library                Purpose
  ----------------------------------- -----------------------------------
  HTML5                               Page structure and forms

  CSS                                 Custom interface styles

  JavaScript                          Application logic and dynamic
                                      rendering

  Tailwind CSS CDN                    Utility-based styling

  Chart.js 4.4.1                      Charts and attendance
                                      visualizations

  SheetJS (`xlsx`) 0.18.5             Spreadsheet-related library
                                      included by the page

  jsPDF 2.5.1                         PDF generation library included by
                                      the page

  jsPDF-AutoTable 3.8.2               Table layout support for PDF
                                      exports

  Browser Local Storage               Local persistence of application
                                      records
  -----------------------------------------------------------------------

Some libraries are loaded from external CDNs. An internet connection is
therefore needed for those external libraries to load reliably. The page
is not a fully self-contained offline bundle.

------------------------------------------------------------------------

## Getting Started

### Requirements

-   A modern browser such as Chrome, Edge, Firefox, or Safari.
-   The `index.html` project file.
-   Internet access for the external CDN libraries used by the page.

### Option A --- Open locally

1.  Save `index.html` to a folder on your computer.
2.  Open the file with a modern browser.
3.  The SmartAttend dashboard should load.
4.  Use **＋ Add** to create a department.
5.  Open the department and create a class.
6.  Add students and subjects, then start recording attendance.

For a more consistent development experience, use a local development
server instead of opening the file directly.

### Option B --- Run with Visual Studio Code

1.  Install Visual Studio Code.
2.  Open the folder containing `index.html`.
3.  Use a local preview extension or start a simple local web server.
4.  Open the local address in your browser.
5.  Keep the browser console open while testing so JavaScript errors can
    be identified.

### Option C --- Publish as a static website

Because the current project is client-side, it can be hosted on a static
hosting service.

1.  Create a repository for the project.
2.  Add `index.html` to the repository.
3.  Enable the host's static-site publishing feature.
4.  Open the published URL and test the complete workflow.
5.  Confirm that the CDN dependencies load and that browser storage
    behaves as expected.

**Deployment warning:** Static hosting does not add user accounts,
server-side storage, secure roles, or cross-device synchronization. Each
browser profile maintains its own local records.

------------------------------------------------------------------------

## How to Use the Application

### Step 1 --- Create a department

1.  Open the dashboard.
2.  Select **＋ Add** or **＋ Add Department**.
3.  Enter a department name using English characters.
4.  Create the department.

### Step 2 --- Create a class

1.  Open the department.
2.  Select **＋ Add Class**.
3.  Enter the class name.
4.  Create the class and open it.

### Step 3 --- Add students

1.  Open the class workspace.
2.  Select the **Students** tab.
3.  Add each student's name and register number.
4.  Review the list and correct any errors.

Use the institution's approved register numbers. Avoid entering
unnecessary sensitive information.

### Step 4 --- Add subjects

1.  Open the **Subjects** tab.
2.  Create the subjects taught to the class.
3.  Confirm that each subject is attached to the correct class.

### Step 5 --- Mark attendance

1.  Open **Mark Attendance**.
2.  Select the subject and date.
3.  Mark each student's status.
4.  Review the entries before saving.
5.  Repeat for other subjects and dates.

A student may have one attendance record per date per subject. Follow
the institution's policy for handling corrections.

### Step 6 --- Review attendance

-   Open **Overview** for summary cards and attendance information.
-   Open **Calendar** to inspect date-oriented records.
-   Open **History** to review previously recorded entries.
-   Open **Analytics** for the available charts and comparisons.
-   Open **Report** for the report options provided by the application.

### Step 7 --- Configure the attendance threshold

1.  Select the settings gear in the top bar.
2.  Enter a whole-number minimum attendance percentage from **1 to
    100**.
3.  Save the threshold.
4.  Review the updated status categories.

The default minimum attendance threshold is **75%**. The preference is
stored in the current browser.

### Step 8 --- Use the Admin Page

1.  Select **Admin Page** from the sidebar.
2.  Choose the department or class scope.
3.  Use the search field and attendance-status filter.
4.  Review the attendance summary and student directory.
5.  Export the filtered list when required.

### Step 9 --- Back up records

Export available reports and keep a secure backup of important data.
Browser storage is not a substitute for an institutional database or an
independent backup process.

------------------------------------------------------------------------

## Attendance Rules and Calculations

### Attendance percentage

The application counts **Present** and **On Duty** as attended records.
**Absent** records are not counted as attended.

The basic calculation is:

\[ `\text{Attendance \%}`{=tex} =
`\frac{\text{Present records + On Duty records}}`{=tex}
{`\text{All marked records}`{=tex}} `\times 100`{=tex} \]

When there are no marked records, the percentage is not displayed as a
meaningful measured percentage; the interface may show a dash or a
no-data status.

### Status categories

Let `TH` be the configured minimum attendance percentage.

-   **Safe:** attendance is at or above `TH`.
-   **Warning:** attendance is below `TH`, but at or above the critical
    limit.
-   **Critical:** attendance is below the critical limit.
-   **No Data:** the student has no recorded attendance for the relevant
    calculation.

The critical limit is calculated as:

\[ `\text{Critical limit}`{=tex} = `\max`{=tex}(0, TH - 10) \]

For example, with a minimum threshold of 75%, the critical limit is 65%.
A measured attendance rate of 80% is Safe, 70% is Warning, and 60% is
Critical.

The implementation includes special handling for rounded percentages so
that display rounding does not incorrectly move a student across a
threshold.

### Overall attendance in the Admin Page

The Admin Page's overall rate is weighted across recorded
student-subject entries in the selected scope:

**Present/On Duty records ÷ all marked records × 100**

This differs from averaging each student's displayed percentage, so the
two figures may not be identical.

### Attendance completion

The daily completion indicator compares the number of recorded subjects
for a student with the number of subjects assigned to that student's
class. This is a subject-assignment comparison, not a timetable
integration.

------------------------------------------------------------------------

## Reports and Exports

The current code includes CSV downloads for selected administrative
data.

### Filtered student CSV

The Admin Page export can include:

-   Department
-   Class
-   Student name
-   Register number
-   Present / On Duty count
-   Total recorded entries
-   Attendance percentage
-   Attendance status

The exported list follows the active filters.

### Absent-student CSV

Where the absent-list export is available, it includes the student name,
register number, class, and recorded absent subjects for the selected
date.

### PDF and spreadsheet libraries

The HTML loads SheetJS and jsPDF-related libraries. The exact export
formats available to the user depend on the relevant report functions in
the application. Do not assume that every screen automatically exports
to PDF or Excel merely because a library is included.

------------------------------------------------------------------------

## Data Storage and Privacy

### Where is data saved?

The current application stores departments, classes, students, subjects,
attendance history, and the threshold setting in the browser's **Local
Storage**.

This means:

-   Data normally remains in the same browser profile after closing and
    reopening the page.
-   Data is not automatically uploaded to a cloud database.
-   Data is not automatically shared with faculty members using other
    devices.
-   Clearing site/browser storage may erase saved records.
-   Private/incognito sessions may discard data when the session ends.
-   Browser storage capacity and browser policies can affect saving.
-   Opening the same website in a different browser or device will not
    automatically bring the same records across.

The application includes data validation, recovery-oriented handling for
some malformed stored records, and safeguards for failed multi-key
saves. These safeguards are helpful but do not replace regular backups.

### Student data safety

Student names, register numbers, and attendance records can be personal
information.

-   Use only data you are authorized to manage.
-   Do not publish real student records in a public repository or public
    demo.
-   Use fictional sample records for screenshots and demonstrations.
-   Restrict access to the device and browser profile used for real
    records.
-   Follow the institution's data-retention and privacy policies.
-   Do not treat the current Admin Page as a security boundary.

### No cloud synchronization

There is no backend API, server database, or authenticated multi-user
synchronization in the current single-file implementation. These would
need to be added for a production deployment shared by multiple faculty
members.

------------------------------------------------------------------------

## Important Limitations

1.  **Local-only storage:** records are stored in the current browser,
    not a central database.
2.  **No login system:** the Faculty/Admin labels are interface
    elements; they do not establish verified identity.
3.  **No server-side authorization:** a user who can access the page and
    browser storage may be able to inspect or modify local records.
4.  **Rule-based alerts:** attendance warnings are based on percentage
    thresholds, not machine learning.
5.  **External dependencies:** CDN libraries may fail to load without
    internet access or if a CDN is blocked.
6.  **No automatic cross-device sync:** records do not travel between
    devices automatically.
7.  **No built-in institutional integration:** the current project does
    not connect to an official college database, timetable, biometric
    device, or student information system.
8.  **Backups are essential:** clearing browser data can remove local
    records.
9.  **Not yet a production-grade multi-user service:** real
    institutional deployment needs authentication, authorization, a
    backend, data protection, backups, and testing.

------------------------------------------------------------------------

## Troubleshooting

### The page is blank or a chart is missing

-   Confirm that the browser is up to date.
-   Check that the internet connection is working for CDN resources.
-   Reload the page.
-   Open Developer Tools and inspect the Console for errors.

### My records disappeared

-   Check that you are using the same browser and browser profile.
-   Confirm that you did not switch to private/incognito mode.
-   Check whether browser/site data was cleared.
-   Avoid clearing site storage before exporting or backing up records.

### Changes are not saving

-   Confirm that browser storage is enabled.
-   Check whether the browser is in a restricted/private environment.
-   Free storage space if the browser reports storage problems.
-   Export any available data before attempting major changes.
-   Review the on-screen toast message for save errors.

### The theme changed back

The theme preference is stored locally. Check that Local Storage is
available and that you are opening the same site origin or browser
profile.

### The exported CSV looks unusual

-   Open it in a spreadsheet application that supports CSV.
-   Confirm the delimiter and character encoding.
-   Remember that CSV exports contain values, not the formatting of the
    dashboard.

------------------------------------------------------------------------

## Customization

### Change the application title

Update the `<title>` element in `index.html`.

### Change the brand color

The Tailwind configuration defines the brand color palette near the top
of the file. Update those values and any matching custom CSS values if
you want to change the visual theme consistently.

### Change the default attendance threshold

The application defaults to 75% when no valid saved threshold is found.
Users can also change the threshold using the Settings control. The
saved browser value takes precedence until it is changed or cleared.

### Split the single HTML file

For a larger project, the application can be reorganized into:

``` text
SmartAttend-AI/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── app.js
└── README.md
```

If the code is split, update the HTML references to the new CSS and
JavaScript files and test all navigation, modals, storage, exports, and
chart rendering.

------------------------------------------------------------------------

## Future Enhancements

Potential next steps for a more robust version include:

-   Secure faculty login and role-based permissions.
-   Backend API and central database.
-   Encrypted transport and appropriate protection for stored records.
-   Institution-wide backups and data recovery.
-   Multi-user, multi-device synchronization.
-   Audit history for attendance edits.
-   Better import/export workflows for CSV and Excel.
-   Automated testing for calculations, data validation, and record
    migration.
-   Timetable integration and class-session validation.
-   Optional authorized student/parent views.
-   Accessibility improvements and more extensive keyboard navigation.
-   Offline-first packaging with locally bundled dependencies.
-   Server-side reporting and controlled data retention.
-   Clear separation of demo data and real student data.

These are proposed enhancements, not claims about features already
implemented.

------------------------------------------------------------------------

## Project Author

**Designed by:** Bharathraj\
**Project name:** SmartAttend AI --- Students Attendance Tracker

This README documents the current uploaded `index.html` implementation.
If the code changes, update this document to keep the feature
descriptions, setup steps, and limitations accurate.

## License

No specific open-source license is declared in the current project file.
Add a license file and name the intended license before redistributing
the project as open source.
