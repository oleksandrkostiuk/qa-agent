# Boundary / Security Input Handling — Test Cases
Feature: login
Scope: UI
Total: 5 cases (Critical: 0, High: 0, Medium: 0, Low: 5)

---
ID: TC-LOGIN-BOUNDARY-001
Title: Long string input in username field does not crash or bypass login
Type: UI
Feature: login
Flow: boundary-security
Priority: Low
Tags: boundary, security, negative
Preconditions: User is not logged in
Test Data: username = 500-character string of the letter "a", password = SuperSecretPassword!
Steps:
  1. Navigate to /login
  2. Enter a 500-character string of "a" in the Username field
  3. Enter "SuperSecretPassword!" in the Password field
  4. Click the "Login" button
Expected Result: The application does not crash or return a 500 error; login is rejected with the standard "Your username is invalid!" error, and the login page remains fully functional.
Linked Requirement: None

---
ID: TC-LOGIN-BOUNDARY-002
Title: XSS-style payload in username field is not executed or reflected
Type: UI
Feature: login
Flow: boundary-security
Priority: Low
Tags: security, negative, boundary
Preconditions: User is not logged in
Test Data: username = <script>alert(1)</script>, password = SuperSecretPassword!
Steps:
  1. Navigate to /login
  2. Enter "<script>alert(1)</script>" in the Username field
  3. Enter "SuperSecretPassword!" in the Password field
  4. Click the "Login" button
Expected Result: No JavaScript alert/dialog fires, the payload is not reflected as executable markup anywhere in the resulting page's DOM, and login is rejected with the standard "Your username is invalid!" error.
Linked Requirement: None

---
ID: TC-LOGIN-BOUNDARY-003
Title: SQL-injection-style payload does not bypass authentication
Type: UI
Feature: login
Flow: boundary-security
Priority: Low
Tags: security, negative, boundary
Preconditions: User is not logged in
Test Data: username = ' OR '1'='1, password = ' OR '1'='1
Steps:
  1. Navigate to /login
  2. Enter "' OR '1'='1" in the Username field
  3. Enter "' OR '1'='1" in the Password field
  4. Click the "Login" button
Expected Result: Login is rejected with the standard "Your username is invalid!" error (no authentication bypass), and no server error (500) or unhandled exception occurs.
Linked Requirement: None

---
ID: TC-LOGIN-BOUNDARY-004
Title: Whitespace-only username and password are treated as invalid, not empty
Type: UI
Feature: login
Flow: boundary-security
Priority: Low
Tags: boundary, negative
Preconditions: User is not logged in
Test Data: username = "   " (3 spaces), password = "   " (3 spaces)
Steps:
  1. Navigate to /login
  2. Enter three space characters in the Username field
  3. Enter three space characters in the Password field
  4. Click the "Login" button
Expected Result: Login is rejected with error flash message "Your username is invalid!" — whitespace is not trimmed to an empty value that would trigger different handling, and no crash occurs.
Linked Requirement: None

---
ID: TC-LOGIN-BOUNDARY-005
Title: Unicode characters in username field are accepted without crashing
Type: UI
Feature: login
Flow: boundary-security
Priority: Low
Tags: boundary, negative
Preconditions: User is not logged in
Test Data: username = тестユーザー日本語, password = SuperSecretPassword!
Steps:
  1. Navigate to /login
  2. Enter "тестユーザー日本語" in the Username field
  3. Enter "SuperSecretPassword!" in the Password field
  4. Click the "Login" button
Expected Result: The application accepts the unicode input without crashing or rendering errors; login is rejected with the standard "Your username is invalid!" error.
Linked Requirement: None
