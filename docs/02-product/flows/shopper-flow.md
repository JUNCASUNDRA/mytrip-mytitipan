---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-1
status: approved
priority: must-have
depends_on:
  - docs/02-product/planning/phases/phase-1-foundation/scope.md
outputs:
  - ux-flow
---

# Shopper Happy Path Flow

> **Status**: Approved **Last Updated**: 2026-06-14

This document captures the happy path sequence for Shoppers requesting items across Phase 1, Phase 2, and Phase 3.

---

## Phase 1 Behavior: Foundation MVP

The shopper interacts with the platform as a simple coordination tool:

1.  **Open Link:** Clicks the traveler's link shared via social media or WhatsApp.
2.  **Inspect Profile:** Inspects the traveler's profile page details (trip history, request completion history, past reviews).
3.  **Authentication:** Clicks "Request Item" and authenticates using Google OAuth or Email OTP.
4.  **Submit Request:** Fills the form (Item Name, Photo, URL, Quantity, Notes) and clicks "Submit Request" (status changes to `Requested`).
5.  **Status timelines:** Monitors request timeline status updates (`Requested` → `Accepted` → `Purchased` → `Delivered`).
6.  **Confirm Receipt:** Receives package physically, clicks "Confirm Receipt" (status changes to `Completed`).
7.  **Review Traveler:** Leaves a written text review and 1-5 star rating.

---

## Phase 2 Extension: Payments & Quotes

In Phase 2, payment and quote approvals are integrated:

1.  **Review Quote:** Shopper receives email notification for quote. Inspects Item Price, Jastip Fee, and total IDR.
2.  **Escrow Funding:** Click "Pay Now" and completes checkout payment widget (funds locked in platform escrow).
3.  **Logistics Tracking:** Inspects traveler's courier tracking number on the dashboard.
4.  **Delivery confirmation:** Confirming delivery releases escrow funds to traveler's bank account.

---

## Phase 3 Extension: Discovery Feed & Real-time Logistics

Phase 3 introduces internal discovery search and shipping detail maps:

1.  **Discovery Feed Search:** Shopper searches active trips by country/city destination.
2.  **Storefront ordering:** Shopper browses traveler storefront collections and submits structured requests from templates.
3.  **Fulfillment Map:** Click tracking code to view map showing shipment location.
