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

# Traveler User Stories - Trip Creation & Profile

> **Status**: Approved **Last Updated**: 2026-06-14

This document captures the user stories related to trip publication and public profiles for travelers under Phase 1.

---

## US-002-001: Publish Trip

**As a** Traveler,
**I want to** publish my upcoming trip details (destination, travel dates, optional baggage notes),
**So that** shoppers can know when and where I am traveling and submit product requests.

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
  And I enter optional baggage notes (e.g., "Max 5kg space left, preferring cosmetics")
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

## US-002-003: Public Traveler Profile

**As a** Shopper,
**I want to** view a traveler's trip page containing their active requests, trip history, completion records, and reviews,
**So that** I can assess their trustworthiness and reliability before coordinating with them.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: View traveler trip page via shareable link
  Given I click a shared traveler trip link
  When the page loads in my browser
  Then I should see the Traveler's Profile Card showing:
    | Detail | Expected Output |
    | Name & Photo | Traveler's registered name and avatar |
    | Trip History | List and count of past completed trips |
    | Request Completion History | List and count of successfully completed shopper requests |
    | Ratings & Reviews | Star rating average and text feedback history |
  And I should see the Trip destination, travel dates, optional baggage notes, and active shopper requests
```
