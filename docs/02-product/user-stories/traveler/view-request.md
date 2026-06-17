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

# Traveler User Stories - View Requests & Timeline

> **Status**: Approved **Last Updated**: 2026-06-14

This document captures the traveler user stories related to dashboard viewing and the request status timeline.

---

## US-005-001: Traveler Request Dashboard

**As a** Traveler,
**I want to** track my incoming and active requests through all lifecycle stages on a unified dashboard,
**So that** I know exactly which requests to review, which ones are accepted, and their current coordination state.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Traveler views request list dashboard
  Given I am logged in as a Traveler
  When I open the traveler dashboard
  Then I should see my requests grouped by active status categories:
    | Category | Description |
    | Requests | Incoming shopper requests in status "Requested" |
    | Accepted | Requests I have committed to find in status "Accepted" |
    | Processing | Sourced/procured requests currently in progress in status "Processing" |
    | Completed | Finalized requests in status "Completed" or "Reviewed" |
```

---

## US-005-006: Request Timeline Viewer (Traveler)

**As a** Traveler,
**I want to** view a chronological status history log of the request on the details screen,
**So that** I have a clear visual log of the coordination milestones.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 3 |

### Acceptance Criteria

```gherkin
Scenario: Traveler views request timeline log
  Given an active request is on my traveler dashboard
  When I open the details page for that request
  Then I should see the status history logs showing:
    | State | Action Taken |
    | Requested | Shopper submitted the request |
    | Accepted | Traveler accepted the request |
    | Processing | Traveler updated status to processing |
```
