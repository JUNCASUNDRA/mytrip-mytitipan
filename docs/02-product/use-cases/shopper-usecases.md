---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/use-cases/use-case-specifications.md
outputs:
  - shopper-usecases
depends_on:
  - state-machine.md
---

# Shopper Use Case Specifications

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the formal Use Case specifications for the Shopper actor (demand side) on the **My Trip My Titipan** platform.

---

## 1. Actor Use Case Index

| Use Case ID | Use Case Name | Priority | Status |
| :--- | :--- | :--- | :--- |
| **UC-001** | Register & Login (Shopper Role) | Must Have | Done |
| **UC-003** | View Traveler Profile & Trip Page | Must Have | Done |
| **UC-004** | Submit Product Request | Must Have | Done |
| **UC-007** | Pay via Escrow | Must Have | Done |
| **UC-008** | Track Order Status | Must Have | Done |
| **UC-010** | Confirm Delivery | Must Have | Done |
| **UC-011** | Submit Review & Rating | Must Have | Done |

---

## 2. Use Case Specifications

### UC-001: Register & Login (Shopper Role)
* **Use Case ID:** UC-001
* **Use Case Name:** Register & Login
* **Primary Actor:** Shopper
* **Goal:** Create a shopper account or access an existing shopper profile on the platform.
* **Preconditions:** Shopper has a valid email address or Google account.
* **Trigger:** User opens the platform web app and clicks "Login/Register".
* **Main Flow:**
  1. Shopper selects authentication method (OTP via Email or Google Social Login).
  2. If OTP: Shopper enters email, receives code, and enters OTP.
  3. If Google Login: Shopper authorizes application via Google consent page.
  4. System verifies credentials/OAuth token.
  5. System logs user in. If new user, creates database record and redirects to role onboarding.
* **Alternate Flow:**
  * *Authentication Fails:* If OTP is incorrect, system displays "Invalid OTP code" and prompts resubmission.
* **Postconditions:** Shopper is authenticated and assigned a session token.

### UC-003: View Traveler Profile & Trip Page
* **Use Case ID:** UC-003
* **Use Case Name:** View Traveler Profile & Trip Page
* **Primary Actor:** Shopper
* **Goal:** Verify traveler credibility and details before requesting an item.
* **Preconditions:** A trip has been published by a traveler.
* **Trigger:** Shopper clicks a shared trip URL.
* **Main Flow:**
  1. System displays traveler trip page containing: traveler name, photo, trip route/dates, and remaining baggage capacity status (`Open`/`Limited`/`Full`).
  2. Shopper clicks "View Profile".
  3. System displays traveler's completed trips count, completed orders count, and reviews/ratings history.
* **Alternate Flow:**
  * *Trip Closed:* If trip capacity is full or dates have passed, page displays "Full" or "Closed for requests" status; request button is disabled.
* **Postconditions:** Shopper has reviewed traveler trust signals.

### UC-004: Submit Product Request
* **Use Case ID:** UC-004
* **Use Case Name:** Submit Product Request
* **Primary Actor:** Shopper
* **Goal:** Request a traveler to buy an item from their destination.
* **Preconditions:** Shopper is logged in; trip is open for requests.
* **Trigger:** Shopper clicks "Request Item" on traveler's trip page.
* **Main Flow:**
  1. Shopper enters Item Name, Reference URL, Photo, Quantity, and Willingness to Pay.
  2. System validates that required fields are filled.
  3. Shopper submits request.
  4. System registers order in state `REQUESTED`.
  5. System triggers notification to the Traveler.
* **Alternate Flow:**
  * *User not logged in:* System redirects shopper to UC-001 (Register & Login) before saving request details.
* **Postconditions:** Request is saved; order status is `REQUESTED`.

### UC-007: Pay via Escrow
* **Use Case ID:** UC-007
* **Use Case Name:** Pay via Escrow
* **Primary Actor:** Shopper
* **Goal:** Securely fund the transaction into escrow to authorize purchase.
* **Preconditions:** Order status is `QUOTED`.
* **Trigger:** Shopper clicks "Pay Now" on quote.
* **Main Flow:**
  1. Shopper clicks "Pay Now". Order status transitions to `PAYMENT_PENDING`.
  2. System redirects shopper to payment page and creates a transaction on the payment gateway (status: Created/Pending).
  3. Shopper completes checkout within payment gateway widget.
  4. Payment gateway sends payment webhook notification (Success) to platform.
  5. System locks funds in Escrow account.
  6. System locks baggage capacity (deducts from reserved, adds to locked).
  7. Status changes to `PAID`.
  8. System sends email notification to the Traveler indicating it is safe to proceed with procurement.
* **Alternate Flow:**
  * *Payment Fails/Expires:* If the payment gateway sends a Failed/Expired callback, or the 24-hour payment window closes, status transitions directly to `EXPIRED` and system triggers capacity release.
* **Postconditions:** Escrow is funded; status changes to `PAID` (or `EXPIRED` on failure).

### UC-008: Track Order Status
* **Use Case ID:** UC-008
* **Use Case Name:** Track Order Status
* **Primary Actor:** Shopper
* **Goal:** Monitor status changes and tracking updates.
* **Preconditions:** Order has been created.
* **Trigger:** User accesses the dashboard.
* **Main Flow:**
  1. Shopper logs in and selects order.
  2. System displays tracking history showing: Status, Timestamp, and Courier tracking details (if in transit).
* **Postconditions:** Shopper is informed of exact status.

### UC-010: Confirm Delivery
* **Use Case ID:** UC-010
* **Use Case Name:** Confirm Delivery
* **Primary Actor:** Shopper
* **Goal:** Release escrow funds to traveler upon receipt.
* **Preconditions:** Order status is `IN_TRANSIT`.
* **Trigger:** Shopper receives item and clicks "Confirm Receipt" in dashboard.
* **Main Flow:**
  1. Shopper clicks "Confirm Receipt".
  2. System changes status to `DELIVERED`.
  3. System initiates escrow payout to traveler.
  4. Status changes to `COMPLETED`.
* **Postconditions:** Escrow funds are released; order is `COMPLETED`.

### UC-011: Submit Review & Rating
* **Use Case ID:** UC-011
* **Use Case Name:** Submit Review & Rating
* **Primary Actor:** Shopper
* **Goal:** Rate traveler performance to build platform reputation.
* **Preconditions:** Order status is `DELIVERED` or `COMPLETED`.
* **Trigger:** Shopper completes delivery confirmation.
* **Main Flow:**
  1. Shopper selects star rating (1–5) and inputs text review.
  2. Shopper clicks "Submit".
  3. System saves review and links it to traveler's profile page.
  4. System recalculates traveler's aggregate rating.
* **Postconditions:** Review is saved and visible on traveler profile.
