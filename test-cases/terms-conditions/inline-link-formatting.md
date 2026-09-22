# Inline Link Formatting — Test Cases
Feature: terms-conditions
Scope: UI (formatting only)
Total: 3 cases (Critical: 0, High: 0, Medium: 0, Low: 3)

---
ID: TC-TERMS-LINKS-001
Title: Verify inline "SKYLINE DESIGN PRIVACY POLICY" link is visually distinguishable from surrounding body text
Type: UI
Feature: terms-conditions
Flow: inline-link-formatting
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page (https://dev.skyline.glass/terms-conditions/) is loaded
Test Data: Inline link text = "SKYLINE DESIGN PRIVACY POLICY"
Steps:
  1. Open the Terms & Conditions page
  2. Locate the paragraph containing the inline "SKYLINE DESIGN PRIVACY POLICY" link
  3. Compare the link's color/underline styling against the surrounding body text
Expected Result: The inline link is visually distinguishable from surrounding body text (e.g. distinct color and/or underline), so a user can clearly identify it as clickable.
Linked Requirement: None

---
ID: TC-TERMS-LINKS-002
Title: Verify inline "SKYLINE DESIGN PRIVACY POLICY" link points to the correct external URL
Type: UI
Feature: terms-conditions
Flow: inline-link-formatting
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: Inline link text = "SKYLINE DESIGN PRIVACY POLICY"
Steps:
  1. Open the Terms & Conditions page
  2. Locate the inline "SKYLINE DESIGN PRIVACY POLICY" link
  3. Read its href attribute
  4. Click the link and verify the destination page loads successfully
Expected Result: The link's href points to the correct Privacy Policy destination and clicking it loads that page successfully, with no 404 or other error.
Linked Requirement: None

---
ID: TC-TERMS-LINKS-003
Title: Verify inline link hover/focus state is visually indicated
Type: UI
Feature: terms-conditions
Flow: inline-link-formatting
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: Inline link text = "SKYLINE DESIGN PRIVACY POLICY"
Steps:
  1. Open the Terms & Conditions page
  2. Locate the inline "SKYLINE DESIGN PRIVACY POLICY" link
  3. Hover over the link with the mouse and observe any style change
  4. Tab to the link via keyboard and observe the focus indicator
Expected Result: A visible style change occurs on hover (e.g. color change or underline toggle) and a visible focus indicator (e.g. outline) appears when the link receives keyboard focus.
Linked Requirement: None
