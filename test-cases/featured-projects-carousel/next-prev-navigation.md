# Next/Prev Navigation — Test Cases
Feature: featured-projects-carousel
Scope: UI
Total: 5 cases (Critical: 0, High: 3, Medium: 2, Low: 0)

---
ID: TC-CAROUSEL-NAV-001
Title: Verify Next advances the carousel by exactly one slide
Type: UI
Feature: featured-projects-carousel
Flow: next-prev-navigation
Priority: High
Tags: smoke, regression, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: slide_step = about 891px at 1280px viewport (slide width 890px); tolerance = +/-5px
Steps:
  1. Read the translate3d X offset of the slide track and the title of the first visible slide
  2. Click the Next button (#carousel__next) once
  3. Wait about 1 second for the slide animation to finish
  4. Read the translate3d X offset and the title of the first visible slide again
Expected Result: The track offset decreases by one slide step (about 891px, within tolerance) and the previously second slide becomes the first visible slide. The page URL does not change.
Linked Requirement: None

---
ID: TC-CAROUSEL-NAV-002
Title: Verify Next on the last slide wraps back to the first slide
Type: UI
Feature: featured-projects-carousel
Flow: next-prev-navigation
Priority: High
Tags: boundary, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: clicks_to_reach_last_slide = data-total - 1 (4 at the time of exploration)
Steps:
  1. Click Next once, then wait about 1 second for the slide animation to finish; repeat until the last slide (item--4 for 5 slides) is the current slide (data-total - 1 clicks in total)
  2. Read the translate3d X offset of the slide track
  3. Click Next once more and wait about 1 second for the slide animation to finish
  4. Read the translate3d X offset and the title of the first visible slide
Expected Result: After the extra Next click the carousel wraps: the track returns to the initial (first slide) offset and the first slide is the first visible slide again.
Linked Requirement: None

---
ID: TC-CAROUSEL-NAV-003
Title: Verify Prev moves back by exactly one slide after Next
Type: UI
Feature: featured-projects-carousel
Flow: next-prev-navigation
Priority: High
Tags: regression, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: slide_step = about 891px at 1280px viewport; tolerance = +/-5px
Steps:
  1. Click Next once and wait about 1 second for the slide animation to finish
  2. Read the translate3d X offset (offset A)
  3. Click Next once more and wait about 1 second for the slide animation to finish
  4. Click the Prev button (#carousel__prev) once and wait about 1 second for the slide animation to finish
  5. Read the translate3d X offset (offset B)
Expected Result: Offset B equals offset A (within tolerance): Prev moves the carousel back by exactly one slide.
Linked Requirement: None

---
ID: TC-CAROUSEL-NAV-004
Title: Verify Prev on the first slide does not move or wrap the carousel
Type: UI
Feature: featured-projects-carousel
Flow: next-prev-navigation
Priority: Medium
Tags: boundary, negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: note = asserts current behaviour; Prev does not wrap (see OPEN RISKS in explorer handoff)
Steps:
  1. Read the translate3d X offset of the slide track and the title of the first visible slide
  2. Click the Prev button (#carousel__prev) once
  3. Wait about 1 second for the slide animation to finish
  4. Read the translate3d X offset and the title of the first visible slide again
Expected Result: Nothing changes: the track offset and the first visible slide are the same as before the click (no movement, no wrap to the last slide). No error is shown and the page does not navigate.
Linked Requirement: None

---
ID: TC-CAROUSEL-NAV-005
Title: Verify rapid repeated Next clicks do not break the carousel
Type: UI
Feature: featured-projects-carousel
Flow: next-prev-navigation
Priority: Medium
Tags: boundary, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: rapid_clicks = 5; interval_ms = under 100, no waiting between clicks; tolerance = +/-5px
Steps:
  1. Click the Next button (#carousel__next) 5 times in quick succession without waiting between clicks
  2. Wait about 1 second for the slide animation to finish
  3. Read the translate3d X offset of the slide track and check the browser console for uncaught errors
  4. Click Next once more, wait about 1 second for the slide animation to finish, and read the offset again
Expected Result: No uncaught JavaScript error is raised and all slides are still present. After the rapid clicks the track rests at a valid slide position (offset is 0 or a negative whole multiple of one slide step, within tolerance). The additional Next click still changes the track position.
Linked Requirement: None
