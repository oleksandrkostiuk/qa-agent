# Logout — Test Cases
Feature: login
Scope: UI
Total: 2 cases (Critical: 0, High: 1, Medium: 1, Low: 0)

---
ID: TC-LOGIN-LOGOUT-001
Title: Logout from the secure area ends the session
Type: UI
Feature: login
Flow: logout
Priority: High
Tags: smoke, regression
Preconditions: User is logged in (see TC-LOGIN-SUCCESS-001)
Test Data: None
Steps:
  1. From the https://the-internet.herokuapp.com/secure page, click the "Logout" button
Expected Result: User is redirected to https://the-internet.herokuapp.com/login, a flash message "You logged out of the secure area!" is displayed, and the session is ended.
Linked Requirement: None

---
ID: TC-LOGIN-LOGOUT-002
Title: https://the-internet.herokuapp.com/secure is inaccessible immediately after logout
Type: UI
Feature: login
Flow: logout
Priority: Medium
Tags: negative, security
Preconditions: User has just logged out (see TC-LOGIN-LOGOUT-001)
Test Data: None
Steps:
  1. Immediately after logout, navigate directly to https://the-internet.herokuapp.com/secure via the URL bar
Expected Result: User is redirected to https://the-internet.herokuapp.com/login with flash message "You must login to view the secure area!"; the previously authenticated session is not reusable.
Linked Requirement: None
