# Product Roadmap

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-06

This roadmap aligns engineering effort with the Go-To-Market strategy, focusing heavily on a lean 3-month MVP launch.

## Month 1: Foundation & Supply Core
**Goal:** Build the tools for Travelers to publish trips and Shoppers to request items.

* **Tech:** Auth setup, Database schema, Cloud infrastructure.
* **Product:**
  * Trip Publisher (URL Generation).
  * Structured Request Form.
  * Basic Manual Admin Dashboard (for transaction and trip overview).

## Month 2: Transaction & Escrow Engine
**Goal:** Enable secure matching and payment.

* **Tech:** Payment Gateway Integration (Escrow holding logic).
* **Product:**
  * Quotation Engine (Traveler sending quote to Shopper).
  * Checkout Flow (Shopper funding Escrow).

## Month 3: Fulfillment & Launch Preparation
**Goal:** Complete the loop and launch the constrained MVP (Japan ↔ Indonesia route).

* **Tech:** Payout logic (releasing funds to Traveler).
* **Product:**
  * 4-State Order Dashboard (Paid → Purchased → In Transit → Delivered).
  * Basic Reviews & Ratings System (text reviews and star ratings).
  * Final QA and Security Audit.
* **Milestone:** **MVP Public Launch (Constrained to 50 subsidized Travelers)**.

---

## Month 4: The "Friction Reduction" Update (V1.1)
**Goal:** Listen to the first 100 transactions and reduce manual friction.

* **Product:**
  * Auto-Generated AWB (Logistics Integration).
  * Automated Email/Push Notifications.
  * Public Traveler Profiles (Completed trips & orders count).

## Month 5-6: The "Liquidity & Discovery" Update (V2.0)
**Goal:** Shift from link-based sharing to internal platform discovery.

* **Product:**
  * Destination Discovery Feed (Browse active trips by city).
  * Creator Storefronts (Curated item lists).
  * Traveler Identity Verification (Government ID / KYC submission and approval workflow).
* **Milestone:** Expand routes to South Korea and Singapore.
