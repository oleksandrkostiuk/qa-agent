# Social Links — Test Cases
Feature: footer
Scope: UI
Total: 4 cases (Critical: 0, High: 0, Medium: 4, Low: 0)

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
Expected Result: Instagram link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". (Destination page load is out of scope for this suite — see OPEN RISKS in explorer-output/footer.md.)
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
Expected Result: LinkedIn link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". (Destination page load is out of scope for this suite.)
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
Expected Result: Facebook link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". (Destination page load is out of scope for this suite.)
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
Expected Result: YouTube link has a non-empty href, target="_blank", and rel="noopener noreferrer nofollow". (Destination page load is out of scope for this suite.)
Linked Requirement: None
