---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/planning/mvp-definition.md
outputs:
  - platform-slas
  - role-constraints
  - currency-policies
depends_on:
  - mvp-definition.md
---

# Platform SLA & Product Requirements Spec

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the platform-level constraints, Service Level Agreements (SLAs), user role permissions, baggage capacity boundaries, and financial policies governing the **My Trip My Titipan** MVP.

---

## 1. Service Level Agreements (SLAs) & Timers

To guarantee transaction momentum and protect baggage inventory, the platform enforces two core automated timers:

### A. 24-Hour Quote Expiration
* **Rule:** A traveler's quotation is valid for exactly **24 hours (1440 minutes)** from the timestamp of quote creation.
* **System Action:** If the shopper does not complete payment via the payment gateway within 24 hours, the order status changes to `EXPIRED`.
* **Inventory Action:** The reserved baggage capacity is immediately released back to the traveler's trip.
* **Exceptions:** If the shopper initiates checkout at hour 23:59, the payment gateway session may remain active for its standard widget duration (e.g., 15 minutes). However, if webhook validation fails or is delayed beyond that window, the platform status reverts to `EXPIRED`.

### B. 7-Day Auto-Delivery Settlement
* **Rule:** When the traveler transitions an order to `IN_TRANSIT` and registers a tracking number, a **7-calendar-day (168 hours)** timer starts.
* **System Action:** If the shopper does not click "Confirm Receipt" or file a dispute/support request within this 7-day window, the platform triggers an automated settlement.
* **Settlement Action:** The order status is updated to `COMPLETED`, and the escrow release webhook is dispatched to initiate traveler payout.

---

## 2. User Role Rules & Constraints

The system distinguishes between three actor roles: **Shopper**, **Traveler**, and **Admin**.

1. **Self-Request Prevention:**
   * A traveler cannot submit a product request on their own published trip link. The system must block requests where `request.shopper_id == trip.traveler_id`.
2. **Access Requirements:**
   * **Trip Publication:** Anyone logged in as a registered user can publish a trip. No pre-KYC verification is required for the MVP.
   * **Product Request:** Any registered user can submit a product request. Unauthenticated users can view public trip pages, but clicking "Request Item" redirects them to the authentication flow.
3. **Admin Rights:**
   * Administrators have read-write access to override order states (e.g., to trigger a refund or force order cancellation) but cannot create trips or edit quotation amounts directly on behalf of users.

---

## 3. Baggage Capacity Boundaries

Baggage suitcase inventory is tracked as a physical constraint:
* **Metric Units:** Baggage capacity is tracked exclusively in **Kilograms (kg)**. Values must be positive floating-point numbers with up to one decimal place (e.g., `1.5 kg`).
* **Maximum Capacities:** The default maximum baggage allowance per trip is set to **30.0 kg** to prevent data entry abuse, unless overridden by admin privileges.
* **Quotation Constraints:** Travelers are prevented from sending quotes if the estimated item weight exceeds the trip's current remaining available capacity:
  $$\text{Remaining Available} = \text{Total Capacity} - (\text{Locked Capacity} + \text{Reserved Capacity})$$

---

## 4. Currency & Financial Policies

To minimize complexity for the MVP, the financial ledger operates under strict boundaries:

1. **IDR Base Currency:**
   * The ledger, payment gateway checkout, and traveler payouts are processed exclusively in **Indonesian Rupiah (IDR)**.
2. **Manual Foreign Exchange Conversion:**
   * The platform does not calculate foreign exchange rates dynamically.
   * If a traveler buys an item in Japanese Yen (JPY), US Dollars (USD), or any other foreign currency, the traveler must calculate the conversion manually and enter the finalized **Item Price in IDR** within the quotation form.
3. **No Partial Payments:**
   * The shopper must pay 100% of the quote total (Item Price + Jastip Fee) to fund the escrow. Partial payments, deposits, or milestone payments are not supported.
4. **Idempotency & Gateway Integrations:**
   * All payment webhook endpoints must enforce strict idempotency (using transaction IDs as keys) to prevent duplicate ledger entries or double-crediting of escrow funds.
