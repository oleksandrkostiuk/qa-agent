# Carousel Structure and Content — Test Cases
Feature: featured-projects-carousel
Scope: UI
Total: 5 cases (Critical: 0, High: 0, Medium: 3, Low: 2)

---
ID: TC-CAROUSEL-STRUCT-001
Title: Verify Featured Projects section shows heading, Prev/Next buttons and slide count matching data-total
Type: UI
Feature: featured-projects-carousel
Flow: carousel-structure
Priority: Medium
Tags: smoke, regression, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in
Test Data: carousel_selector = #projects-carousel; slide_selector = #projects-carousel article.js-drag-item; prev_selector = #carousel__prev; next_selector = #carousel__next; note = exact titles and order are not asserted
Steps:
  1. Scroll to the section with the h3 heading "Featured Projects"
  2. Read the data-total attribute of #projects-carousel
  3. Count the slides matching "#projects-carousel article.js-drag-item"
  4. Locate the Prev (#carousel__prev) and Next (#carousel__next) buttons
Expected Result: The heading "Featured Projects" is visible. At least one slide exists and the slide count equals the data-total value (5 at the time of exploration). Both the Prev and Next buttons are present and visible.
Linked Requirement: None

---
ID: TC-CAROUSEL-STRUCT-002
Title: Verify every slide has a non-empty title, a Technique line and a View Project link
Type: UI
Feature: featured-projects-carousel
Flow: carousel-structure
Priority: Medium
Tags: regression, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view
Test Data: title_selector = h4; link_selector = a.more-link; link_text = View Project; note = slide image loading is not asserted (known dev data issue)
Steps:
  1. List all slides in "#projects-carousel article.js-drag-item"
  2. For each slide read the text of the h4 title
  3. For each slide check that a "Technique:" line with a non-empty value is present
  4. For each slide check that a link a.more-link with the text "View Project" is present
Expected Result: Every slide has a non-empty h4 title, a "Technique:" line with a non-empty value, and an a.more-link link labelled "View Project".
Linked Requirement: None

---
ID: TC-CAROUSEL-STRUCT-003
Title: Verify a slide without a "Pattern type" line renders no empty Pattern type row
Type: UI
Feature: featured-projects-carousel
Flow: carousel-structure
Priority: Low
Tags: boundary, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; At least one slide has no "Pattern type:" line (Alma Lasers at the time of exploration); if every slide has one, the "absent" part of the check is not applicable
Test Data: optional_line = Pattern type:
Steps:
  1. For each slide check whether a "Pattern type:" line is present
  2. For slides that have the line, read its value
  3. For slides that do not have the line, inspect the slide text block for an empty "Pattern type:" label or an empty row
Expected Result: Slides that have a "Pattern type:" line show a non-empty value. Slides without it show no "Pattern type:" label and no empty row; the rest of the slide (title, Technique, View Project) renders normally.
Linked Requirement: None

---
ID: TC-CAROUSEL-STRUCT-004
Title: Verify the carousel starts on the first slide and does not autoplay
Type: UI
Feature: featured-projects-carousel
Flow: carousel-structure
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view
Test Data: wait_seconds = 8
Steps:
  1. Reload the home page and scroll the Featured Projects section into view
  2. Read the inline transform (translate3d X offset) of the slide track inside #projects-carousel and the first visible slide title
  3. Wait 8 seconds without interacting with the page
  4. Read the translate3d X offset and the first visible slide title again
Expected Result: The first slide (item--0) is the first visible slide on load. The track offset and the first visible slide are identical before and after the 8-second wait (no autoplay).
Linked Requirement: None

---
ID: TC-CAROUSEL-STRUCT-005
Title: Verify slide description is visible on desktop width
Type: UI
Feature: featured-projects-carousel
Flow: carousel-structure
Priority: Low
Tags: boundary, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view
Test Data: description_selector = .pt-box; viewport = 1280x800; note = long descriptions may be truncated with "..."
Steps:
  1. For the first slide, read the .pt-box description text and check it is displayed
  2. Click Next and wait about 1 second for the slide animation to finish; repeat the description check for the slide now in view
  3. Repeat the previous step until every slide has been checked (or the carousel wraps)
Expected Result: At desktop width the .pt-box description of each checked slide is displayed and non-empty. Truncation with an ellipsis ("...") is acceptable for long descriptions.
Linked Requirement: None
