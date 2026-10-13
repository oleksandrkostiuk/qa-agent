# Drag Interaction — Test Cases
Feature: featured-projects-carousel
Scope: UI
Total: 5 cases (Critical: 0, High: 0, Medium: 2, Low: 3)

---
ID: TC-CAROUSEL-DRAG-001
Title: Verify dragging the carousel left moves the content without navigating
Type: UI
Feature: featured-projects-carousel
Flow: drag-interaction
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: drag = mouse down on the first slide image area, move 300px to the left in small steps, release; note = final snap position is not asserted
Steps:
  1. Read the translate3d X offset of the slide track and the current page URL
  2. Press the left mouse button on the first slide image area, move the pointer 300px to the left in small steps and release the button
  3. Read the translate3d X offset and the current page URL again
Expected Result: The track offset decreases (content moved to the left) compared to the initial value. The page URL is unchanged: the drag does not navigate to a project page.
Linked Requirement: None

---
ID: TC-CAROUSEL-DRAG-002
Title: Verify dragging the carousel right moves the content back without navigating
Type: UI
Feature: featured-projects-carousel
Flow: drag-interaction
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: drag_left = 300px; drag_right = 300px
Steps:
  1. Drag the carousel 300px to the left (mouse down, move, release) and read the translate3d X offset (offset A)
  2. Drag the carousel 300px to the right (mouse down, move, release) and read the translate3d X offset (offset B)
  3. Read the current page URL
Expected Result: Offset B is greater than offset A (content moved back to the right). The page URL is unchanged.
Linked Requirement: None

---
ID: TC-CAROUSEL-DRAG-003
Title: Verify a plain click without dragging does not move the carousel
Type: UI
Feature: featured-projects-carousel
Flow: drag-interaction
Priority: Low
Tags: negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: click_target = first slide image area
Steps:
  1. Read the translate3d X offset of the slide track
  2. Click once on the first slide image area without moving the pointer
  3. Wait about 1 second for the slide animation to finish
  4. Read the translate3d X offset again
Expected Result: The track offset is unchanged after the click.
Linked Requirement: None

---
ID: TC-CAROUSEL-DRAG-004
Title: Verify a very short drag does not break the carousel or navigate
Type: UI
Feature: featured-projects-carousel
Flow: drag-interaction
Priority: Low
Tags: boundary, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: drag_distance = 10px (below the 30px threshold observed during exploration); note = resulting offset is not asserted
Steps:
  1. Press the left mouse button on the first slide image area, move the pointer 10px to the left and release
  2. Read the current page URL and check the browser console for uncaught errors
  3. Check that all slides and the Prev/Next buttons are still displayed
Expected Result: The page URL is unchanged, no uncaught JavaScript error is raised, and all slides and the Prev/Next buttons remain displayed.
Linked Requirement: None

---
ID: TC-CAROUSEL-DRAG-005
Title: Verify dragging far beyond the first and last slide does not break the page
Type: UI
Feature: featured-projects-carousel
Flow: drag-interaction
Priority: Low
Tags: boundary, negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: drag_right_at_start = 600px; drag_left_repeated = 3 drags of 600px; note = bounds behaviour is not fully characterised; only stability is asserted
Steps:
  1. Drag the carousel 600px to the right while on the first slide
  2. Drag the carousel 600px to the left three times in a row
  3. Read the current page URL, check the browser console for uncaught errors, and check that the slides, the Prev/Next buttons and the "Featured Projects" heading are still displayed
Expected Result: The page URL is unchanged, no uncaught JavaScript error is raised, and the heading, the carousel container, the slides and the Prev/Next buttons are still displayed.
Linked Requirement: None
