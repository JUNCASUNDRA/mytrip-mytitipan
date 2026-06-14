---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/information-architecture/navigation-map.md
outputs:
  - sitemap
depends_on:
  - navigation-map.md
---

# Site Map & Route Structure

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document maps the application site structure, URL endpoints, and route hierarchies for **My Trip My Titipan** based on user roles and permissions.

---

## 1. Guest & Public Directory Routes

These pages are accessible publicly without any authentication guards:

*   **Homepage / Switcher Redirect `/`**
    *   *Role:* Guest / Unauthenticated.
    *   *Purpose:* Brand introduction, service explanation, and role switcher landing.
*   **Trip Landing Page `/t/:trip_share_slug`**
    *   *Screen ID:* `SCR-002`
    *   *Purpose:* Dynamic public landing page generated for a traveler's specific trip link shared on social media. Displays traveler statistics, luggage capacity, and open request CTA.
*   **Authentication Portal `/login`**
    *   *Screen ID:* `SCR-001`
    *   *Purpose:* Register or login via Google Single Sign-On (SSO) or mobile OTP verification.

---

## 2. Shopper Authenticated Directory Structure

All routes prefixed with `/shopper` require active shopper session guards:

*   **Shopper Dashboard `/shopper/dashboard`**
    *   *Screen ID:* `SCR-004`
    *   *Tabs:* Active Requests, Unpaid Quotes, In-Transit tracking, Completed History.
*   **Product Request Form `/shopper/request/:trip_id`**
    *   *Screen ID:* `SCR-003`
    *   *Purpose:* Structured page to input item name, budget budget, link references, and photo details.
*   **Quote checkout Page `/shopper/checkout/:quote_id`**
    *   *Screen ID:* `SCR-005`
    *   *Purpose:* Price invoice summary (Item cost + fees) with virtual account/e-wallet checkout gateway actions.
*   **Review Submission `/shopper/review/:order_id`**
    *   *Screen ID:* `SCR-011`
    *   *Purpose:* Closed-loop star rating and comment feedback input after domestic delivery confirmation.

---

## 3. Traveler Authenticated Directory Structure

All routes prefixed with `/traveler` require active traveler session guards:

*   **Traveler Dashboard `/traveler/dashboard`**
    *   *Screen ID:* `SCR-006`
    *   *Tabs:* Active Trips, Pending Requests Inbox, active Sourcing Orders, Wallet/Earnings balance list.
*   **Create Trip Form `/traveler/create`**
    *   *Screen ID:* `SCR-007`
    *   *Purpose:* Form to submit travel routes, scheduled arrival/departure dates, and baggage capacity weights.
*   **Trip Share Widget `/traveler/share/:trip_id`**
    *   *Screen ID:* `SCR-008`
    *   *Purpose:* Modal displaying copying text triggers and social media (WhatsApp, Instagram) sharing options.
*   **Request Review Panel `/traveler/request/:request_id`**
    *   *Screen ID:* `SCR-009`
    *   *Purpose:* Panel for reviewing shopper item requests, proposing budgets, and sending quotes.
*   **Traveler Order details `/traveler/order/:order_id`**
    *   *Screen ID:* `SCR-010`
    *   *Purpose:* Step-by-step checklist to track item purchase procurement, upload paper invoices, and input JNE/J&T/Sicepat domestic courier tracking numbers.

---

## 4. Administration Directory Structure

All routes prefixed with `/admin` require active administrator session guards:

*   **Admin Dashboard `/admin/dashboard`**
    *   *Screen ID:* `SCR-012`
    *   *Purpose:* Desktop view containing high-level counters (active trips, disputes) and tabular auditing ledger logs.
*   **Admin Dispute Resolver `/admin/dispute/:order_id`**
    *   *Screen ID:* `SCR-013`
    *   *Purpose:* Detail screen displaying item photos, courier APIs, and action triggers for manual escrow refund or traveler payout releases.
