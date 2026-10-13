# Keyboard Operability (documents current behaviour) — Test Cases
Feature: featured-projects-carousel
Scope: UI
Total: 2 cases (Critical: 0, High: 0, Medium: 0, Low: 2)

---
ID: TC-CAROUSEL-KEYBOARD-001
Title: Verify Prev/Next buttons are not reachable with Tab and have no accessible name
Type: UI
Feature: featured-projects-carousel
Flow: keyboard-operability
Priority: Low
Tags: negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Current behaviour is documented; if keyboard accessibility becomes a requirement this case is a defect and its expected result flips (see OPEN RISKS)
Test Data: tab_presses = 15; buttons = #carousel__prev, #carousel__next
Steps:
  1. Click on the "Featured Projects" heading (a non-interactive element) to set the keyboard starting point
  2. Press Tab up to 15 times and after each press record document.activeElement
  3. Read the tabindex, role and aria-label attributes of #carousel__prev and #carousel__next
Expected Result: Neither #carousel__prev nor #carousel__next ever receives focus during the Tab sequence (tabindex is -1). Both elements have no aria-label and no role attribute.
Linked Requirement: None

---
ID: TC-CAROUSEL-KEYBOARD-002
Title: Verify arrow keys do not move the carousel
Type: UI
Feature: featured-projects-carousel
Flow: keyboard-operability
Priority: Low
Tags: negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide; Current behaviour is documented; if keyboard support is added this case must be updated
Test Data: keys = ArrowRight x3, ArrowLeft x3
Steps:
  1. Click on the "Featured Projects" heading to move focus to the page body area
  2. Read the translate3d X offset of the slide track
  3. Press ArrowRight 3 times, then ArrowLeft 3 times
  4. Read the translate3d X offset again and check the browser console for uncaught errors
Expected Result: The track offset is unchanged after the key presses and no uncaught JavaScript error is raised.
Linked Requirement: None
