# Login After Registration — Test Cases
Feature: register
Scope: UI+API
Total: 3 cases (Critical: 0, High: 2, Medium: 1, Low: 0)

---
ID: TC-REGISTER-POSTLOGIN-001
Title: Logging in immediately after registration succeeds with the same credentials
Type: UI
Feature: register
Flow: login-after-registration
Priority: High
Tags: regression
Preconditions: A new account was just registered successfully (e.g. via TC-REGISTER-MALE-001) and the app has redirected to /login; the registered userName/password are known
Test Data: userName = "<the username used in the preceding successful registration>", password = "Passw0rd1"
Steps:
  1. On the /login page, enter the just-registered userName
  2. Enter the matching password
  3. Click the Login/Submit button
Expected Result: Login succeeds and the user reaches an authenticated/logged-in state (the newly created account can actually authenticate — this is not just a UI redirect assumption).
Linked Requirement: None

---
ID: TC-REGISTER-POSTLOGIN-002
Title: API — login with freshly-registered credentials returns a token
Type: API
Feature: register
Flow: login-after-registration
Priority: High
Tags: regression
Preconditions: A new account was just registered via POST /api/user/ (e.g. the userName/password from TC-REGISTER-MALE-001)
Test Data:
  Method: POST
  Endpoint: /api/login/
  Headers: { "Content-Type": "application/json" }
  Body: { "userName": "<the username used in the preceding successful registration>", "password": "Passw0rd1" }
  Expected Status: 200
Steps:
  1. Send POST /api/login/ with the freshly-registered userName and correct password
Expected Result: Response status is 200; response body contains a "token" field and a "userDetails" object with "userId" and "username" matching the registered account.
Linked Requirement: None

---
ID: TC-REGISTER-POSTLOGIN-003
Title: API — login with correct username but wrong password is rejected
Type: API
Feature: register
Flow: login-after-registration
Priority: Medium
Tags: negative
Preconditions: A new account was just registered via POST /api/user/ (e.g. the userName from TC-REGISTER-MALE-001)
Test Data:
  Method: POST
  Endpoint: /api/login/
  Headers: { "Content-Type": "application/json" }
  Body: { "userName": "<the username used in the preceding successful registration>", "password": "WrongPassword1" }
  Expected Status: 401
Steps:
  1. Send POST /api/login/ with the freshly-registered userName and an incorrect password
Expected Result: Response status is 401; response body is empty.
Linked Requirement: None

---
