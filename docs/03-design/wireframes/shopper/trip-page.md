---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-002-spec
depends_on:
  - docs/02-product/user-stories/traveler/create-trip.md
---

# SCR-002: Trip Landing Page

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This is the primary public entry point for Shoppers. Accessible via a shared trip link without initial authentication, it displays traveler reputation parameters and baggage capacities.

---

## 1. Visual Mockup & ASCII Wireframe Layout

![SCR-002: Trip Landing Page Mockup](scr-002-trip-landing.png)

```text
--------------------------------------------------
| [Profile Avatar]  Budi Santoso                 |
|                   Completed Trips: 8           |
|                   Completed Orders: 24         |
|                   Rating: ⭐ 4.8 (12 Reviews)   |
|                                                |
|  ----------- Active Trip Details -----------   |
|  Route: Tokyo (HND) -> Jakarta (CGK)           |
|  Departure: 20 Jun 2026                        |
|  Return: 28 Jun 2026                           |
|                                                |
|  Baggage Availability:                         |
|  [||||||||||||||||-------] 12.5 kg / 20.0 kg    |
|  Status: Open for Requests                     |
|                                                |
|  ---------------- Reviews -----------------   |
|  - "Fast response and safe!" - Andi (⭐ 5)    |
|  - "Item arrived intact." - Maria (⭐ 4)      |
|                                                |
|  [ Button: Request Item from Tokyo           ] |
--------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Traveler Profile Avatar (`IMG-002-001`):**
   * *Type:* Circle image placeholder. Displays traveler profile image.
2. **Reputation Counters (`TXT-002-001`):**
   * *Trips Count:* Non-interactive label showing total completed trips.
   * *Orders Count:* Non-interactive label showing completed jastip orders.
   * *Stars:* Average rating scale (out of 5) with review counts linking to the profile reviews section.
3. **Trip Timeline Card (`CRD-002-001`):**
   * Displays departure and arrival airports (e.g., Tokyo HND to Jakarta CGK) and date schedules.
4. **Baggage Capacity Progress Bar (`BAR-002-001`):**
   * *Visual:* HSL-colored status indicator (Green for > 50% available, Orange for 10% - 50%, Red for < 10%).
   * *Text:* Displays numeric occupancy (e.g., `12.5 kg / 20.0 kg occupied`).
5. **Request Item Button (`BTN-002-001`):**
   * *Type:* Fixed bottom sticky action button.
   * *Action:* Redirects to `SCR-003: Product Request Form`.
   * *Validation:* Disabled if remaining available capacity is 0, displaying "Baggage Capacity Full" on button.

---

## 3. UI State Variations

### A. Capacity Full State
* `BAR-002-001` is filled red (100%).
* Status text changes to `Trip Full`.
* `BTN-002-001` is disabled and greyed out, displaying `Baggage capacity limit reached`.

### B. Expired Trip State
* If travel dates have passed, displays `This trip has ended. No new requests accepted.` at the top.
* `BTN-002-001` is completely hidden.

---

## 4. Traceability

* **User Story:** [US-002-003](../../../../02-product/user-stories/traveler/create-trip.md#us-002-003-public-traveler-profile)
* **Requirement:** [Baggage capacity boundaries](../../../02-product/requirements/product-requirements.md#3-baggage-capacity-boundaries)
