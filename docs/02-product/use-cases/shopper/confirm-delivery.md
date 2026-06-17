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

# Use Case Specification: Confirm Delivery & Feedback (UC-010 / UC-011)

> **Status**: Approved **Last Updated**: 2026-06-14

## 1. Brief Description
Allows a Shopper to confirm receipt of the item physically (changing request status from `Processing` to `Completed`) and write a review with star ratings (changing status from `Completed` to `Reviewed`).

---

## 2. Actors & Preconditions
*   **Primary Actor:** Shopper
*   **Preconditions:** Shopper is authenticated, and the request status is `Processing`.

---

## 3. Basic Flow (Happy Path)
1.  Shopper navigates to their request details page.
2.  Shopper inspects the status updates on the **Request Timeline**.
3.  Shopper clicks "Confirm Receipt" once they physically receive the package and coordinate offline payment.
4.  System updates request status to `Completed` and appends confirmation to the timeline.
5.  System prompts the shopper to leave traveler feedback.
6.  Shopper inputs a Star Rating (1 to 5 stars) and enters a written feedback review.
7.  Shopper clicks "Submit Review".
8.  System saves review in the database, updates status to `Reviewed`, updates the traveler's aggregate score, and shows the feedback on the traveler's profile page.

---

## 4. Alternative Flows & Exception Paths

### Alternative Flow 1: Pre-Delivery Cancellation by Shopper
*   If request is in `Requested` or `Accepted` status and shopper wants to abort:
    1.  Shopper clicks "Cancel Request".
    2.  System updates status to `Cancelled`, notifies traveler, and logs cancellation on the timeline.
