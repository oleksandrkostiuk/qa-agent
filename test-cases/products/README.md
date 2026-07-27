# Products — Test Cases

| Flow | Cases | Critical | High | Medium | Low | Status |
|------|-------|----------|------|--------|-----|--------|
| search | 8 | 1 | 2 | 3 | 2 | covered |
| filter-category | 7 | 1 | 3 | 3 | 0 | covered |
| reset-filters | 3 | 0 | 1 | 1 | 1 | covered |
| open-product | 4 | 1 | 2 | 1 | 0 | covered |
| hover-feedback | — | — | — | — | — | skipped (descoped — no reliable Playwright-assertable signal; hover has no visible/computed-style change) |
| pagination | — | — | — | — | — | skipped (descoped — feature confirmed absent on this page; all 19 products render on a single load) |

Coverage: 4/6 flows (67%)

Note: `search` cases TC-PRODUCTS-SEARCH-001 and TC-PRODUCTS-SEARCH-002 document the current search-relevance baseline (loose/inconsistent matching) rather than ideal behavior — see OPEN RISKS in explorer-output/products.md. This is tracked as a known issue for the product/dev team, not treated as a passing "correct search" assertion.
