# 🧪 Testing Documentation

## Purpose

Stores quality assurance strategies, release test plans, detailed functional test cases, and QA verification reports.

## Rules

- **Core Transactions Priority:** Focus major test scenarios on critical transaction flows (escrow payment, escrow release, delivery confirmation, and order cancellations).
- **Testing Pyramid:** Ensure a healthy test distribution: maximize Unit Tests (for speed and isolation), followed by Integration Tests, and limit E2E Tests to critical user paths.
- **User Story Alignment:** Every written Test Case must map back to the Acceptance Criteria defined in the product User Stories.
- **Continuous Validation:** Integrate unit and integration tests into the CI/CD pipeline to run automatically on every Pull Request.

---

## Document Index

| # | Document | Description |
|---|----------|-------------|
| 1 | [Test Strategy](test-strategy.md) | Quality assurance approach and testing methodologies |
| 2 | [Test Plan](test-plan.md) | Release-specific QA schedules and scopes |
| 3 | [Test Cases](test-cases/) | Detailed functional test scenario logs |

---

## Testing Pyramid

```
          ╱╲
         ╱  ╲
        ╱ E2E╲          Few, slow, expensive
       ╱──────╲
      ╱        ╲
     ╱Integration╲      Moderate
    ╱──────────────╲
   ╱                ╲
  ╱    Unit Tests    ╲   Many, fast, cheap
 ╱────────────────────╲
```

---

## Test Types & Location

| Type | Location | Runs On | Coverage Target |
|------|----------|---------|----------------|
| Unit | `apps/*/tests/unit/` | Every commit | > 80% |
| Integration | `apps/*/tests/integration/` | Every PR | > 60% |
| E2E | `apps/*/tests/e2e/` | Pre-deploy | Critical user flows |
| Performance | `apps/*/tests/performance/` | Weekly | SLA latency targets |
| Security | CI/CD pipeline | Every PR | OWASP Top 10 vulnerabilities |

---

## Relationship to Other Docs

- **← Product**: User Stories → Test Cases (acceptance criteria)
- **← Technical**: API Spec → API Tests
- **→ CI/CD**: Test results → Deployment gate
