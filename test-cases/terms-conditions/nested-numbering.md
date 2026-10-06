# Nested Numbering — Test Cases
Feature: terms-conditions
Scope: UI (formatting only)
Total: 4 cases (Critical: 0, High: 0, Medium: 2, Low: 2)

---
ID: TC-TERMS-NUMBERING-001
Title: Verify Section 11 three-level nested numbering (numeric → alpha → roman) renders with correct visual nesting
Type: UI
Feature: terms-conditions
Flow: nested-numbering
Priority: Medium
Tags: UI, boundary
Preconditions: Terms & Conditions page (https://dev.skyline.glass/terms-conditions/) is loaded
Test Data: Section 11 numbering: numeric (1–11) → alpha (a–e) → roman numeral (i–v)
Steps:
  1. Open the Terms & Conditions page
  2. Scroll to Section 11
  3. Inspect the numeric top-level item, its alpha sub-items (a–e), and the roman-numeral sub-items (i–v) nested under item 11.b
  4. Compare indentation levels between the numeric, alpha, and roman tiers
Expected Result: All three numbering tiers (numeric, alpha, roman) render with visually distinct, progressively increasing indentation — the nesting is preserved, not flattened to a single visual level.
Linked Requirement: None

---
ID: TC-TERMS-NUMBERING-002
Title: Verify top-level numeric section list (1–11) is sequential with no gaps or duplicates
Type: UI
Feature: terms-conditions
Flow: nested-numbering
Priority: Medium
Tags: UI, boundary
Preconditions: Terms & Conditions page is loaded
Test Data: Section numbers 1 through 11
Steps:
  1. Open the Terms & Conditions page
  2. Scroll through the full document, noting each top-level section number as it renders
Expected Result: Section numbers render sequentially from 1 to 11 with no skipped, repeated, or misrendered numbers.
Linked Requirement: None

---
ID: TC-TERMS-NUMBERING-003
Title: Verify alpha sub-list (a–e) indentation is visually distinct from its parent numeric item
Type: UI
Feature: terms-conditions
Flow: nested-numbering
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: Section 11, alpha items a–e
Steps:
  1. Open the Terms & Conditions page
  2. Scroll to Section 11
  3. Inspect the left-indentation of alpha items (a–e) relative to the numeric parent item (11)
Expected Result: Alpha sub-items are indented further right than the parent numeric item, with consistent indentation across all five alpha items (a–e).
Linked Requirement: None

---
ID: TC-TERMS-NUMBERING-004
Title: Verify roman numeral sub-list (i–v) indentation is visually distinct from its parent alpha item
Type: UI
Feature: terms-conditions
Flow: nested-numbering
Priority: Low
Tags: UI
Preconditions: Terms & Conditions page is loaded
Test Data: Section 11.b, roman numeral items i–v
Steps:
  1. Open the Terms & Conditions page
  2. Scroll to Section 11.b
  3. Inspect the left-indentation of roman numeral items (i–v) relative to the parent alpha item (b)
Expected Result: Roman numeral sub-items are indented further right than the parent alpha item, with consistent indentation across all five roman items (i–v).
Linked Requirement: None
