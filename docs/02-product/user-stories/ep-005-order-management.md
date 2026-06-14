---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/flows/transaction-flow.md
---

# Epic 005: Order & Admin Management

> **Status**: 📝 Draft
> **Sprint**: TBD

---

## US-005-001: Order Tracking Dashboard

**As a** User (Shopper/Traveler),
**I want to** track my order through all lifecycle stages on a unified dashboard,
**So that** I know exactly what state my transaction is in.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: View order tracking history
  Given I am logged in as a Shopper or Traveler
  When I open the dashboard and click on a specific order
  Then I should see a visual tracking timeline showing:
    | State | Active Indicator | Description |
    | Requested | Yes | Shopper submitted request |
    | Quoted | Yes | Traveler sent quote |
    | Payment Pending | Yes | Checkout is open (24h window) |
    | Paid | Yes | Escrow funded by shopper |
    | Purchasing | Yes | Traveler is procurement processing |
    | Purchased | Yes | Traveler bought item abroad |
    | In Transit | Yes | Domestic tracking number exists |
    | Delivered | Yes | Shopper confirmed receipt |
    | Completed | Yes | Payout completed to Traveler |
  And if the order was cancelled, I should see "Cancelled" status
  And if the payment window expired, I should see "Expired" status
```

---

## US-005-002: Delivery Confirmation & Payout Trigger

**As a** Shopper,
**I want to** confirm receipt of my item upon delivery,
**So that** the platform releases the escrow funds to the traveler's bank account.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Manual shopper delivery confirmation releases escrow
  Given an order is in status "In Transit"
  And I am logged in as the Shopper
  When I click "Confirm Receipt"
  Then the order status should change to "Delivered"
  And the platform should trigger a payout process to release escrow funds to the Traveler
  And upon successful payout, the status should change to "Completed"

Scenario: Automated escrow release after 7 days
  Given an order has been marked "In Transit" for exactly 7 days
  And the Shopper has not clicked "Confirm Receipt"
  When the 7-day auto-completion window closes
  Then the system should automatically change the status to "Completed"
  And release the escrow funds to the Traveler
```

---

## US-005-003: Reviews & Ratings System

**As a** Shopper,
**I want to** submit a written review and rating for the traveler after receiving my item,
**So that** I can build platform trust and help future shoppers assess the traveler.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Submit review successfully
  Given my order status is "Completed"
  And I am logged in as the Shopper
  When I navigate to the feedback form
  And I select a rating of "5 Stars"
  And I write a text review: "Great service, item arrived in perfect condition!"
  And I click "Submit Review"
  Then the review should be saved in the database
  And the review should be publicly visible on the Traveler's profile page
  And the Traveler's aggregate star rating should be updated
```

---

## US-005-004: Admin Dashboard

**As an** Admin,
**I want to** monitor active trips, transaction values, and order lifecycles in a central dashboard,
**So that** I can oversee operations and handle customer support requests.

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
```

---

## US-005-005: Procure & Purchase Item

**As a** Traveler,
**I want to** update my order status when I start procurement and upload optional receipts/photos when the item is purchased,
**So that** the shopper is kept informed and trusts the purchase validity.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Start procurement transitions status to Purchasing
  Given I am logged in as a Traveler
  And my order status is "Paid"
  When I click "Start Purchasing"
  Then the order status should change to "Purchasing"

Scenario: Mark purchased with optional receipt upload
  Given my order status is "Purchasing"
  And I am logged in as the Traveler
  When I upload a photo of the receipt or item (optional)
  And I click "Mark as Purchased"
  Then the order status should change to "Purchased"
```

---

> **Total Story Points**: 25
> **Related Use Cases**: [UC-008](use-cases/use-case-specifications.md#uc-008-track-order-status), [UC-010](use-cases/use-case-specifications.md#uc-010-confirm-delivery), [UC-011](use-cases/use-case-specifications.md#uc-011-submit-review--rating), [UC-012](use-cases/use-case-specifications.md#uc-012-monitor-transactions--trips), [UC-016](use-cases/use-case-specifications.md#uc-016-procure-&--purchase-item)
