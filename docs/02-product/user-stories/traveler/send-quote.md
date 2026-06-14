---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/user-stories/ep-004-quotation.md
outputs:
  - traveler-quote-stories
depends_on:
  - state-machine.md
---

# Traveler User Stories - Quotation & Procurement

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document captures the user stories related to sending quotes, quote expiry constraints, receiving payment confirmations, and procurement fulfillment.

---

## US-004-001: Create & Send Quotation

**As a** Traveler,
**I want to** send a pricing quote (Item Price + Jastip Fee) in response to a product request,
**So that** the shopper knows the exact cost and can fund the escrow.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Send a quotation successfully
  Given I am logged in as a Traveler
  And I have a request for "Tokyo Banana Classic" in status "Requested"
  When I select the request and enter:
    | Pricing Field | Value |
    | Item Price | IDR 250,000 |
    | Jastip Fee | IDR 100,000 |
    | Estimated Weight | 1.0 kg |
  And I click "Send Quote"
  Then the quote should be registered in the system
  And the order status should change to "Quoted"
  And the platform should temporarily reserve 1.0 kg of my baggage capacity
  And the system should trigger a notification to the Shopper containing the quote details
```

---

## US-004-002: Quote Expiry & Capacity Release

**As a** Traveler,
**I want** unpaid quotes to automatically expire after 24 hours and release their reserved capacity,
**So that** my baggage capacity is not locked indefinitely by non-responsive shoppers.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Automatic expiration of unpaid quotes
  Given a quotation was sent 24 hours ago
  And the order status is currently "Quoted" or "Payment Pending" (unpaid)
  And 1.0 kg baggage capacity is currently in "reserved capacity" status for this quote
  When the 24-hour payment window closes
  Then the system should change the status to "Expired"
  And the system should remove the 1.0 kg from "reserved capacity" and add it back to "available capacity"
  And the system should notify both the Traveler and Shopper that the quote has expired
```

---

## US-004-003: Traveler Payment Notification

**As a** Traveler,
**I want to** receive automated notifications when a shopper completes payment for my quote,
**So that** I know it is safe to proceed with purchasing the item.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 3 |

### Acceptance Criteria

```gherkin
Scenario: Traveler receives notification of successful payment
  Given a Shopper completes payment for a quote
  Then the Traveler should receive a notification stating: "Payment Received. You are safe to purchase Tokyo Banana Classic."
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
