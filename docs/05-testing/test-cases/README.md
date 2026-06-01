# Test Cases

> Kasus pengujian terperinci per modul.

## Naming Convention

File: `tc-[module]-[feature].md`

## Test Case Index

| ID | Module | Feature | Type | Priority | Status |
|----|--------|---------|------|----------|--------|
| TC-AUTH-001 | Auth | Registration | E2E | Critical | ⬜ |
| TC-AUTH-002 | Auth | Login | E2E | Critical | ⬜ |
| TC-AUTH-003 | Auth | Password Reset | E2E | High | ⬜ |
| TC-ORDER-001 | Order | Create Order | E2E | Critical | ⬜ |
| TC-ORDER-002 | Order | Cancel Order | E2E | High | ⬜ |
| TC-PAY-001 | Payment | Process Payment | E2E | Critical | ⬜ |
| TC-PAY-002 | Payment | Refund | E2E | High | ⬜ |

## Test Case Template

```markdown
# TC-[MODULE]-[NUMBER]: [Title]

**Priority**: Critical / High / Medium / Low
**Type**: Unit / Integration / E2E
**Status**: ⬜ Not Run / ✅ Pass / ❌ Fail

## Preconditions
- 

## Test Steps
| Step | Action | Expected Result | Actual Result | Status |
|------|--------|----------------|---------------|--------|
| 1 | | | | |
| 2 | | | | |

## Test Data
- 

## Notes
- 
```
