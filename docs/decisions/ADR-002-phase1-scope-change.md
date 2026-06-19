---
decision: Refactor MVP to Lightweight Record-Keeping Platform
date: 2026-06-14
status: approved
approved_by:
  - Product Manager Agent (PMA)
  - Lead Architect (Human)
---

# ADR-002: Refactor MVP to Lightweight Record-Keeping Platform

## Context

Prior iterations of the product roadmap prioritized building a high-fidelity e-commerce marketplace at launch, complete with automated baggage weight capacity slots, real-time logistics courier APIs, and government identity verification (KYC).

For early validation, this introduces high friction for user acquisition and requires operational overrides for complex exception cases (e.g. lost courier shipments, custom clearances).

## Decision

We have decided to refactor the Phase 1 MVP into a lightweight **Record-Keeping and Trip Coordination Tool**. 

The system validates the core hypothesis of whether Travelers and Shoppers will use a single structured platform to coordinate jastip lists instead of relying on unstructured messaging apps (Instagram Stories/WhatsApp chats).

## Consequences

*   **Baggage Capacity:** Automated weight calculations (kg) are removed. Baggage limitations are coordinated manually via optional trip notes.
*   **KYC / Identity:** KYC verification workflows are removed. User identity validation is managed by pre-existing social/network trust loops where travelers share direct links.
*   **Fulfillment States:** Restructured the order/request lifecycle to use five simple manual statuses: `Requested` → `Accepted` → `In Progress` → `Ready for Delivery` → `Completed`.
*   **Deferred Scope:** Courier API integrations, admin dashboards, and KYC verification are deferred to future stages (Phase 2 / Phase 3).
