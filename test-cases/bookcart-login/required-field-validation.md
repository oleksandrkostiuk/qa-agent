# Required-Field Validation — Test Cases
Feature: bookcart-login
Scope: UI
Total: 3 cases (Critical: 0, High: 0, Medium: 3, Low: 0)

---
ID: TC-BOOKCARTLOGIN-REQUIREDFIELDS-001
Title: Submitting the login form with an empty username shows a required-field message
Type: UI
Feature: bookcart-login
Flow: required-field-validation
Priority: Medium
Tags: negative
Preconditions: User is not logged in
Test Data: username = (empty), password = SomePassword123
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Leave the Username field empty; click into it and then blur it (tab away) without typing
  3. Enter "SomePassword123" in the Password field
  4. Click the "Login" button
Expected Result: An inline validation message "Username is required" appears under the Username field. No POST /api/login network call is made — the block is entirely client-side and the Login button click is a no-op. The user remains on /login.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-REQUIREDFIELDS-002
Title: Submitting the login form with an empty password shows a required-field message
Type: UI
Feature: bookcart-login
Flow: required-field-validation
Priority: Medium
Tags: negative
Preconditions: User is not logged in
Test Data: username = someuser, password = (empty)
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Enter "someuser" in the Username field
  3. Leave the Password field empty; click into it and then blur it (tab away) without typing
  4. Click the "Login" button
Expected Result: An inline validation message "Password is required" appears under the Password field. No POST /api/login network call is made — the block is entirely client-side and the Login button click is a no-op. The user remains on /login.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-REQUIREDFIELDS-003
Title: Submitting the login form with both fields empty shows both required-field messages
Type: UI
Feature: bookcart-login
Flow: required-field-validation
Priority: Medium
Tags: negative
Preconditions: User is not logged in
Test Data: username = (empty), password = (empty)
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Leave both the Username and Password fields empty; click into and blur each one in turn
  3. Click the "Login" button
Expected Result: Both "Username is required" and "Password is required" inline validation messages appear. No POST /api/login network call is made. The user remains on /login.
Linked Requirement: None
