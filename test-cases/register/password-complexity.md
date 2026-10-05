# Password Complexity Validation — Test Cases
Feature: register
Scope: UI
Total: 5 cases (Critical: 0, High: 1, Medium: 4, Low: 0)

---
ID: TC-REGISTER-PASSWORD-001
Title: Password exactly 8 characters meeting all complexity rules is accepted
Type: UI
Feature: register
Flow: password-complexity
Priority: Medium
Tags: boundary
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_pwd_boundary_ok_<timestamp>", password = "Passw0rd" (8 chars: 1 upper, 1 lower, 1 digit), confirmPassword = "Passw0rd", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name with valid data
  3. Enter "Passw0rd" into the Password field
  4. Enter "Passw0rd" into the Confirm Password field
  5. Select a gender
  6. Click the Register/Submit button
Expected Result: No password-complexity validation error is shown; combined with otherwise-valid fields, the form submits successfully and the app redirects to /login (same success behavior as the happy-path case).
Linked Requirement: None

---
ID: TC-REGISTER-PASSWORD-002
Title: Password one character under the minimum length (7 chars) is rejected
Type: UI
Feature: register
Flow: password-complexity
Priority: High
Tags: negative, boundary
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_pwd_boundary_bad_<timestamp>", password = "Passw0r" (7 chars, otherwise meets pattern), confirmPassword = "Passw0r", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name with valid data
  3. Enter "Passw0r" into the Password field
  4. Enter "Passw0r" into the Confirm Password field
  5. Select a gender
  6. Click the Register/Submit button
Expected Result: Form is not submitted; the Password field shows a validation error indicating the password does not meet complexity requirements (min 8 chars, 1 uppercase, 1 lowercase, 1 digit — exact message text not confirmed during exploration, verify wording on first execution); no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-PASSWORD-003
Title: Password missing an uppercase letter is rejected
Type: UI
Feature: register
Flow: password-complexity
Priority: Medium
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_pwd_noupper_<timestamp>", password = "passw0rd1" (no uppercase), confirmPassword = "passw0rd1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name with valid data
  3. Enter "passw0rd1" into the Password field
  4. Enter "passw0rd1" into the Confirm Password field
  5. Select a gender
  6. Click the Register/Submit button
Expected Result: Form is not submitted; the Password field shows a complexity validation error (exact message text not confirmed during exploration, verify wording on first execution); no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-PASSWORD-004
Title: Password missing a lowercase letter is rejected
Type: UI
Feature: register
Flow: password-complexity
Priority: Medium
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_pwd_nolower_<timestamp>", password = "PASSW0RD1" (no lowercase), confirmPassword = "PASSW0RD1", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name with valid data
  3. Enter "PASSW0RD1" into the Password field
  4. Enter "PASSW0RD1" into the Confirm Password field
  5. Select a gender
  6. Click the Register/Submit button
Expected Result: Form is not submitted; the Password field shows a complexity validation error (exact message text not confirmed during exploration, verify wording on first execution); no POST /api/user/ request fires.
Linked Requirement: None

---
ID: TC-REGISTER-PASSWORD-005
Title: Password missing a digit is rejected
Type: UI
Feature: register
Flow: password-complexity
Priority: Medium
Tags: negative
Preconditions: Anonymous user on the register page (bookcart environment)
Test Data: firstName = "QA", lastName = "Tester", userName = "qa_pwd_nodigit_<timestamp>", password = "Password" (no digit), confirmPassword = "Password", gender = "Male"
Steps:
  1. Navigate to the register page
  2. Fill First Name, Last Name, User Name with valid data
  3. Enter "Password" into the Password field
  4. Enter "Password" into the Confirm Password field
  5. Select a gender
  6. Click the Register/Submit button
Expected Result: Form is not submitted; the Password field shows a complexity validation error (exact message text not confirmed during exploration, verify wording on first execution); no POST /api/user/ request fires.
Linked Requirement: None

---
