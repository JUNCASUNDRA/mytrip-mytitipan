---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/wireframes/README.md
outputs:
  - scr-012-spec
depends_on:
  - user-stories/admin/review-dispute.md
---

# SCR-012: Admin Dashboard

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This is a desktop-first management dashboard layout allowing platform administrators to monitor transactional volume summaries, query records, and open transaction profiles.

---

## 1. ASCII Wireframe Layout

```text
-------------------------------------------------------------------------------------
| ADMIN PANEL |  Active Trips: 342  | Active Escrow Ledger: IDR 45,200,000  [Logout] |
-------------------------------------------------------------------------------------
| Search Orders / Users                                                             |
| [ input: search by Order ID, Shopper Name, or AWB...                 ] [Search]   |
|                                                                                   |
| ----------- System Transactions Log -----------                                   |
| Order ID | Shopper    | Traveler | Price       | Status      | Actions            |
| ORD-1002 | Maria      | Budi     | IDR 350,000 | PAID        | [View Details]     |
| ORD-1003 | Andi       | Maria    | IDR 620,000 | DISPUTED    | [Audit Dispute]    |
| ORD-1004 | Jenny      | Budi     | IDR 120,000 | EXPIRED     | [View Log]         |
| ORD-1005 | Clara      | Andi     | IDR 450,000 | COMPLETED   | [View Log]         |
-------------------------------------------------------------------------------------
```

---

## 2. UI Elements Specification

1. **System Statistics Header (`TXT-012-001`):**
   * Non-interactive labels showing active trips counts, total order volumes, and sum totals of escrow holdings currently locked.
2. **Search Input Field (`FLD-012-001`):**
   * *Type:* Text search box.
   * *Query Targets:* Order ID, User ID, transaction references, or courier tracking codes.
3. **Search Submit Trigger (`BTN-012-001`):**
   * Executed queries filters the transactions log table log results.
4. **Transactions Log Table (`TBL-012-001`):**
   * Relational grid listing columns: Order ID, Shopper Name, Traveler Name, total price, current status tag, and action triggers.
5. **View Details / Audit Button (`BTN-012-002`):**
   * Redirects admin to transaction details or `SCR-013: Admin Dispute Manager` for disputed orders.

---

## 3. UI State Variations

### A. Empty Search Results State
* If query yields no matches:
  * Hide table body.
  * Display alert panel: `No transaction records matching your query search found.`

---

## 4. Traceability

* **User Story:** [US-005-004](../user-stories/admin/review-dispute.md#us-005-004-admin-dashboard--override-controls)
* **Requirement:** [Admin Dashboard specification](../../02-product/requirements/feature-requirements.md#10-admin-dashboard--exception-handling)
