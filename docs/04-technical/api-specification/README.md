# API Specification

> REST API specification mengikuti OpenAPI 3.0 standard.

## Base URL

- Development: `http://localhost:3000/api/v1`
- Staging: `https://api-staging.mytrip-mytitipan.com/v1`
- Production: `https://api.mytrip-mytitipan.com/v1`

## Authentication

All protected endpoints require `Authorization: Bearer <token>` header.

## API Index

| Module | Endpoint Prefix | Spec File | Status |
|--------|----------------|-----------|--------|
| Auth | `/auth` | [auth.yaml](auth.yaml) | 📝 Draft |
| Users | `/users` | [users.yaml](users.yaml) | ⬜ Todo |
| Orders | `/orders` | [orders.yaml](orders.yaml) | ⬜ Todo |
| Payments | `/payments` | [payments.yaml](payments.yaml) | ⬜ Todo |
| Reviews | `/reviews` | [reviews.yaml](reviews.yaml) | ⬜ Todo |
| Notifications | `/notifications` | [notifications.yaml](notifications.yaml) | ⬜ Todo |

## Response Format

### Success Response

```json
{
  "success": true,
  "data": {},
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 100
  }
}
```

### Error Response

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input",
    "details": [
      {
        "field": "email",
        "message": "Email is required"
      }
    ]
  }
}
```

## HTTP Status Codes

| Code | Usage |
|------|-------|
| 200 | Success |
| 201 | Created |
| 204 | No Content (successful delete) |
| 400 | Bad Request (validation error) |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict (duplicate) |
| 422 | Unprocessable Entity |
| 429 | Too Many Requests |
| 500 | Internal Server Error |

## Rate Limiting

| Tier | Limit | Window |
|------|-------|--------|
| Public | 100 req | per minute |
| Authenticated | 500 req | per minute |
| Admin | 1000 req | per minute |

---

> **Input dari**: [Database Design](../database-design.md), [Use Cases](../../02-product/use-cases/)
> **Output ke**: Backend & Frontend implementation
