---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-013-spec
depends_on:
  - docs/02-product/user-stories/admin/review-dispute.md
---

# SCR-013: Admin Dispute Manager

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This desktop-first administration panel details disputed transaction parameters, lists courier status log events, and provides manual override buttons.

---

## 1. ASCII Wireframe Layout

```text
-------------------------------------------------------------------------------------
| [Back]                    Dispute Resolution Audit Manager                        |
-------------------------------------------------------------------------------------
|  Order Details                                                                    |
|  Order ID: ORD-1003  | Shopper: Andi  | Traveler: Maria                           |
|  Status: DISPUTED (Escrow Locked: IDR 620,000)                                    |
|  Dispute Reason: Andi claims item arrived damaged.                                |
|                                                                                   |
|  ----------- Photo Evidence & Receipt -----------                                  |
|  Shopper Evidence Photo: [ damaged_perfume.jpg ]                                  |
|  Traveler Sourcing Receipt: [ korea_dutyfree_receipt.png ]                        |
|                                                                                   |
|  ----------- Logistics & Courier Validation -----------                           |
|  Courier: JNE | AWB Code: JNE-99082302                                            |
|  Courier Webhook status: DELIVERED (Recipient: Security Guard)                    |
|                                                                                   |
|  ----------- Manual Escrow Overrides -----------                                  |
|  Reason / Justification for Override (Mandatory Log Entry):                       |
|  [ text input: Enter detailed rationale here for audit trail...               ]  |
|                                                                                   |
|  [ Button: Release Payout to Traveler ]      [ Button: Refund Escrow to Shopper ] |
-------------------------------------------------------------------------------------
```

---

## 2. UI Elements Specification

1. **Back Button (`BTN-013-001`):**
   * *Action:* Returns to `SCR-012: Admin Dashboard`.
2. **Dispute Parameters Panel (`CRD-013-001`):**
   * Displays Order details, escrow balance sum, and shopper's reported text explanation of the dispute.
3. **Photo Evidence Grid (`CRD-013-002`):**
   * Lists thumbnails of shopper's photo evidence of damage alongside traveler's uploaded receipt. Clicking opens photo previews.
4. **Logistics Webhook Audit Log (`TXT-013-001`):**
   * Shows data queried from courier tracking APIs (status, dates, recipient name).
5. **Justification Input Field (`FLD-013-001`):**
   * *Type:* Textarea field. Required.
   * *Validation:* Minimum 20 characters must be entered to prevent empty override audits.
6. **Release Payout Button (`BTN-013-002`):**
   * *Type:* Danger action button.
   * *Validation:* Disabled until a valid explanation is inputted in `FLD-013-001`.
   * *Action:* Updates status to `COMPLETED`, initiates payout release to traveler, and logs the justification.
7. **Refund Escrow Button (`BTN-013-003`):**
   * *Type:* Danger action button.
   * *Validation:* Disabled until `FLD-013-001` is filled.
   * *Action:* Updates status to `REFUNDED`, invokes payment gateway refund API, returns funds to shopper, releases capacity, and logs the justification.

---

## 3. UI State Variations

### A. Override Execution State
* Displays confirmation modal: `Are you sure you want to execute this escrow override? This action is permanent and will be logged.`
* On confirm, locks fields and displays progress loader.

---

## 4. Traceability

* **User Story:** [US-005-004](../../../../02-product/user-stories/admin/review-dispute.md#us-005-004-admin-dashboard--override-controls)
* **Requirement:** [Dispute Management and overrides](../../../02-product/requirements/feature-requirements.md#10-admin-dashboard--exception-handling)
