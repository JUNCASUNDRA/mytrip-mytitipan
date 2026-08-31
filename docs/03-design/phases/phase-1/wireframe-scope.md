---
agent: UX Designer Agent (UXA)
version: 1.2.0
date: 2026-06-17
phase: phase-1
status: Approved
---

# Wireframe Design Scope - Phase 1

This document specifies the exact screen inventory, user access permissions, and design components required for the Phase 1 Foundation wireframes.

## Screen Inventory

| Screen ID | Screen Name | Actor Access | Core UX Objective & Description | Primary Call to Actions (CTAs) | Preceding Screen ID |
| --- | --- | --- | --- | --- | --- |
| **SCR-001** | Login | All | Authenticates users via Google SSO or mobile phone OTP. | "Log in with Google", "Send OTP" | Landing / Redirected |
| **SCR-002** | Trip Landing Page | Shopper (Public) | Public page showing traveler profile, travel routes, dates, past completed trips, and shopper reviews. | "Request Item" | Clicked Shared Link |
| **SCR-003** | Request Form | Shopper | Structured input form to submit product name, URL, photo, estimated/reference price, and notes for traveler. | "Submit Request" | SCR-002 |
| **SCR-004** | Shopper Dashboard | Shopper | Personal space to manage active requests, tracking progress, and profile details. | "Confirm Receipt", "View Details" | SCR-001 |
| **SCR-005** | Request Detail | Shopper | Shopper-side tracking view showing request timeline progression. | "Confirm Receipt", "Cancel Request" | SCR-004 |
| **SCR-006** | Traveler Dashboard | Traveler | Portal showing active trips, pending incoming shopper requests, active requests, and profile stats. | "+ Create Trip", "Review Request" | SCR-001 |
| **SCR-007** | Create Trip | Traveler | Form to publish travel details: departure/arrival airports, dates, and optional coordinator notes. | "Publish Trip" | SCR-006 |
| **SCR-008** | Trip Share | Traveler | Displays the unique shareable link for copying and posting. | "Copy Link", "Share to WhatsApp" | SCR-007 |
| **SCR-009** | Request Review | Traveler | Interface for reviewing shopper request parameters. | "Accept Request", "Decline Request" | SCR-006 / Email Alert |
| **SCR-010** | Traveler Request Detail| Traveler | Detailed request tracking screen with status indicators and state transitions. | "Update Progress", "Mark Ready", "Fulfill Request" | SCR-006 |
| **SCR-011** | Review Form | Shopper | Text and star rating form to evaluate traveler performance after receipt. | "Submit Review" | SCR-005 / SCR-004 |

---

## Wireframe Constraints & Changes

1. **Removed Phase 2 Features**:
   - **SCR-005 Quote & Checkout**: Deleted. Payments and quotations are handled offline.
   - **SCR-012/SCR-013 Admin Dashboards**: Deleted. Admin role and dispute managers are out of scope.
   - **Wallet Balances & Raise Dispute CTAs**: Removed from dashboards and detail views.
2. **Tab Navigation Simplification**:
   - Tab structures are limited strictly to dashboard-level views (Home, Profile) and floating CTAs (e.g., Traveler "+ Create Trip").
