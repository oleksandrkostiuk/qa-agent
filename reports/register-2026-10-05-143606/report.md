# Test Report — Register 2026-10-05
Environment: book
URL: https://bookcart.azurewebsites.net/

## Notes
- No `feature`/`tag`/`priority`/`ids`/`file` filter was given. The only filter was an ad-hoc instruction to run "only those with type API" (not one of the Runner's standard arguments), so all `Type: API` test cases across the whole repo were selected (8 total, all under feature `register` — no other feature currently has API-type cases).
- `book` has no credentials configured in `PROJECT_CONFIG.json`. None of the selected API cases require login, so this had no effect.
- `TC-REGISTER-POSTLOGIN-002` and `TC-REGISTER-POSTLOGIN-003` each require a "freshly registered account" as precondition. Since this is a data-setup step (not an authentication requirement), a fresh account was registered via `POST /api/user/` to satisfy it rather than skipping/blocking. For `POSTLOGIN-002` this setup was attempted twice (once per execution + retry) with two different freshly-generated usernames — both times `POST /api/user/` returned 200 but the account was never actually persisted (`validateUserName` still reported it as available afterward), so the login step consistently got 401 instead of the expected 200. This is recorded as a `fail`, with the apparent root cause (same registration bug surfaced by `TC-REGISTER-USERNAME-006`) noted in `actual_result`.

## Summary
| Total | Pass | Fail | Blocked | Flaky |
|-------|------|------|---------|-------|
| 8     | 6    | 2    | 0       | 0     |

Pass rate: 75% (flaky counted separately, not as pass)

## Results by Priority
| Priority | Total | Pass | Fail | Blocked | Flaky |
|----------|-------|------|------|---------|-------|
| Critical | 0     | 0    | 0    | 0       | 0     |
| High     | 2     | 0    | 2    | 0       | 0     |
| Medium   | 4     | 4    | 0    | 0       | 0     |
| Low      | 2     | 2    | 0    | 0       | 0     |

## Failed Cases
| ID | Title | Actual Result | Evidence |
|----|-------|---------------|----------|
| TC-REGISTER-USERNAME-006 | API - registering with an already-taken username is not rejected by the server (bug) | Expected 400, got 200 (both attempt and retry) — duplicate username "test" accepted | POST /api/user/ → 200 (expected 400) |
| TC-REGISTER-POSTLOGIN-002 | API - login with freshly-registered credentials returns a token | Expected 200, got 401 (both attempt and retry) — registered account never persisted, so login can't succeed | POST /api/login/ → 401 (expected 200) |

## Flaky Cases
| ID | Title | Attempt 1 | Attempt 2 |
|----|-------|-----------|-----------|
| (none) | | | |

## Blocked Cases
| ID | Title | Reason | Evidence |
|----|-------|--------|----------|
| (none) | | | |

## Passed Cases
| ID | Title |
|----|-------|
| TC-REGISTER-GENDER-002 | API - registering with an invalid gender enum value is rejected |
| TC-REGISTER-POSTLOGIN-003 | API - login with correct username but wrong password is rejected |
| TC-REGISTER-USERNAME-002 | API - validateUserName returns false for an existing username |
| TC-REGISTER-USERNAME-003 | API - validateUserName returns true for an available username |
| TC-REGISTER-USERNAME-004 | API - validateUserName treats a whitespace-only username as available |
| TC-REGISTER-USERNAME-005 | API - validateUserName with empty path segment returns an inconsistent response shape |
