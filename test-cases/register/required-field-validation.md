# Required-Field Validation — Test Cases
Feature: register
Scope: UI
Total: 6 cases (Critical: 0, High: 6, Medium: 0, Low: 0)

---
ID: TC-REGISTER-REQUIRED-001
Title: Submitting with First Name empty is rejected
Type: UI
Feature: register
Flow: required-field-validation
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "" (empty), lastName = "Tester", userName = "qa_required_001", password = "Passw0rd1", confirmPassword = "Passw0rd1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Leave the First Name field empty
  3. Fill all other fields with valid data and select a gender
  4. Click the Register/Submit button
Expected Result: Form is not submitted; the exact client-side message "First Name is required" is displayed under the First Name field; no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-REQUIRED-002
Title: Submitting with Last Name empty is rejected
Type: UI
Feature: register
Flow: required-field-validation
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "" (empty), userName = "qa_required_002", password = "Passw0rd1", confirmPassword = "Passw0rd1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Leave the Last Name field empty
  3. Fill all other fields with valid data and select a gender
  4. Click the Register/Submit button
Expected Result: Form is not submitted; the exact client-side message "Last Name is required" is displayed under the Last Name field; no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-REQUIRED-003
Title: Submitting with User Name empty is rejected
Type: UI
Feature: register
Flow: required-field-validation
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "" (empty), password = "Passw0rd1", confirmPassword = "Passw0rd1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Leave the User Name field empty
  3. Fill all other fields with valid data and select a gender
  4. Click the Register/Submit button
Expected Result: Form is not submitted; the exact client-side message "User Name is required" is displayed under the User Name field; no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-REQUIRED-004
Title: Submitting with Password empty is rejected
Type: UI
Feature: register
Flow: required-field-validation
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_required_004", password = "" (empty), confirmPassword = "Passw0rd1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Leave the Password field empty
  3. Fill all other fields with valid data and select a gender
  4. Click the Register/Submit button
Expected Result: Form is not submitted; the exact client-side message "Password is required" is displayed under the Password field; no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-REQUIRED-005
Title: Submitting with Confirm Password empty is rejected
Type: UI
Feature: register
Flow: required-field-validation
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_required_005", password = "Passw0rd1", confirmPassword = "" (empty), gender = "Male"
Steps:
  1. Navigate to the register page
  2. Leave the Confirm Password field empty
  3. Fill all other fields with valid data and select a gender
  4. Click the Register/Submit button
Expected Result: Form is not submitted; the exact client-side message "Password is required" is displayed under the Confirm Password field (verbatim — the app reuses the same message text for both Password and Confirm Password); no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-REQUIRED-006
Title: Submitting with all required fields empty is rejected
Type: UI
Feature: register
Flow: required-field-validation
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "" (empty), lastName = "" (empty), userName = "" (empty), password = "" (empty), confirmPassword = "" (empty), gender = not selected
Steps:
  1. Navigate to the register page
  2. Leave all fields empty and gender unselected
  3. Click the Register/Submit button
Expected Result: Form is not submitted; all applicable required-field messages are displayed simultaneously — "First Name is required", "Last Name is required", "User Name is required", "Password is required" (shown once under Password and once under Confirm Password); no POST /api/user/ request fires.
Linked Requirement: None

---
