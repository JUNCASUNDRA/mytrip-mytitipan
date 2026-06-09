---
agent: UX Designer Agent (UXA)
version: 1.0.0
date: 2026-06-09
status: Draft
predecessor: docs/03-design/user-flow/README.md
---

# Screen Inventory

This document lists all the screens required to support the **My Trip My Titipan** MVP. The unique screen IDs (e.g., `SCR-001`) serve as direct references for low-fidelity wireframes, high-fidelity mockups, and frontend routes.

---

## Screen Inventory Table

The MVP interface is divided by actor access controls:

| Screen ID | Screen Name | Actor Access | Core UX Objective & Description | Primary Call to Actions (CTAs) | Preceding Screen ID |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SCR-001** | Login / Register | All | Authenticates users via Google SSO or mobile phone OTP. | "Log in with Google", "Send OTP" | Landing / Redirected |
| **SCR-002** | Trip Landing Page | Shopper (Public) | Public page showing traveler profile stats, travel routes, dates, and available capacity. | "Request Item" | Clicked Shared Link |
| **SCR-003** | Product Request Form | Shopper | Structured input form to submit product name, URL, photo upload, and max budget. | "Submit Request" | SCR-002 |
| **SCR-004** | Shopper Dashboard | Shopper | Personal space to manage active requests, unpaid quotes, and active order tracking. | "Review Quote", "Confirm Receipt", "Raise Dispute" | SCR-001 |
| **SCR-005** | Quote & Checkout Page | Shopper | Detailed traveler quote breakdown (Item cost + Jastip fee) and payment method triggers. | "Pay Now", "Cancel Request" | SCR-004 |
| **SCR-006** | Traveler Dashboard | Traveler | Portal showing active trips, pending shopper requests, active orders, and wallet balance. | "Create Trip", "Review Request" | SCR-001 |
| **SCR-007** | Create Trip Form | Traveler | Form to publish new travel details: departure/arrival airports, dates, and baggage capacity. | "Publish Trip" | SCR-006 |
| **SCR-008** | Trip Share Modal | Traveler | Presents the unique shareable link for copying and posting. | "Copy Link", "Share to WhatsApp" | SCR-007 |
| **SCR-009** | Request Review Screen | Traveler | Screen to review shopper request parameters and draft/send quote. | "Send Quote", "Decline Request" | SCR-006 |
| **SCR-010** | Traveler Order Details | Traveler | Order tracking screen with status indicators and inputs for domestic shipment. | "Mark as Purchased", "Submit Tracking", "Mark Out of Stock" | SCR-006 |
| **SCR-011** | Review Submission | Shopper | Text and star rating form to evaluate traveler performance after receipt. | "Submit Review" | SCR-004 |
| **SCR-012** | Admin Dashboard | Admin | High-level metrics view showing transactions list and system stats. | "Audit Transactions", "View Disputes" | Admin Login |
| **SCR-013** | Admin Dispute Manager | Admin | Detail view of open disputes with manual release and refund triggers. | "Refund Shopper", "Payout Traveler" | SCR-012 |

---

## Wireframe & Routing Reference

1.  **Prefix System**: All low-fidelity wireframes must match the `SCR-[ID]` prefix to ensure consistency.
2.  **Authentication Guard**: Screens `SCR-004` through `SCR-013` require active user sessions. Unauthenticated users visiting these routes will be redirected to `SCR-001`.
3.  **Public Access**: Screen `SCR-002` must be accessible publicly without requiring a logged-in session, maximizing conversion rates for shared travel links.
