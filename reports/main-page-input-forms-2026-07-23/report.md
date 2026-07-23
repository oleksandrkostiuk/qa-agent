# Test Report — main-page-input-forms 2026-07-23
Environment: dev
URL: https://dev.skyline.glass/

## Summary
| Total | Pass | Fail | Blocked | Flaky |
|-------|------|------|---------|-------|
| 2     | 1    | 1    | 0       | 0     |

Pass rate: 50% (flaky counted separately, not as pass)

## Results by Priority
| Priority | Total | Pass | Fail | Blocked | Flaky |
|----------|-------|------|------|---------|-------|
| Critical | 2     | 1    | 1    | 0       | 0     |

## Failed Cases
| ID | Title | Actual Result | Screenshot |
|----|-------|---------------|------------|
| TC-MAINPAGE-NEWSLETTER-001 | Subscribe with a valid test-domain email succeeds | "There was a problem with your submission. Please review the fields below." — email field marked invalid despite valid format. Reproduced on retry (same result both attempts). | screenshots/TC-MAINPAGE-NEWSLETTER-001.png |

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
| TC-MAINPAGE-SEARCH-001 | Searching with a valid query returns to the search results page |
