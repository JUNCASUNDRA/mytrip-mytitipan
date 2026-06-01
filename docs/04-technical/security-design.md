# Security Design

> **Status**: 📝 Draft
> **Last Updated**: YYYY-MM-DD

---

## 1. Security Architecture

```
┌─────────────────────────────────────────────────┐
│                 SECURITY LAYERS                   │
├─────────────────────────────────────────────────┤
│  WAF (Web Application Firewall)                  │
├─────────────────────────────────────────────────┤
│  DDoS Protection (Cloudflare / AWS Shield)       │
├─────────────────────────────────────────────────┤
│  SSL/TLS Termination                             │
├─────────────────────────────────────────────────┤
│  API Gateway (Rate Limiting, Auth)               │
├─────────────────────────────────────────────────┤
│  Application Security (Input Validation, OWASP)  │
├─────────────────────────────────────────────────┤
│  Data Security (Encryption, Access Control)      │
└─────────────────────────────────────────────────┘
```

## 2. Authentication & Authorization

| Aspect | Implementation |
|--------|---------------|
| Auth Protocol | OAuth 2.0 + JWT |
| Token Type | Access Token (15min) + Refresh Token (7d) |
| Password Hashing | bcrypt (cost factor 12) |
| MFA | TOTP (Google Authenticator) - optional |
| Session Management | Stateless JWT + Redis blacklist |
| RBAC | Role-Based Access Control |

### Roles & Permissions

| Permission | User | Provider | Admin |
|-----------|------|----------|-------|
| View own profile | ✅ | ✅ | ✅ |
| Edit own profile | ✅ | ✅ | ✅ |
| Place order | ✅ | ❌ | ✅ |
| Manage orders | ❌ | ✅ | ✅ |
| View all users | ❌ | ❌ | ✅ |
| System settings | ❌ | ❌ | ✅ |

## 3. OWASP Top 10 Mitigation

| Risk | Mitigation |
|------|-----------|
| Injection | Parameterized queries, ORM |
| Broken Auth | JWT + secure session management |
| Sensitive Data Exposure | AES-256 encryption, TLS 1.3 |
| XXE | Disable XML external entities |
| Broken Access Control | RBAC, middleware guards |
| Security Misconfig | Hardened configs, security headers |
| XSS | Content Security Policy, input sanitization |
| Insecure Deserialization | Input validation, schema enforcement |
| Known Vulnerabilities | Automated dependency scanning |
| Insufficient Logging | Centralized logging, audit trail |

## 4. Data Protection

| Data Type | At Rest | In Transit | Access |
|-----------|---------|-----------|--------|
| Passwords | bcrypt hash | TLS 1.3 | Never exposed |
| PII (email, phone) | AES-256 | TLS 1.3 | Authenticated only |
| Payment data | PCI-DSS compliant | TLS 1.3 | Tokenized |
| Session tokens | Redis (encrypted) | TLS 1.3 | HTTP-only cookies |

## 5. Security Headers

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Content-Security-Policy: default-src 'self'
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=()
```

## 6. Incident Response Plan

| Severity | Response Time | Escalation |
|----------|-------------|------------|
| Critical (data breach) | < 1 hour | CEO, CTO, Legal |
| High (service compromise) | < 4 hours | CTO, DevOps |
| Medium (vulnerability found) | < 24 hours | Security Lead |
| Low (minor issue) | < 72 hours | Dev Team |

---

> **Input dari**: [System Architecture](system-architecture.md)
> **Output ke**: Backend implementation, [Deployment Architecture](deployment-architecture.md)
