---
agent: UX Designer Agent (UXA)
version: 1.0.0
date: 2026-06-09
status: Draft
predecessor: docs/03-design/user-flow/README.md
---

# Handoff: UX User Flow Design (MT-13)

*   **From**: UX Designer Agent (UXA)
*   **To**: Solution Architect Agent (SAA) / Domain Architect Agent (DAA)
*   **Date**: 2026-06-09
*   **Ticket**: MT-13 (Initialize Design Documentation)

---

## 1. Executive Summary

In this phase, the product requirements, user journeys, and core flows were successfully translated into a concrete, mobile-first **UX User Flow** mapping. The resulting artifact has been written to [docs/03-design/user-flow/README.md](file:///d:/mytrip-mytitipan/docs/03-design/user-flow/README.md).

This flow strictly adheres to the MVP constraints, omitting all V2 features (no in-app chat, no discovery feed, no KYC, no creator storefronts) and focuses on establishing the core escrow-based request-and-fulfillment transaction loop.

---

## 2. Key Decisions

*   **Mobile-First Navigation**: All screens and actions are optimized for mobile web integration, since shoppers and travelers primarily interact on social media and mobile messaging apps.
*   **Luggage Capacity Management**: Implemented a two-stage capacity process:
    1.  *Reservation (Temporary)*: Initiated during the `Quoted` state, expiring automatically after 24 hours if unpaid to prevent luggage lockups.
    2.  *Lock (Confirmed)*: Secured during the `Paid` state when the shopper completes the escrow payment.
*   **Trust Mechanics Without KYC**: Due to KYC deferral to V2, trust is built through public profiles showing verified transaction histories (completed trips and orders counts), star ratings, and detailed text reviews.
*   **No In-App Chat**: The flow uses comprehensive structured request and quote forms, supported by transactional notifications, to avoid the security and operational complexities of in-app messaging.

---

## 3. Deliverables Produced

*   **User Flow Overview**: Defines roles and interactions of the **Traveler**, **Shopper**, and **Admin** actors.
*   **Traveler User Flow**: Flowchart and detailed steps from trip creation and capacity sharing to domestic shipment and escrow payout.
*   **Shopper User Flow**: Flowchart and detailed steps from shared link click to checkout, tracking, and review submission.
*   **Admin User Flow**: Flowchart and steps for active trip oversight, transaction audits, and dispute/refund resolutions.
*   **Screen Inventory**: Details 13 screens required for the MVP, including primary call-to-actions and navigation paths.
*   **State Transitions**: Maps the database-friendly Request and Fulfillment lifecycles (Requested, Quoted, Payment Pending, Paid, Purchased, In Transit, Delivered, Completed) alongside Expiry and Cancellation paths.
*   **UX Notes**: Outlines potential user confusion points, error states, empty states, and a required notification trigger matrix.

---

## 4. Remaining Risks & Considerations

1.  **Traveler Capital Risk**: Travelers must pay out-of-pocket for items abroad before receiving escrow payouts. Clear UI micro-copy is required to reassure travelers that shopper funds are guaranteed and held in escrow.
2.  **Tracking Validation**: Handled by manual tracking number input. SAA/DAA must design backend validators to verify input format for local courier APIs.
3.  **Dispute Volume**: If a traveler goes missing or buys the wrong item, the admin must manually intervene. The DAA must design clear state pathways for admin-triggered cancellations/refunds.

---

## 5. Next Steps

1.  **Strategy Sign-off**: Obtain approval from the Human Gatekeeper (Business/Product Owner) for Gate 1.
2.  **Architecture Transition**: Hand off these flows to the **Solution Architect Agent (SAA)** and **Domain Architect Agent (DAA)** to begin database design and API specification updates.
