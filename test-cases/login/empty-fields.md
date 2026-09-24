# Failed Login — Empty Fields — Test Cases
Feature: login
Scope: UI
Total: 3 cases (Critical: 0, High: 0, Medium: 3, Low: 0)

---
ID: TC-LOGIN-EMPTY-001
Title: Login fails with empty username and valid password
Type: UI
Feature: login
Flow: empty-fields
Priority: Medium
Tags: negative, boundary
Preconditions: User is not logged in
Test Data: username = "" (empty), password = SuperSecretPassword!
Steps:
  1. Navigate to https://the-internet.herokuapp.com/login
  2. Leave the Username field empty
  3. Enter "SuperSecretPassword!" in the Password field
  4. Click the "Login" button
Expected Result: Login is rejected with error flash message "Your username is invalid!" (empty username is treated as an invalid username, not a distinct required-field error — no client-side `required` validation exists on this field).
Linked Requirement: None

---
ID: TC-LOGIN-EMPTY-002
Title: Login fails with valid username and empty password
Type: UI
Feature: login
Flow: empty-fields
Priority: Medium
Tags: negative, boundary
Preconditions: User is not logged in
Test Data: username = tomsmith, password = "" (empty)
Steps:
  1. Navigate to https://the-internet.herokuapp.com/login
  2. Enter "tomsmith" in the Username field
  3. Leave the Password field empty
  4. Click the "Login" button
Expected Result: Login is rejected with error flash message "Your password is invalid!".
Linked Requirement: None

---
ID: TC-LOGIN-EMPTY-003
Title: Login fails with both username and password empty
Type: UI
Feature: login
Flow: empty-fields
Priority: Medium
Tags: negative, boundary
Preconditions: User is not logged in
Test Data: username = "" (empty), password = "" (empty)
Steps:
  1. Navigate to https://the-internet.herokuapp.com/login
  2. Leave the Username field empty
  3. Leave the Password field empty
  4. Click the "Login" button
Expected Result: Login is rejected with error flash message "Your username is invalid!" (username is checked before password, so the username error takes precedence even though both fields are empty).
Linked Requirement: None
