# Username Availability — Test Cases
Feature: register
Scope: UI+API
Total: 6 cases (Critical: 0, High: 2, Medium: 2, Low: 2)

---
ID: TC-REGISTER-USERNAME-001
Title: Username already taken shows inline "not available" message
Type: UI
Feature: register
Flow: username-availability
Priority: High
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment); username "test" already exists on the instance
Test Data: userName = "test" (known pre-existing username, fixed fixture — do not substitute)
Steps:
  1. Navigate to the register page
  2. Enter "test" into the User Name field
  3. Move focus away from the User Name field (blur)
Expected Result: An async check fires (GET /api/user/validateUserName/test) and the exact client-side message "User Name is not available" is displayed inline under the User Name field.
Linked Requirement: None

---
ID: TC-REGISTER-USERNAME-002
Title: API — validateUserName returns false for an existing username
Type: API
Feature: register
Flow: username-availability
Priority: Medium
Tags: negative
Preconditions: Username "test" already exists on the instance
Test Data:
  Method: GET
  Endpoint: /api/user/validateUserName/test
  Headers: { }
  Body: null
  Expected Status: 200
Steps:
  1. Send GET /api/user/validateUserName/test
Expected Result: Response status is 200; response body is the boolean "false" (username is not available).
Linked Requirement: None

---
ID: TC-REGISTER-USERNAME-003
Title: API — validateUserName returns true for an available username
Type: API
Feature: register
Flow: username-availability
Priority: Low
Tags: boundary
Preconditions: None
Test Data:
  Method: GET
  Endpoint: /api/user/validateUserName/qa_avail_check_<timestamp>
  Headers: { }
  Body: null
  Expected Status: 200
Steps:
  1. Send GET /api/user/validateUserName/qa_avail_check_<timestamp> with a username value not used elsewhere
Expected Result: Response status is 200; response body is the boolean "true" (username is available).
Linked Requirement: None

---
ID: TC-REGISTER-USERNAME-004
Title: API — validateUserName treats a whitespace-only username as available
Type: API
Feature: register
Flow: username-availability
Priority: Low
Tags: boundary
Preconditions: None
Test Data:
  Method: GET
  Endpoint: /api/user/validateUserName/%20
  Headers: { }
  Body: null
  Expected Status: 200
Steps:
  1. Send GET /api/user/validateUserName/%20 (single whitespace character, URL-encoded)
Expected Result: Response status is 200; response body is the boolean "true" — documents a gap: a whitespace-only value is treated as "available" rather than being rejected as invalid input.
Linked Requirement: None

---
ID: TC-REGISTER-USERNAME-005
Title: API — validateUserName with empty path segment returns an inconsistent response shape
Type: API
Feature: register
Flow: username-availability
Priority: Medium
Tags: negative, boundary
Preconditions: None
Test Data:
  Method: GET
  Endpoint: /api/user/validateUserName/
  Headers: { }
  Body: null
  Expected Status: 200
Steps:
  1. Send GET /api/user/validateUserName/ (no username path segment)
Expected Result: Response status is 200; response body is "0", not a boolean — documents a contract gap: the endpoint's documented response shape is boolean, but an empty path segment returns a numeric 0 instead.
Linked Requirement: None

---
ID: TC-REGISTER-USERNAME-006
Title: API — registering with an already-taken username is not rejected by the server (bug)
Type: API
Feature: register
Flow: username-availability
Priority: High
Tags: security, negative
Preconditions: Username "test" already exists on the instance
Test Data:
  Method: POST
  Endpoint: /api/user/
  Headers: { "Content-Type": "application/json" }
  Body: { "firstName": "QA", "lastName": "Tester", "userName": "test", "password": "Passw0rd1", "confirmPassword": "Passw0rd1", "gender": "Male" }
  Expected Status: 400
Steps:
  1. Send POST /api/user/ directly (bypassing the UI's client-side availability check) with userName "test" and otherwise valid data
Expected Result: Server should reject the duplicate username registration (e.g. 400/409) — this is the intended/correct behavior being asserted. NOTE: this case currently FAILS against the live app, which returns 200 OK and creates/accepts the request despite the duplicate username; server-side uniqueness enforcement is not implemented. This is a known product gap (see explorer-output/register.md GAPS FOUND) — the test documents the bug rather than being skipped.
Linked Requirement: None

---
