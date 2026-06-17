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

# Traveler Happy Path Flow

> **Status**: Approved **Last Updated**: 2026-06-14

This document captures the happy path sequence for Travelers managing trips and requests across Phase 1, Phase 2, and Phase 3.

---

## Phase 1 Behavior: Foundation MVP

The happy path represents a manual record-keeping loop:

1.  **Authentication:** Register/login via Google OAuth or Email OTP.
2.  **Create Trip:** Input Destination, travel dates, and optional notes (space availability, preferred stores).
3.  **Copy shareable URL:** Share link externally (WhatsApp, Instagram bio).
4.  **Dashboard review:** Monitor incoming shopper requests.
5.  **Accept Request:** Review product info, URL, image, and click "Accept Request" (status changes to `Accepted`).
6.  **Sourcing/Procurement:** Sourced item abroad, click "Mark as Purchased" (status changes to `Purchased`).
7.  **Domestic shipping:** Return home, drop package at domestic courier, and click "Mark as Delivered" (status changes to `Delivered`).
8.  **Feedback view:** Once shopper confirms receipt, view shopper ratings/reviews history on the profile page.

---

## Phase 2 Extension: Escrow Payments & Quotations

In Phase 2, the traveler takes a more active financial and quoting role:

1.  **Quotation:** Traveler reviews incoming request, inputs Jastip Fee, Item Price in IDR, and Estimated weight. Sends Quote (status changes to `Quoted`).
2.  **Payment Watch:** Watch dashboard for successful shopper escrow payment.
3.  **Procurement Start:** Once payment gateway confirms escrow funding (`Paid`), traveler clicks "Start Sourcing" (status changes to `Purchasing`).
4.  **Courier Tracking:** Ship package domestically, enter tracking number in the system, and click "Mark Shipped" (status changes to `In Transit`).
5.  **Escrow Payout:** Receive bank transfer payout after shopper confirmation.

---

## Phase 3 Extension: Curation & Logistics Automation

Phase 3 automates shipping administration and allows curated recommend items:

1.  **Storefront Curation:** Traveler curates recommendations lists (e.g. "Tokyo Drugstore Must-Haves") on their profile storefront.
2.  **Auto Dispatch AWB:** From dashboard, click "Print Shipping Label". System calls courier dispatch API to generate shipping barcode. Drop package at courier (tracking number is registered automatically).
