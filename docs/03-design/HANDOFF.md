---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: draft
phase: phase-1-foundation
depends_on:
  - docs/02-product/planning/phases/phase-1-foundation/scope.md
  - docs/02-product/flows/core-user-flow.md
outputs:
  - user-flow
  - screen-inventory
  - wireframe-requirements
---

# Phase 1 UX Design Specification

## Context

My Trip My Titipan Phase 1 MVP is a lightweight request tracking platform.

The goal is NOT to process transactions.

The platform only helps:
- Travelers publish upcoming trips
- Shoppers submit product requests
- Travelers manage request progress
- Both parties maintain request history and reputation

The following features are OUT OF SCOPE:
- Payment
- Escrow
- Checkout
- Quotation engine
- Capacity reservation
- Admin dashboard
- KYC verification
- Courier API integration


## UX Principles

1. Reduce coordination friction
2. Replace scattered chat records with structured tracking
3. Make request status transparent
4. Build trust through history and reviews


## Primary User Flows

### Traveler Flow

1. Login
2. Create Trip
3. Generate Trip Link
4. Share Trip Link
5. Receive Request
6. Review Request
7. Accept Request
8. Mark Purchased
9. Mark Delivered
10. Complete Request
11. Receive Review


### Shopper Flow

1. Open Trip Link
2. View Traveler Profile
3. Submit Product Request
4. Wait for Traveler Response
5. Track Request Status
6. Confirm Receipt
7. Submit Review


## Status Lifecycle

REQUESTED
↓
ACCEPTED
↓
PURCHASED
↓
DELIVERED
↓
COMPLETED


Every status must have:
- current owner/action
- CTA button
- explanation
- next expected step


## Screens Required

### Traveler:

1. Traveler Dashboard
2. Create Trip
3. Trip Detail Page
4. Incoming Requests
5. Request Detail
6. Active Requests
7. Completed History
8. Profile & Reviews


### Shopper:

1. Trip Landing Page
2. Traveler Profile Preview
3. Submit Request Form
4. Request Detail Tracking
5. Confirm Receipt
6. Review Form


## UX States

Empty states:
- No trips
- No requests
- No active requests

Loading states

Success states

Error states:
- Invalid request
- Trip unavailable
- Completed trip cannot accept requests


## Future Compatibility

Do not design UI that blocks future phases.

Reserve extension points for:
- Payment status
- Quote information
- Capacity status
- Discovery feed

but do not expose these in Phase 1.
