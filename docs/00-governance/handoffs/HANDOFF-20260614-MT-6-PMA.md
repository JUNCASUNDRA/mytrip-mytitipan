---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/00-governance/handoffs/HANDOFF-20260609-MT-13-UXA.md
---

# Handoff: Core User Flow, Lifecycle & Feature Prioritization Refinement (MT-6)

*   **From**: Product Manager Agent (PMA)
*   **To**: Solution Architect Agent (SAA)
*   **Date**: 2026-06-14
*   **Ticket**: MT-6 (Update Core Product Documentation)

---

## 1. Executive Summary

This phase completes the final refinement of the **Core User Flow**, **MVP Order Status Lifecycle**, and **Feature Prioritization (MoSCoW)** based on detailed PMA review feedback. The documents are now aligned with payment gateway mechanics, traveler workflows, and monorepo governance standards. 

All documentation is finalized and ready for **Gate 1 PMA Approval** and transition to the Solution Architect Agent (SAA).

---

## 2. Key Decisions

*   **Validation Metrics**: Added explicit metrics to validate the core hypothesis (quotation success rates, escrow payment completion rates, repeat usage metrics).
*   **Traveler Profile & Trip Page Separation**: Split Traveler Profile (social proof, ratings, reviews) and Traveler Trip Page (route details, timelines, status CTAs) to align database design abstractions.
*   **Quotation Request Review**: Clarified that travelers must first review incoming requests before accepting and generating quotes, preventing forced quoting on high-volume requests.
*   **Refined Capacity Wording**: Capacity management logic explicitly details that reservation occurs when quotes are sent (expiring in 24 hours), and baggage slots are strictly locked only post-payment.
*   **Payment Gateway Direct Expiry**: Refined checkout flows to transition directly from `Payment Pending` to `Expired` upon gateway webhook callbacks for failures/expirations, rather than remaining open.
*   **Fulfillment Procurement Stage (`PURCHASING`)**: Integrated the `Purchasing` order state between `Paid` and `Purchased` to indicate active traveler travel/shopping.
*   **Receipt Verification**: Added optional receipt upload to traveler purchase marking to enhance platform trust.
*   **Split Notification Scope**: Standardized **Basic Notifications** (Email) as a "Must Have" MVP feature, while deferring **In-App & Push Notifications** to "Should Have" (V1.1).
*   **Traveler Identity Verification (KYC)**: Positioned KYC strictly as a "V2 Trust Enhancement" under the "Could Have" scope, aligned with the invisible trust strategy.
*   **Escrow-Style Messaging**: Adjusted wording around payment gateway to "escrow-style fund holding workflow" to match Indonesian payment standards.
*   **Strict Scope on Partial Payments**: Explicitly deferred **Partial Payment** or deposits to the "Won't Have" category to prevent developers from adding premature financial schema complexities.
*   **Manual Exception Handling**: Formally documented transaction exceptions (out-of-stock, cancellations, refunds, shipping issues) to provide a manual safety net for disputes.

---

## 3. Deliverables Produced

The following files have been modified and synchronized:
*   **[core-user-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/core-user-flow.md)**: Updated steps and request/fulfillment lifecycle definitions.
*   **[feature-prioritization.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/feature-prioritization.md)**: Standardized front matter metadata (outputs/depends_on), updated quotation, capacity, and escrow priorities, added email notifications to Must Have, and partial payment to Won't Have.
*   **[mvp-definition.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/mvp-definition.md)**: Updated order status checklist.
*   **[product-roadmap.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/product-roadmap.md)**: Updated deliverables in roadmap.
*   **[user-journey.md](file:///d:/mytrip-mytitipan/docs/02-product/strategy/user-journey.md)**: Integrated procurement and receipt upload stages.
*   **[use-case-specifications.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/use-case-specifications.md)**: Refined UC steps and added **UC-016 (Procure & Purchase Item)**.
*   **[ep-004-quotation.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/ep-004-quotation.md)**: Adjusted quote capacity rules and notification channels.
*   **[ep-005-order-management.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/ep-005-order-management.md)**: Added **US-005-005 (Procure & Purchase Item)**.
*   **[ep-006-escrow-payment.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/ep-006-escrow-payment.md)**: Added webhook failure transition scenario.
*   **[order-lifecycle.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/order-lifecycle.md)**: Updated design status transition matrix and diagrams.
*   **[exception-flows.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/exception-flows.md)**: Updated scenarios and exceptions flowchart.

---

## 4. Next Steps

1.  **PMA Strategy Sign-off (Gate 1)**: Business owner reviews and signs off on the PMA strategy deliverables.
2.  **Solution Architect Handoff**: Solution Architect Agent (SAA) consumes this handoff log and begins the high-level system architecture and DDL schema specifications.
