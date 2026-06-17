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

# Use Case Specification: Publish Trip (UC-002)

> **Status**: Approved **Last Updated**: 2026-06-14

## 1. Brief Description
Allows a Traveler to register an upcoming journey (Destination, dates, optional baggage/sourcing notes) and generate a shareable URL so shoppers can submit product requests.

---

## 2. Actors & Preconditions
*   **Primary Actor:** Traveler
*   **Preconditions:** Traveler is registered and authenticated in the platform.

---

## 3. Basic Flow (Happy Path)
1.  Traveler navigates to the "Create Trip" page.
2.  Traveler enters a valid Destination (Country & City).
3.  Traveler selects Departure and Return Dates.
4.  Traveler inputs optional Baggage Notes (e.g. constraints on space, items preferred).
5.  Traveler clicks "Publish Trip".
6.  System validates inputs, saves the trip in database with status `Open`, and generates a unique shareable slug (e.g., `mytrip.com/t/budi-tokyo-24`).
7.  System displays a success screen with a copyable URL.

---

## 4. Alternative Flows & Exception Paths

### Alternative Flow 1: Past Dates Entered
*   At step 6, if departure or return date is in the past:
    1.  System blocks publication.
    2.  System shows validation error: "Departure and Return dates must be in the future."
    3.  Flow returns to step 2.

### Alternative Flow 2: Return Date Before Departure Date
*   At step 6, if return date is before departure date:
    1.  System blocks publication.
    2.  System shows validation error: "Return date must be equal to or after departure date."
    3.  Flow returns to step 3.
