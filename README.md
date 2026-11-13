# Login Test Design

Test design for a login feature, written while learning test design techniques.

**Status:** designed, not executed. The specification below is hypothetical (there is no real app behind it), so the Actual Result and Status columns are still "Not Run".

## Assumed specification

- Login with email and password
- Password must be at least 8 characters
- Account is locked after 3 failed attempts
- Wrong credentials always show the same generic message ("Email atau password salah"), so the system does not reveal which emails are registered
- All accounts and passwords in the files are dummy data

## Files

| File | Content |
|---|---|
| `test-cases-login.xlsx` | 14 test cases: ID, description, pre-condition, steps, data, expected result, priority, technique |
| `test-cases-login.csv` | Same table as CSV, readable directly on GitHub |

## Techniques used

| Technique | Test cases |
|---|---|
| Positive test | TC-LOG-01 |
| Decision Table | TC-LOG-02, 03 |
| Boundary Value Analysis (password 7 / 8 / 9 characters) | TC-LOG-04, 05, 06 |
| State Transition (lock after 3 attempts) | TC-LOG-07, 08 |
| Equivalence Partitioning (empty fields, invalid email format) | TC-LOG-09, 10, 12 |
| Error Guessing (spaces, SQL injection, script input) | TC-LOG-11, 13, 14 |

### Decision table

| Email correct? | Password correct? | Result |
|---|---|---|
| Yes | Yes | Login succeeds |
| Yes | No | Login fails |
| No | Yes | Login fails |
| No | No | Login fails |

## What I would improve (self-review)

- TC-LOG-01 and TC-LOG-05 use the same account and data, so one of them is redundant.
- TC-LOG-04 lists two acceptable outcomes. After confirming the specification it should have a single expected result.
- TC-LOG-08 depends on TC-LOG-07 (the account must already be locked). The execution order or a separate locked account should be documented.
- Password length boundaries are usually tested at registration or password change, not at login.
