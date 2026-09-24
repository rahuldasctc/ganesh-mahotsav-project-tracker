# Interview Playbook

## 60-second explanation

“I built a live collection and expense tracker for a Ganesh Mahotsav project. The starting point was a Google Sheet where collections and expenses were maintained, but the process needed stronger validation, automated calculations and a simple live reporting interface.

I kept Google Sheets as the source of truth and built a Google Apps Script synchronization layer between the sheet and a Hatchable web application. The script validates amounts and dates, maintains stable Sync IDs, prevents duplicates, handles updates and uses a separate confirmation workflow for deletions.

The tracker also supports an as-on-date view and reconciles live totals with the source data. I tested the solution with real project data, including a deletion-control test where normal synchronization returned HTTP 409 and the confirmed deletion removed exactly the intended test record.”

## Questions and answers

### 1. What problem did you solve?

The process needed a reliable way to maintain collections and expenses, synchronize them to a live application and verify financial totals.

### 2. Why Google Sheets?

Users were already comfortable with it. It also provided an accessible operational source of truth and made auditing easier.

### 3. Why Apps Script?

It integrates naturally with Google Sheets and can automate validation, synchronization and control logic without a separate backend server.

### 4. What is a Sync ID?

A stable identifier that connects a source record to its corresponding application record.

### 5. How did you prevent duplicates?

The synchronization process uses stable Sync IDs and change detection. Re-running synchronization does not create a second record for the same source row.

### 6. Why is deletion handled separately?

Deletion can permanently remove application data. A normal sync therefore should not silently interpret a missing source row as permission to delete live data.

### 7. What validations were used?

Numeric, non-negative, required-field and date validation.

### 8. How did you calculate the balance?

Opening balance plus collections minus total outflow.

### 9. How did you prove the system was correct?

By reconciling record counts and financial totals between the source and live application.

### 10. What was technically difficult?

Synchronization integrity. Handling create, update and delete scenarios safely is more important than simply making an API call succeed.

### 11. What would you improve?

I would add role-based access, audit logs, monitoring, alerts, automated regression testing and a stronger database/API architecture for scale.

### 12. Is this enterprise production software?

It is a working operational portfolio project. A large enterprise deployment would require additional security, access control, monitoring, audit and backup controls.

### 13. How is this relevant to your professional background?

The project applies the same principles used in revenue assurance and financial analytics: source-to-report data flow, validation, reconciliation, exception handling, calculation accuracy and automation.

## Strong interview framing

Do not say:

> “I made a Google Sheet tracker.”

Say:

> “I designed and implemented a source-to-report financial workflow with automated synchronization, validation, reconciliation and controlled data operations.”

That accurately describes what the project demonstrates without overstating its production scale.
