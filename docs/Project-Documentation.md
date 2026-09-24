# Project Documentation

## 1. Executive Summary

The Ganesh Mahotsav-2026 Project Tracker was created to solve an operational problem involving collection and expense management. The source information was maintained in Google Sheets, but the process required stronger validation, controlled synchronization, financial reconciliation and a live reporting interface.

The solution retained Google Sheets as the operational source of truth and added Google Apps Script as the automation and synchronization layer, with Hatchable providing the live web application.

## 2. Business Problem

The original process had several risks:

- manual calculation errors
- inconsistent data entry
- duplicate records during repeated synchronization
- lack of a convenient live reporting view
- risk of accidental deletion
- difficulty confirming whether source and application totals matched
- need for an explicit as-on-date position

## 3. Product Requirements

### Functional requirements

- Maintain collection records.
- Maintain expense records.
- Calculate total outflow.
- Calculate available balance.
- Synchronize source records to the live application.
- Support updates without creating duplicates.
- Validate amounts, dates and required fields.
- Protect normal synchronization from unintended deletion.
- Provide explicit deletion confirmation.
- Support as-on-date reporting.
- Reconcile source and application totals.

### Non-functional requirements

- Simple for non-technical operators.
- Low-cost.
- Easy to audit.
- Reliable repeated synchronization.
- Readable live reporting.
- Maintainable automation.

## 4. Data Model

### Collections

Collection records contain contributor/collection information, amount, date and Sync ID.

### Expenses

Expense records contain:

- Item Type
- Advance
- Settled amount
- Date
- SPOC
- Sync ID

### Sync identity

Stable Sync IDs identify records across the source and live application.

## 5. Implementation

### Source layer

Google Sheets was used as the operational source of truth.

### Automation layer

Google Apps Script handled:

- validation
- Sync ID creation and repair
- change detection
- synchronization
- duplicate prevention
- deletion confirmation
- reconciliation

### Application layer

Hatchable provided the live browser-based tracker.

## 6. Financial Logic

`Total Outflow = Advance + Balance/Settlement + Final Amount`

`Available Balance = Opening Balance + Collections - Total Outflow`

Blank settlement values are treated as zero.

## 7. Testing

Testing covered:

1. Initial synchronization
2. Financial reconciliation
3. Blank settlement handling
4. Existing-record update
5. Duplicate protection
6. Validation
7. Deletion protection
8. Confirmed deletion
9. Post-sync status

## 8. Results

- 21 collection records
- ₹2,72,504 total collections
- 34 expense records
- ₹1,63,542 total outflow
- ₹1,08,962 available balance

## 9. Key lesson

The main technical challenge was synchronization integrity. Create, update and delete operations need different controls. Stable record identity makes updates safe, while deletion requires an explicit confirmation path.

## 10. Future production improvements

- Role-based access
- Audit log
- Automated alerts
- Regression testing
- Monitoring
- Backup/restore
- Formal database/API layer for larger scale
