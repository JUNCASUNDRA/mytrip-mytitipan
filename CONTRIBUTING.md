# Contributing Guide

> Panduan kontribusi untuk tim pengembangan.

## 🌿 Branch Strategy (Git Flow)

```
main ──────────────────────────────────────── Production
  │
  └── staging ─────────────────────────────── Pre-production
        │
        └── develop ───────────────────────── Integration
              │
              ├── feature/auth-login ──────── Feature branch
              ├── feature/order-create ────── Feature branch
              └── bugfix/payment-error ────── Bugfix branch
```

### Branch Naming

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/[ticket-id]-description` | `feature/MT-123-user-login` |
| Bugfix | `bugfix/[ticket-id]-description` | `bugfix/MT-456-payment-error` |
| Hotfix | `hotfix/[ticket-id]-description` | `hotfix/MT-789-critical-fix` |
| Release | `release/v[version]` | `release/v1.0.0` |

## 📝 Commit Convention

Format: `type(scope): description`

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation |
| `style` | Code style (formatting, semicolons) |
| `refactor` | Code refactoring |
| `test` | Adding tests |
| `chore` | Maintenance tasks |
| `perf` | Performance improvement |
| `ci` | CI/CD changes |

Examples:
```
feat(auth): add Google OAuth login
fix(payment): handle timeout error in payment gateway
docs(api): update auth endpoint documentation
test(order): add unit tests for order creation
```

## 🔄 Pull Request Process

1. Create branch from `develop`
2. Implement changes
3. Write/update tests
4. Update documentation
5. Self-review your code
6. Create PR with description template
7. Request review from 2 team members
8. Address review comments
9. Merge after approval

### PR Template

```markdown
## Description
[What does this PR do?]

## Type of Change
- [ ] New feature
- [ ] Bug fix
- [ ] Documentation
- [ ] Refactoring
- [ ] Other

## Related Issues
Closes #[issue-number]

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] Manual testing performed

## Checklist
- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] No new warnings
```

## 📏 Code Standards

| Aspect | Standard |
|--------|----------|
| Language | TypeScript (strict mode) |
| Linting | ESLint + Prettier |
| Testing | Jest, min 80% coverage |
| Naming | camelCase (vars), PascalCase (classes/types) |
| Documentation | JSDoc for public APIs |
| Error Handling | Custom error classes, never throw raw strings |
