# Skip To Content — Test Cases
Feature: terms-conditions
Scope: UI (formatting only)
Total: 3 cases (Critical: 0, High: 0, Medium: 0, Low: 3)

---
ID: TC-TERMS-SKIPLINK-001
Title: Verify "Skip to content" link is visually hidden by default
Type: UI
Feature: terms-conditions
Flow: skip-to-content
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page (https://dev.skyline.glass/terms-conditions/) is loaded, no keyboard interaction yet
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Without interacting via keyboard, inspect the top of the page for a visible "Skip to content" link
Expected Result: The "Skip to content" link is not visibly rendered on the page before any keyboard interaction (e.g. positioned off-screen or visually hidden).
Linked Requirement: None

---
ID: TC-TERMS-SKIPLINK-002
Title: Verify "Skip to content" link becomes visible on keyboard focus
Type: UI
Feature: terms-conditions
Flow: skip-to-content
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Press Tab once to move keyboard focus to the first focusable element
Expected Result: The "Skip to content" link becomes visible on-screen with a clear focus indicator as soon as it receives keyboard focus.
Linked Requirement: None

---
ID: TC-TERMS-SKIPLINK-003
Title: Verify activating "Skip to content" link moves focus to the main content area
Type: UI
Feature: terms-conditions
Flow: skip-to-content
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded, "Skip to content" link is focused
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Press Tab to focus the "Skip to content" link
  3. Press Enter to activate it
Expected Result: Keyboard focus and page scroll position move to the main content area (past the header/nav), and the link itself returns to its hidden state.
Linked Requirement: None
