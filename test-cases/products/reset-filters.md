# Reset Filters — Test Cases
Feature: products
Scope: UI
Total: 3 cases (Critical: 0, High: 1, Medium: 1, Low: 1)

---
ID: TC-PRODUCTS-RESET-001
Title: Verify "Reset filters" link clears all selected category filters and returns to the unfiltered product list
Type: UI
Feature: products
Flow: reset-filters
Priority: High
Tags: smoke, regression
Preconditions: Products page is loaded with at least one category filter active
Test Data: Category = "Smart Glass" (active filter before reset)
Steps:
  1. Check the "Smart Glass" category checkbox and confirm the filtered result count (3 products)
  2. Click the "Reset filters" link
  3. Observe the resulting URL and product list
Expected Result: The page navigates back to the plain https://dev.skyline.glass/products/ URL with no query params, the category checkbox is unchecked, the "Selected filters" summary is gone, and all 19 products are displayed.
Linked Requirement: None

---
ID: TC-PRODUCTS-RESET-002
Title: Verify "Reset filters" clears both an active category filter and an active search query together
Type: UI
Feature: products
Flow: reset-filters
Priority: Medium
Tags: regression
Preconditions: Products page is loaded with a category filter and a search query both active
Test Data: Category = "Smart Glass"; Search keyword = "glass"
Steps:
  1. Check the "Smart Glass" category checkbox
  2. Additionally enter "glass" in the search box and submit
  3. Click the "Reset filters" link
  4. Observe the resulting URL and product list
Expected Result: The page returns to the plain https://dev.skyline.glass/products/ URL with no ?keyw= or ?product_category[]= params of any kind, and all 19 products are displayed unfiltered.
Linked Requirement: None

---
ID: TC-PRODUCTS-RESET-003
Title: Verify "Reset filters" link is a no-op when clicked with no active filters or search
Type: UI
Feature: products
Flow: reset-filters
Priority: Low
Tags: boundary, negative
Preconditions: Products page is loaded, no filters or search query active
Test Data: None
Steps:
  1. Confirm no category filter is checked and the search box is empty
  2. Click the "Reset filters" link
  3. Observe the resulting URL and product list
Expected Result: Page remains at (or reloads to) the plain https://dev.skyline.glass/products/ URL with all 19 products displayed, no console errors, and no unexpected state change.
Linked Requirement: None
