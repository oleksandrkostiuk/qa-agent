# Mobile Layout (390px) — Test Cases
Feature: featured-projects-carousel
Scope: UI
Total: 3 cases (Critical: 0, High: 0, Medium: 3, Low: 0)

---
ID: TC-CAROUSEL-MOBILE-001
Title: Verify mobile layout shows one slide per view, hides descriptions and has no horizontal overflow
Type: UI
Feature: featured-projects-carousel
Flow: mobile-layout
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at mobile viewport 390x844; user is not logged in; Featured Projects section is scrolled into view
Test Data: viewport = 390x844; expected_slide_width = about 390px; description_selector = .pt-box
Steps:
  1. Read the width of a slide and the width of the carousel container
  2. Check how many slides are fully visible in the carousel viewport
  3. Check whether the .pt-box description is displayed on each slide
  4. Compare document.documentElement.scrollWidth with the viewport width
Expected Result: Slide width is about 390px (the viewport width) and exactly one slide is visible at a time. The .pt-box description is hidden on every slide. The page has no horizontal overflow (scrollWidth does not exceed the viewport width).
Linked Requirement: None

---
ID: TC-CAROUSEL-MOBILE-002
Title: Verify Prev/Next buttons are visible below the heading and work on mobile
Type: UI
Feature: featured-projects-carousel
Flow: mobile-layout
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at mobile viewport 390x844; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: viewport = 390x844; slide_step = about 390px; tolerance = +/-5px
Steps:
  1. Locate the Prev (#carousel__prev) and Next (#carousel__next) buttons and check they are displayed below the "Featured Projects" heading and not covered by other elements
  2. Read the translate3d X offset of the slide track
  3. Tap Next once, wait about 1 second for the slide animation to finish, and read the offset again
  4. Tap Prev once, wait about 1 second for the slide animation to finish, and read the offset again
Expected Result: Both buttons are displayed below the heading and can be tapped. Next moves the track by one slide step (about 390px, within tolerance) and Prev moves it back to the initial offset.
Linked Requirement: None

---
ID: TC-CAROUSEL-MOBILE-003
Title: Verify the View Project link opens the matching project page on mobile
Type: UI
Feature: featured-projects-carousel
Flow: mobile-layout
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at mobile viewport 390x844; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: viewport = 390x844; title_comparison = h1 text equals slide h4 title, ignoring case and surrounding whitespace
Steps:
  1. Note the title and the href of the slide in view
  2. Tap its "View Project" link
  3. Read the page URL and the h1 text of the opened page
Expected Result: The opened page URL matches the slide link href, the page loads without an error, and its h1 text matches the slide title.
Linked Requirement: None
