---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/planning/mvp-definition.md
---

# Product Roadmap

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-14

This roadmap aligns engineering effort with the Go-To-Market strategy, focusing heavily on a lean 3-month MVP launch.

## Month 1: Foundation & Supply Core
**Goal:** Build the tools for Travelers to publish trips and Shoppers to request items.

* **Tech:** Auth setup (OTP / Google), Database schema, Cloud infrastructure.
* **Product:**
  * Trip Publisher (URL Generation).
  * Traveler Profile (displaying name, photo, reviews, and completed counts).
  * Product Request Form.
  * Admin Dashboard (basic transaction and trip overview).

## Month 2: Transaction Engine
**Goal:** Enable secure matching and payment.

* **Tech:** Payment Gateway Integration (Escrow holding logic).
* **Product:**
  * Quotation Engine.
  * Capacity Management (baggage slot tracking, capacity reservation).
  * Quote Expiry (24-hour auto-release of reserved capacity).
  * Escrow Integration.
  * Checkout Flow (Shopper funding Escrow).

## Month 3: Fulfillment & Launch
**Goal:** Complete the loop and launch the constrained MVP (Japan ↔ Indonesia route).

* **Tech:** Payout logic (releasing funds to Traveler).
* **Product:**
  * Order Tracking Dashboard (Requested → Quoted → Payment Pending → Paid → Purchasing → Purchased → In Transit → Delivered → Completed).
  * Email Notifications (automated status updates).
  * Reviews & Ratings System (text reviews and star ratings).
  * QA & Security Audit.
* **Milestone:** **MVP Public Launch (Constrained to 50 subsidized Travelers; Japan ↔ Indonesia route)**.

---

## Month 4: Friction Reduction (V1.1)
**Goal:** Listen to the first 100 transactions and reduce manual friction.

* **Product:**
  * Push Notifications.
  * Better Admin Reporting.
  * Operational Tools.

## Month 5-6: Liquidity & Discovery (V2)
**Goal:** Shift from link-based sharing to internal platform discovery.

* **Product:**
  * Destination Discovery Feed (Browse active trips by city).
  * Creator Storefronts (Curated item lists).
  * Traveler Identity Verification (KYC submission and approval workflow).
  * Logistics Integration (Auto-Generated AWB for JNE/GoSend shipping labels).
* **Milestone:** Expand routes to South Korea and Singapore.
