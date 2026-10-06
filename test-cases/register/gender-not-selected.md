# Gender Not Selected — Test Cases
Feature: register
Scope: UI+API
Total: 2 cases (Critical: 0, High: 0, Medium: 2, Low: 0)

---
ID: TC-REGISTER-GENDER-001
Title: Submitting with no gender selected silently blocks the form
Type: UI
Feature: register
Flow: gender-not-selected
Priority: Medium
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_gender_none_<timestamp>", password = "Passw0rd1", confirmPassword = "Passw0rd1", gender = not selected
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name, Password, and Confirm Password with valid data
  3. Do not select either gender radio button
  4. Click the Register/Submit button
Expected Result: The click is a no-op — no validation error is shown anywhere on the page, the submit button remains enabled, no POST /api/user/ network request fires, and the page remains on /register.
Linked Requirement: None

---
ID: TC-REGISTER-GENDER-002
Title: API — registering with an invalid gender enum value is rejected
Type: API
Feature: register
Flow: gender-not-selected
Priority: Medium
Tags: negative, security
Preconditions: None
Test Data:
  Method: POST
  Endpoint: /api/user/
  Headers: { "Content-Type": "application/json" }
  Body: { "firstName": "QA", "lastName": "Tester", "userName": "qa_gender_invalid_<timestamp>", "password": "Passw0rd1", "confirmPassword": "Passw0rd1", "gender": "Other" }
  Expected Status: 400
Steps:
  1. Send POST /api/user/ directly with gender set to "Other" (a value not exposed by the UI's two radio options) and otherwise valid data
Expected Result: Response status is 400 Bad Request — the server enforces the gender enum (Male/Female) even though this value can't be produced through the UI.
Linked Requirement: None

---
