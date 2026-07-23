# Legal Links — Test Cases
Feature: footer
Scope: UI
Total: 2 cases (Critical: 0, High: 0, Medium: 2, Low: 0)

---
ID: TC-FOOTER-LEGAL-001
Title: Verify "Privacy Policy" footer link has a valid href
Type: UI
Feature: footer
Flow: legal-links
Priority: Medium
Tags: UI
Preconditions: Homepage is loaded
Test Data: Link label = "Privacy Policy"
Steps:
  1. Scroll to the footer legal links section
  2. Locate the "Privacy Policy" link
  3. Read its href attribute (and target/rel attributes, if present)
  4. Click the link and verify the destination page loads successfully (no 404 or other error page)
Expected Result: The "Privacy Policy" link is visible, has a non-empty href pointing to a privacy-policy destination, any target/rel attributes present are well-formed, and clicking it successfully loads the destination page with no 404 or other error.
Linked Requirement: None

---
ID: TC-FOOTER-LEGAL-002
Title: Verify "Terms & Conditions" footer link has a valid href
Type: UI
Feature: footer
Flow: legal-links
Priority: Medium
Tags: UI
Preconditions: Homepage is loaded
Test Data: Link label = "Terms & Conditions"
Steps:
  1. Scroll to the footer legal links section
  2. Locate the "Terms & Conditions" link
  3. Read its href attribute (and target/rel attributes, if present)
  4. Click the link and verify the destination page loads successfully (no 404 or other error page)
Expected Result: The "Terms & Conditions" link is visible, has a non-empty href pointing to a terms-and-conditions destination, any target/rel attributes present are well-formed, and clicking it successfully loads the destination page with no 404 or other error.
Linked Requirement: None
