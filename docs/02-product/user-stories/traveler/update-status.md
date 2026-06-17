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

## US-005-005: Update Sourcing and Processing Status

**As a** Traveler,
**I want to** manually update my request status when I accept the request and when I start sourcing/delivering it,
**So that** the shopper is kept informed of the request progress.

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

Scenario: Mark request as processing
  Given I am logged in as a Traveler
  And my request status is "Accepted"
  When I click "Update to Processing" to indicate I am sourcing/shipping the item
  Then the request status should change to "Processing"
```
