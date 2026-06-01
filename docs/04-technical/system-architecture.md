# System Architecture

> **Status**: 📝 Draft
> **Last Updated**: YYYY-MM-DD
> **Architect**: [Nama]

---

## 1. Architecture Overview

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                          CLIENTS                                     │
│  ┌──────────┐  ┌──────────┐                                         │
│  │ Web App  │  │ Admin    │                                         │
│  │ (React)  │  │ Panel    │                                         │
│  └────┬─────┘  └────┬─────┘                                         │
└───────┼──────────────┼──────────────────────────────────────────────┘
        │              │
        ▼              ▼              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                     API GATEWAY / LOAD BALANCER                      │
│                    (Nginx / Kong / AWS ALB)                          │
└────────────────────────────┬────────────────────────────────────────┘
                             │
        ┌────────────────────┼────────────────────┐
        ▼                    ▼                    ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│  Auth        │  │  Core        │  │  Notification│
│  Service     │  │  Service     │  │  Service     │
│              │  │              │  │              │
│  - Login     │  │  - Orders    │  │  - Push      │
│  - Register  │  │  - Search    │  │  - Email     │
│  - OAuth     │  │  - Payment   │  │  - SMS       │
└──────┬───────┘  └──────┬───────┘  └──────┬───────┘
       │                 │                 │
       ▼                 ▼                 ▼
┌─────────────────────────────────────────────────────────────────────┐
│                        DATA LAYER                                    │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐           │
│  │PostgreSQL│  │  Redis   │  │   S3     │  │Elastic   │           │
│  │(Primary) │  │ (Cache)  │  │(Storage) │  │(Search)  │           │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘           │
└─────────────────────────────────────────────────────────────────────┘
```

## 2. Architecture Principles

| Principle | Description |
|-----------|-------------|
| **Clean Architecture** | Domain-centric, framework-independent |
| **Separation of Concerns** | Each layer has single responsibility |
| **Dependency Inversion** | Depend on abstractions, not concretions |
| **12-Factor App** | Cloud-native application methodology |
| **API-First** | Design APIs before implementation |
| **Event-Driven** | Async communication between services |

## 3. Clean Architecture Layers

```
┌─────────────────────────────────┐
│         Presentation            │  ← Controllers, Routes, Views
├─────────────────────────────────┤
│         Application             │  ← Use Cases, DTOs, Mappers
├─────────────────────────────────┤
│           Domain                │  ← Entities, Value Objects, Interfaces
├─────────────────────────────────┤
│        Infrastructure           │  ← Database, External APIs, Cache
└─────────────────────────────────┘

Dependency Rule: Inner layers NEVER depend on outer layers
```

### Layer Responsibilities

| Layer | Responsibility | Example |
|-------|---------------|---------|
| **Presentation** | Handle HTTP, format responses | Express routes, React components |
| **Application** | Orchestrate use cases | CreateOrderUseCase, AuthenticateUserUseCase |
| **Domain** | Business rules & entities | User, Order, Payment entities |
| **Infrastructure** | External concerns | PostgreSQL repo, Redis cache, S3 storage |

## 4. Data Flow

```
Request → Route → Controller → Use Case → Domain Service → Repository → Database
                                                                          │
Response ← Presenter ← Use Case ← Domain Service ← Repository ◄─────────┘
```

## 5. Communication Patterns

| Pattern | Use Case | Technology |
|---------|----------|-----------|
| Synchronous REST | Client ↔ API | HTTP/HTTPS |
| WebSocket | Real-time updates | Socket.io |
| Message Queue | Async processing | RabbitMQ |
| Event Bus | Service-to-service | Redis Pub/Sub |

## 6. Scalability Strategy

| Component | Strategy | Target |
|-----------|----------|--------|
| API | Horizontal scaling (containers) | Auto-scale based on CPU |
| Database | Read replicas + Connection pooling | 10k concurrent |
| Cache | Redis Cluster | Sub-ms latency |
| Storage | CDN + Object Storage | Global distribution |
| Search | Elasticsearch cluster | < 100ms queries |

## 7. Technology Decision Records (ADR)

| ID | Decision | Status | Date |
|----|----------|--------|------|
| ADR-001 | Use PostgreSQL over MongoDB | Accepted | |
| ADR-002 | Use Clean Architecture | Accepted | |
| ADR-003 | Monorepo over Polyrepo | Accepted | |
| ADR-004 | REST API over GraphQL (MVP) | Accepted | |

---

> **Input dari**: [PRD](../02-product/prd.md), [Business Flow TO-BE](../01-business/04-business-flow/to-be.md)
> **Output ke**: [Database Design](database-design.md), [API Specification](api-specification/), Source Code
