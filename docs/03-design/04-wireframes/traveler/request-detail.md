---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-009-spec
depends_on:
  - docs/02-product/user-stories/traveler/send-quote.md
---

# SCR-009: Request Review Screen

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This screen allows travelers to review a shopper's product request, accept it by proposing quotation prices and estimating weight, or decline it.

---

## 1. ASCII Wireframe Layout

```text
--------------------------------------------------
| [Back]            Review Product Request       |
|                                                |
|  From Shopper: Maria                           |
|  Item: Tokyo Banana Classic 8-pack             |
|  Quantity: 2                                   |
|  Shopper Willing-to-Pay: IDR 350,000           |
|                                                |
|  Reference Image:                              |
|  +------------------------------------------+  |
|  |               [ Image ]                  |  |
|  +------------------------------------------+  |
|                                                |
|  ----------- Propose Quotation -----------     |
|  Item Purchase Price (in IDR)                  |
|  IDR [ input: 250,000                        ] |
|  Jastip Service Fee (in IDR)                   |
|  IDR [ input: 100,000                        ] |
|                                                |
|  Estimated Suitcase Weight                     |
|  [ input: 1.0 ] kg                             |
|                                                |
|  [ Button: Send Quote (Expires in 24h)       ] |
|  [ Button: Decline & Cancel Request ]          |
--------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Back Button (`BTN-009-001`):**
   * *Action:* Returns to `SCR-006: Traveler Dashboard`.
2. **Shopper Request Info Cards (`CRD-009-001`):**
   * Displays shopper name, item name, quantity requested, external reference links, and the shopper's declared willingness to pay budget.
3. **Item Price Input (`FLD-009-001`):**
   * *Type:* Currency numeric field, required. Represents traveler's base purchasing price in IDR.
4. **Jastip Service Fee Input (`FLD-009-002`):**
   * *Type:* Currency numeric field, required. Represents traveler's profit margin.
5. **Estimated Weight Input (`FLD-009-003`):**
   * *Type:* Numeric input (in kg). Required.
   * *Validation:* Weight estimate cannot exceed the traveler's remaining available capacity on the trip.
6. **Send Quote Button (`BTN-009-002`):**
   * *Type:* Primary action button.
   * *Action:* Validates inputs. Temporarily reserves the estimated suitcase weight and transitions status to `QUOTED`. Sends email quote notification to the shopper.
7. **Decline Request Button (`BTN-009-003`):**
   * *Type:* Secondary action button.
   * *Action:* Prompts verification. Transitions status to `CANCELLED` and notifies shopper.

---

## 3. UI State Variations

### A. Weight Allocation Exceeded
* If traveler inputs weight exceeding remaining trip available capacity:
  * Highlight `FLD-009-003` border red.
  * Disable `BTN-009-002` and display error: `Insufficient baggage capacity on this trip.`

### B. Price Invalid
* If numeric fields are empty or negative:
  * Highlight fields red with: `Price values must be positive integers.`

---

## 4. Traceability

* **User Story:** [US-004-001](../../../../02-product/user-stories/traveler/send-quote.md#us-004-001-create--send-quotation)
* **Requirement:** [Quotation Engine specifications](../../../02-product/requirements/feature-requirements.md#3-quotation-engine)
