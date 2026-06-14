---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/user-stories/ep-002-trip-planner.md
outputs:
  - traveler-trip-stories
depends_on:
  - state-machine.md
---

# Traveler User Stories - Trip Creation & Profile

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document captures the user stories related to trip publication, baggage capacity setup, and public profiles for travelers.

---

## US-002-001: Publish Trip

**As a** Traveler,
**I want to** publish my upcoming trip details (destination, travel dates, available capacity),
**So that** shoppers can know when and where I am traveling and submit requests.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Successful trip publication
  Given I am logged in as a Traveler
  When I navigate to "Create Trip"
  And I enter a valid Destination (e.g., Tokyo)
  And I enter valid departure and return dates (must be in the future)
  And I set my initial baggage capacity
  And I click "Publish"
  Then the trip should be registered in the system with status "Open"
  And the system should generate a unique shareable link (e.g., mytrip.com/t/budi-tokyo-24)
  And I should see a success message with a copyable link

Scenario: Attempt trip publication with invalid dates
  Given I am logged in as a Traveler
  When I attempt to publish a trip with dates in the past
  Then the system should display a validation error "Dates cannot be in the past"
  And the trip should not be published
```

---

## US-002-002: Baggage Capacity Management

**As a** Traveler,
**I want to** manage my trip baggage capacity through automated reservations and locks,
**So that** I do not exceed my physical luggage limits.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Temporary capacity reservation when quotation is sent
  Given a Traveler has a trip open with 15kg remaining capacity
  And a Shopper submits a request for a 2kg item
  When the Traveler creates and sends a Quote to the Shopper
  Then the system should temporarily subtract 2kg from "available capacity"
  And add 2kg to "reserved capacity"
  And the quote is set to expire in 24 hours

Scenario: Capacity lock on successful payment
  Given an order has 2kg in "reserved capacity" status
  When the Shopper completes payment within the 24-hour window
  Then the system should convert the 2kg from "reserved capacity" to "locked capacity"
  And confirm the capacity deduction as final

Scenario: Trip automatically closes when capacity is full
  Given a Traveler's trip has 1kg remaining capacity
  And the Traveler sends a Quote for a 1.5kg item
  When the Shopper pays for the quote, locking the capacity
  Then the trip's available capacity should fall to 0 (or negative)
  And the system should change the Trip status to "Full"
  And new product request submissions for this trip link should be disabled
```

---

## US-002-003: Public Traveler Profile

**As a** Shopper,
**I want to** view a traveler's profile page containing their transaction stats and reviews,
**So that** I can assess their trustworthiness and reliability before paying.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: View traveler profile via shareable link
  Given I click a shared traveler trip link
  When the page loads in my browser
  Then I should see the Traveler's Profile Card showing:
    | Detail | Expected Output |
    | Name & Photo | Traveler's registered name and avatar |
    | Completed Trips | Total count of finalized trips |
    | Completed Orders | Total count of successfully paid/delivered orders |
    | Ratings & Reviews | Star rating average and text feedback history |
  And I should see the Trip destination, travel dates, and status (Open / Limited / Full)
```
