# 🔧 Technical Documentation

> Arsitektur sistem, spesifikasi API, desain database, dan dokumentasi teknis lainnya.

## Document Index

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 1 | [System Architecture](system-architecture.md) | 📝 Draft | Arsitektur sistem keseluruhan |
| 2 | [Database Design](database-design.md) | 📝 Draft | Schema, ERD, dan migrasi |
| 3 | [API Specification](api-specification/) | 📝 Draft | REST/GraphQL API docs |
| 4 | [Security Design](security-design.md) | 📝 Draft | Keamanan dan compliance |
| 5 | [Sequence Diagrams](sequence-diagrams/) | 📝 Draft | Interaksi antar service |
| 6 | [Deployment Architecture](deployment-architecture.md) | 📝 Draft | Infrastructure & deployment |

## Reading Order

```
System Architecture → Database Design → API Specification
→ Security Design → Sequence Diagrams → Deployment Architecture
```

## Tech Stack Overview

| Layer | Technology | Reason |
|-------|-----------|--------|
| Frontend | React / Next.js | SSR, SEO, ecosystem |
| Backend | Node.js / Go | Performance, ecosystem |
| Database | PostgreSQL | ACID, reliability |
| Cache | Redis | Performance |
| Queue | RabbitMQ / Kafka | Async processing |
| Storage | S3 / GCS | File storage |
| Search | Elasticsearch | Full-text search |
| Auth | JWT + OAuth 2.0 | Industry standard |
| CI/CD | GitHub Actions | Automation |
| Cloud | GCP / AWS | Scalability |

## Relationship to Other Docs

- **← Product**: PRD & Use Cases → System Architecture
- **← Design**: Design System → Frontend Components
- **→ Infrastructure**: Deployment Architecture → Docker configs
- **→ Source Code**: All tech docs guide implementation in `apps/` and `packages/`
