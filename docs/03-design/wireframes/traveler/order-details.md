---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-010-spec
depends_on:
  - docs/02-product/user-stories/traveler/send-quote.md
---

# SCR-010: Traveler Order Details

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This screen contains the traveler order details, including buyer contact info, visual "Escrow Secured" verification indicators, procurement state updates, and domestic shipping courier form controls.

---

## 1. Visual Mockup & ASCII Wireframe Layout

![SCR-010: Traveler Order Details Mockup](scr-010-traveler-order-details.png)

```text
--------------------------------------------------
| [Back]            Order Fulfillment Details    |
|                                                |
|  Order ID: #ORD-9902                           |
|  Shopper: Maria   | Contact: email@mail.com    |
|  Item: Tokyo Banana Classic (Qty: 2)           |
|                                                |
|  Status: PAID (Escrow Secured 🔒)               |
|                                                |
|  ----------- Procurement Status -----------    |
|  [ Button: Start Purchasing ] (Moves to PURCHASING)
|                                                |
|  [ Button: Mark as Purchased ] (Moves to PURCHASED)
|  Optional: Upload photo of receipt/item        |
|                                                |
|  ----------- Shipping & Dispatch -----------   |
|  Courier Service                               |
|  [ dropdown: JNE / J&T / Sicepat             ] |
|  Courier Tracking AWB                          |
|  [ input: Enter AWB tracking number          ] |
|  [ Button: Submit Tracking & Ship ]            |
|                                                |
|  [ Link: Mark as Out of Stock ] (Dispute/Refund)
--------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Back Button (`BTN-010-001`):**
   * *Action:* Returns to `SCR-006: Traveler Dashboard`.
2. **Escrow Locked Verification Indicator (`TXT-010-001`):**
   * Prominent visual badge displayed on paid orders: `Status: PAID (Escrow Secured 🔒)`.
   * *Tooltip Description:* *"Shopper funds are secured in platform escrow. You are guaranteed payout upon shipping."*
3. **Start Sourcing Trigger (`BTN-010-002`):**
   * *Type:* Action button, enabled if order status is `PAID`.
   * *Action:* Updates status to `PURCHASING`.
4. **Mark as Purchased Trigger (`BTN-010-003`):**
   * *Type:* Action button, enabled if status is `PURCHASING`.
   * *Option:* Optional image uploader box to submit photo of the store receipt or bought product.
   * *Action:* Updates status to `PURCHASED`.
5. **Courier Service Selector (`FLD-010-001`):**
   * *Type:* Dropdown selection, required. Courier options: JNE, J&T, Sicepat.
6. **Courier tracking AWB Code Input (`FLD-010-002`):**
   * *Type:* Text input, required.
   * *Validation:* Alphanumeric, must match standard courier formatting regex.
7. **Submit Shipment Button (`BTN-010-004`):**
   * *Type:* Primary action button. Disabled until dropdown and AWB are valid.
   * *Action:* Saves tracking details, transitions status to `IN_TRANSIT`, and triggers shipping confirmation email notifications to the shopper.
8. **Mark Out-of-Stock Link (`BTN-010-005`):**
   * *Action:* Prompts out-of-stock warning, initiates cancel process, and redirects to refund handler queue.

---

## 3. UI State Variations

### A. Non-Paid States
* If order is not paid yet (e.g., `Quoted`), hide the procurement and shipping sections, showing status card only.

### B. Procurement Complete State
* Once marked `Purchased`, hide the procurement actions and focus screen content on the Shipping & Dispatch input sections.

---

## 4. Traceability

* **User Story:** [US-005-005](../../../../02-product/user-stories/traveler/send-quote.md#us-005-005-procure--purchase-item)
* **Requirement:** [Procurement and Delivery specifications](../../../02-product/requirements/feature-requirements.md#4-baggage-capacity-management)
