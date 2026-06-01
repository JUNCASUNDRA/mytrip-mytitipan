# Database Design

> **Status**: 📝 Draft
> **Last Updated**: YYYY-MM-DD
> **Database**: PostgreSQL

---

## 1. Entity Relationship Diagram

```mermaid
erDiagram
    USER ||--o{ ORDER : places
    USER ||--o{ REVIEW : writes
    USER {
        uuid id PK
        string email UK
        string password_hash
        string name
        string phone
        string avatar_url
        enum role
        timestamp created_at
        timestamp updated_at
    }

    ORDER ||--|{ ORDER_ITEM : contains
    ORDER ||--o| PAYMENT : has
    ORDER {
        uuid id PK
        uuid user_id FK
        enum status
        decimal total_amount
        text notes
        timestamp created_at
        timestamp updated_at
    }

    ORDER_ITEM {
        uuid id PK
        uuid order_id FK
        string name
        int quantity
        decimal price
    }

    PAYMENT {
        uuid id PK
        uuid order_id FK
        enum method
        enum status
        decimal amount
        string transaction_id
        timestamp paid_at
    }

    REVIEW {
        uuid id PK
        uuid user_id FK
        uuid order_id FK
        int rating
        text comment
        timestamp created_at
    }

    NOTIFICATION {
        uuid id PK
        uuid user_id FK
        string title
        text body
        enum type
        boolean is_read
        timestamp created_at
    }
```

## 2. Table Specifications

### users

| Column | Type | Constraints | Description |
|--------|------|------------|-------------|
| id | UUID | PK, DEFAULT gen_random_uuid() | |
| email | VARCHAR(255) | UNIQUE, NOT NULL | |
| password_hash | VARCHAR(255) | NOT NULL | bcrypt hash |
| name | VARCHAR(100) | NOT NULL | |
| phone | VARCHAR(20) | UNIQUE | |
| avatar_url | TEXT | NULLABLE | |
| role | ENUM | DEFAULT 'user' | user, admin, provider |
| email_verified_at | TIMESTAMP | NULLABLE | |
| created_at | TIMESTAMP | DEFAULT NOW() | |
| updated_at | TIMESTAMP | DEFAULT NOW() | |

### Indexes

```sql
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_role ON users(role);
CREATE INDEX idx_orders_user_id ON orders(user_id);
CREATE INDEX idx_orders_status ON orders(status);
CREATE INDEX idx_orders_created_at ON orders(created_at);
```

## 3. Migration Strategy

| Version | Description | Status |
|---------|-------------|--------|
| 001 | Create users table | ⬜ |
| 002 | Create orders & order_items tables | ⬜ |
| 003 | Create payments table | ⬜ |
| 004 | Create reviews table | ⬜ |
| 005 | Create notifications table | ⬜ |

## 4. Data Policies

| Policy | Detail |
|--------|--------|
| Backup | Daily automated, 30-day retention |
| Encryption | AES-256 at rest, TLS in transit |
| PII Handling | Hashed passwords, encrypted sensitive data |
| Retention | User data deleted 30 days after account deletion |
| Soft Delete | All tables use `deleted_at` column |

---

> **Input dari**: [System Architecture](system-architecture.md), [PRD](../02-product/prd.md)
> **Output ke**: [API Specification](api-specification/), Backend implementation
