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
Expected Result: The "Privacy Policy" link is visible, has a non-empty href pointing to a privacy-policy destination, and any target/rel attributes present are well-formed. (Destination page load is out of scope for this suite — see OPEN RISKS in explorer-output/footer.md.)
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
Expected Result: The "Terms & Conditions" link is visible, has a non-empty href pointing to a terms-and-conditions destination, and any target/rel attributes present are well-formed. (Destination page load is out of scope for this suite.)
Linked Requirement: None
