---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/00-governance/handoffs/HANDOFF-20260614-MT-6-PMA.md
---

# Handoff: Stable Domain Structure & Phase 1 Scope Refinement (MT-14)

*   **From**: Product Manager Agent (PMA)
*   **To**: Solution Architect Agent (SAA) / UX Designer Agent (UXA)
*   **Date**: 2026-06-14
*   **Ticket**: MT-14 (Stable Reorganization & Phase 1 Refinement)

---

## 1. Executive Summary

This handoff details the final alignments for the **My Trip My Titipan** Phase 1 MVP. Based on design reviews to prevent overlap and premature commitments, we restructured the files:

1.  **Phase 1 Flow Simplification:** `core-user-flow.md` is strictly limited to the Phase 1 Foundation happy path sequence diagram. All future phase extensions are removed.
2.  **Request Lifecycle Refactoring:** Sourcing, payment, and delivery status names are refactored to non-transactional terms: `Requested` → `Accepted` → `Processing` → `Completed` → `Reviewed`.
3.  **Flow Separation:** Splitting flows into `core-user-flow.md` (interaction sequence), `order-lifecycle.md` (state machine), `user-journey.md` (emotional journey), and `exception-flow.md` (failure paths).
4.  **Handoff Contract:** Formal PMA-to-UXA contract is created at [docs/02-product/planning/phases/phase-1-foundation/handoff.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/handoff.md).
5.  **Design Isolation:** Design assets (`wireframes/` and `mockups/`) contain only Phase 1 assets stored directly under their root directories. Phase-specific design subfolders are deleted to keep focus on current scope.

---

## 2. Reorganized Catalog

### Decisions (ADRs)
*   [ADR-001-remove-escrow.md](file:///d:/mytrip-mytitipan/docs/decisions/ADR-001-remove-escrow.md) — Context and decision for excluding payment gateways from Phase 1.
*   [ADR-002-phase1-scope-change.md](file:///d:/mytrip-mytitipan/docs/decisions/ADR-002-phase1-scope-change.md) — Scope refactoring to coordination record-keeping.

### Planning Phases
*   **Phase 1 (Foundation):**
    *   [scope.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/scope.md) — Baseline capabilities.
    *   [success-metrics.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/success-metrics.md) — Operational targets.
    *   [handoff.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/handoff.md) — Handoff contract ready for UXA.
*   **Phase 2 (Growth):**
    *   [scope.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-2-growth/scope.md) — Payment/escrow boundaries.
    *   [migration-impact.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-2-growth/migration-impact.md) — Schema and UI migration impacts.
*   **Phase 3 (Platform):**
    *   [scope.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-3-platform/scope.md) — Discovery and logistics boundaries.

### Flows
*   [core-user-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/core-user-flow.md) — Happy path interaction diagram.
*   [order-lifecycle.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/order-lifecycle.md) — Formal state machine logic.
*   [user-journey.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/user-journey.md) — Traveler/Shopper emotional journey mapping.
*   [exception-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/exception-flow.md) — Manual declines and cancellations.

### Use Cases (Subdivided by Actor)
*   [use-cases/README.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/README.md)
*   [use-cases/traveler/create-trip.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/traveler/create-trip.md) — UC-002: Publish Trip.
*   [use-cases/traveler/manage-request.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/traveler/manage-request.md) — UC-005: Request Lifecycle updates.
*   [use-cases/shopper/submit-request.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/shopper/submit-request.md) — UC-004: Submit Product Request.
*   [use-cases/shopper/confirm-delivery.md](file:///d:/mytrip-mytitipan/docs/02-product/use-cases/shopper/confirm-delivery.md) — UC-010/UC-011: Confirm receipt & reviews.

### User Stories (Subdivided by Actor)
*   [user-stories/README.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/README.md)
*   [user-stories/traveler/publish-trip.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/traveler/publish-trip.md) — US-002-001 (Publish Trip) and US-002-003 (Public profile).
*   [user-stories/traveler/view-request.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/traveler/view-request.md) — US-005-001 (Traveler dashboard list) and US-005-006 (Timeline log).
*   [user-stories/traveler/update-status.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/traveler/update-status.md) — US-005-005 (Manual state updates).
*   [user-stories/shopper/submit-request.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/shopper/submit-request.md) — US-001-001 (Register), US-001-002 (Login), and US-003-001 (Request form).
*   [user-stories/shopper/review-traveler.md](file:///d:/mytrip-mytitipan/docs/02-product/user-stories/shopper/review-traveler.md) — US-005-002 (Confirm receipt), US-005-003 (Submit review), and US-005-006 (Timeline log).

### Design Subfolder
*   `ux-research/`, `usability-testing/`, `information-architecture/`, `user-flow/`, `wireframes/`, `mockups/`, `design-system/`, `ui-assets/` — Restructured evergreen paths. Wireframe and mockup files reside directly under parent folders.

---

## 3. Recommended Next Agent

1.  **UX Designer Agent (UXA):** Read Phase 1 Handoff contract at `planning/phases/phase-1-foundation/handoff.md` and build wireframes in `wireframes/` and mockups in `mockups/`.
2.  **Solution Architect Agent (SAA):** Consume database schemas, transition maps in `flows/order-lifecycle.md` and user flows to prepare architecture plans.
