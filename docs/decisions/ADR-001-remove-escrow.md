---
decision: Remove Escrow from Phase 1 MVP
date: 2026-06-14
status: approved
approved_by:
  - Product Manager Agent (PMA)
  - Lead Architect (Human)
---

# ADR-001: Remove Escrow from Phase 1 MVP

## Context

The original MVP definition for MyTrip - MyTitipan included a full transactional checkout pipeline, local payment gateway integrations (Midtrans/Xendit), escrow-style fund holding, and automated capacity locking.

Integrating these capabilities immediately introduces significant operational and engineering complexity (handling currency conversions, payment webhooks, split-transaction failures, refund exceptions, dispute management, and compliance rules).

## Decision

We have decided to **completely remove** all payment, escrow, checkout, and financial processing features from the Phase 1 MVP.

Instead, the product is repositioned as a **Jastip Request Management & Trip Coordination Tool**. All cash/payment exchanges are handled offline directly between the Traveler and the Shopper.

## Consequences

*   **Engineering Effort:** Reduced development time from 3 months of heavy integration down to 1 month of simple status coordination.
*   **Trust Layer Shift:** Since escrow is removed, platform trust will be built on public rating/reviews and a visible **Request Timeline** detailing status transitions.
*   **Operational Risk:** Platform holds zero financial risk, liability, or compliance overhead for peer-to-peer exchanges during early validation.
*   **Deferred Scope:** Payment Gateway integrations and escrow ledgers are deferred to Phase 2.
