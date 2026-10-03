# Implement-Client-Script-UI-Policy-Incident-
Implement Client Script & UI Policy (Incident)

Team Members

Team Leader

Sharukesh T A

Team Members

- Ananth M
- M S Giri Munnesh
- Ajith R
- E Santhosh

---

Problem Statement

Incident records often require consistent and accurate data entry to ensure effective triage, routing, and resolution. Relying on manual checks can lead to incomplete, inconsistent, or incorrect information.

This project implements ServiceNow UI Policies and Client Scripts to enforce conditional field behavior and validation directly at the user interface level.

---

Objective

The objective of this project is to demonstrate how ServiceNow client-side controls can be used to improve data integrity on Incident records.

The implementation demonstrates:

- Dynamic field behavior
- Automatic value population
- Mandatory field validation
- Form save validation
- List edit restrictions

---

Skills

- Incident Management
- UI Policy
- UI Policy Actions
- Client Scripts
- Form Validation

---

Project Implementation

Task 1: UI Policy – High Impact Control

Table: Incident

Name: High Impact Control

Condition:

- Field: Impact
- Operator: is
- Value: 1 – High

Active: True

Reverse if false: True

The UI Policy applies additional controls when the Incident Impact is High.

---

Task 2: UI Policy Action – Urgency

Field: Urgency

Read-only: True

When Impact is High, the Urgency field becomes read-only.

---

Task 3: onChange Client Script

Name: Auto set urgency for high impact

Table: Incident

Type: onChange

Field: Impact

This Client Script automatically sets Urgency to High when Impact is High.

---

Task 4: onSubmit Client Script

Name: Prevent save if Assigned To missing

Table: Incident

Type: onSubmit

This Client Script prevents the Incident from being saved when:

- Impact is High
- Assigned To is empty

---

Task 5: onCellEdit Client Script

Name: Prevent state change via list edit

Table: Incident

Type: onCellEdit

Field: State

This Client Script prevents users from changing the State directly from the Incident list.

---

Testing

Test 1: Mandatory Enforcement

1. Create a new Incident.
2. Set Impact to High.
3. Leave Assigned To empty.
4. Click Submit.
5. The Incident should not be saved.
6. An error message should be displayed.

Test 2: Successful Save

1. Set Impact to High.
2. Fill the Assigned To field.
3. Click Submit.
4. The Incident should save successfully.
5. Urgency should automatically be set to High.

Test 3: Reverse Condition

1. Open an Incident where Impact is High.
2. Change Impact to Medium.
3. Assigned To should no longer be mandatory.
4. Urgency should become editable.

Test 4: List Edit Blocking

1. Open the Incident list.
2. Try to edit the State directly from the list.
3. An alert message should appear.
4. The State change should be blocked.

Test 5: Form-Based Update

1. Open the Incident form.
2. Change the State.
3. Click Update.
4. The State change should be saved successfully.

---

Conclusion

This micro project demonstrates how ServiceNow UI Policies and Client Scripts can work together to improve Incident data quality and user experience.

The implementation uses UI Policies together with onChange, onSubmit, and onCellEdit Client Scripts to control field behavior, automatically populate values, validate records, and prevent unwanted list edits.

---

Repository Structure

Implement-Client-Script-UI-Policy-Incident-/
│
├── README.md
│
├── Client-Scripts/
│   ├── Auto-Set-Urgency-onChange.js
│   ├── Prevent-Save-if-Assigned-To-Missing-onSubmit.js
│   └── Prevent-State-Change-onCellEdit.js
│
├── UI-Policy/
│   ├── High-Impact-Control.md
│   └── Urgency-UI-Policy-Action.md
│
└── Screenshots/
