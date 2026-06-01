# Test Plan

> **Status**: 📝 Draft
> **Release**: v1.0 (MVP)
> **Last Updated**: YYYY-MM-DD

---

## 1. Scope

### In Scope

| Module | Test Type | Priority |
|--------|----------|----------|
| Authentication | Unit, Integration, E2E | Critical |
| Order Management | Unit, Integration, E2E | Critical |
| Payment | Unit, Integration, E2E | Critical |
| Search | Unit, Integration | High |
| Profile | Unit, Integration | Medium |
| Notifications | Unit | Medium |

### Out of Scope

- Performance testing (deferred to v1.1)
- Accessibility testing (deferred to v1.1)

## 2. Test Schedule

| Phase | Activity | Duration | Owner |
|-------|---------|----------|-------|
| Sprint N | Write unit tests | Continuous | Dev |
| Sprint N | Write integration tests | Continuous | Dev |
| Pre-release | E2E test execution | 2 days | QA |
| Pre-release | Regression testing | 1 day | QA |
| Pre-release | UAT | 2 days | Product |

## 3. Entry & Exit Criteria

### Entry Criteria

- [ ] Code complete and merged to staging
- [ ] Unit tests passing (> 80% coverage)
- [ ] Test environment available
- [ ] Test data prepared

### Exit Criteria

- [ ] All P0/P1 bugs fixed and verified
- [ ] E2E test suite passing
- [ ] No open critical/high bugs
- [ ] Product owner sign-off
- [ ] Performance within SLA

## 4. Risks & Mitigations

| Risk | Impact | Mitigation |
|------|--------|-----------|
| Delayed development | Testing timeline shift | Parallel test development |
| Environment issues | Blocked testing | Maintain stable test env |
| Test data issues | Incomplete coverage | Automated seed scripts |

---

> **Input dari**: [Test Strategy](test-strategy.md), [PRD](../02-product/prd.md)
