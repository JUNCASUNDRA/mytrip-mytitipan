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

# Traveler User Stories - Request Status Updates

> **Status**: Approved **Last Updated**: 2026-06-14

This document captures the traveler stories related to manually advancing request statuses.

---

## US-005-005: Update Progress and Delivery Status

**As a** Traveler,
**I want to** manually update the request status as I progress through sourcing and delivery,
**So that** the shopper is kept informed of the request state.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Accept incoming request
  Given I am logged in as a Traveler
  And my request status is "Requested"
  When I click "Accept Request"
  Then the request status should change to "Accepted"
  And the shopper should see the updated status on their dashboard

Scenario: Mark request as in progress
  Given I am logged in as a Traveler
  And my request status is "Accepted"
  When I click "Update Progress" to indicate I am sourcing or coordinating the item
  Then the request status should change to "In Progress"

Scenario: Mark request as ready for delivery
  Given I am logged in as a Traveler
  And my request status is "In Progress"
  When I click "Mark Ready" to indicate sourcing is complete
  Then the request status should change to "Ready for Delivery"

Scenario: Hand over item to complete request
  Given I am logged in as a Traveler
  And my request status is "Ready for Delivery"
  When I click "Hand Over Item"
  Then the request status should change to "Completed"
```
