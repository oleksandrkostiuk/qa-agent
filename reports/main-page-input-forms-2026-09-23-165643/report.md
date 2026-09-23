# Test Report — Main Page Input Forms 2026-09-23
Environment: dev
URL: https://dev.skyline.glass/

## Summary
| Total | Pass | Fail | Blocked | Flaky |
|-------|------|------|---------|-------|
| 17    | 15   | 2    | 0       | 0     |

Pass rate: 88.2% (flaky counted separately, not as pass)

## Results by Priority
| Priority | Total | Pass | Fail | Blocked | Flaky |
|----------|-------|------|------|---------|-------|
| Critical | 2     | 1    | 1    | 0       | 0     |
| High     | 4     | 3    | 1    | 0       | 0     |
| Medium   | 7     | 7    | 0    | 0       | 0     |
| Low      | 4     | 4    | 0    | 0       | 0     |

## Failed Cases
| ID | Title | Actual Result | Screenshot |
|----|-------|---------------|------------|
| TC-MAINPAGE-NEWSLETTER-001 | Subscribe with a valid test-domain email succeeds | "There was a problem with your submission. Please review the fields below." — valid email rejected. Reproduced on retry. Matches known BUG-001. | screenshots/TC-MAINPAGE-NEWSLETTER-001.png |
| TC-MAINPAGE-NEWSLETTER-010 | Legitimate submission is not blocked by invisible reCAPTCHA v3 | Same generic submission-rejected error on both attempts — same root cause as BUG-001. Recorded as known execution risk per this case's own OPEN RISK note, not a new defect. | screenshots/TC-MAINPAGE-NEWSLETTER-010.png |

## Flaky Cases
| ID | Title | Attempt 1 | Attempt 2 |
|----|-------|-----------|-----------|
| — | — | — | — |

## Blocked Cases
| ID | Title | Reason |
|----|-------|--------|
| — | — | — |

## Passed Cases
| ID | Title |
|----|-------|
| TC-MAINPAGE-NEWSLETTER-002 | Submitting the newsletter form with an empty email is rejected |
| TC-MAINPAGE-NEWSLETTER-003 | Submitting an email missing the "@" symbol is rejected |
| TC-MAINPAGE-NEWSLETTER-004 | Submitting an email missing the domain part is rejected |
| TC-MAINPAGE-NEWSLETTER-005 | Submitting an email containing spaces is rejected |
| TC-MAINPAGE-NEWSLETTER-006 | Submitting an email with a trailing dot is handled correctly |
| TC-MAINPAGE-NEWSLETTER-007 | Submitting a very long email string is handled without error |
| TC-MAINPAGE-NEWSLETTER-008 | Submitting an email with special/unicode characters is handled correctly |
| TC-MAINPAGE-NEWSLETTER-009 | Rapid repeated submissions of the newsletter form do not create duplicate/erroneous requests |
| TC-MAINPAGE-SEARCH-001 | Searching with a valid query returns to the search results page |
| TC-MAINPAGE-SEARCH-002 | Submitting an empty search query is handled gracefully |
| TC-MAINPAGE-SEARCH-003 | Search query containing a script injection string is safely handled |
| TC-MAINPAGE-SEARCH-004 | Submitting a very long search query string is handled without error |
| TC-MAINPAGE-SEARCH-005 | Submitting a whitespace-only search query is handled gracefully |
| TC-MAINPAGE-SEARCH-006 | Header search is fully usable without authentication |
| TC-MAINPAGE-SEARCH-007 | Autocomplete suggestions appear while typing in the header search field |
