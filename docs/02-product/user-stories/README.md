# User Stories Specification

> Kumpulan user stories diorganisasi berdasarkan Aktor (Traveler, Shopper, Admin).

## Format

```
As a [persona/role],
I want to [action/capability],
So that [benefit/value].
```

## Story Template

Setiap file user story di folder ini mengikuti format:

- **Story ID**: US-[Epic]-[Number]
- **Priority**: Must / Should / Could / Won't
- **Story Points**: 1 / 2 / 3 / 5 / 8 / 13
- **Acceptance Criteria**: Given-When-Then format (Gherkin syntax)

---

## User Stories Index

### 👥 Traveler User Stories (Supply Side)

| File | Story ID | Description | Priority |
| :--- | :--- | :--- | :--- |
| **[create-trip.md](traveler/create-trip.md)** | `US-002-001` | Publish trip details and travel dates | Must Have |
| | `US-002-002` | Manage baggage capacity automatically | Must Have |
| | `US-002-003` | View traveler profile with ratings | Must Have |
| **[review-request.md](traveler/review-request.md)** | `US-005-001` | Track incoming requests and active order list | Must Have |
| **[send-quote.md](traveler/send-quote.md)** | `US-004-001` | Create and send quotation to shopper | Must Have |
| | `US-004-002` | Auto-expire quote after 24 hours | Must Have |
| | `US-004-003` | Receive notification for escrow payment success | Must Have |
| | `US-005-005` | Sourcing & mark as purchased with optional receipt | Must Have |

### 👥 Shopper User Stories (Demand Side)

| File | Story ID | Description | Priority |
| :--- | :--- | :--- | :--- |
| **[submit-request.md](shopper/submit-request.md)** | `US-001-001` | User registration via Google OAuth or OTP | Must Have |
| | `US-001-002` | User login validation | Must Have |
| | `US-003-001` | Submit structured product request on trip page | Must Have |
| **[pay-order.md](shopper/pay-order.md)** | `US-006-001` | Pay and fund the quote via escrow gateway | Must Have |
| **[confirm-delivery.md](shopper/confirm-delivery.md)** | `US-005-002` | Confirm receipt and release escrow funds | Must Have |
| | `US-005-003` | Submit traveler review and rating | Must Have |

### ⚙️ Admin User Stories (Operations)

| File | Story ID | Description | Priority |
| :--- | :--- | :--- | :--- |
| **[review-dispute.md](admin/review-dispute.md)** | `US-005-004` | Monitor transaction metrics and trigger override refunds | Must Have |
