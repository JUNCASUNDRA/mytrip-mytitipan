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

# Use Case Specification: Submit Product Request (UC-004)

> **Status**: Approved **Last Updated**: 2026-06-14

## 1. Brief Description
Allows a Shopper to fill out a structured product request form on a traveler's trip page to express interest in specific items.

---

## 2. Actors & Preconditions
*   **Primary Actor:** Shopper
*   **Preconditions:** Shopper is authenticated. (If guest, system triggers registration/login before final submission).

---

## 3. Basic Flow (Happy Path)
1.  Shopper visits a Traveler's public trip landing page.
2.  Shopper inspects traveler's **trip history**, **request completion history**, and past reviews.
3.  Shopper clicks "Request Item".
4.  Shopper fills out the form:
    *   Item Name (Required)
    *   Reference URL (Optional)
    *   Reference Image (Optional)
    *   Quantity (Required, positive integer)
    *   Notes (Optional)
5.  Shopper clicks "Submit Request".
6.  System saves the request record with status `Requested`, notifies the traveler, and initializes the **Request Timeline**.

---

## 4. Alternative Flows & Exception Paths

### Alternative Flow 1: Guest User Submission
*   At step 3, if shopper is not logged in:
    1.  System prompts the shopper to Register or Log In (Google OAuth / OTP).
    2.  Upon successful authentication, the shopper is returned to the request form with any draft details preserved.
    3.  Flow continues at step 4.
