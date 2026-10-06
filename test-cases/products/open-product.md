# Open Product From Listing — Test Cases
Feature: products
Scope: UI
Total: 4 cases (Critical: 1, High: 2, Medium: 1, Low: 0)

---
ID: TC-PRODUCTS-OPEN-001
Title: Verify clicking a product card from the unfiltered listing opens a valid product detail page
Type: UI
Feature: products
Flow: open-product
Priority: Critical
Tags: smoke, regression
Preconditions: Products page is loaded, no filters or search query active
Test Data: First product card in the unfiltered listing
Steps:
  1. Click the first product card in the listing
  2. Wait for navigation to complete
Expected Result: A valid product detail page opens (no 404, no blank page, no console errors); the page content corresponds to the clicked product (matching product name/title).
Linked Requirement: None

---
ID: TC-PRODUCTS-OPEN-002
Title: Verify clicking a product card from filtered results opens the correct product's detail page
Type: UI
Feature: products
Flow: open-product
Priority: High
Tags: regression
Preconditions: Products page is loaded with "Smart Glass" category filter active (3 products shown)
Test Data: Category = "Smart Glass"
Steps:
  1. Check the "Smart Glass" category checkbox and wait for the filtered results
  2. Note the name of one of the filtered product cards
  3. Click that product card
Expected Result: The product detail page that opens matches the exact product that was clicked (name/title on the detail page matches the card noted in step 2), not a different product from the unfiltered set.
Linked Requirement: None

---
ID: TC-PRODUCTS-OPEN-003
Title: Verify navigating back from a product detail page opened via search results returns to the products page with the search query preserved
Type: UI
Feature: products
Flow: open-product
Priority: High
Tags: regression
Preconditions: Products page is loaded, no filters or search query active
Test Data: Search keyword = "glass"
Steps:
  1. Search for "glass" and wait for results to load
  2. Click on one of the returned product cards to open its detail page
  3. Use the browser Back button to return to the products page
Expected Result: The products page reloads with the "glass" search query still active in the URL (?keyw=glass) and the same search result set displayed, not a reset to the full unfiltered list.
Linked Requirement: None

---
ID: TC-PRODUCTS-OPEN-004
Title: Verify directly navigating to a non-existent product detail URL shows an appropriate not-found state instead of crashing
Type: UI
Feature: products
Flow: open-product
Priority: Medium
Tags: negative, boundary
Preconditions: None (direct URL navigation)
Test Data: URL = https://dev.skyline.glass/product/this-product-does-not-exist-xyz/
Steps:
  1. Navigate directly to https://dev.skyline.glass/product/this-product-does-not-exist-xyz/
  2. Observe the page response
  3. Check the browser console/network tab for a 500 error or unhandled exception
Expected Result: Page shows a proper 404/not-found state (or a graceful redirect to a valid page), with no 500 error, no unhandled exception, and no blank/broken page.
Linked Requirement: None
