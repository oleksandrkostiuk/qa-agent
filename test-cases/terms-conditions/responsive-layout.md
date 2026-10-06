# Responsive Layout — Test Cases
Feature: terms-conditions
Scope: UI (formatting only)
Total: 4 cases (Critical: 0, High: 0, Medium: 4, Low: 0)

---
ID: TC-TERMS-RESPONSIVE-001
Title: Verify page renders correctly at mobile viewport (390px)
Type: UI
Feature: terms-conditions
Flow: responsive-layout
Priority: Medium
Tags: UI
Preconditions: Terms & Conditions page (https://dev.skyline.glass/terms-conditions/) is loaded
Test Data: Viewport width = 390px (mobile)
Steps:
  1. Resize the browser/viewport to 390px width
  2. Open the Terms & Conditions page
  3. Scroll through the full page, checking for horizontal scroll, text reflow, and header nav state
Expected Result: No horizontal scroll appears at any point on the page; body text reflows to fit the viewport width; header navigation collapses into its mobile pattern (e.g. hamburger menu) correctly.
Linked Requirement: None

---
ID: TC-TERMS-RESPONSIVE-002
Title: Verify page renders correctly at tablet viewport (~768px)
Type: UI
Feature: terms-conditions
Flow: responsive-layout
Priority: Medium
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: Viewport width = ~768px (tablet)
Steps:
  1. Resize the browser/viewport to ~768px width
  2. Open the Terms & Conditions page
  3. Scroll through the full page, checking for horizontal scroll, text reflow, and header nav state
Expected Result: No horizontal scroll appears at any point on the page; body text reflows correctly for the tablet breakpoint; header navigation renders in its intended tablet layout.
Linked Requirement: None

---
ID: TC-TERMS-RESPONSIVE-003
Title: Verify page renders correctly at desktop viewport (1280px+)
Type: UI
Feature: terms-conditions
Flow: responsive-layout
Priority: Medium
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: Viewport width = 1280px and above (desktop)
Steps:
  1. Resize the browser/viewport to 1280px width (and repeat at a wider desktop width, e.g. 1920px)
  2. Open the Terms & Conditions page
  3. Scroll through the full page, checking layout, max-width constraints, and header nav state
Expected Result: Content is constrained to a readable max-width (not stretched edge-to-edge on very wide screens), no horizontal scroll appears, and the full desktop header navigation displays correctly.
Linked Requirement: None

---
ID: TC-TERMS-RESPONSIVE-004
Title: Verify long unbroken paragraph (Section 11.b) does not overflow or clip on narrow viewports
Type: UI
Feature: terms-conditions
Flow: responsive-layout
Priority: Medium
Tags: UI, boundary
Preconditions: Terms & Conditions page is loaded
Test Data: Section 11.b liability clause paragraph (~1900 characters, single unbroken block)
Steps:
  1. Resize the browser/viewport to 390px width (mobile)
  2. Scroll to Section 11.b
  3. Inspect the full paragraph for overflow, clipping, or horizontal scroll
  4. Repeat at ~768px (tablet) width
Expected Result: The long paragraph wraps within the viewport at all tested widths with no clipping, no text cut off, and no horizontal scroll introduced.
Linked Requirement: None
