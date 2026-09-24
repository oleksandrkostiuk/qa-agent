# Successful Login — Test Cases
Feature: login
Scope: UI
Total: 2 cases (Critical: 1, High: 1, Medium: 0, Low: 0)

---
ID: TC-LOGIN-SUCCESS-001
Title: Successful login with valid username and password
Type: UI
Feature: login
Flow: successful-login
Priority: Critical
Tags: smoke, regression
Preconditions: User is not logged in; a valid account exists (username: tomsmith, password: SuperSecretPassword!)
Test Data: username = tomsmith, password = SuperSecretPassword!
Steps:
  1. Navigate to https://the-internet.herokuapp.com/login
  2. Enter "tomsmith" in the Username field
  3. Enter "SuperSecretPassword!" in the Password field
  4. Click the "Login" button
Expected Result: User is redirected to https://the-internet.herokuapp.com/secure, a success flash message "You logged into a secure area!" is displayed, and the Logout button is visible.
Linked Requirement: None

---
ID: TC-LOGIN-SUCCESS-002
Title: Authenticated session persists on direct navigation to https://the-internet.herokuapp.com/secure
Type: UI
Feature: login
Flow: successful-login
Priority: High
Tags: regression
Preconditions: User has successfully logged in (see TC-LOGIN-SUCCESS-001) and the session cookie is still valid
Test Data: None
Steps:
  1. While logged in, navigate away from https://the-internet.herokuapp.com/secure (e.g. to https://the-internet.herokuapp.com/login)
  2. Navigate directly to https://the-internet.herokuapp.com/secure via the URL bar
Expected Result: The https://the-internet.herokuapp.com/secure page loads directly without redirecting to https://the-internet.herokuapp.com/login; the user remains authenticated and the secure area content is shown.
Linked Requirement: None
