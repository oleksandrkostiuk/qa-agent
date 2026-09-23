# Failed Login — Invalid Username — Test Cases
Feature: login
Scope: UI
Total: 2 cases (Critical: 0, High: 1, Medium: 1, Low: 0)

---
ID: TC-LOGIN-INVALIDUSER-001
Title: Login fails with an unregistered username
Type: UI
Feature: login
Flow: invalid-username
Priority: High
Tags: negative
Preconditions: User is not logged in
Test Data: username = invalidUser123, password = SuperSecretPassword!
Steps:
  1. Navigate to /login
  2. Enter "invalidUser123" in the Username field
  3. Enter "SuperSecretPassword!" in the Password field
  4. Click the "Login" button
Expected Result: Login is rejected, the page remains on /login, and an error flash message "Your username is invalid!" is displayed. No session cookie is set.
Linked Requirement: None

---
ID: TC-LOGIN-INVALIDUSER-002
Title: Username is validated before password when both are invalid
Type: UI
Feature: login
Flow: invalid-username
Priority: Medium
Tags: negative
Preconditions: User is not logged in
Test Data: username = wronguser, password = wrongpass
Steps:
  1. Navigate to /login
  2. Enter "wronguser" in the Username field
  3. Enter "wrongpass" in the Password field
  4. Click the "Login" button
Expected Result: The error flash message shown is "Your username is invalid!" (not a password error), confirming the username is validated before the password server-side.
Linked Requirement: None
