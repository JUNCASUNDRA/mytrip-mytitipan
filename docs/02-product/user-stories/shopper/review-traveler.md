---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-1
status: approved
priority: must-have
depends_on:
  - docs/02-product/flows/core-user-flow.md
outputs:
  - ux-flow
  - technical-requirement
---

# Shopper User Stories - Delivery Confirmation & Reviews

> **Status**: Approved **Last Updated**: 2026-06-14

This document captures the shopper stories related to confirming delivery and leaving traveler feedback reviews.

---

## US-005-002: Delivery Confirmation

**As a** Shopper,
**I want to** confirm receipt of my item upon delivery,
**So that** the traveler knows I have received the product and the request lifecycle is complete.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Manual shopper delivery confirmation
  Given a request is in status "Processing"
  And I am logged in as the Shopper
  When I click "Confirm Receipt"
  Then the request status should change to "Completed"
  And the traveler should see the updated status on their dashboard
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
  Given my request status is "Completed"
  And I am logged in as the Shopper
  When I navigate to the feedback form for this request
  And I select a rating of "5 Stars"
  And I write a text review: "Great service, item arrived in perfect condition!"
  And I click "Submit Review"
  Then the review should be saved in the database
  And the request status changes to "Reviewed"
  And the review should be publicly visible on the Traveler's profile page
  And the Traveler's aggregate star rating should be updated
```

---

## US-005-006: Request Timeline Viewer (Shopper)

**As a** Shopper,
**I want to** view a chronological status history log of my request,
**So that** I can track the traveler's coordination progress transparently.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Shopper views request timeline history
  Given my request is in status "Processing"
  When I navigate to my request details page
  Then I should see a chronological Request Timeline showing:
    | Timestamp | Event | Action Taken |
    | 2026-06-14 10:00 | Requested | Shopper submitted the request form |
    | 2026-06-14 14:00 | Accepted | Traveler accepted the request |
    | 2026-06-14 18:00 | Processing | Traveler updated status to processing |
```
