# Failed Login — Invalid Password — Test Cases
Feature: login
Scope: UI
Total: 1 case (Critical: 0, High: 1, Medium: 0, Low: 0)

---
ID: TC-LOGIN-INVALIDPASS-001
Title: Login fails with a valid username and wrong password
Type: UI
Feature: login
Flow: invalid-password
Priority: High
Tags: negative
Preconditions: User is not logged in
Test Data: username = tomsmith, password = WrongPassword1
Steps:
  1. Navigate to /login
  2. Enter "tomsmith" in the Username field
  3. Enter "WrongPassword1" in the Password field
  4. Click the "Login" button
Expected Result: Login is rejected, the page remains on /login, and an error flash message "Your password is invalid!" is displayed. No session cookie is set.
Linked Requirement: None
