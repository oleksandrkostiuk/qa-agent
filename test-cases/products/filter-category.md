# Filter By Category — Test Cases
Feature: products
Scope: UI
Total: 7 cases (Critical: 1, High: 3, Medium: 3, Low: 0)

---
ID: TC-PRODUCTS-FILTER-001
Title: Verify selecting a single category filter returns only matching products
Type: UI
Feature: products
Flow: filter-category
Priority: Critical
Tags: smoke, regression
Preconditions: Products page (https://dev.skyline.glass/products/) is loaded, no filters active
Test Data: Category = "Smart Glass" (3 known matching products)
Steps:
  1. Open the category filter checkbox list
  2. Check the "Smart Glass" category checkbox
  3. Wait for the page to reload with ?product_category[]=<Smart Glass id>
  4. Count the displayed product results
Expected Result: Only the 3 products belonging to the "Smart Glass" category are displayed; all other products are excluded from the result set.
Linked Requirement: None

---
ID: TC-PRODUCTS-FILTER-002
Title: Verify selecting multiple categories filters using OR logic (union of results)
Type: UI
Feature: products
Flow: filter-category
Priority: High
Tags: regression
Preconditions: Products page is loaded, no filters active
Test Data: Categories = "Smart Glass" (3 products) + "Artwork" (1 product)
Steps:
  1. Check the "Smart Glass" category checkbox
  2. Additionally check the "Artwork" category checkbox
  3. Wait for the page to reload with both category IDs in ?product_category[]=
  4. Count the displayed product results
Expected Result: Exactly 4 products are displayed — the union (OR) of "Smart Glass" (3) and "Artwork" (1) results, not their intersection.
Linked Requirement: None

---
ID: TC-PRODUCTS-FILTER-003
Title: Verify selected category filters float to top of the filter list with a "Selected filters" summary
Type: UI
Feature: products
Flow: filter-category
Priority: Medium
Tags: UI
Preconditions: Products page is loaded, no filters active
Test Data: Category = "Artwork"
Steps:
  1. Note the current position of "Artwork" in the category checkbox list
  2. Check the "Artwork" category checkbox
  3. Observe the re-ordered category list and any summary text above/below it
Expected Result: "Artwork" moves to the top of the category checkbox list, and a "Selected filters: Artwork" summary line is displayed.
Linked Requirement: None

---
ID: TC-PRODUCTS-FILTER-004
Title: Verify filtering by a category with a unicode/emoji name returns the correct product
Type: UI
Feature: products
Flow: filter-category
Priority: Medium
Tags: boundary
Preconditions: Products page is loaded, no filters active
Test Data: Category = "TEST 2. 🐶👍🔥 Modi quaerat fugiat alias distinctio." (1 known matching product)
Steps:
  1. Locate the category checkbox with the unicode/emoji label "TEST 2. 🐶👍🔥 Modi quaerat fugiat alias distinctio."
  2. Check that category checkbox
  3. Count the displayed product results
Expected Result: Exactly 1 product is displayed — the single product belonging to that unicode/emoji-named category. The category label renders correctly (no mojibake/broken characters).
Linked Requirement: None

---
ID: TC-PRODUCTS-FILTER-005
Title: Verify deselecting an active category filter removes it and updates the results
Type: UI
Feature: products
Flow: filter-category
Priority: High
Tags: regression
Preconditions: Products page is loaded with "Smart Glass" category filter already active (3 products shown)
Test Data: Category = "Smart Glass"
Steps:
  1. Uncheck the already-selected "Smart Glass" category checkbox
  2. Wait for the page to reload without the category param
  3. Count the displayed product results
Expected Result: The "Smart Glass" filter is removed, the "Selected filters" summary no longer lists it, and all 19 products are displayed again.
Linked Requirement: None

---
ID: TC-PRODUCTS-FILTER-006
Title: Verify category filter selection persists across browser back-navigation after opening a product
Type: UI
Feature: products
Flow: filter-category
Priority: High
Tags: regression
Preconditions: Products page is loaded, no filters active
Test Data: Category = "Smart Glass"
Steps:
  1. Check the "Smart Glass" category checkbox and wait for the filtered results
  2. Click on one of the filtered product cards to open its detail page
  3. Use the browser Back button to return to the products page
Expected Result: The products page reloads with the "Smart Glass" filter still active — the same 3 filtered products are shown, not the full unfiltered list.
Linked Requirement: None

---
ID: TC-PRODUCTS-FILTER-007
Title: Verify filtering via a manually edited URL with a non-existent category ID is handled gracefully
Type: UI
Feature: products
Flow: filter-category
Priority: Medium
Tags: negative, boundary
Preconditions: None (direct URL navigation)
Test Data: URL = https://dev.skyline.glass/products/?product_category[]=999999 (category ID that does not exist)
Steps:
  1. Navigate directly to https://dev.skyline.glass/products/?product_category[]=999999
  2. Observe the page response and product results
  3. Check the browser console/network tab for errors
Expected Result: Page loads without a 500 error or crash, and shows either "No results found" or the full unfiltered list — never a broken page or exposed server error.
Linked Requirement: None
