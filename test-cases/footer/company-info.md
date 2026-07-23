# Company Info — Test Cases
Feature: footer
Scope: UI
Total: 3 cases (Critical: 0, High: 0, Medium: 0, Low: 3)

---
ID: TC-FOOTER-INFO-001
Title: Verify company address displays correctly in footer
Type: UI
Feature: footer
Flow: company-info
Priority: Low
Tags: UI
Preconditions: Homepage is loaded
Test Data: Expected address text = "Skyline, 1240 N Homan Ave, Chicago, IL 60651"
Steps:
  1. Scroll to the footer company-info block
  2. Read the displayed address text
Expected Result: Footer displays the exact address text "Skyline, 1240 N Homan Ave, Chicago, IL 60651" as plain text (not a clickable link).
Linked Requirement: None

---
ID: TC-FOOTER-INFO-002
Title: Verify company email displays correctly in footer
Type: UI
Feature: footer
Flow: company-info
Priority: Low
Tags: UI
Preconditions: Homepage is loaded
Test Data: Expected email text = "sales@skyline.glass"
Steps:
  1. Scroll to the footer company-info block
  2. Read the displayed email text
  3. Check whether the email text is rendered as a clickable mailto: link or as plain text
Expected Result: Footer displays "sales@skyline.glass" as plain text with no mailto: link. This is documented current behavior (see GAPS in explorer-output/footer.md) and is not treated as a defect.
Linked Requirement: None

---
ID: TC-FOOTER-INFO-003
Title: Verify company phone number displays correctly in footer
Type: UI
Feature: footer
Flow: company-info
Priority: Low
Tags: UI
Preconditions: Homepage is loaded
Test Data: Expected phone text = "773-278-4660"
Steps:
  1. Scroll to the footer company-info block
  2. Read the displayed phone number text
  3. Check whether the phone text is rendered as a clickable tel: link or as plain text
Expected Result: Footer displays "773-278-4660" as plain text with no tel: link. This is documented current behavior (see GAPS in explorer-output/footer.md) and is not treated as a defect.
Linked Requirement: None
