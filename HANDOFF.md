# Project Handoff: Stable Domain Structure & Phase 1 Scope Refinement

This document outlines the final alignments for the **MyTrip - MyTitipan** Phase 1 MVP, focusing on trip sharing and request list coordination without transactional or escrow layers.

---

## 1. Document Architecture

We have restructured the directories as follows:
*   **Decisions (ADRs):** Global product decisions are documented at [docs/decisions/](file:///d:/mytrip-mytitipan/docs/decisions) to track key historical modifications for AI context.
*   **Flows:** Separated into [core-user-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/core-user-flow.md) (interaction diagram), [order-lifecycle.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/order-lifecycle.md) (state machine transitions), [user-journey.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/user-journey.md) (actor journeys), and [exception-flow.md](file:///d:/mytrip-mytitipan/docs/02-product/flows/exception-flow.md) (failure paths).
*   **Planning Phases:** 
    *   **Phase 1 (Foundation):** [scope.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/scope.md) and [success-metrics.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/success-metrics.md) detailing coordination loops.
    *   **Phase 2 (Growth):** [scope.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-2-growth/scope.md) and [migration-impact.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-2-growth/migration-impact.md) detailing transaction/escrow checkouts.
    *   **Phase 3 (Platform):** [scope.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-3-platform/scope.md) detailing discovery feeds & courier integrations.
*   **Design Folder Structure:** Restructured to remove digit prefixes. Wireframes and Mockups contain only Phase 1 assets located directly under [docs/03-design/wireframes/](file:///d:/mytrip-mytitipan/docs/03-design/wireframes/) and [docs/03-design/mockups/](file:///d:/mytrip-mytitipan/docs/03-design/mockups/).

---

## 2. Updated References

*   **PMA Handoff Contract (Phase 1):** Located at [docs/02-product/planning/phases/phase-1-foundation/handoff.md](file:///d:/mytrip-mytitipan/docs/02-product/planning/phases/phase-1-foundation/handoff.md) specifically targetting the **UX Designer Agent (UXA)**.
*   **Order Status Transitions:** Status values are refactored to non-transactional terms: `Requested` → `Accepted` → `Processing` → `Completed` → `Reviewed`.
*   **Usability Testing logs:** Located at [docs/03-design/usability-testing/](file:///d:/mytrip-mytitipan/docs/03-design/usability-testing/README.md).

---

## 3. Next Steps
*   **UX Designer Agent (UXA):** Read the Phase 1 Handoff contract and generate layout designs directly inside `wireframes/` and `mockups/`.
