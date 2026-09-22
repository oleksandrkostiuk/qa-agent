# Typography Headings — Test Cases
Feature: terms-conditions
Scope: UI (formatting only)
Total: 4 cases (Critical: 0, High: 0, Medium: 2, Low: 2)

---
ID: TC-TERMS-TYPO-001
Title: Verify heading hierarchy renders correctly despite H1→H3 level skip
Type: UI
Feature: terms-conditions
Flow: typography-headings
Priority: Medium
Tags: UI, boundary
Preconditions: Terms & Conditions page (https://dev.skyline.glass/terms-conditions/) is loaded
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Inspect the page's heading structure (H1 "Terms & Conditions" followed directly by an H3 "Terms & Conditions", with no H2 in between)
  3. Visually compare the H1 and H3 rendering against the rest of the page's heading styles
Expected Result: Despite the missing H2 level, the H1 and H3 headings render with clear, consistent visual hierarchy (size/weight/spacing) and no visible layout gap, overlap, or broken structure results from the skipped level.
Linked Requirement: None

---
ID: TC-TERMS-TYPO-002
Title: Verify ALL-CAPS legal clauses render without truncation, odd wrapping, or double case-transformation
Type: UI
Feature: terms-conditions
Flow: typography-headings
Priority: Medium
Tags: UI, boundary
Preconditions: Terms & Conditions page is loaded
Test Data: ALL-CAPS clauses in Sections 1, 6, 7, and 11.b
Steps:
  1. Open the Terms & Conditions page
  2. Scroll to Section 1 and inspect the ALL-CAPS clause text
  3. Repeat for Sections 6, 7, and 11.b
  4. Check computed CSS (e.g. text-transform) is not applied on top of literal uppercase source text
Expected Result: Each ALL-CAPS clause renders fully in uppercase, with no truncation, no unexpected line wrapping mid-word, and no double-transformation artifacts (e.g. text remains uppercase, not altered by a conflicting text-transform rule).
Linked Requirement: None

---
ID: TC-TERMS-TYPO-003
Title: Verify special characters render correctly in legal body text
Type: UI
Feature: terms-conditions
Flow: typography-headings
Priority: Low
Tags: UI, boundary
Preconditions: Terms & Conditions page is loaded
Test Data: Registered trademark symbol (®), curly quotes/apostrophes (" " '), em dash (–)
Steps:
  1. Open the Terms & Conditions page
  2. Locate and inspect instances of ® in the body text
  3. Locate and inspect curly quotes/apostrophes
  4. Locate and inspect em dash characters
Expected Result: All special characters render as their intended glyphs (®, curly quotes/apostrophes, em dash) with no mojibake, missing-character boxes, or fallback substitution.
Linked Requirement: None

---
ID: TC-TERMS-TYPO-004
Title: Verify visual typographic consistency between H1 and H3 heading styles
Type: UI
Feature: terms-conditions
Flow: typography-headings
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: None
Steps:
  1. Open the Terms & Conditions page
  2. Inspect font family, size, weight, and color of the H1 "Terms & Conditions"
  3. Inspect font family, size, weight, and color of the H3 "Terms & Conditions"
Expected Result: Font family and color are consistent with the site's design system for both headings; size/weight differences (if any) follow a clear, intentional visual hierarchy rather than appearing arbitrary or broken.
Linked Requirement: None
