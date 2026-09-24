# Ganesh Mahotsav 2026 Project Tracker

> A live collection and expense management solution built with Google Sheets, Google Apps Script and Hatchable.

[![Live Tracker](https://img.shields.io/badge/Live%20Tracker-Open%20Project-blue)](https://puja-collections.hatchable.site)
[![Project Status](https://img.shields.io/badge/Status-Completed-success)]()
[![Portfolio Project](https://img.shields.io/badge/Type-Portfolio%20Project-informational)]()

## Project at a glance

This project converts a manually maintained event-finance spreadsheet into a controlled, automated reporting workflow.

The design keeps **Google Sheets as the operational source of truth**, uses **Google Apps Script** for validation and synchronization, and presents the information through a **Hatchable live web application**.

### Architecture

```text
                 OPERATIONAL LAYER
              ┌─────────────────────┐
              │     Google Sheets   │
              │ Collections/Expense │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Google Apps Script  │
              │                     │
              │ • Validation        │
              │ • Sync IDs          │
              │ • Change detection  │
              │ • Duplicate control │
              │ • Delete control    │
              │ • Reconciliation    │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Hatchable Web App   │
              │                     │
              │ • Live tracker      │
              │ • KPI reporting     │
              │ • As-on-date view   │
              └──────────┬──────────┘
                         │
                         ▼
                 MANAGEMENT VIEW
```

## Business problem

Collection and expense records for the event were being maintained in a spreadsheet. The process needed:

- reliable financial calculations
- validation before synchronization
- a simple live reporting interface
- safe handling of updates
- duplicate prevention
- controlled deletion
- reconciliation between source and live application
- an explicit reporting date

The project was therefore designed as a small but complete **source-to-report data workflow** rather than simply a spreadsheet redesign.

## Objectives

1. Maintain a single operational source of truth.
2. Automate synchronization with the live application.
3. Validate financial and date fields.
4. Prevent duplicate records.
5. Support updates to existing records.
6. Protect against accidental deletion.
7. Reconcile source and live totals.
8. Provide an accessible live tracker.

## Key features

- Collection tracking
- Expense tracking
- Stable Sync IDs
- Automated synchronization
- Change detection
- Duplicate protection
- Numeric and date validation
- Controlled deletion workflow
- Financial reconciliation
- As-on-date reporting
- Live browser-based reporting

## Financial model

### Total outflow

`Total Outflow = Advance + Balance/Settlement + Final Amount`

### Available balance

`Available Balance = Opening Balance + Collections - Total Outflow`

Blank settlement values are treated as zero for reporting.

## Validated project snapshot

| Metric | Value |
|---|---:|
| Collection records | 21 |
| Total collections | ₹2,72,504 |
| Expense records | 34 |
| Advance | ₹21,000 |
| Settled amount | ₹1,42,542 |
| Total outflow | ₹1,63,542 |
| Opening balance | ₹50,000 |
| Available balance | ₹1,08,962 |

## Testing

The project was tested for:

- initial synchronization
- financial reconciliation
- blank settlement handling
- update of existing records
- duplicate protection
- numeric/date/required-field validation
- deletion protection
- confirmed deletion
- post-sync status

### Important control test

Deletion was treated differently from normal create/update synchronization.

A normal synchronization attempt returned **HTTP 409 Conflict** rather than silently deleting live data. The explicit deletion confirmation workflow then removed exactly the intended test record.

This demonstrated an important principle: **financial synchronization should be designed for data integrity, not merely successful API calls.**

## Screenshots

### Live Tracker
![Live Tracker](screenshots/01-live-tracker.png)

The deployed tracker provides a management-level view of collections, expenses, balance, entry counts and financial flow.

### Source Data
![Source Data](screenshots/02-source-data.png)

Google Sheets acts as the operational source of truth for collection and expense records.

### Synchronization & Validation
![Sync Validation](screenshots/03-sync-validation.png)

Google Apps Script controls synchronization, validation, change detection and deletion protection.

## Technology stack

| Technology | Role |
|---|---|
| Google Sheets | Operational source of truth |
| Google Apps Script | Automation and synchronization |
| Hatchable | Live web application |
| API integration | Source-to-application data movement |
| Spreadsheet formulas | Financial calculation and reconciliation |
| Browser testing | Functional validation |

## Skills demonstrated

- Requirements analysis
- Data modelling
- Financial reconciliation
- Spreadsheet engineering
- Google Apps Script automation
- API/data synchronization
- CRUD concepts
- Record identity management
- Data validation
- Exception handling
- Functional testing
- Operational reporting
- AI-assisted application development

## Project documentation

Detailed documentation is available in:

`docs/Ganesh-Mahotsav-Project-Tracker-Portfolio-Interview-Document.docx`

The document contains the PRD, implementation approach, architecture, testing strategy, risks and controls, project results, portfolio description and interview preparation.

## Portfolio description

**Ganesh Mahotsav 2026 Project Tracker** is a live collection and expense management solution built using Google Sheets, Google Apps Script and Hatchable. It automates source-to-application synchronization, validates financial data, prevents duplicate records, supports controlled deletion and provides reconciled as-on-date reporting.

## Interview positioning

The project can be explained as:

> Business problem → data model → financial rules → validation → automation → synchronization → live reporting → reconciliation → testing.

This framing demonstrates practical data and automation skills rather than presenting the project as only a spreadsheet tracker.

## Production improvements

For a larger production deployment, the next improvements would include:

- role-based access control
- formal audit logging
- automated failure alerts
- stronger deletion approval
- automated regression tests
- backup and restore procedures
- monitoring and retry handling
- a formal database/API architecture for higher scale

## Live project

**[Open the Live Tracker](https://puja-collections.hatchable.site)**

## Repository

**[GitHub Repository](https://github.com/rahuldasctc/ganesh-mahotsav-project-tracker)**

---

**Project Owner:** Rahul Das  
**Project:** Ganesh Mahotsav 2026 Project Tracker  
**Status:** Completed
