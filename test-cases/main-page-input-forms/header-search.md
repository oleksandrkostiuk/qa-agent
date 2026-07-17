# Header Search — Test Cases
Feature: main-page-input-forms
Scope: UI
Total: 6 cases (Critical: 1, High: 1, Medium: 2, Low: 2)

---
ID: TC-MAINPAGE-SEARCH-001
Title: Searching with a valid query returns to the search results page
Type: UI
Feature: main-page-input-forms
Flow: header-search
Priority: Critical
Tags: smoke, regression
Preconditions: Anonymous user on the main page; header search form visible
Test Data: query = "glass"
Steps:
  1. Click into the header search field
  2. Enter "glass" as the query
  3. Submit the search form
Expected Result: Browser navigates to "/?s=glass" (or equivalent results route) and a search results page is rendered with no error.
Linked Requirement: None

---
ID: TC-MAINPAGE-SEARCH-002
Title: Submitting an empty search query is handled gracefully
Type: UI
Feature: main-page-input-forms
Flow: header-search
Priority: Medium
Tags: negative, boundary
Preconditions: Anonymous user on the main page; header search form visible
Test Data: query = "" (empty)
Steps:
  1. Click into the header search field
  2. Leave the query field empty
  3. Submit the search form
Expected Result: Form either prevents submission client-side, or navigates to a results page showing an appropriate empty/no-query state; no page crash or server error.
Linked Requirement: None

---
ID: TC-MAINPAGE-SEARCH-003
Title: Search query containing a script injection string is safely handled
Type: UI
Feature: main-page-input-forms
Flow: header-search
Priority: High
Tags: security, negative
Preconditions: Anonymous user on the main page; header search form visible
Test Data: query = "<script>alert(1)</script>"
Steps:
  1. Click into the header search field
  2. Enter "<script>alert(1)</script>" as the query
  3. Submit the search form
Expected Result: Query string is escaped/encoded in the URL and rendered results page; no script execution occurs (no JS alert), no unescaped HTML injection is visible in the rendered page.
Linked Requirement: None

---
ID: TC-MAINPAGE-SEARCH-004
Title: Submitting a very long search query string is handled without error
Type: UI
Feature: main-page-input-forms
Flow: header-search
Priority: Low
Tags: boundary
Preconditions: Anonymous user on the main page; header search form visible
Test Data: query = 500-character alphanumeric string
Steps:
  1. Click into the header search field
  2. Enter a 500-character alphanumeric string as the query
  3. Submit the search form
Expected Result: Results page loads without a crash, unhandled JS error, or server 500; an appropriate results/no-results state is shown.
Linked Requirement: None

---
ID: TC-MAINPAGE-SEARCH-005
Title: Submitting a whitespace-only search query is handled gracefully
Type: UI
Feature: main-page-input-forms
Flow: header-search
Priority: Medium
Tags: negative, boundary
Preconditions: Anonymous user on the main page; header search form visible
Test Data: query = "   " (three spaces)
Steps:
  1. Click into the header search field
  2. Enter "   " (whitespace only) as the query
  3. Submit the search form
Expected Result: Form treats the query as effectively empty — either blocks submission or shows an appropriate empty/no-query results state; no page crash or server error.
Linked Requirement: None

---
ID: TC-MAINPAGE-SEARCH-006
Title: Header search is fully usable without authentication
Type: UI
Feature: main-page-input-forms
Flow: header-search
Priority: Low
Tags: security, UI
Preconditions: Anonymous (unauthenticated) user on the main page; no login state exists on this site
Test Data: query = "test"
Steps:
  1. As an anonymous user (no login performed), click into the header search field
  2. Enter "test" as the query
  3. Submit the search form
Expected Result: Search executes successfully with no authentication prompt, redirect to a login page, or access-denied error.
Linked Requirement: None
