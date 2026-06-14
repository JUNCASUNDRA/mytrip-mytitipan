---
agent: UX Designer Agent (UXA)
version: 1.0.0
date: 2026-06-09
status: Draft
predecessor: docs/02-product/flows/transaction-flow.md
---

# User Flow

This directory contains the modularized UX user flows for the **My Trip My Titipan** MVP. The documentation is split into separate files to help developers and system architects read specific sections without parsing a single monolithic document.

## Actors

*   **Traveler**: The supply provider who publishes trips to share baggage capacity, reviews shopper requests, issues quotes, purchases items abroad using their own funds, ships them domestically, and receives the escrow payout.
*   **Shopper**: The demand creator who visits traveler trip pages, requests products, completes escrow payments, tracks order fulfillment, and reviews travelers.
*   **Admin**: The platform operator who oversees active trips and transactions, resolves escrow disputes, and processes manual refund/payout actions.

## Flow Map

Click the links below to view the specific flows and inventories:

1.  **[Traveler Flow](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/traveler-flow.md)**: Maps the complete traveler lifecycle from trip setup to final wallet payout.
2.  **[Shopper Flow](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/shopper-flow.md)**: Maps the shopper experience from finding a trip link to checkout and delivery confirmation.
3.  **[Admin Flow](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/admin-flow.md)**: Maps administrative audit capabilities and dispute resolution actions.
4.  **[Order Lifecycle](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/order-lifecycle.md)**: Focuses on backend-facing order state transitions, database triggers, and pre-payment vs. post-payment lifecycles.
5.  **[Screen Inventory](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/screen-inventory.md)**: Lists all 13 screens required for the MVP with unique Screen IDs for wireframe mapping.
6.  **[Notifications Map](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/notifications.md)**: Documents the transactional notification triggers, recipient targets, channels, and message templates.
7.  **[Exception and Dispute Flows](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/exception-flows.md)**: Details the step-by-step UX flows, triggers, and mechanics for handling cancellations, out-of-stock items, and escrow disputes.

*   [Transaction Flow](file:///d:/mytrip-mytitipan/docs/02-product/flows/transaction-flow.md)
*   [Business Flow](file:///d:/mytrip-mytitipan/docs/02-product/flows/business-flow.md)
*   [State Machine](file:///d:/mytrip-mytitipan/docs/02-product/flows/state-machine.md)
*   [User Journeys](file:///d:/mytrip-mytitipan/docs/02-product/flows/user-journey.md)
*   [MVP Definition](file:///d:/mytrip-mytitipan/docs/02-product/planning/mvp-definition.md)
*   [Feature Prioritization](file:///d:/mytrip-mytitipan/docs/02-product/planning/feature-prioritization.md)
*   [Product Requirements](file:///d:/mytrip-mytitipan/docs/02-product/requirements/product-requirements.md)
