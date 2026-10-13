# Social Links — Test Cases
Feature: footer
Scope: UI
Total: 9 cases (Critical: 0, High: 0, Medium: 8, Low: 1)

---
ID: TC-FOOTER-SOCIAL-001
Title: Verify Instagram footer icon opens in a new tab with secure rel attributes
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: security, UI
Preconditions: Homepage is loaded
Test Data: Icon label = "Instagram"
Steps:
  1. Scroll to the footer social links section
  2. Locate the Instagram icon link
  3. Read its href, target, and rel attributes
  4. Click the icon link, switch to the newly opened tab, and verify the destination page loads successfully (no 404 or other error page)
Expected Result: Instagram link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". Clicking it opens a new tab whose destination page loads successfully with no 404 or other error.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-002
Title: Verify LinkedIn footer icon opens in a new tab with secure rel attributes
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: security, UI
Preconditions: Homepage is loaded
Test Data: Icon label = "LinkedIn"
Steps:
  1. Scroll to the footer social links section
  2. Locate the LinkedIn icon link
  3. Read its href, target, and rel attributes
  4. Click the icon link, switch to the newly opened tab, and verify the destination page loads successfully (no 404 or other error page)
Expected Result: LinkedIn link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". Clicking it opens a new tab whose destination page loads successfully with no 404 or other error.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-003
Title: Verify Facebook footer icon opens in a new tab with secure rel attributes
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: security, UI
Preconditions: Homepage is loaded
Test Data: Icon label = "Facebook"
Steps:
  1. Scroll to the footer social links section
  2. Locate the Facebook icon link
  3. Read its href, target, and rel attributes
  4. Click the icon link, switch to the newly opened tab, and verify the destination page loads successfully (no 404 or other error page)
Expected Result: Facebook link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". Clicking it opens a new tab whose destination page loads successfully with no 404 or other error.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-004
Title: Verify YouTube footer icon opens in a new tab with secure rel attributes
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: security, UI
Preconditions: Homepage is loaded
Test Data: Icon label = "YouTube"
Steps:
  1. Scroll to the footer social links section
  2. Locate the YouTube icon link
  3. Read its href, target, and rel attributes
  4. Click the icon link, switch to the newly opened tab, and verify the destination page loads successfully (no 404 or other error page)
Expected Result: YouTube link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". Clicking it opens a new tab whose destination page loads successfully with no 404 or other error.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-005
Title: Verify Instagram footer icon has no platform-identifying accessible name (known gap)
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: regression, UI
Preconditions: Homepage is loaded; Desktop viewport (>1200px)
Test Data: icon label = "Instagram", expected href = "https://www.instagram.com/skylineglass/", current aria label = " social profile - opens in a new tab"
Steps:
  1. Scroll to the footer social links section
  2. Locate the Instagram icon link (href = https://www.instagram.com/skylineglass/)
  3. Read the link's aria-label attribute
  4. Read the alt attribute of the <img> inside the link
  5. Read the link's accessible name as computed by the browser (accessibility tree)
Expected Result: Documents CURRENT behavior (known accessibility gap, not a defect filed): the Instagram link's aria-label is exactly " social profile - opens in a new tab" (leading space, no platform name, identical to the other 3 social icons), the inner <img> has no alt attribute, and the computed accessible name contains no reference to "Instagram". If a platform name is later added, this case fails and must be updated.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-006
Title: Verify LinkedIn footer icon has no platform-identifying accessible name (known gap)
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: regression, UI
Preconditions: Homepage is loaded; Desktop viewport (>1200px)
Test Data: icon label = "LinkedIn", expected href = "https://www.linkedin.com/company/skyline-design/", current aria label = " social profile - opens in a new tab"
Steps:
  1. Scroll to the footer social links section
  2. Locate the LinkedIn icon link (href = https://www.linkedin.com/company/skyline-design/)
  3. Read the link's aria-label attribute
  4. Read the alt attribute of the <img> inside the link
  5. Read the link's accessible name as computed by the browser (accessibility tree)
Expected Result: Documents CURRENT behavior (known accessibility gap, not a defect filed): the LinkedIn link's aria-label is exactly " social profile - opens in a new tab" (leading space, no platform name, identical to the other 3 social icons), the inner <img> has no alt attribute, and the computed accessible name contains no reference to "LinkedIn". If a platform name is later added, this case fails and must be updated.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-007
Title: Verify Facebook footer icon has no platform-identifying accessible name (known gap)
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: regression, UI
Preconditions: Homepage is loaded; Desktop viewport (>1200px)
Test Data: icon label = "Facebook", expected href = "https://www.facebook.com/skylinedesignglass/", current aria label = " social profile - opens in a new tab"
Steps:
  1. Scroll to the footer social links section
  2. Locate the Facebook icon link (href = https://www.facebook.com/skylinedesignglass/)
  3. Read the link's aria-label attribute
  4. Read the alt attribute of the <img> inside the link
  5. Read the link's accessible name as computed by the browser (accessibility tree)
Expected Result: Documents CURRENT behavior (known accessibility gap, not a defect filed): the Facebook link's aria-label is exactly " social profile - opens in a new tab" (leading space, no platform name, identical to the other 3 social icons), the inner <img> has no alt attribute, and the computed accessible name contains no reference to "Facebook". If a platform name is later added, this case fails and must be updated.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-008
Title: Verify YouTube footer icon has no platform-identifying accessible name (known gap)
Type: UI
Feature: footer
Flow: social-links
Priority: Medium
Tags: regression, UI
Preconditions: Homepage is loaded; Desktop viewport (>1200px)
Test Data: icon label = "YouTube", expected href = "http://www.youtube.com/@skyline-glass", current aria label = " social profile - opens in a new tab"
Steps:
  1. Scroll to the footer social links section
  2. Locate the YouTube icon link (href = http://www.youtube.com/@skyline-glass)
  3. Read the link's aria-label attribute
  4. Read the alt attribute of the <img> inside the link
  5. Read the link's accessible name as computed by the browser (accessibility tree)
Expected Result: Documents CURRENT behavior (known accessibility gap, not a defect filed): the YouTube link's aria-label is exactly " social profile - opens in a new tab" (leading space, no platform name, identical to the other 3 social icons), the inner <img> has no alt attribute, and the computed accessible name contains no reference to "YouTube". If a platform name is later added, this case fails and must be updated.
Linked Requirement: None

---
ID: TC-FOOTER-SOCIAL-009
Title: Verify YouTube footer link uses http:// while other social links use https://
Type: UI
Feature: footer
Flow: social-links
Priority: Low
Tags: boundary, security, UI
Preconditions: Homepage is loaded
Test Data: youtube href = "http://www.youtube.com/@skyline-glass", other hrefs = ["https://www.instagram.com/skylineglass/", "https://www.linkedin.com/company/skyline-design/", "https://www.facebook.com/skylinedesignglass/"]
Steps:
  1. Scroll to the footer social links section
  2. Read the href of the Instagram, LinkedIn, Facebook and YouTube icon links
  3. Note the protocol (scheme) of each href
  4. Click the YouTube icon link and switch to the newly opened tab
  5. Observe the final URL in the new tab and any security/insecure-connection warning
Expected Result: Documents CURRENT behavior: Instagram, LinkedIn and Facebook hrefs start with "https://"; the YouTube href starts with "http://" (protocol inconsistency). Opening the YouTube link ends on an https:// URL (server redirect) with no browser insecure-connection warning. Any other outcome (warning page, no redirect, load failure) is a deviation to report.
Linked Requirement: None
