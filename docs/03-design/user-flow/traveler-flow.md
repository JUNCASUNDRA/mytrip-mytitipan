---
agent: UX Designer Agent (UXA)
version: 1.2.0
date: 2026-06-17
phase: phase-1
status: Approved
---

# Traveler User Flow - Phase 1

This document outlines the user interface flow for travelers managing trips and shopper requests in Phase 1.

## 1. Happy Path Flow

1. **Authentication**: Traveler logs in via Google SSO or OTP.
2. **Create Trip**: Traveler submits itinerary details (Origin, Destination, Travel Dates, Capacity details).
3. **Share Link**: Traveler copies the unique sharing URL and shares it externally (IG, WA, Telegram).
4. **Review Request**: Traveler opens traveler dashboard to review a shopper's incoming request parameters and photos.
5. **Accept Request**: Traveler clicks "Accept Request" (moves state to `ACCEPTED`).
6. **Update Progress**: Traveler clicks "Update Progress" to indicate they are sourcing/coordinating the item (moves state to `IN_PROGRESS`).
7. **Mark Ready**: Traveler clicks "Mark Ready" when the item has been procured and is ready for delivery (moves state to `READY_FOR_DELIVERY`).
8. **Hand Over Item**: Traveler hands over the item physically or ships it, triggering coordination updates (moves state to `COMPLETED`).
9. **Receive Feedback**: Traveler reviews the rating and feedback left by the shopper.

## 2. Exception Paths

- **Decline Request**: Traveler can click "Decline Request" on a pending request (moves state to `CANCELLED`).
- **Cancel Request**: Traveler cancels an accepted request if sourcing becomes impossible, entering a reason (moves state to `CANCELLED`).
