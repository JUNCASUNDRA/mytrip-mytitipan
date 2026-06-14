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

The product documentation structure has been completely reorganized and synchronized to enable down-funnel agent handoffs. The following deliverables have been produced:

### A. Planning & Flows
*   **[roadmap.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/roadmap.md)** [RENAMED]: Replaces `product-roadmap.md` with updated references.
*   **[business-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/business-flow.md)** [NEW]: High-level process milestones and platform guardrails.
*   **[state-machine.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/state-machine.md)** [NEW]: Detailed transition mapping for all order states and baggage capacity checks.

### B. Requirements & Specs
*   **[product-requirements.md](file:///d:/mytrip-mytitipan/docs/02-product/requirements/product-requirements.md)** [NEW]: Standard platform SLA limits, currency conversion rules, and error handling policies.
*   **[feature-requirements.md](file:///d:/mytrip-mytitipan/docs/02-product/requirements/feature-requirements.md)** [NEW]: Functional feature specifications and input validations for Must Have and Should Have features.

### C. Use Case Specifications [SPLIT & REORGANIZED]
*   **[traveler-usecases.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/traveler-usecases.md)** [NEW]: Formally documents Traveler use cases (`UC-001`, `UC-002`, `UC-005`, `UC-009`, `UC-015`, `UC-016`).
*   **[shopper-usecases.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/shopper-usecases.md)** [NEW]: Formally documents Shopper use cases (`UC-001`, `UC-003`, `UC-004`, `UC-007`, `UC-008`, `UC-010`, `UC-011`).
*   **[admin-usecases.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/admin-usecases.md)** [NEW]: Formally documents Admin and System automation use cases (`UC-012`, `UC-006`, `UC-013`, `UC-014`).
*   **[README.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/README.md)** [UPDATED]: Updated to link to actor-specific use case files.
*   *Deleted obsolete `use-case-specifications.md`.*

### D. User Stories [SPLIT & REORGANIZED BY ACTOR]
*   **[traveler/](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/traveler/)** [NEW]: Subfolder housing traveler stories:
    - `create-trip.md`: Stories `US-002-001`, `US-002-002`, `US-002-003`.
    - `review-request.md`: Story `US-005-001`.
    - `send-quote.md`: Stories `US-004-001`, `US-004-002`, `US-004-003`, `US-005-005`.
*   **[shopper/](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/shopper/)** [NEW]: Subfolder housing shopper stories:
    - `submit-request.md`: Stories `US-001-001`, `US-001-002`, `US-003-001`.
    - `pay-order.md`: Story `US-006-001`.
    - `confirm-delivery.md`: Stories `US-005-002`, `US-005-003`.
*   **[admin/](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/admin/)** [NEW]: Subfolder housing admin stories:
    - `review-dispute.md`: Story `US-005-004`.
*   **[README.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/README.md)** [UPDATED]: Updated index mapping for actor-based stories.
*   *Deleted obsolete epic files `ep-001` through `ep-006`.*

### E. Design & Navigation Link Syncing
*   **[README.md](file:///d:/mytrip-mytitipan/docs/README.md)** [UPDATED]: Synchronized global documentation hub links.
*   **[README.md](file:///d:/mytrip-mytitipan/docs/02-product/README.md)** [UPDATED]: Synced product doc tables with new directory tree.
*   **[README.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/README.md)** [UPDATED]: Added references to new flows and requirements.
*   **[order-lifecycle.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/order-lifecycle.md)** [UPDATED]: Synced predecessor header links.
*   **[exception-flows.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/exception-flows.md)** [UPDATED]: Synced predecessor header links.

---

## 4. Next Steps

1.  **Gate 1 Sign-off**: Verify formatting and merge this PRD/governance package.
2.  **Solution Architect Handoff**: Solution Architect Agent (SAA) consumes this package to structure technical architecture.
