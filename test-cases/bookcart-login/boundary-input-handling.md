# Boundary Input Handling — Test Cases
Feature: bookcart-login
Scope: UI+API
Total: 6 cases (Critical: 0, High: 0, Medium: 0, Low: 6)

---
ID: TC-BOOKCARTLOGIN-BOUNDARY-001
Title: Login form accepts a very long (2000-character) username without client-side truncation or error
Type: UI
Feature: bookcart-login
Flow: boundary-input-handling
Priority: Low
Tags: boundary
Preconditions: User is not logged in. No maxLength, pattern, or native required HTML attributes exist on the username/password inputs (Angular reactive-form validation only, confirmed via DOM query).
Test Data: username = "a" repeated 2000 times, password = SomePassword123
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Enter a 2000-character string into the Username field
  3. Enter "SomePassword123" in the Password field
  4. Click the "Login" button
Expected Result: No client-side length validation blocks submission or truncates the input. A POST /api/login request is sent. The server responds 401 (treated as invalid credentials, not a request error). No visible error message appears on the page; the user remains on /login.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-BOUNDARY-002
Title: Login form accepts a whitespace-only username without client-side validation
Type: UI
Feature: bookcart-login
Flow: boundary-input-handling
Priority: Low
Tags: boundary
Preconditions: User is not logged in
Test Data: username = "   " (3 spaces), password = SomePassword123
Steps:
  1. Navigate to https://bookcart.azurewebsites.net/login
  2. Enter "   " (three spaces, no other characters) into the Username field
  3. Enter "SomePassword123" in the Password field
  4. Click the "Login" button
Expected Result: Whitespace-only input is not treated as "empty" by the form's required validator, so no client-side "Username is required" message appears. A POST /api/login request is sent. The server responds 401. The user remains on /login with no visible feedback.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-BOUNDARY-003
Title: POST /api/login with an empty JSON body returns 401, not 400
Type: API
Feature: bookcart-login
Flow: boundary-input-handling
Priority: Low
Tags: boundary
Preconditions: None
Test Data:
  Method: POST
  Endpoint: /api/login
  Headers: { "Content-Type": "application/json" }
  Body: {}
  Expected Status: 401
Steps:
  1. Send the request described in Test Data to the resolved environment's base URL
Expected Result: Response status is 401 (the API does not distinguish a malformed/empty request from wrong credentials; it never returns 400 for this input). Response body is empty.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-BOUNDARY-004
Title: POST /api/login with empty string username and password returns 401
Type: API
Feature: bookcart-login
Flow: boundary-input-handling
Priority: Low
Tags: boundary
Preconditions: None
Test Data:
  Method: POST
  Endpoint: /api/login
  Headers: { "Content-Type": "application/json" }
  Body: { "username": "", "password": "" }
  Expected Status: 401
Steps:
  1. Send the request described in Test Data to the resolved environment's base URL
Expected Result: Response status is 401. Response body is empty.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-BOUNDARY-005
Title: POST /api/login with a 2000-character username returns 401, not a request-size error
Type: API
Feature: bookcart-login
Flow: boundary-input-handling
Priority: Low
Tags: boundary
Preconditions: None
Test Data:
  Method: POST
  Endpoint: /api/login
  Headers: { "Content-Type": "application/json" }
  Body: { "username": "<2000-character string of 'a'>", "password": "SomePassword123" }
  Expected Status: 401
Steps:
  1. Send the request described in Test Data to the resolved environment's base URL
Expected Result: Response status is 401. The API accepts the oversized field rather than rejecting it with a 400/413-class error. Response body is empty.
Linked Requirement: None

---
ID: TC-BOOKCARTLOGIN-BOUNDARY-006
Title: POST /api/login with a whitespace-only username returns 401
Type: API
Feature: bookcart-login
Flow: boundary-input-handling
Priority: Low
Tags: boundary
Preconditions: None
Test Data:
  Method: POST
  Endpoint: /api/login
  Headers: { "Content-Type": "application/json" }
  Body: { "username": "   ", "password": "SomePassword123" }
  Expected Status: 401
Steps:
  1. Send the request described in Test Data to the resolved environment's base URL
Expected Result: Response status is 401. Response body is empty.
Linked Requirement: None
