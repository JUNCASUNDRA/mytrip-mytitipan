---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-005-spec
depends_on:
  - docs/02-product/user-stories/shopper/pay-order.md
---

# SCR-005: Quote & Checkout Page

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This screen presents shoppers with the item price and traveler fee breakdown, quote expiration countdown alerts, and payment method selectors.

---

## 1. Visual Mockup & ASCII Wireframe Layout

![SCR-005: Quote & Checkout Page Mockup](scr-005-quote-checkout.png)

```text
--------------------------------------------------
| [Back]            Quotation & Payment          |
|                                                |
|  Quote for: Tokyo Banana Classic (Qty: 2)       |
|  Traveler: Budi Santoso                        |
|  Weight Estimate: 1.0 kg                       |
|                                                |
|  ----------- Quote Breakdown -----------       |
|  Item Price:         IDR  250,000              |
|  Jastip Service Fee: IDR  100,000              |
|  ---------------------------------------       |
|  Total Quote Cost:   IDR  350,000              |
|                                                |
|  [!] Funds will be held securely in escrow.    |
|  Quote expires in: 14h 23m                     |
|                                                |
|  Select Payment Method:                        |
|  ( ) Mandiri Virtual Account                   |
|  ( ) GoPay / QRIS                              |
|                                                |
|  [ Button: Pay IDR 350,000                   ] |
|  [ Link: Decline & Cancel Request ]            |
--------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Back Button (`BTN-005-001`):**
   * *Action:* Returns to `SCR-004: Shopper Dashboard`.
2. **Billing Breakdown Card (`CRD-005-001`):**
   * Displays individual line items: Item Price, Jastip Service Fee, and Total Quote Cost.
3. **Escrow Disclaimer Badge (`TXT-005-001`):**
   * Informative visual panel stating that shopper funds are secured in platform escrow until delivery confirmation.
4. **Countdown Expiry Timer (`TXT-005-002`):**
   * Displays time remaining before quotation expiration (e.g., `Quote expires in: 14h 23m`). Refreshes every minute.
5. **Payment Method Selectors (`FLD-005-001`):**
   * *Type:* Radio button lists. Options: Virtual Account, GoPay/QRIS.
6. **Pay Quote Button (`BTN-005-002`):**
   * *Type:* Primary action button.
   * *Action:* Initiates payment gateway transaction session, redirects to payment widget or transitions status to `PAYMENT_PENDING`.
7. **Decline Link (`BTN-005-003`):**
   * *Action:* Displays cancellation confirmation. Upon yes, declines the quote and updates status to `CANCELLED`.

---

## 3. UI State Variations

### B. Payment Processing / Pending State
* Displays a loader overlay: `Processing transaction with payment provider...`.
* The state changes to `PAYMENT_PENDING` while waiting for webhook success.

### C. Capacity Exceeded Block State
* If the traveler's baggage capacity was depleted by another paid order while this page was open:
  * Radio options and Pay button are disabled.
  * Displays error: `Baggage capacity limit reached. Checkout unavailable.`

---

## 4. Traceability

* **User Story:** [US-006-001](../../../../02-product/user-stories/shopper/pay-order.md#us-006-001-fund-escrow-payment)
* **Requirement:** [Quotation Specs & Capacity Locks](../../../02-product/requirements/feature-requirements.md#3-quotation-engine)
