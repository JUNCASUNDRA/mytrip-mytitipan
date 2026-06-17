---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
phase: phase-1-foundation
status: draft
---

# Wireframe Requirements - Phase 1

## Screen Inventory

### Traveler Experience (Mobile-First)

1.  **Traveler Dashboard**: Summary of active trips, total requests, and "Create Trip" CTA.
2.  **Create Trip Form**: Minimal inputs for Route, Dates, and Description.
3.  **Trip Detail Page**: View specific trip with its unique sharing link and list of associated requests.
4.  **Incoming Requests List**: Inbox-style list of requests in "Requested" status.
5.  **Request Detail Review**: Card-based view of a specific request with "Accept" and "Decline" actions.
6.  **Active Requests Tracking**: List of requests in "Accepted", "Purchased", or "Delivered" status.
7.  **Completed History**: Archive of all past "Completed" or "Cancelled" requests.
8.  **Profile & Reviews**: Public-facing view showing the traveler's success metrics and shopper feedback.

### Shopper Experience (Mobile-First)

1.  **Trip Landing Page**: Mobile-optimized page seen by shoppers when clicking a shared link.
2.  **Traveler Profile Preview**: Minimalist trust signals (Joined date, number of successful trips, reviews).
3.  **Submit Request Form**: Single-page form for item name, quantity, estimated price, and image upload.
4.  **Request Detail Tracking**: Progress timeline view for a specific request.
5.  **Confirm Receipt Screen**: Simple modal or focused screen for "Confirm Receipt".
6.  **Review Form**: Star rating selector and text area for feedback.

## Universal UX States

### Empty States
- **No Trips**: "You haven't planned any trips yet. [Create Your First Trip]"
- **No Incoming Requests**: "No pending requests. Share your trip link to get started!"
- **No Active Coordination**: "All caught up! Check your history for completed items."

### Error States
- **Invalid Shared Link**: "This trip link is invalid or has expired."
- **Form Validation**: Clear red indicators for missing item name or quantity.
- **Network Error**: Graceful retry buttons for failed status updates.

## Technical UI Constraints
- **Mobile First**: Design for 375px width (Standard Mobile).
- **No Real-time Chat**: UI must emphasize status updates rather than messaging.
- **Link Sharing**: Link sharing widget must be prominent on trip creation success.
