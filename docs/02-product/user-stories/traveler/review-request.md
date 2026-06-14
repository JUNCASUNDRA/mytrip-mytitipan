---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/user-stories/ep-005-order-management.md
outputs:
  - traveler-review-stories
depends_on:
  - state-machine.md
---

# Traveler User Stories - Review Request & Order Tracking

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document captures the user stories related to travelers tracking active requests, reviewing product request details, and managing orders.

---

## US-005-001: Traveler Order Tracking Dashboard

**As a** Traveler,
**I want to** track my incoming requests and paid orders through all lifecycle stages on a unified dashboard,
**So that** I know exactly which requests to review, which ones are paid, and their current fulfillment state.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Traveler views order list dashboard
  Given I am logged in as a Traveler
  When I open the traveler dashboard
  Then I should see my orders grouped by active status categories:
    | Category | Description |
    | Requests | Incoming shopper requests in status "Requested" |
    | Unpaid Quotes | Active quotes in status "Quoted" or "Payment Pending" |
    | To Purchase | Paid requests in status "Paid" or "Purchasing" |
    | Shipped | Items in status "Purchased" or "In Transit" |
    | Completed | Completed orders in status "Completed"

Scenario: Traveler tracks details of a specific order
  Given I am logged in as a Traveler
  When I select a specific active order on my dashboard
  Then I should see the unified tracking timeline showing:
    | State | Description |
    | Requested | Shopper submitted request |
    | Quoted | Traveler sent quote |
    | Payment Pending | Checkout is open (24h window) |
    | Paid | Escrow funded by shopper |
    | Purchasing | Traveler is procurement processing |
    | Purchased | Traveler bought item abroad |
    | In Transit | Domestic tracking number exists |
    | Delivered | Shopper confirmed receipt |
    | Completed | Payout completed to Traveler
  And if the order was cancelled, I should see the "Cancelled" status
  And if the payment window expired, I should see the "Expired" status
```
