# Happy Path (Female) — Test Cases
Feature: register
Scope: UI
Total: 1 cases (Critical: 0, High: 0, Medium: 1, Low: 0)

---
ID: TC-REGISTER-FEMALE-001
Title: Register new account with valid data and Female gender succeeds
Type: UI
Feature: register
Flow: happy-path-female
Priority: Medium
Tags: regression
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_register_f_<timestamp>" (dynamic — generate a unique value per run, e.g. "qa_register_f_20261005143000"), password = "Passw0rd1", confirmPassword = "Passw0rd1", gender = "Female"
Steps:
  1. Navigate to the register page
  2. Enter "QA" into the First Name field
  3. Enter "Tester" into the Last Name field
  4. Enter the generated unique username into the User Name field
  5. Enter "Passw0rd1" into the Password field
  6. Enter "Passw0rd1" into the Confirm Password field
  7. Select the "Female" gender radio button
  8. Click the Register/Submit button
Expected Result: No validation errors are shown on any field; the app redirects to /login (there is no on-page success/confirmation message — the redirect itself is the success signal).
Linked Requirement: None

---
