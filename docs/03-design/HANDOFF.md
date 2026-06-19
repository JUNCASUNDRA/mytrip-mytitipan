---
agent: UX Designer Agent (UXA)
version: 1.2.0
date: 2026-06-17
status: Approved
phase: phase-1
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

My Trip My Titipan Phase 1 MVP is a lightweight request tracking and coordination platform.

The goal is NOT to process payments or act as a discovery marketplace.

The platform only helps:
- Travelers publish upcoming trips
- Shoppers submit product requests via shared links
- Travelers manage request progress
- Both parties maintain request history and reputation feedback

The following features are OUT OF SCOPE:
- Payment Gateway / digital escrow
- Checkout screen
- Quotation engine / price calculators
- Capacity lock / reservations
- Admin dashboard panel
- KYC / trust indicators (other than review/trip history logs)
- Courier shipping API integrations

## UX Principles

1. **Reduce Coordination Friction**: Streamline communication from social media shares to structured request fields.
2. **Replace Scattered Chat Records**: Consolidate agreements and logistics into a single tracking log.
3. **Transparent Request Lifecycle**: Establish clear states so both actors understand what comes next.
4. **Build Reputation Through History**: Leverage completed trips and shopper feedback to establish safety/reliability.

## Primary User Flows

### Traveler Flow
1. Login
2. Create Trip
3. Generate Trip Link
4. Share Trip Link
5. Receive Sourcing Request
6. Review Request
7. Accept Request (state: `ACCEPTED`)
8. Update Progress (state: `IN_PROGRESS`)
9. Mark Ready (state: `READY_FOR_DELIVERY`)
10. Hand Over Item (offline payment / handover coordinated directly)
11. Complete (state: `COMPLETED`)
12. Receive Review

### Shopper Flow
1. Open Trip Link
2. View Traveler History, Trips, and Reviews
3. Submit Product Request
4. Wait for Traveler Response
5. Track Request Status
6. Confirm Receipt (state: `COMPLETED`)
7. Submit Review Form

## Status Lifecycle

```
REQUESTED
    ↓
ACCEPTED
    ↓
IN_PROGRESS
    ↓
READY_FOR_DELIVERY
    ↓
COMPLETED
```

Every status has:
- **Owner/Action**: Actor responsible for the next step.
- **Primary CTA**: Button to progress the state.
- **Explanation**: Context showing what state the request is currently in.
- **Next Step**: Expectation of the next stage.

## Screens Required

### Traveler Screens:
1. **SCR-006: Traveler Dashboard**: Overview of active trips, pending incoming requests, and "+ Create Trip" CTA.
2. **SCR-007: Create Trip**: Simple itinerary form.
3. **SCR-008: Trip Share**: Success modal showing share links.
4. **SCR-009: Request Review**: Sourcing request details with Accept/Decline triggers.
5. **SCR-010: Traveler Request Detail**: Progress tracker with state-advancement actions ("Update Progress", "Mark Ready", "Hand Over").

### Shopper Screens:
1. **SCR-002: Trip Landing Page**: Public landing page seen by shoppers clicking shared links. Displays route and traveler history.
2. **SCR-003: Request Form**: Inputs for product details, URLs, quantity, budget, and image.
3. **SCR-004: Shopper Dashboard**: Main view containing the list of active shopper requests.
4. **SCR-005: Request Detail**: Tracking dashboard mapping the request status timeline.
5. **SCR-011: Review Form**: Rating selector and text feedback block.

### Shared Access:
1. **SCR-001: Login**: Authentication portal (Google OAuth or OTP).

## UX States

- **Empty States**: Custom placeholders for "No trips planned", "No pending requests", and "No active coordination".
- **Error States**: Clear inline forms validation and page guards (e.g. invalid trip links, expired trips, unauthorized router blocks).

## Future Compatibility
Do not design user interface elements that block future scale. Leave logical hooks for:
- Payment status badge insertion.
- Price quotation details.
- Baggage weight/size capacities.
- Discovery search tabs.

However, do not expose any of these in Phase 1 wireframes.
