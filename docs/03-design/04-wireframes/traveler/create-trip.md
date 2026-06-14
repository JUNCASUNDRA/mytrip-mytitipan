---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-007-spec
depends_on:
  - docs/02-product/user-stories/traveler/create-trip.md
---

# SCR-007: Create Trip Form

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This screen contains the form inputs traveler uses to publish dates, destinations, and baggage capacity weights.

---

## 1. ASCII Wireframe Layout

```text
--------------------------------------------------
| [Back]            Publish New Trip             |
|                                                |
|  Destination Route                             |
|  Departure Airport                             |
|  [ input: Jakarta (CGK)                      ] |
|  Arrival Airport                               |
|  [ input: Tokyo (HND)                        ] |
|                                                |
|  Travel Schedule                               |
|  Departure Date                                |
|  [ date picker: 2026-06-20                   ] |
|  Return Date                                   |
|  [ date picker: 2026-06-28                   ] |
|                                                |
|  Baggage Capacity Limit                        |
|  [ input: 20.0                               ] kg
|  (Max platform weight: 30.0 kg)                |
|                                                |
|  [ Button: Publish Trip & Generate Link      ] |
--------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Back Button (`BTN-007-001`):**
   * *Action:* Returns to `SCR-006: Traveler Dashboard`.
2. **Departure Airport Autocomplete (`FLD-007-001`):**
   * *Type:* Text input with dropdown query. Required.
3. **Arrival Airport Autocomplete (`FLD-007-002`):**
   * *Type:* Text input with dropdown query. Required.
4. **Departure Date Picker (`FLD-007-003`):**
   * *Type:* Calendar selector. Required. Must be greater than current date.
5. **Return Date Picker (`FLD-007-004`):**
   * *Type:* Calendar selector. Required. Must be greater than or equal to `FLD-007-003`.
6. **Baggage Capacity Input (`FLD-007-005`):**
   * *Type:* Numeric input (1 decimal place). Required.
   * *Validation:* Minimum 1.0 kg, maximum 30.0 kg.
7. **Publish Trip Button (`BTN-007-002`):**
   * *Type:* Primary action button.
   * *Action:* Submits data to backend, generates active trip record, and opens `SCR-008: Trip Share Modal` upon success.

---

## 3. UI State Variations

### A. Date Selection Error
* If departure date is in the past, highlights `FLD-007-003` border red with message: `Departure date cannot be in the past.`
* If return date is before departure, highlights `FLD-007-004` border red with message: `Return date cannot be before departure date.`

### B. Weight Limit Error
* If weight exceeds 30kg, highlights `FLD-007-005` with error: `Baggage capacity cannot exceed 30.0 kg.`

---

## 4. Traceability

* **User Story:** [US-002-001](../../../../02-product/user-stories/traveler/create-trip.md#us-002-001-publish-trip)
* **Requirement:** [Trip Publisher specification](../../../02-product/requirements/feature-requirements.md#1-trip-publisher)
