---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-011-spec
depends_on:
  - docs/02-product/user-stories/shopper/confirm-delivery.md
---

# SCR-011: Review Submission

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This screen contains the star selection and review feedback text form controls shopper uses to evaluate a traveler post-delivery.

---

## 1. ASCII Wireframe Layout

```text
--------------------------------------------------
| [Back]            Submit Traveler Review       |
|                                                |
|  Order ID: #ORD-9902                           |
|  Traveler: Budi Santoso                        |
|                                                |
|  How was your experience?                      |
|  Rating: ⭐ ⭐ ⭐ ⭐ ⭐                         |
|  (Click stars to rate traveler)                |
|                                                |
|  Write a Review:                               |
|  +------------------------------------------+  |
|  | textarea: Fast response, item arrived     |  |
|  | safely in perfect condition.              |  |
|  +------------------------------------------+  |
|                                                |
|  [ Button: Submit Review & Rating            ] |
--------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Back Button (`BTN-011-001`):**
   * *Action:* Returns to `SCR-004: Shopper Dashboard`.
2. **Star Rating Selector (`FLD-011-001`):**
   * *Type:* Interactive star icons (1 to 5).
   * *Interaction:* Hovering highlights the stars. Clicking sets the selection count (e.g., `4 Stars`).
   * *Validation:* Required. Default state is 0 stars (none selected).
3. **Review Textarea Form (`FLD-011-002`):**
   * *Type:* Multiline text input box. Optional.
   * *Validation:* Limit text entry to maximum 500 characters (character counter displays remaining count: `432 / 500`).
4. **Submit Review Button (`BTN-011-002`):**
   * *Type:* Primary action button.
   * *Validation:* Disabled until star selector `FLD-011-001` is clicked (> 0 stars).
   * *Action:* Submits feedback, updates traveler profile aggregate ratings, and redirects shopper back to the dashboard.

---

## 3. UI State Variations

### A. Submitting Feedback State
* Submit button shows spinner and updates to `Submitting review...`.
* Inputs are locked.

---

## 4. Traceability

* **User Story:** [US-005-003](../../../../02-product/user-stories/shopper/confirm-delivery.md#us-005-003-reviews--ratings-system)
* **Requirement:** [Reviews & Ratings specification](../../../02-product/requirements/feature-requirements.md#9-reviews--ratings-system)
