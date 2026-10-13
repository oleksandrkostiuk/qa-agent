# View Project Links — Test Cases
Feature: featured-projects-carousel
Scope: UI
Total: 5 cases (Critical: 0, High: 2, Medium: 3, Low: 0)

---
ID: TC-CAROUSEL-LINK-001
Title: Verify every slide View Project link has a valid href that returns a successful response
Type: UI
Feature: featured-projects-carousel
Flow: view-project-links
Priority: High
Tags: smoke, regression, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view
Test Data: link_selector = a.more-link; expected_label = View Project; expected_path_contains = /project/
Steps:
  1. For each slide read the label and the href of its a.more-link link
  2. Request each href (HTTP GET) and read the response status
Expected Result: Every link is labelled "View Project", has a non-empty href that points to a project page (path contains "/project/"), and its URL responds with HTTP 200 (no 404 or other error).
Linked Requirement: None

---
ID: TC-CAROUSEL-LINK-002
Title: Verify clicking View Project opens the matching project page for every slide
Type: UI
Feature: featured-projects-carousel
Flow: view-project-links
Priority: High
Tags: regression, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: title_comparison = h1 text equals slide h4 title, ignoring case and surrounding whitespace
Steps:
  1. Note the title and the href of the slide currently first in view
  2. Click its "View Project" link
  3. Read the page URL and the h1 text of the opened page
  4. Navigate back to the home page, scroll to the Featured Projects section, and click Next as many times as needed to bring the next slide into view
  5. Repeat steps 1-4 for each remaining slide
Expected Result: For each slide the opened page URL matches the slide link href, the page loads without an error, and its h1 text matches the slide title.
Linked Requirement: None

---
ID: TC-CAROUSEL-LINK-003
Title: Verify clicking a slide image does not navigate
Type: UI
Feature: featured-projects-carousel
Flow: view-project-links
Priority: Medium
Tags: negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: click_target = first slide image (.js-drag-img)
Steps:
  1. Read the current page URL
  2. Click the first slide image once without moving the pointer
  3. Wait about 1 second for the slide animation to finish
  4. Read the current page URL
Expected Result: The page stays on the home page: the URL is unchanged and no project page opens.
Linked Requirement: None

---
ID: TC-CAROUSEL-LINK-004
Title: Verify clicking a slide title does not navigate
Type: UI
Feature: featured-projects-carousel
Flow: view-project-links
Priority: Medium
Tags: negative, UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: click_target = first slide title (h4)
Steps:
  1. Read the current page URL
  2. Click the first slide title (h4) once
  3. Wait about 1 second for the slide animation to finish
  4. Read the current page URL
Expected Result: The page stays on the home page: the URL is unchanged and no project page opens.
Linked Requirement: None

---
ID: TC-CAROUSEL-LINK-005
Title: Verify returning to the home page with browser Back resets the carousel to the first slide
Type: UI
Feature: featured-projects-carousel
Flow: view-project-links
Priority: Medium
Tags: UI
Preconditions: Home page (/) is loaded on the target environment at desktop viewport 1280x800; user is not logged in; Featured Projects section is scrolled into view; Carousel is on the first slide
Test Data: next_clicks = 2
Steps:
  1. Click Next twice, waiting for the animation after each click, and read the translate3d X offset
  2. Click the "View Project" link of the first slide in view
  3. Wait for the project page to load, then use the browser Back button
  4. Scroll to the Featured Projects section and read the translate3d X offset and the first visible slide title
Expected Result: The home page is shown again and the carousel is back at its start position: the first slide (item--0) is the first visible slide and the offset equals the initial value.
Linked Requirement: None
