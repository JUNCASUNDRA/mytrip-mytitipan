---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/03-user-flow/README.md
outputs:
  - shopper-ux-flow
  - shopper-journey-states
depends_on:
  - requirements/feature-requirements.md
---

# Shopper UX User Flow Specifications

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the step-by-step user interaction flow, navigation entry/exit points, screen inventory mappings, and interface states for the **Shopper** actor (demand side).

---

## 1. Journey Entry & Exit Points

* **Entry Point (Input):** Shopper clicks Budi's shared traveler trip link (e.g., `mytrip.com/t/budi-tokyo-24`) posted on social media or messaging platforms, landing on the public Trip details screen.
* **Exit Point (Output):** Shopper receives domestic shipment package, confirms receipt on the dashboard, and submits feedback reviews.

---

## 2. Screen Mapping & Step-by-Step Flow

Every shopper interaction maps to a unique Screen ID from the design inventory:

```mermaid
flowchart TD
    E[Entry: Click Shared Trip URL] --> S1[SCR-002: Trip Landing Page]
    S1 --> S2[View Traveler Stats & Reviews]
    S2 --> S3[SCR-003: Product Request Form]
    S3 --> S4{Logged In?}
    
    S4 -->|No| S5[SCR-001: Login / Register]
    S5 --> S6[Authenticate & Auto-Submit Request]
    S4 -->|Yes| S6
    
    S6 --> S7[Status: Requested & Wait for Quote]
    S7 --> S8{Quote Received?}
    
    S8 -->|No / Declined| S9[Cancel Request & Status: Cancelled]
    S8 -->|Yes| S10[SCR-004: Shopper Dashboard]
    S10 --> S11[SCR-005: Quote & Checkout Page]
    
    S11 --> S12{Pay Escrow in 24h?}
    S12 -->|No / Timeout| S13[Status: Expired & Capacity Released]
    S12 -->|Yes| S14[Gateway Redirect & Status: Payment Pending]
    
    S14 --> S15{Payment Webhook Callback}
    S15 -->|Failed| S11
    S15 -->|Success| S16[Status: Paid & Escrow Secured]
    
    S16 --> S17[SCR-004: Track Status: Purchased -> In Transit]
    S17 --> S18[Receive domestic courier shipment]
    S18 --> S19[SCR-004: Click Confirm Receipt]
    S19 --> S20[Status: Delivered & Completed]
    
    S20 --> S21[SCR-011: Review Submission]
    S21 --> EX[Exit: Feedback Saved]
```

### Flow Breakdown & Screen Actions:
1. **Trip Discovery (`SCR-002`):** Shopper views Budi's route dates, available suitcase capacity limit bar, and ratings list. Clicks "Request Item".
2. **Item Specification (`SCR-003`):** Shopper enters Item Name, reference links, budget currency in IDR, and uploads a product reference image. Clicks "Submit Request".
   * *Authentication Guard:* If not logged in, system redirects shopper to `SCR-001` to login via Google SSO or Email-OTP, then automatically creates request.
3. **Shopper Panel Tracker (`SCR-004`):** Shopper views active requests list. Active quotes displays countdown timers. Clicks "Review Quote".
4. **Quotation & Checkout (`SCR-005`):** Shopper reviews Item Price + Jastip Fee pricing breakdown. Selects payment method (Virtual Account or GoPay) and clicks "Pay Now".
5. **Review Submission (`SCR-011`):** Shopper clicks stars (1 to 5) and enters review text feedback. Clicks "Submit Review".

---

## 3. Separation of Business Rules vs. UX Behaviors

To guide development backend/frontend boundaries, logical rules are isolated from interface widgets:

### A. Expiry of Unpaid Quotations
* **Business Rule:**
  * Quotes must automatically expire and release suitcase weight back to traveler availability after 24 hours.
* **UX Behavior:**
  * Shopper Dashboard (`SCR-004`) and Checkout Page (`SCR-005`) display a real-time countdown timer: `Review Quote & Pay (Expires in 14h 23m)`.
  * System sends a reminder notification email to shopper 2 hours prior to expiration.

### B. Payment Success & Escrow Locking
* **Business Rule:**
  * 100% of quote total must fund the platform escrow. Virtual capacity reserves are converted to locked capacity upon gateway webhook success callback.
* **UX Behavior:**
  * Payment checkout forms display visual trust badges detailing platform escrow safety guarantees.
  * Successful payment updates order statuses to `Paid` instantly, showing secure badge icons.

---

## 4. Journey State & Exception UX Variations

### A. Empty State (No Active Requests)
* **Visual:** Box illustration icon on `SCR-004`.
* **UX Copy:** *"No active titipan. Once you find a traveler's trip link, you can submit product requests here."*

### B. Sourcing Processing State
* **UX Behavior:** Display processing overlay during virtual account generation: `Generating Virtual Account invoice number...`

### C. Capacity Exceeded Error State
* **UX Behavior:** If trip capacity is depleted, shopper is prevented from requesting items on `SCR-002` (displays red banner: *"Baggage capacity limit reached"* and disables CTA). If checkout is active, displays error banner: *"Luggage capacity exceeded. Transaction cancelled."*

### D. Permission Denied Block State
* **UX Behavior:** If guest tries to access `SCR-004`, router redirects to `SCR-001` with error message: *"Please login to view your shopper dashboard."*
