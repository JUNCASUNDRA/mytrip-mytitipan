---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/flows/transaction-flow.md
---

# Epic 004: Quotation & Expiry

> **Status**: 📝 Draft
> **Sprint**: TBD

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

## US-004-003: Email Notifications

**As a** User (Traveler/Shopper),
**I want to** receive automated email notifications when key transaction milestones are reached,
**So that** I am immediately informed of changes without manually polling the web app.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 3 |

### Acceptance Criteria

```gherkin
Scenario: Shopper receives notification of incoming quote
  Given a Traveler sends a Quote for "Tokyo Banana Classic"
  Then the Shopper should receive a notification containing the price breakdown and direct link to fund escrow

Scenario: Traveler receives notification of successful payment
  Given a Shopper completes payment for a quote
  Then the Traveler should receive a notification stating: "Payment Received. You are safe to purchase Tokyo Banana Classic."

Scenario: Shopper receives notification of shipment
  Given a Traveler marks an order as "In Transit" and inputs a tracking number
  Then the Shopper should receive a notification with the tracking details and courier link
```

---

> **Total Story Points**: 13
> **Related Use Cases**: [UC-005](use-cases/use-case-specifications.md#uc-005-create--send-quotation), [UC-013](use-cases/use-case-specifications.md#uc-013-auto-expire-quote--release-capacity), [UC-014](use-cases/use-case-specifications.md#uc-014-send-email-notification)
