# Failed Login — Test Cases
Feature: bookcart-login
Scope: UI+API
Total: 3 cases (Critical: 0, High: 2, Medium: 1, Low: 0)

---
ID: TC-BOOKCARTLOGIN-FAILEDLOGIN-001
Title: Login fails silently with an unknown username and an arbitrary password
Type: UI
Feature: bookcart-login
Flow: failed-login
Priority: High
Tags: negative
Preconditions: User is not logged in
Test Data: username = nonexistentuser12345, password = WrongPassword123!
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Enter "nonexistentuser12345" in the Username field
  3. Enter "WrongPassword123!" in the Password field
  4. Click the "Login" button
Expected Result: Login fails — the user remains on /login and no session is established. No visible error, toast, or inline message appears anywhere on the page (confirmed app behavior: the server responds 401 with an empty body and the UI surfaces zero feedback). Pass criterion is "still on /login, no session cookie", not any visible message.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-FAILEDLOGIN-002
Title: Login fails with a known/existing username and the wrong password
Type: UI
Feature: bookcart-login
Flow: failed-login
Priority: Medium
Tags: negative
Preconditions: User is not logged in; username "adminuser" is confirmed to exist on this instance (per GET /api/user/validateUserName) though its real password is unknown
Test Data: username = adminuser, password = definitely-wrong-password
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Enter "adminuser" in the Username field
  3. Enter "definitely-wrong-password" in the Password field
  4. Click the "Login" button
Expected Result: Login fails — the user remains on /login and no session is established. No visible error, toast, or inline message appears (same silent-401 behavior as an unknown username; the app does not distinguish the two cases to the end user).
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-FAILEDLOGIN-003
Title: POST /api/login with invalid credentials returns 401 with an empty body
Type: API
Feature: bookcart-login
Flow: failed-login
Priority: High
Tags: negative
Preconditions: None
Test Data:
  Method: POST
  Endpoint: /api/login
  Headers: { "Content-Type": "application/json" }
  Body: { "username": "nonexistentuser12345", "password": "WrongPassword123!" }
  Expected Status: 401
Steps:
  1. Send the request described in Test Data to the resolved environment's base URL
Expected Result: Response status is 401. Response body is empty (content-length: 0). No session token/cookie is returned in the response headers.
Linked Requirement: None
