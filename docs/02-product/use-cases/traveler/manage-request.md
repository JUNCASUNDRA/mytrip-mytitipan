---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-1
status: approved
priority: must-have
depends_on:
  - core-user-flow.md
outputs:
  - ux-flow
  - technical-requirement
---

# Use Case Specification: Request Lifecycle Management (UC-005)

> **Status**: Approved **Last Updated**: 2026-06-14

## 1. Brief Description
Allows a Traveler to view shopper requests submitted to their active trip link and manually transition request statuses through the simplified fulfillment pipeline.

---

## 2. Actors & Preconditions
*   **Primary Actor:** Traveler
*   **Preconditions:** Traveler is authenticated and has at least one active trip with incoming requests.

---

## 3. Basic Flow (Happy Path)
1.  Traveler opens their dashboard.
2.  Traveler selects an incoming request in `Requested` status.
3.  Traveler inspects the photo, product reference URL, quantity, and notes.
4.  Traveler clicks "Accept Request" to commit to finding the item.
5.  System updates request status to `Accepted`, notifies the shopper, and appends an entry to the **Request Timeline**.
6.  Traveler clicks "Update Progress" to indicate the request is in progress, transitioning status to `In Progress`.
7.  Traveler procures/arranges the item and clicks "Mark Ready" to shift status to `Ready for Delivery`.
8.  Traveler coordinates handover and offline payment, clicks "Hand Over Item" (or Shopper clicks "Confirm Receipt") to finalize and transition the status to `Completed`.

---

## 4. Alternative Flows & Exception Paths

### Alternative Flow 1: Decline Request
*   At step 4, if traveler cannot procure the item:
    1.  Traveler clicks "Decline Request".
    2.  System updates request status to `Cancelled`.
    3.  System notifies shopper and logs decline in the request timeline.

### Alternative Flow 2: Post-Acceptance Cancellation
*   At step 6, if traveler finds the item out-of-stock or travel plans abort:
    1.  Traveler clicks "Cancel Request".
    2.  System updates request status to `Cancelled`.
    3.  System notifies shopper and logs cancellation reasons in the timeline.
