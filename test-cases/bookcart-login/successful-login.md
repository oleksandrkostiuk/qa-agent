# Successful Login — Test Cases
Feature: bookcart-login
Scope: UI
Total: 1 case (Critical: 1, High: 0, Medium: 0, Low: 0)

---
ID: TC-BOOKCARTLOGIN-SUCCESS-001
Title: Successful login with valid username and password
Type: UI
Feature: bookcart-login
Flow: successful-login
Priority: Critical
Tags: smoke, regression
Preconditions: User is not logged in; a valid bookcart account exists. No working credential is currently available for this environment (PROJECT_CONFIG.json → credentials.book is empty, and the only candidate seed credential does not authenticate — see explorer-output/login.md OPEN RISKS #1). This case requires a human to supply a valid username/password before it can execute past "blocked".
Test Data: username = <human-supplied valid bookcart username>, password = <human-supplied valid bookcart password>
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Enter the valid username in the Username field
  3. Enter the valid password in the Password field
  4. Click the "Login" button
Expected Result: User is redirected away from /login (e.g. to the home/products page), a session is established, and authenticated-only UI becomes visible (e.g. account/profile controls in the header).
Linked Requirement: None
