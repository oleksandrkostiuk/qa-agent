# Footer Navigation — Test Cases
Feature: footer
Scope: UI
Total: 2 cases (Critical: 0, High: 0, Medium: 1, Low: 1)

---
ID: TC-FOOTER-NAV-001
Title: Verify footer navigation menu displays all 15 links with valid labels and hrefs
Type: UI
Feature: footer
Flow: footer-navigation
Priority: Medium
Tags: smoke, UI
Preconditions: Homepage is loaded
Test Data: Expected link count = 15
Steps:
  1. Scroll to the footer navigation menu
  2. Count the number of navigation links displayed
  3. For each link, read its visible label text and its href attribute
  4. For each link, click it and verify the destination page loads successfully (no 404 or other error page), then navigate back to the homepage
Expected Result: Exactly 15 navigation links are displayed. Each link has non-empty, readable label text and a non-empty, valid href attribute. Clicking each link successfully loads its destination page with no 404 or other error.
Linked Requirement: None

---
ID: TC-FOOTER-NAV-002
Title: Verify "Home" footer nav link shows active state on homepage
Type: UI
Feature: footer
Flow: footer-navigation
Priority: Low
Tags: UI
Preconditions: Homepage is loaded
Test Data: None
Steps:
  1. Scroll to the footer navigation menu
  2. Locate the "Home" link
  3. Inspect the link element's class attribute
Expected Result: The "Home" link includes the current-menu-item class (or equivalent active-state indicator) while the user is on the homepage.
Linked Requirement: None
