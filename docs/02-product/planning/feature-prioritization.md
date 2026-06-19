---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-1
status: approved
priority: must-have
depends_on:
  - core-user-flow.md
outputs:
  - ux-flow
  - technical-requirement
---

# Feature Prioritization (MoSCoW)

> **Status**: Approved **Last Updated**: 2026-06-14

This document strictly prioritizes features based on the Phase 1 MVP simplified requirements. Any feature outside the "Must Have" list is explicitly deferred to ensure a 3-month launch window and feasibility for a small engineering team.

## 1. Must Have (Phase 1 MVP - Month 1 to 3)

These are non-negotiable. Without these, the platform cannot function as a request-keeping coordination tool.

| Feature | Description | Reason |
| --- | --- | --- |
| **Trip Publisher** | Travelers can input travel destination, dates, optional notes and get a shareable URL. | Creates the supply loop. |
| **Product Request Form** | Shoppers can upload photo, URL, item name, quantity, and notes. No budget or payment required. | Captures structured shopper demand. |
| **Request Lifecycle Management** | Travelers review incoming requests and manually transition status: Requested → Accepted → In Progress → Ready for Delivery → Completed. | Replaces spreadsheets with a central tracking workflow. |
| **Request Timeline** | Users can view state change history logs for trust. | Since escrow is out of scope, the timeline history serves as the primary trust verification loop. |
| **Traveler Profile** | Public profiles showing traveler name, photo, trip history, request completion history, and reviews. | Builds trust through social proof and history instead of count indicators that start at 0. |
| **Reviews & Ratings** | Star ratings (1-5) and written feedback, triggered when shopper marks request as completed. | Core mechanism to build reputation. |
| **Simple Record History** | Persistent logs of completed requests and trip history. | Base database structure for future trust features. |

## 2. Should Have (V1.1 - Month 4)

These add significant value but are not strictly required for the first 100 requests.

| Feature | Description | Reason |
| --- | --- | --- |
| **Basic Email Notifications** | Email notifications sent when order status changes (e.g. accepted, in progress, ready for delivery). | Prevents users from needing to poll the platform. |

## 3. Could Have (V2.0 - Month 5 to 6)

| Feature | Description | Reason |
| --- | --- | --- |
| **In-App Notifications** | Native in-app notifications and badges. | Enhances mobile web user engagement. |

## 4. Won't Have (Deferred Indefinitely / Future Phases)

These features are explicitly removed from Phase 1 to minimize operational and engineering complexity.

| Feature | Description | Reason |
| --- | --- | --- |
| **Payment Gateway & Escrow** | Escrow holding, payment integration (Xendit/Midtrans), or checkout interfaces. | Validates request workflow adoption before introducing transaction complexities. |
| **Quotation Engine** | Forms and states for travelers to input Item Price, Jastip Fee, or negotiate total pricing. | Defer financial negotiation to external channels (e.g., chat) if needed. |
| **Baggage Capacity Automation** | Strict suitcase weight calculation (in kg) and automatic quote reservations. | Adds unnecessary database and logic complexity for early-stage validation. |
| **Quote Expiry & 24h Expiry Clock**| Automatic expiration timers for requests or quotes. | Unnecessary without payment constraints. |
| **Admin Dispute / Refund Overrides**| Admin dashboards to override transaction payments and trigger refunds. | Escrow is out of scope; hence disputes are settled offline. |
| **Logistics & Courier APIs** | Integration with local couriers (JNE/GoSend) or automated AWB generation. | Travelers handle shipping and delivery confirmation manually. |
| **KYC Identity Verification** | Government ID upload and admin approval for travelers. | Relies on pre-existing social trust and links sharing. |
| **In-App Chat** | Embedded instant messaging between shopper and traveler. | Causes massive scope creep; structured forms are sufficient. |
