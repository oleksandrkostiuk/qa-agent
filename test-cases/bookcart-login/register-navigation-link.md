# Register Navigation Link — Test Cases
Feature: bookcart-login
Scope: UI
Total: 1 case (Critical: 0, High: 0, Medium: 0, Low: 1)

---
ID: TC-BOOKCARTLOGIN-REGISTERNAV-001
Title: "New User? Register" link navigates to the register page
Type: UI
Feature: bookcart-login
Flow: register-navigation-link
Priority: Low
Tags: UI
Preconditions: Anonymous user on the login page (bookcart environment)
Test Data: None
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Click the "New User? Register" link
Expected Result: The app navigates to the /register page.
Linked Requirement: None
