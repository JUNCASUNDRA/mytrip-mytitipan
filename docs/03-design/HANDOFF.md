---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/03-user-flow/README.md
---

# UX Design Phase Handoff (HANDOFF.md)

*   **From**: UX Designer Agent (UXA)
*   **To**: Solution Architect Agent (SAA) / Domain Architect Agent (DAA)
*   **Date**: 2026-06-14
*   **Ticket**: MT-13 (Initialize Design Documentation & Alignment)

---

## 1. Completed Flows & Structure

The UX design framework and user flows have been updated and validated to align with the latest **PMA Gate 1** product requirements and state-machine transitions:

1.  **[UX Research Principles](01-ux-research/ux-principles.md)** & **[Usability Assumptions](01-ux-research/usability-assumptions.md)**: Establishes invisible trust design patterns, capacity color coding, and anxiety triggers.
2.  **[User Pain Points](01-ux-research/user-pain-points.md)**: Details the specific friction points for travelers/shoppers and their mitigations.
3.  **[Information Architecture Navigation Map](02-information-architecture/navigation-map.md)**, **[Site Map](02-information-architecture/sitemap.md)**, & **[Screen Inventory](02-information-architecture/screen-inventory.md)**: Maps application routes, role selectors, permission boundaries, and MVP screen indexes.
4.  **[Traveler Flow](03-user-flow/traveler-flow.md)**: Details the traveler's happy path from authentication and trip creation, through link sharing, quote generation, procurement, domestic courier shipping, and balance payout.
5.  **[Shopper Flow](03-user-flow/shopper-flow.md)**: Maps the shopper's journey from landing on a shared link, submitting requests, reviewing quotes, escrow payments, tracking updates, and receipt confirmation.
6.  **[Admin Flow](03-user-flow/admin-flow.md)**: Rebuilt desktop interface flow detailing metrics widgets and resolution actions (refund/release modal justifications).
7.  **[Exception & Dispute Flows](03-user-flow/exception-flows.md)**: Detailed step-by-step resolution pathways for out-of-stock items, quote expiry, traveler cancellation, lost courier packages, and item damage.
8.  **[Notification Flow](03-user-flow/notification-flow.md)**: Synced to use **Email** as the primary MVP channel for critical milestones, while marking **Web Push** as deferred.

---

## 2. Screens Created (Screen Inventory)

*   **[04-wireframes/](04-wireframes/)**: Restructured to house 13 detailed screen layout specs grouped by actor role:
    *   **Common/**:
        *   [login.md](04-wireframes/common/login.md) (`SCR-001`): Mobile authentication view via Google SSO or Email-OTP.
    *   **Shopper/**:
        *   [trip-page.md](04-wireframes/shopper/trip-page.md) (`SCR-002`): Publicly accessible trust screen with dates, routes, baggage weight bars, and active request CTA.
        *   [request-form.md](04-wireframes/shopper/request-form.md) (`SCR-003`): Structured item description, URL input, and photo uploader.
        *   [shopper-dashboard.md](04-wireframes/shopper/shopper-dashboard.md) (`SCR-004`): Tracking space for active orders, invoice status, and receipt release CTAs.
        *   [checkout.md](04-wireframes/shopper/checkout.md) (`SCR-005`): Pricing invoice breakdown (Item Price + Jastip Fee) with payment gateway checkout controls.
        *   [review-submission.md](04-wireframes/shopper/review-submission.md) (`SCR-011`): Star and feedback rating inputs to close the trust loop.
    *   **Traveler/**:
        *   [trip-dashboard.md](04-wireframes/traveler/trip-dashboard.md) (`SCR-006`): Traveler core space tracking trips, baggage capacities, incoming requests, and payout balance.
        *   [create-trip.md](04-wireframes/traveler/create-trip.md) (`SCR-007`): Route inputs, date selectors, and suitcase capacity limits (kg).
        *   [trip-share.md](04-wireframes/traveler/trip-share.md) (`SCR-008`): Copyable link widget with WhatsApp/Instagram share actions.
        *   [request-detail.md](04-wireframes/traveler/request-detail.md) (`SCR-009`): Detail review card where travelers accept requests and specify price details.
        *   [order-details.md](04-wireframes/traveler/order-details.md) (`SCR-010`): Sourcing milestone updates (mark purchasing, mark purchased, upload receipts) and domestic courier input (JNE, J&T, Sicepat + AWB).
    *   **Admin/**:
        *   [dashboard.md](04-wireframes/admin/dashboard.md) (`SCR-012`): Desktop overview auditing system stats and lists of transactions.
        *   [dispute.md](04-wireframes/admin/dispute.md) (`SCR-013`): Detail view for manual transaction release or refund overrides with mandatory justification log inputs.
    *   Embedded 6 visual PNG mockups directly inside the `05-mockups/` subfolders mapped from these specs (`trip-page`, `request-form`, `shopper-dashboard`, `checkout`, `trip-dashboard`, and `order-details`).

---

## 3. Open Questions

1.  **Automated Shipping Verification**: For traveler order details, can we integrate with third-party logistics APIs (e.g., RajaOngkir/Biteship) to auto-verify tracking code format in the MVP, or is simple alphanumeric regex validation sufficient? (Regex recommended to keep MVP simple).
2.  **Extended Disputes Evidence**: When a shopper raises a dispute in the admin dispute resolver for damage, should they upload a video showing unboxing? (Highly recommended to document as a guideline in the help screens).

---

## 4. Risks & Mitigations

*   **Risk 1: Traveler Capital Risk Anxiety**:
    *   *Description:* Traveler pays out-of-pocket for items before receiving payouts, causing checkout hesitation.
    *   *Mitigation:* Clear green "Escrow Secured 🔒" indicators on `trip-dashboard.md` and `order-details.md` to visually guarantee that the buyer's money is successfully locked by the platform.
*   **Risk 2: Suitcase Overbooking under Concurrent Requests**:
    *   *Description:* Multiple shoppers attempting to pay quotes concurrently for a trip with limited capacity.
    *   *Mitigation:* Automatic status update to `EXPIRED` or checkout block once trip available capacity hits zero.
*   **Risk 3: Unresponsive Shoppers locking Suitcase Space**:
    *   *Description:* Shoppers requesting items but not paying, keeping capacity reserved indefinitely.
    *   *Mitigation:* Strict 24-hour expiration window in `checkout.md` that automatically releases reservation weights.

