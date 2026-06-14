---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/strategy/user-persona.md
outputs:
  - usability-assumptions
depends_on:
  - user-persona.md
---

# Usability Assumptions & UX Solutions

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document outlines the core usability assumptions regarding shopper and traveler behaviors, their associated risks, and the UX solutions implemented inside the platform.

---

## 1. User Behavior Assumptions

### A. The Shopper
* **Discovery Context:** Shoppers discover travelers via external social media posts on mobile phones, expecting quick conversions.
* **Risk Tolerance:** Low tolerance for prepaying individuals directly. Shoppers require platform escrow assurance before checking out.
* **Communication preference:** Prefer structured item detail forms over chaotic chat negotiations.

### B. The Traveler
* **Sourcing Context:** Sourcing takes place while traveling, where internet connectivity might be intermittent or limited.
* **Risk Tolerance:** High anxiety regarding out-of-pocket capital risk. Travelers will not buy items abroad unless they are 100% sure the shopper's money is locked in escrow.
* **Administrative Load:** Travelers want a simplified list of what to buy and when to ship without administrative overhead.

---

## 2. UX Risk & Solution Matrix

| Usability Risk / Concern | Target Actor | UX Solution / Mechanism | Screen Mapping |
| :--- | :--- | :--- | :--- |
| **Capital Sourcing Anxiety** | Traveler | Display a prominent green lock badge (`Escrow Secured 🔒`) on the dashboard and order card as soon as payment completes. Tooltip microcopy guarantees payout upon courier shipment. | `SCR-006`, `SCR-010` |
| **Baggage Overbooking** | Traveler | System checks remaining capacity and disables quote proposal buttons if the estimated weight exceeds remaining trip capacity. | `SCR-009` |
| **Unpaid Quote Hold** | Traveler | Clear countdown timer displaying the 24-hour expiration rule to shoppers. Auto-expiry returns suitcase weight to traveler availability immediately. | `SCR-004`, `SCR-005` |
| **Checkout Abandonment** | Shopper | Unauthenticated shoppers can fill out request details without login barrier. Session drafts are stored, and redirect to login OTP happens only at final submission. | `SCR-002` -> `SCR-003` |
| **Disputed Deliveries** | Traveler & Shopper | Mandatory rationale input in Admin dispute manager audits. Courier tracking numbers link to external shipping status webhooks to verify dispatch validity. | `SCR-013` |
