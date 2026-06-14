---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/use-cases/use-case-specifications.md
outputs:
  - traveler-usecases
depends_on:
  - state-machine.md
---

# Traveler Use Case Specifications

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the formal Use Case specifications for the Traveler actor (supply side) on the **My Trip My Titipan** platform.

---

## 1. Actor Use Case Index

| Use Case ID | Use Case Name | Priority | Status |
| :--- | :--- | :--- | :--- |
| **UC-001** | Register & Login (Traveler Role) | Must Have | Done |
| **UC-002** | Publish Trip | Must Have | Done |
| **UC-005** | Create & Send Quotation | Must Have | Done |
| **UC-009** | Ship & Deliver Item | Must Have | Done |
| **UC-015** | Complete Trip | Must Have | Done |
| **UC-016** | Procure & Purchase Item | Must Have | Done |

---

## 2. Use Case Specifications

### UC-001: Register & Login (Traveler Role)
* **Use Case ID:** UC-001
* **Use Case Name:** Register & Login
* **Primary Actor:** Traveler
* **Goal:** Create a traveler account or access an existing traveler profile on the platform.
* **Preconditions:** Traveler has a valid email address or Google account.
* **Trigger:** User opens the platform web app and clicks "Login/Register".
* **Main Flow:**
  1. Traveler selects authentication method (OTP via Email or Google Social Login).
  2. If OTP: Traveler enters email, receives code, and enters OTP.
  3. If Google Login: Traveler authorizes application via Google consent page.
  4. System verifies credentials/OAuth token.
  5. System logs user in. If new user, creates database record and redirects to role onboarding.
* **Alternate Flow:**
  * *Authentication Fails:* If OTP is incorrect, system displays "Invalid OTP code" and prompts resubmission.
* **Postconditions:** Traveler is authenticated and assigned a session token.

### UC-002: Publish Trip
* **Use Case ID:** UC-002
* **Use Case Name:** Publish Trip
* **Primary Actor:** Traveler
* **Goal:** Broadcast traveler travel plans and suitcase capacity.
* **Preconditions:** Traveler is registered and logged in.
* **Trigger:** Traveler clicks "Create Trip" on dashboard.
* **Main Flow:**
  1. Traveler inputs Destination (e.g. Tokyo), Dates (departure and return), and baggage capacity.
  2. System validates input data.
  3. Traveler clicks "Publish Trip".
  4. System saves trip details, sets status to `Open`, and generates a unique shareable link (e.g., `mytrip.com/t/budi-tokyo-24`).
  5. Traveler copies link to share on social media.
* **Alternate Flow:**
  * *Invalid inputs:* If dates are in the past, system shows error validation and stays on creation form.
* **Postconditions:** Trip is saved and active; shareable URL is active.

### UC-005: Create & Send Quotation
* **Use Case ID:** UC-005
* **Use Case Name:** Create & Send Quotation
* **Primary Actor:** Traveler
* **Goal:** Present shopper with clear pricing terms for their request.
* **Preconditions:** Order status is `REQUESTED`; traveler is logged in.
* **Trigger:** Traveler opens a request on their dashboard.
* **Main Flow:**
  1. Traveler reviews request.
  2. Traveler accepts request.
  3. System creates quotation.
  4. Traveler inputs: Item Price, Jastip Fee, and estimated weight.
  5. Traveler clicks "Send Quote".
  6. Status changes to `QUOTED`.
  7. System reserves baggage capacity (subtracts from available, adds to reserved).
  8. System sends email notification to the Shopper with a 24-hour payment link.
* **Alternate Flow:**
  * *Traveler Rejects Request:* Traveler clicks "Decline Request". Status changes to `CANCELLED` and shopper is notified.
* **Postconditions:** Quotation is sent; baggage capacity is reserved.

### UC-009: Ship & Deliver Item
* **Use Case ID:** UC-009
* **Use Case Name:** Ship & Deliver Item
* **Primary Actor:** Traveler
* **Goal:** Fulfill delivery to shopper post-travel.
* **Preconditions:** Order status is `PURCHASED`; traveler has returned.
* **Trigger:** Traveler drops package at courier and inputs tracking details.
* **Main Flow:**
  1. Traveler inputs domestic tracking number and courier name into the platform order dashboard.
  2. Traveler clicks "Mark as Shipped".
  3. Status changes to `IN_TRANSIT`.
  4. System sends email notification to Shopper with tracking details.
* **Postconditions:** Status is `IN_TRANSIT`.

### UC-016: Procure & Purchase Item
* **Use Case ID:** UC-016
* **Use Case Name:** Procure & Purchase Item
* **Primary Actor:** Traveler
* **Goal:** Procure requested items and verify the purchase to build trust.
* **Preconditions:** Order status is `PAID`.
* **Trigger:** Traveler travels/begins procurement OR traveler successfully buys the item.
* **Main Flow:**
  1. Traveler begins procurement process. Status changes to `PURCHASING`.
  2. Traveler successfully purchases the item.
  3. Traveler navigates to dashboard and clicks "Mark as Purchased", with the option to upload a receipt image or product photo.
  4. Status changes to `PURCHASED`.
* **Postconditions:** Status is `PURCHASED`.

### UC-015: Complete Trip
* **Use Case ID:** UC-015
* **Use Case Name:** Complete Trip
* **Primary Actor:** Traveler
* **Goal:** Close the trip lifecycle to calculate performance/revenues.
* **Preconditions:** All active orders for the trip have reached final states (`COMPLETED`, `EXPIRED`, or `CANCELLED`).
* **Trigger:** Traveler clicks "Mark Trip Completed" on their trip dashboard.
* **Main Flow:**
  1. Traveler requests trip completion.
  2. System verifies all active requests/orders for this trip are in final states.
  3. System updates Trip status to `Completed`.
  4. System archives the trip from the active planner list.
* **Postconditions:** Trip status is `Completed`.
