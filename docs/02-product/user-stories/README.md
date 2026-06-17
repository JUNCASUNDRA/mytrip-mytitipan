# User Stories Specification

> Kumpulan user stories diorganisasi berdasarkan Aktor (Traveler, Shopper).

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
| **[publish-trip.md](traveler/publish-trip.md)** | `US-002-001` | Publish trip details, travel dates, and optional notes | Must Have |
| | `US-002-003` | View traveler profile with ratings | Must Have |
| **[view-request.md](traveler/view-request.md)** | `US-005-001` | Track incoming requests on traveler dashboard | Must Have |
| | `US-005-006` | View request status timelines | Must Have |
| **[update-status.md](traveler/update-status.md)** | `US-005-005` | Manually transition request status | Must Have |

### 👥 Shopper User Stories (Demand Side)

| File | Story ID | Description | Priority |
| :--- | :--- | :--- | :--- |
| **[submit-request.md](shopper/submit-request.md)** | `US-001-001` | User registration via Google OAuth or OTP | Must Have |
| | `US-001-002` | User login validation | Must Have |
| | `US-003-001` | Submit structured product request on trip page | Must Have |
| **[review-traveler.md](shopper/review-traveler.md)** | `US-005-002` | Confirm receipt of item | Must Have |
| | `US-005-003` | Submit traveler review and rating | Must Have |
| | `US-005-006` | Track request timelines history logs | Must Have |
