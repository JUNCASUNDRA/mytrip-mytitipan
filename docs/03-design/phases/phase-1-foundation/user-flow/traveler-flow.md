---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
phase: phase-1-foundation
status: draft
---

# Traveler User Flow - Phase 1 (Foundation)

## Happy Path Flow

1.  **Login**: Traveler authenticates via mobile (Google SSO or Email-OTP).
2.  **Create Trip**: Traveler enters route (From/To), dates, and optional baggage notes.
3.  **Generate Trip Link**: System creates a unique sharing URL for the trip.
4.  **Share Trip Link**: Traveler copies and shares the link via social media/chats.
5.  **Receive Request**: System notifies traveler of a new incoming shopper request.
6.  **Review Request**: Traveler opens the request detail to check item details and photos.
7.  **Accept Request**: Traveler commits to finding the item by clicking "Accept Request".
8.  **Mark Purchased**: Traveler updates the request status once the item is bought.
9.  **Mark Delivered**: Traveler updates the status once the item has been handed over or shipped.
10. **Complete Request**: Final status update to close the tracking loop.
11. **Receive Review**: Traveler views feedback and rating from the shopper.

## Exception Paths

- **Decline Request**: Traveler can decline an incoming request if they cannot find the item or have no capacity.
- **Cancel Accepted Request**: If the item becomes unavailable during sourcing, traveler can cancel with a reason.
