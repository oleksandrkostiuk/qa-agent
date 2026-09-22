# Last Modified & Contact Info — Test Cases
Feature: terms-conditions
Scope: UI (formatting only)
Total: 2 cases (Critical: 0, High: 0, Medium: 0, Low: 2)

---
ID: TC-TERMS-CONTACT-001
Title: Verify "last modified" date is displayed and formatted consistently
Type: UI
Feature: terms-conditions
Flow: last-modified-contact-info
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page (https://dev.skyline.glass/terms-conditions/) is loaded
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Locate the "last modified" date text
  3. Inspect its date format and surrounding spacing/typography
Expected Result: The "last modified" date is visible, uses a consistent, human-readable date format, and its typography/spacing matches the rest of the page's body text style.
Linked Requirement: None

---
ID: TC-TERMS-CONTACT-002
Title: Verify contact info block renders with correct formatting
Type: UI
Feature: terms-conditions
Flow: last-modified-contact-info
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Scroll to the contact info block (typically at the end of the document)
  3. Inspect line breaks, spacing, and any linked contact details (e.g. email/address) for correct rendering
Expected Result: The contact info block renders with clear line breaks between distinct fields, consistent spacing/typography with the rest of the page, and any linked contact details (e.g. mailto links) are correctly formatted and functional.
Linked Requirement: None
