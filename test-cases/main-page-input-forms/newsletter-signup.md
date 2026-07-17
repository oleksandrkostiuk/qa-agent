# Newsletter Signup — Test Cases
Feature: main-page-input-forms
Scope: UI
Total: 10 cases (Critical: 1, High: 3, Medium: 4, Low: 2)

---
ID: TC-MAINPAGE-NEWSLETTER-001
Title: Subscribe with a valid test-domain email succeeds
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Critical
Tags: smoke, regression
Preconditions: Anonymous user on the main page (dev environment); footer visible
Test Data: email = "qa-test-001@example.com"
Steps:
  1. Scroll to the footer newsletter signup form (Gravity Forms #5)
  2. Enter "qa-test-001@example.com" into the email field
  3. Submit the form
Expected Result: Form submits successfully and a confirmation/success message is displayed to the user; no error is shown.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-002
Title: Submitting the newsletter form with an empty email is rejected
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: High
Tags: negative, boundary
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "" (empty)
Steps:
  1. Scroll to the footer newsletter signup form
  2. Leave the email field empty
  3. Submit the form
Expected Result: Form is not submitted; a validation error indicating the email field is required is displayed.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-003
Title: Submitting an email missing the "@" symbol is rejected
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: High
Tags: negative, boundary
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "qatestexample.com"
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qatestexample.com" into the email field
  3. Submit the form
Expected Result: Form is not submitted; a validation error indicating an invalid email format is displayed.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-004
Title: Submitting an email missing the domain part is rejected
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Medium
Tags: negative, boundary
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "qatest@"
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qatest@" into the email field
  3. Submit the form
Expected Result: Form is not submitted; a validation error indicating an invalid email format is displayed.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-005
Title: Submitting an email containing spaces is rejected
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Medium
Tags: negative, boundary
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "qa test@example.com"
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qa test@example.com" into the email field
  3. Submit the form
Expected Result: Form is not submitted; a validation error indicating an invalid email format is displayed.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-006
Title: Submitting an email with a trailing dot is handled correctly
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Low
Tags: negative, boundary
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "qa-test-006@example.com."
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qa-test-006@example.com." (note trailing dot) into the email field
  3. Submit the form
Expected Result: Form either rejects the value with a validation error, or normalizes/accepts it consistently — behavior must not silently fail or throw an unhandled error. Record actual behavior observed.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-007
Title: Submitting a very long email string is handled without error
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Low
Tags: boundary
Preconditions: Anonymous user on the main page; footer visible; field has no visible maxLength attribute
Test Data: email = 300-character local part + "@example.com" (e.g. "a" x 300 + "@example.com")
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter a 300+ character email string into the email field
  3. Submit the form
Expected Result: Form either accepts and submits successfully or rejects with a clear validation error; no page crash, no unhandled JS error, no server 500.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-008
Title: Submitting an email with special/unicode characters is handled correctly
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Medium
Tags: negative, boundary
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "qa-tëst+special_008@example.com"
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qa-tëst+special_008@example.com" into the email field
  3. Submit the form
Expected Result: Form either accepts the value as valid or rejects it with a clear validation error; behavior must be consistent and not throw an unhandled error.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-009
Title: Rapid repeated submissions of the newsletter form do not create duplicate/erroneous requests
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: Medium
Tags: negative
Preconditions: Anonymous user on the main page; footer visible
Test Data: email = "qa-test-009@example.com"
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qa-test-009@example.com" into the email field
  3. Click submit multiple times in rapid succession (e.g. 5 clicks within 1 second)
Expected Result: Only one submission is processed (button disables/debounces after first click, or duplicate clicks are ignored); no duplicate confirmation messages and no client-side error.
Linked Requirement: None

---
ID: TC-MAINPAGE-NEWSLETTER-010
Title: Legitimate submission is not blocked by invisible reCAPTCHA v3
Type: UI
Feature: main-page-input-forms
Flow: newsletter-signup
Priority: High
Tags: security
Preconditions: Anonymous user on the main page; footer visible. NOTE (OPEN RISK, user-confirmed): this form is protected by invisible reCAPTCHA v3 and posts to a live Gravity Forms backend — automated submissions may receive a low bot score and be silently blocked. A resulting failure here is a known execution risk, not a confirmed functional defect, and should not automatically be filed as a bug.
Test Data: email = "qa-test-010@example.com"
Steps:
  1. Scroll to the footer newsletter signup form
  2. Enter "qa-test-010@example.com" into the email field
  3. Submit the form
  4. Observe network tab / response for any reCAPTCHA-related rejection
Expected Result: Form submits successfully with no reCAPTCHA-related block. If blocked, record as a known execution risk per OPEN RISKS before escalating as a bug.
Linked Requirement: None
