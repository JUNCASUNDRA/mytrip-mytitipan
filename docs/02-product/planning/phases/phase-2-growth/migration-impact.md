---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-2
status: draft
priority: should-have
depends_on:
  - scope.md
outputs:
  - migration-strategy
---

# Migration Impact: Phase 1 to Phase 2

> **Status**: Draft **Last Updated**: 2026-06-14

This document captures the technical and user-experience impacts of transitioning from Phase 1 Foundation to Phase 2 Growth.

---

## 1. Database Schema Changes
*   **Order Statuses:** Introduce database enum expansion from `Requested`, `Accepted`, `In Progress`, `Ready for Delivery`, `Completed` to:
    *   `Quoted`
    *   `Payment Pending`
    *   `Paid`
    *   `Purchasing`
    *   `Purchased`
    *   `In Transit`
    *   `Delivered`
*   **Billing Ledger:** Add transactional tables (`ledger_entries`, `invoices`, `payout_records`).
*   **Traveler KYC:** Add verification status fields to `users` profile table.

---

## 2. UX & Flow Extensions
*   **Quoting Step:** Insert Traveler quote input dialogs after request review.
*   **Checkout Step:** Insert Shopper payment widget screen before request acceptance is confirmed.
*   **Baggage Capacity:** Show remaining baggage space in kilograms on trip publishing and request validation.
