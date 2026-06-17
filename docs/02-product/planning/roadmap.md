---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/planning/feature-prioritization.md
---

# Product Roadmap

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-14

This roadmap aligns engineering effort with the Go-To-Market strategy, focusing heavily on a lean 3-month MVP launch of the simplified Record-Keeping and Trip Coordination Tool.

## Month 1: Foundation & Profile Core
**Goal:** Build the essential user accounts, traveler profiles, and trip sharing capabilities.

* **Tech:** Auth setup (OTP / Google), Database schema, Cloud infrastructure.
* **Product:**
  * Trip Publisher (destination, travel dates, optional baggage notes).
  * Unique shareable trip URL generation.
  * Traveler Profile (displaying name, photo, completed trips count, completed requests count, ratings/reviews history).

## Month 2: Sourcing & Request Core
**Goal:** Build the shopper product request form and traveler incoming request tracker.

* **Tech:** Request database records, status schema, notification templates.
* **Product:**
  * Structured Product Request Form (item name, product URL, reference photo, quantity, notes; no budget inputs).
  * Traveler incoming request list dashboard.
  * Traveler manually accepts requests (Requested → Accepted).

## Month 3: Sourcing & Delivery
**Goal:** Complete the request lifecycle and enable user feedback.

* **Tech:** Simple status state transition mechanics, review submission endpoints.
* **Product:**
  * Sourcing status updates (Traveler marks as Purchased).
  * Dispatch status updates (Traveler marks as Delivered).
  * Shopper receipt confirmation (transitions request to Completed).
  * Reviews & Ratings System (text reviews and star ratings).
* **Milestone:** **MVP Public Launch (Constrained to early adoption validation on Indonesia ↔ Japan route)**.

---

## Month 4: Transaction & Escrow (V1.5)
**Goal:** Introduce transaction security and escrow payments.

* **Product:**
  * Payment Gateway Integration (Xendit/Midtrans invoice generation and webhooks).
  * Escrow fund locking mechanics.
  * Automated 24h payment window expiration.
  * Basic transaction email notifications.

## Month 5-6: Liquidity & Operations (V2.0)
**Goal:** Expand features to reduce operational friction and grow matching liquidity.

* **Product:**
  * Destination Discovery Feed (Browse active trips by city).
  * Creator Storefronts (Curated item recommendation lists).
  * Traveler Identity Verification (KYC submission and approval workflow).
  * Logistics Integration (Courier API integration & auto-generated shipping labels).
