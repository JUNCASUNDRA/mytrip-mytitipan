---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/user-flow/README.md
---

# UX Design Phase Handoff (HANDOFF.md)

*   **From**: UX Designer Agent (UXA)
*   **To**: Solution Architect Agent (SAA) / Domain Architect Agent (DAA)
*   **Date**: 2026-06-14
*   **Ticket**: MT-13 (Initialize Design Documentation & Alignment)

---

## 1. Completed Flows

The UX user flows have been updated and validated to align with the latest **PMA Gate 1** product requirements and state-machine transitions:

1.  **[Traveler Flow](user-flow/traveler-flow.md)**: Details the traveler's happy path from authentication and trip creation, through link sharing, quote generation, procurement (`PURCHASING` & `PURCHASED`), domestic courier shipping, and balance payout.
2.  **[Shopper Flow](user-flow/shopper-flow.md)**: Maps the shopper's journey from landing on a shared link, submitting requests, reviewing quotes, escrow virtual account/e-wallet payments, tracking updates, and receipt confirmation.
3.  **[Admin Flow](user-flow/admin-flow.md)**: Operational interface flow for auditing transactions, listing active journeys, and manual override capabilities.
4.  **[Exception & Dispute Flows](user-flow/exception-flows.md)**: Detailed step-by-step resolution pathways for out-of-stock items, quote expiry, traveler cancellation, lost courier packages, and item damage.
5.  **[Notifications Map](user-flow/notifications.md)**: Synced to use **Email** as the primary MVP channel for critical milestones, while marking **Web Push** as deferred (Should Have V1.1).

---

## 2. Screens Created (Screen Inventory)

*   **[wireframes/](wireframes/)**: Restructured to house 13 detailed screen layout specs:
    - [scr-001-login.md](wireframes/scr-001-login.md) through [scr-013-admin-dispute.md](wireframes/scr-013-admin-dispute.md).
    - [README.md](wireframes/README.md) [UPDATED]: Centralized dashboard indexing the spec files, with all out-of-scope Home Feed screens removed.
    - Embedded 6 visual PNG mockups directly inside key screen specs (`SCR-002`, `SCR-003`, `SCR-004`, `SCR-005`, `SCR-006`, and `SCR-010`).

*   **[SCR-001: Login / Register](wireframes/README.md#scr-001-login--register)**: Mobile authentication view via Google SSO or Email-OTP.
*   **[SCR-002: Trip Landing Page](wireframes/README.md#scr-002-trip-landing-page)**: Publicly accessible trust screen with dates, routes, baggage weight bars, and active request CTA.
*   **[SCR-003: Product Request Form](wireframes/README.md#scr-003-product-request-form)**: Structured item description, URL input, and photo uploader.
*   **[SCR-004: Shopper Dashboard](wireframes/README.md#scr-004-shopper-dashboard)**: Tracking space for active orders, invoice status, and receipt release CTAs.
*   **[SCR-005: Quote & Checkout Page](wireframes/README.md#scr-005-quote--checkout-page)**: Pricing invoice breakdown (Item Price + Jastip Fee) with payment gateway checkout controls.
*   **[SCR-006: Traveler Dashboard](wireframes/README.md#scr-006-traveler-dashboard)**: Traveler core space tracking trips, baggage capacities, incoming requests, and payout balance.
*   **[SCR-007: Create Trip Form](wireframes/README.md#scr-007-create-trip-form)**: Route inputs, date selectors, and suitcase capacity limits (kg).
*   **[SCR-008: Trip Share Modal](wireframes/README.md#scr-008-trip-share-modal)**: Copyable link widget with WhatsApp/Instagram share actions.
*   **[SCR-009: Request Review Screen](wireframes/README.md#scr-009-request-review-screen)**: Detail review card where travelers accept requests and specify price details.
*   **[SCR-010: Traveler Order Details](wireframes/README.md#scr-010-traveler-order-details)**: Sourcing milestone updates (mark purchasing, mark purchased, upload receipts) and domestic courier input (JNE, J&T, Sicepat + AWB).
*   **[SCR-011: Review Submission](wireframes/README.md#scr-011-review-submission)**: Star and feedback rating inputs to close the trust loop.
*   **[SCR-012: Admin Dashboard](wireframes/README.md#scr-012-admin-dashboard)**: Desktop overview auditing system stats and lists of transactions.
*   **[SCR-013: Admin Dispute Manager](wireframes/README.md#scr-013-admin-dispute-manager)**: Detail view for manual transaction release or refund overrides with mandatory justification log inputs.

---

## 3. Open Questions

1.  **Automated Shipping Verification**: For `SCR-010`, can we integrate with third-party logistics APIs (e.g., RajaOngkir/Biteship) to auto-verify tracking code format in the MVP, or is simple alphanumeric regex validation sufficient? (Regex recommended to keep MVP simple).
2.  **Extended Disputes Evidence**: When a shopper raises a dispute in `SCR-013` for damage, should they upload a video showing unboxing? (Highly recommended to document as a guideline in the help screens).

---

## 4. Risks & Mitigations

*   **Risk 1: Traveler Capital Risk Anxiety**:
    *   *Description:* Traveler pays out-of-pocket for items before receiving payouts, causing checkout hesitation.
    *   *Mitigation:* Clear green "Escrow Secured 🔒" indicators on `SCR-006` and `SCR-010` to visually guarantee that the buyer's money is successfully locked by the platform.
*   **Risk 2: Suitcase Overbooking under Concurrent Requests**:
    *   *Description:* Multiple shoppers attempting to pay quotes concurrently for a trip with limited capacity.
    *   *Mitigation:* Automatic status update to `EXPIRED` or checkout block once trip available capacity hits zero.
*   **Risk 3: Unresponsive Shoppers locking Suitcase Space**:
    *   *Description:* Shoppers requesting items but not paying, keeping capacity reserved indefinitely.
    *   *Mitigation:* Strict 24-hour expiration window in `SCR-005` that automatically releases reservation weights.
