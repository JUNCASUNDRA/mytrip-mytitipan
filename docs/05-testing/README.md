# 🧪 Testing Documentation

> Strategi, rencana, dan kasus pengujian.

## Document Index

| # | Document | Description |
|---|----------|-------------|
| 1 | [Test Strategy](test-strategy.md) | Pendekatan dan metodologi testing |
| 2 | [Test Plan](test-plan.md) | Rencana testing per release |
| 3 | [Test Cases](test-cases/) | Kasus uji terperinci |

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

## Test Types & Location

| Type | Location | Runs On | Coverage Target |
|------|----------|---------|----------------|
| Unit | `apps/*/tests/unit/` | Every commit | > 80% |
| Integration | `apps/*/tests/integration/` | Every PR | > 60% |
| E2E | `apps/*/tests/e2e/` | Pre-deploy | Critical paths |
| Performance | `apps/*/tests/performance/` | Weekly | SLA targets |
| Security | CI/CD pipeline | Every PR | OWASP Top 10 |

## Relationship to Other Docs

- **← Product**: User Stories → Test Cases (acceptance criteria)
- **← Technical**: API Spec → API Tests
- **→ CI/CD**: Test results → Deployment gate
