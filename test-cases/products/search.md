# Search — Test Cases
Feature: products
Scope: UI
Total: 8 cases (Critical: 1, High: 2, Medium: 3, Low: 2)

---
ID: TC-PRODUCTS-SEARCH-001
Title: Verify generic keyword search returns the full unfiltered product list (documented baseline)
Type: UI
Feature: products
Flow: search
Priority: Medium
Tags: smoke, UI
Preconditions: Products page (https://dev.skyline.glass/products/) is loaded, no filters or search query active
Test Data: Search keyword = "glass" (generic term matching most product names/descriptions); Baseline total product count = 19
Steps:
  1. Click the product search box
  2. Type "glass" and submit the search (results load at ?keyw=glass)
  3. Count the number of product results displayed
Expected Result: All 19 products are returned unfiltered — a generic/common search term does not narrow the result set. This is documented current baseline behavior (see explorer-output/products.md OPEN RISKS — search relevance logic unconfirmed, flagged for further investigation), not asserted as ideal relevance matching.
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-002
Title: Verify search for a specific unique product name returns the documented baseline result (unrelated products, not an exact match)
Type: UI
Feature: products
Flow: search
Priority: High
Tags: negative, UI
Preconditions: Products page is loaded, no filters or search query active
Test Data: Search keyword = "Vitracolor" (name of one specific, unique product)
Steps:
  1. Click the product search box
  2. Type "Vitracolor" and submit the search (?keyw=Vitracolor)
  3. Review the returned product list against the expected single "Vitracolor" product
Expected Result: The search returns 5 products, none of which is the exact "Vitracolor" product a user would expect from a unique-name query. This is documented baseline — search relevance logic unconfirmed, flagged for further investigation. Do not treat this result as a pass implying accurate relevance matching; it documents current (likely incorrect) behavior for tracking, and should be raised to the product/dev team outside this test suite.
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-003
Title: Verify search for a nonexistent/gibberish term shows "No results found"
Type: UI
Feature: products
Flow: search
Priority: Medium
Tags: boundary, negative
Preconditions: Products page is loaded, no filters or search query active
Test Data: Search keyword = "zzznonexistentproduct123"
Steps:
  1. Click the product search box
  2. Type "zzznonexistentproduct123" and submit the search
Expected Result: Page displays "No results found" (or equivalent empty-state message), with zero product cards rendered and no console errors.
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-004
Title: Verify empty search query returns the full unfiltered product list
Type: UI
Feature: products
Flow: search
Priority: Low
Tags: boundary
Preconditions: Products page is loaded, no filters active
Test Data: Search keyword = "" (submit search box empty, resulting in ?keyw=)
Steps:
  1. Click the product search box without typing anything
  2. Submit the empty search
  3. Count the number of product results displayed
Expected Result: All 19 products are displayed — an empty query is treated identically to no search filter at all.
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-005
Title: Verify a script-injection (XSS) payload in the search box is safely neutralized
Type: UI
Feature: products
Flow: search
Priority: Critical
Tags: security, negative
Preconditions: Products page is loaded, no filters or search query active
Test Data: Search keyword = "<script>alert(1)</script>"
Steps:
  1. Click the product search box
  2. Type "<script>alert(1)</script>" and submit the search
  3. Check the DOM for reflected/unescaped script content and check the browser console for errors or executed alerts
Expected Result: No script executes (no alert dialog appears), the payload is not reflected unescaped anywhere in the DOM, no console errors are logged, and the page resolves to "No results found".
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-006
Title: Verify a SQL-injection-style payload in the search box does not break the page or expose errors
Type: UI
Feature: products
Flow: search
Priority: High
Tags: security, negative
Preconditions: Products page is loaded, no filters or search query active
Test Data: Search keyword = "' OR '1'='1"
Steps:
  1. Click the product search box
  2. Type "' OR '1'='1" and submit the search
  3. Observe the page response and check the browser console/network tab for server errors (500s) or stack traces
Expected Result: Page loads normally (no 500 error, no exposed stack trace or database error message), and shows either "No results found" or an unfiltered/partial result set — but never raw error output.
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-007
Title: Verify a whitespace-only search query behaves the same as an empty query
Type: UI
Feature: products
Flow: search
Priority: Low
Tags: boundary, negative
Preconditions: Products page is loaded, no filters active
Test Data: Search keyword = "   " (three spaces)
Steps:
  1. Click the product search box
  2. Type three space characters only and submit the search
  3. Count the number of product results displayed
Expected Result: All 19 products are displayed, identical to the empty-query behavior (TC-PRODUCTS-SEARCH-004) — whitespace is not treated as a meaningful filter term.
Linked Requirement: None

---
ID: TC-PRODUCTS-SEARCH-008
Title: Verify an excessively long search input does not crash or error the page
Type: UI
Feature: products
Flow: search
Priority: Medium
Tags: boundary, negative
Preconditions: Products page is loaded, no filters or search query active
Test Data: Search keyword = 300-character repeated string (e.g. "glass" repeated 60 times)
Steps:
  1. Click the product search box
  2. Paste a 300-character string and submit the search
  3. Observe page load and console for errors
Expected Result: Page loads without crashing, freezing, or throwing console/network errors; result set is either empty ("No results found") or a valid product list — never a broken/blank page.
Linked Requirement: None
