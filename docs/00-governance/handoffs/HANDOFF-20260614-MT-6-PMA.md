---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/00-governance/handoffs/HANDOFF-20260609-MT-13-UXA.md
---

# Handoff: Core User Flow & Status Lifecycle Refinement (MT-6)

*   **From**: Product Manager Agent (PMA)
*   **To**: Solution Architect Agent (SAA)
*   **Date**: 2026-06-14
*   **Ticket**: MT-6 (Update Core Product Documentation)

---

## 1. Executive Summary

This phase completes the refinement of the **Core User Flow** and **MVP Order Status Lifecycle** based on user feedback. The statuses and transition sequences have been updated to properly align with standard payment gateway behaviors (Created/Pending -> Success/Failed/Expired) and Traveler procurement operations. 

All strategic, product planning, use case, user story, and user flow design files have been synchronized to utilize the updated transaction flow and order lifecycle states.

---

## 2. Key Decisions

*   **Authentication Abstraction**: Removed low-level OTP/Google specifics from the core traveler setup flow to keep product journey steps focused on core business loops.
*   **Trip Landing Page Definition**: Replaced generic "Trip View" steps with a structured "Trip Landing Page" layout which functions as the platform's primary trust layer (displaying traveler reputation, route timeline, baggage availability, and a Request CTA).
*   **Quotation-Driven Capacity Reservation**: Reordered matching and quote actions. Case baggage capacity is reserved *strictly* upon quote generation by the traveler, not upon initial shopper request, successfully resolving potential concurrent overbooking conflicts.
*   **Payment Gateway Direct Expiry**: Refined payment status paths. If checkouts fail or session timers close on the gateway (Xendit/Midtrans), the transaction transitions directly to `Expired` (releasing suitcase capacity) instead of staying open indefinitely in a pending loop.
*   **Fulfillment Procurement Stage (`PURCHASING`)**: Integrated a new `Purchasing` order state between `Paid` and `Purchased` to indicate that a traveler is active in the travel/shopping phase.
*   **Receipt Verification**: Added an optional upload of a receipt or item photo during the "Mark as Purchased" action to increase shopper confidence and overall trust.
*   **Unified Notifications**: Phrased notifications abstractly as "System notifies [User]" to decouple channel configurations from the core interaction flow.

---

## 3. Deliverables Produced

The following files have been modified and synchronized:
*   **[core-user-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/core-user-flow.md)**: Updated end-to-end steps and request/fulfillment tables.
*   **[mvp-definition.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/mvp-definition.md)**: Updated order status checklist.
*   **[product-roadmap.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/product-roadmap.md)**: Updated Month 3 Deliverables.
*   **[feature-prioritization.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/feature-prioritization.md)**: Updated basic order status definition.
*   **[user-journey.md](file:///d:/mytrip-mytitipan/docs/02-product/strategy/user-journey.md)**: Updated trusted traveler and shopper journey timelines.
*   **[use-case-specifications.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/use-case-specifications.md)**: Refined UC steps, renamed email notifications, and added **UC-016 (Procure & Purchase Item)**.
*   **[ep-004-quotation.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/ep-004-quotation.md)**: Updated acceptance criteria for quotations, capacity releases, and notification paths.
*   **[ep-005-order-management.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/ep-005-order-management.md)**: Updated order timeline table and added **US-005-005 (Procure & Purchase Item)**.
*   **[ep-006-escrow-payment.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/ep-006-escrow-payment.md)**: Added scenario for failed/expired payment webhook.
*   **[order-lifecycle.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/order-lifecycle.md)**: Updated status transition matrix and Mermaid diagrams.
*   **[exception-flows.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/exception-flows.md)**: Updated Scenario B/C/D transition logics and mermaid flowchart.

---

## 4. Next Steps

1.  **Solution Architect Handoff**: Obtain human approval to transition from strategy/requirements validation (PMA) to technical design (SAA).
2.  **Database DDL Update**: Solution Architect Agent (SAA) and Domain Architect Agent (DAA) should update [database-design.md](file:///d:/mytrip-mytitipan/docs/04-technical/database-design.md) with the new `status` enum values (`PURCHASING`, `REFUNDED`).
3.  **API Contract Refinement**: Update API specs under `docs/04-technical/api-specification/` to handle webhook callback models from Midtrans/Xendit matching these states.
