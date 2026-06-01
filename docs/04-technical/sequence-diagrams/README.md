# Sequence Diagrams

> Diagram urutan interaksi antar komponen sistem.

## Diagrams Index

| Diagram | Description | Status |
|---------|-------------|--------|
| User Registration | Alur registrasi user baru | 📝 Draft |
| User Login | Alur autentikasi | ⬜ Todo |
| Place Order | Alur pembuatan order | ⬜ Todo |
| Payment Processing | Alur pembayaran | ⬜ Todo |
| Notification Delivery | Alur pengiriman notifikasi | ⬜ Todo |

## Example: User Registration

```mermaid
sequenceDiagram
    actor User
    participant Client as Web Client
    participant Gateway as API Gateway
    participant Auth as Auth Service
    participant DB as PostgreSQL
    participant Email as Email Service
    participant Cache as Redis

    User->>Client: Fill registration form
    Client->>Gateway: POST /api/v1/auth/register
    Gateway->>Auth: Forward request
    Auth->>Auth: Validate input
    Auth->>DB: Check email exists
    DB-->>Auth: Email not found
    Auth->>Auth: Hash password (bcrypt)
    Auth->>DB: INSERT user
    DB-->>Auth: User created
    Auth->>Cache: Store verification token
    Auth->>Email: Send verification email
    Email-->>User: Verification email
    Auth-->>Gateway: 201 Created + JWT
    Gateway-->>Client: Response
    Client-->>User: Show success + redirect

    Note over User, Cache: Email Verification Flow
    User->>Client: Click verification link
    Client->>Gateway: POST /api/v1/auth/verify-email
    Gateway->>Auth: Forward request
    Auth->>Cache: Validate token
    Cache-->>Auth: Token valid
    Auth->>DB: UPDATE user.email_verified_at
    Auth-->>Client: 200 OK
```

## Example: Place Order

```mermaid
sequenceDiagram
    actor User
    participant Client as Web Client
    participant API as Core Service
    participant Payment as Payment Service
    participant DB as PostgreSQL
    participant Queue as Message Queue
    participant Notif as Notification Service

    User->>Client: Submit order
    Client->>API: POST /api/v1/orders
    API->>API: Validate order data
    API->>DB: CREATE order (status: pending)
    DB-->>API: Order created
    API->>Payment: Create payment intent
    Payment-->>API: Payment URL
    API-->>Client: Order created + payment URL
    Client->>User: Redirect to payment

    User->>Payment: Complete payment
    Payment->>API: Webhook: payment.success
    API->>DB: UPDATE order status = paid
    API->>Queue: Emit: order.paid event
    Queue->>Notif: Process notification
    Notif->>User: Push notification: Order confirmed
```

---

> **Input dari**: [Use Cases](../../02-product/use-cases/), [System Architecture](../system-architecture.md)
> **Output ke**: Backend implementation
