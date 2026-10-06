# Confirm Password Mismatch — Test Cases
Feature: register
Scope: UI
Total: 1 cases (Critical: 0, High: 1, Medium: 0, Low: 0)

---
ID: TC-REGISTER-CONFIRM-001
Title: Confirm Password not matching Password is rejected
Type: UI
Feature: register
Flow: confirm-password-mismatch
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_confirm_mismatch_<timestamp>", password = "Passw0rd1", confirmPassword = "Different1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name with valid data
  3. Enter "Passw0rd1" into the Password field
  4. Enter "Different1" into the Confirm Password field
  5. Select a gender
  6. Click the Register/Submit button
Expected Result: Form is not submitted; the exact client-side message "Password do not match" is displayed under the Confirm Password field (verbatim, including the grammatical error — assert this exact string); no POST /api/user/ request fires.
Linked Requirement: None

---
