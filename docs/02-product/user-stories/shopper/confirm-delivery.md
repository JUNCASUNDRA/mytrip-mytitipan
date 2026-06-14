---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/user-stories/ep-005-order-management.md
outputs:
  - shopper-delivery-stories
depends_on:
  - state-machine.md
---

# Shopper User Stories - Delivery Confirmation & Reviews

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document captures the user stories related to shoppers confirming delivery, triggering traveler payouts, and submitting reviews/ratings.

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
