---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/product-vision.md
outputs:
  - ux-principles
depends_on:
  - product-vision.md
---

# Core UX Design Principles

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the core user experience principles governing the design of the **My Trip My Titipan** platform. These tenets guide visual patterns, interactive layouts, and user flows to establish a trusted and seamless peer-to-peer jastip utility.

---

## 1. Invisible Trust Infrastructure
* **Concept:** P2P transactions are high-friction due to fraud anxieties. The interface must pro-actively communicate security checks and status verifications without adding cognitive load.
* **UX Enforcements:**
  * Displays prominent lock badges (`Escrow Secured 🔒`) on dashboard pages once funding is confirmed.
  * Shows transparent traveler reputation metrics (star counts, verified completed orders/trips counters) in public landing contexts to build trust instantly.
  * Eliminates open, unmoderated chat interfaces, routing agreements through standardized forms to prevent out-of-platform payment scams.

## 2. Suitcase Capacity Transparency
* **Concept:** Luggage space is a finite physical constraint. The traveler must never feel overloaded, and the shopper must immediately know whether space is available.
* **UX Enforcements:**
  * Uses responsive HSL capacity color bars (Green to Orange to Red) illustrating precise weight usage.
  * Displays real-time estimated suitcase weights inside traveler quotation inputs.
  * Automatically closes trip request CTAs and blocks gateway checkouts when capacity is fully depleted.

## 3. Transactional Momentum & Friction Management
* **Concept:** Unpaid quotations lock suitcase inventory. The shopper must be prompted to pay immediately, while the traveler must be notified as soon as funds are secured.
* **UX Enforcements:**
  * Places countdown timers (e.g., `Expires in 14h 23m`) on all active quotation checkout headers.
  * Uses structured, progressive checklists for the traveler procurement flow (Sourcing -> Purchased -> Shipped).

## 4. Mobile-First Layout Focus
* **Concept:** Shoppers discover trip links via social media (Instagram bio, WhatsApp stories, TikTok) on their mobile devices. The checkout and request flows must be optimized for one-handed thumb interaction.
* **UX Enforcements:**
  * Floating, sticky bottom CTAs on product request forms and quote checkout forms.
  * Grayscale minimalist layouts with high visual contrast to ensure outdoor readability during traveling.
