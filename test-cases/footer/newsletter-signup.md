# Newsletter Signup — Test Cases
Feature: footer
Scope: UI
Total: 3 cases (Critical: 0, High: 0, Medium: 2, Low: 1)

---
ID: TC-FOOTER-NEWSLETTER-001
Title: Submit newsletter signup form with empty email field
Type: UI
Feature: footer
Flow: newsletter-signup
Priority: Medium
Tags: negative, boundary, UI
Preconditions: Homepage (https://dev.skyline.glass/) is loaded; footer newsletter signup section is visible
Test Data: email = "" (field left empty)
Steps:
  1. Scroll to the footer newsletter signup section
  2. Leave the email input field empty
  3. Click the newsletter Submit button
Expected Result: Form does not submit successfully. A top banner displays "There was a problem with your submission. Please review the fields below." An inline error "This field is required." appears under the email field, and the field's aria-invalid attribute is set to "true".
Linked Requirement: None

---
ID: TC-FOOTER-NEWSLETTER-002
Title: Submit newsletter signup form with malformed email (missing @ symbol)
Type: UI
Feature: footer
Flow: newsletter-signup
Priority: Medium
Tags: negative, boundary, UI
Preconditions: Homepage is loaded; footer newsletter signup section is visible
Test Data: email = "notanemail"
Steps:
  1. Scroll to the footer newsletter signup section
  2. Enter "notanemail" into the email field
  3. Click the newsletter Submit button
Expected Result: Form does not submit successfully. Inline error "The email address entered is invalid, please check the formatting (e.g. email@domain.com)." appears under the email field, and the field's aria-invalid attribute is set to "true".
Linked Requirement: None

---
ID: TC-FOOTER-NEWSLETTER-003
Title: Submit newsletter signup form with malformed email (missing domain)
Type: UI
Feature: footer
Flow: newsletter-signup
Priority: Low
Tags: negative, boundary, UI
Preconditions: Homepage is loaded; footer newsletter signup section is visible
Test Data: email = "test@domain"
Steps:
  1. Scroll to the footer newsletter signup section
  2. Enter "test@domain" into the email field
  3. Click the newsletter Submit button
Expected Result: Form does not submit successfully. Inline error "The email address entered is invalid, please check the formatting (e.g. email@domain.com)." appears under the email field, and the field's aria-invalid attribute is set to "true".
Linked Requirement: None

---
Note: Happy-path (valid email accepted) is intentionally excluded from this suite per the OPEN RISK decision recorded in explorer-output/footer.md — no disposable test-email convention exists for this shared dev environment, so a real submission would create live records in Gravity Forms/HubSpot/GA.
