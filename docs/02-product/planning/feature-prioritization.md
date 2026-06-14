---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/planning/mvp-definition.md
---

# Feature Prioritization (MoSCoW)

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document strictly prioritizes features based on the core MVP requirements. Any feature outside the "Must Have" list is explicitly deferred to ensure a 3-month launch window.

## 1. Must Have (MVP - Month 1 to 3)

These are non-negotiable. Without these, the platform cannot facilitate a secure transaction.

| Feature | Description | Reason |
| --- | --- | --- |
| **Trip Publisher** | Travelers can input route/dates and get a shareable URL. | Creates the inventory. |
| **Product Request Form** | Shoppers can upload photo, URL, and willing-to-pay budget. | Captures the demand. |
| **Quotation Engine** | Travelers can respond with exact Item Price + Fee. | Enables agreement on pricing. |
| **Capacity Management** | Track available baggage slots, reserve capacity during quotation, and lock capacity after payment. | Prevents overbooking and enables multiple concurrent requests. |
| **Quote Expiry & Capacity Release** | Automatically expires unpaid quotes and releases reserved capacity after 24 hours. | Prevents capacity from being locked indefinitely by unresponsive buyers. |
| **Escrow Integration** | Integration with Xendit/Midtrans for holding funds. | Solves the core "Hit and Run" trust issue. |
| **Traveler Profiles** | Public profiles showing traveler name, photo, completed trips & orders count, and reviews. | Essential for trust since ID verification is deferred. |
| **Basic Order Status** | Dashboard showing Paid, Purchasing, Purchased, In Transit, Delivered, Completed. | Minimum required transparency. |
| **Reviews & Ratings** | Text reviews and star ratings. | Essential for trust since ID verification is deferred. |
| **Basic Admin Dashboard** | Simple backend for admins to monitor transactions and active trips. | Essential for customer service and operational overview during launch. |

## 2. Should Have (V1.1 - Month 4)

These add significant value but are not strictly required for the first 100 transactions.

| Feature | Description | Reason |
| --- | --- | --- |
| **In-App Notifications** | Push/Email notifications for status changes. | Replaces manual checking of the dashboard. |

## 3. Could Have (V2.0 - Month 5 to 6)

These features build the "Social Commerce" vision but are too risky/complex for MVP.

| Feature | Description | Reason |
| --- | --- | --- |
| **Auto-Generated AWB** | Integration with local logistics (JNE/GoSend) to print shipping labels. | Reduces Traveler admin burden; manual shipping is sufficient for early transactions. |
| **Creator Storefronts** | Dedicated pages for "Jastip by Spot" curation. | Requires an existing baseline of reliable Travelers. |
| **Destination Discovery Feed** | Algorithmic feed showing active trips. | Worthless until we have high route density (liquidity). |
| **Traveler Identity Verification** | Admin approval workflow and ID upload. | Initiates government verification for Phase 2 trust. |

## 4. Won't Have (Deferred Indefinitely)

| Feature | Description | Reason |
| --- | --- | --- |
| **In-App Chat / Negotiation** | Direct messaging between Shopper and Traveler. | Causes scope creep (moderation, media storage). Structured forms solve the problem better. |
| **Live Shopping** | Native video broadcasting. | Extremely expensive infrastructure. Creators can use TikTok/IG. |
| **Automated Customs Calculator** | API predicting border taxes. | Impossible to maintain accurately. Travelers must quote manually. |
