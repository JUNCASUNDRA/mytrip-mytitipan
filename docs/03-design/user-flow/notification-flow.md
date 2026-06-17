---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/03-user-flow/README.md
---

# Notifications Map

This document defines the transactional notification triggers, channels, and message copy required for the My Trip My Titipan MVP. Proactive notification touchpoints are crucial to guide users through the escrow payment and capacity reservation expiry workflows.

---

## Notification Matrix

The following table maps the notifications sent to Travelers and Shoppers throughout the order lifecycle:

| Trigger Event | Recipient | Channel (MVP) | Channel (Deferred - V1.1) | Template Message | Linked Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **New Product Request** | Traveler | Email | Web Push | "New request received for your trip to Tokyo! Review details and send a quote." | Opens Request Review Screen (`SCR-009`) |
| **Quote Issued** | Shopper | Email | Web Push | "Budi sent you a quote! Pay within 24 hours to secure your baggage capacity." | Opens Quote & Checkout Page (`SCR-005`) |
| **Escrow Paid** | Traveler | Email | Web Push | "Payment secured! You can now purchase the item during your trip." | Opens Traveler Order Details (`SCR-010`) |
| **Item Marked Purchased** | Shopper | Email | Web Push | "Great news! Budi has purchased your requested item in Tokyo." | Opens Shopper Dashboard (`SCR-004`) |
| **Tracking Number Entered** | Shopper | Email | Web Push | "Your package is on its way! Shipped via [Courier] with tracking number [AWB]." | Opens Shopper Dashboard (`SCR-004`) |
| **Delivery Confirmed** | Traveler | Email | Web Push | "Shopper confirmed delivery! Funds have been released to your wallet." | Opens Traveler Dashboard (`SCR-006`) |
| **Quote Expiry Alert (22h)**| Shopper | Email | Web Push | "Hurry! Your quote for Tokyo items expires in 2 hours. Pay now to secure baggage slots."| Opens Quote & Checkout Page (`SCR-005`) |
| **Order Expired** | Shopper & Traveler | Email | Web Push | "Quote expired. The baggage capacity has been released back to the traveler." | Opens Respective Dashboard |
| **Dispute Opened** | Admin | Email / Alert | System Alert | "Order [ID] has been disputed by [Shopper Name]. Investigation required." | Opens Admin Dispute Manager (`SCR-013`) |
| **Item Out of Stock** | Shopper | Email | Web Push | "Budi reported that the Tokyo item is out of stock. The Admin will process your refund shortly." | Opens Shopper Dashboard (`SCR-004`) |
| **Dispute Resolved (Refunded)** | Shopper & Traveler | Email | Web Push | "Dispute resolved. Shopper has been refunded for the Tokyo item." | Opens Respective Dashboard |
| **Dispute Resolved (Payout)** | Traveler & Shopper | Email | Web Push | "Dispute resolved. Funds released to your traveler wallet." | Opens Respective Dashboard |

---

## Notification Channel Guidelines

1.  **Email Notifications (MVP Primary)**: Used as the core notification channel for all key status transitions, payment invoices, quote notifications, and auto-expiry alerts.
2.  **Mobile Web Push (V1.1 - Deferred)**: Deferred to post-MVP launch. Once implemented, it will be used for real-time status alerts (e.g., `Purchased`, `In Transit`) on mobile devices.
3.  **No In-App Chat Integration**: All notification templates must link directly to structured screens (such as `SCR-005` or `SCR-010`) rather than a chat interface to prevent out-of-platform negotiation.
