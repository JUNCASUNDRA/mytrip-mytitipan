---
agent: UX Designer Agent (UXA)
version: 1.2.0
date: 2026-06-17
phase: phase-1
status: Approved
---

# Shopper User Flow - Phase 1

This document outlines the user interface flow for shoppers interacting with traveler trips in Phase 1.

## 1. Happy Path Flow

1. **Open Trip Link**: Shopper navigates to the shared traveler trip page (via external link, e.g., WhatsApp, Instagram).
2. **Review Traveler History**: Shopper reviews the traveler's historical performance details:
   - Past trips list
   - Completed requests history
   - Historical star ratings and reviews
3. **Submit Product Request**: Shopper fills out the request form (Item Name, Photo, Reference URL, Quantity, Notes).
4. **Wait for Traveler Response**: Shopper tracks status changes on their Shopper Dashboard.
5. **Track Request Status**: Progress updates dynamically: `REQUESTED` -> `ACCEPTED` -> `IN_PROGRESS` -> `READY_FOR_DELIVERY` -> `COMPLETED`.
6. **Confirm Receipt**: Shopper manually clicks "Confirm Receipt" once they have the item.
7. **Submit Feedback**: Shopper fills the Review Form to leave a star rating and written review.

## 2. Exception Paths

- **Edit/Cancel Request**: Allowed as long as request status remains `REQUESTED` (not yet accepted or processed).
- **Trip Closed**: If a trip's dates have passed, request creation is disabled.
