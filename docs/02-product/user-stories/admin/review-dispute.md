---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/user-stories/ep-005-order-management.md
outputs:
  - admin-dispute-stories
depends_on:
  - state-machine.md
---

# Admin User Stories - Operations & Disputes

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document captures the user stories related to administrator dashboards, transaction monitoring, and manually overriding statuses for disputes and cancellations.

---

## US-005-004: Admin Dashboard & Override Controls

**As an** Admin,
**I want to** monitor active trips, transaction values, and order lifecycles in a central dashboard, and manually cancel or refund payments,
**So that** I can oversee operations and handle customer support and dispute requests.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Admin accesses dashboard summary
  Given I am logged in as an Administrator
  When I navigate to the Admin Dashboard
  Then I should see operational summaries:
    | Metric | Description |
    | Total Active Trips | Count of open traveler trips |
    | Total Order Volume | Count of all requests (Requested, Paid, Shipped, etc.) |
    | Escrow Holdings | Total value of funds currently held by platform |
  And I should be able to search trips and orders by user ID or transaction ID

Scenario: Admin triggers a refund override
  Given an order is in status "Paid" or "Purchasing" or "Purchased" or "In Transit"
  And the Shopper has filed a dispute or request for cancellation
  When I click "Refund Order" in the Admin Dashboard
  Then the platform should invoke the payment gateway's Refund API
  And upon gateway success, the order status should change to "Refunded"
  And the system should release the associated baggage capacity weight back to the traveler's trip
  And the system should notify both traveler and shopper of the refund
```
