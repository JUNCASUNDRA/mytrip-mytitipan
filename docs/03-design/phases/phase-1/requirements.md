---
agent: UX Designer Agent (UXA)
version: 1.2.0
date: 2026-06-17
phase: phase-1
status: Approved
---

# Wireframe Requirements - Phase 1

This document outlines the UX requirements, layout specifications, state transitions, and constraints for the Phase 1 Foundation wireframes.

## 1. Interaction Experience (Mobile-First)

### Traveler Dashboards & Forms
- **Traveler Dashboard**: Entry point displaying active trips and a floating "+ Create Trip" CTA. Shows pending request count and active tracking list.
- **Create Trip Form**: Minimal inputs for departure/arrival cities, travel dates, and optional shopper guidance notes.
- **Trip Share Screen**: Instant visual feedback displaying copy-to-clipboard trip link, share widgets, and trip details.
- **Request Review**: Traveler view of shopper request parameters with "Accept Request" and "Decline" buttons.
- **Traveler Request Detail**: Tracking interface mapping the request timeline with state-transition buttons ("Update Progress", "Mark Ready", "Hand Over").

### Shopper Landing Pages & Dashboards
- **Trip Landing Page**: Public landing screen displaying traveler routes, dates, past completed trips list, and shopper reviews. Primary CTA: "Request Item".
- **Request Form**: Form fields for item name, quantity, estimated budget/price, reference link, notes, and photo attachment.
- **Shopper Dashboard**: Home view containing Shopper's active requests log.
- **Request Detail**: Progress tracker with visual timeline (Requested -> Accepted -> In Progress -> Ready for Delivery -> Completed).
- **Review Form**: Feedback submission interface consisting of a star rating selector (1-5 stars) and a text area.

---

## 2. Universal UX States

### Empty Backlogs
- **No Trips Planned**: "You haven't planned any trips yet. Create a trip to get started."
- **No Sourcing Requests**: "No pending requests. Share your trip link with potential shoppers!"

### Form Validations & Errors
- **Validation Errors**: Clear, accessible inline labels for missing item names, negative/zero quantities, or invalid URLs.
- **Expired/Cancelled Trips**: Banner notification indicating trip dates have passed, disabling the "Request Item" button.
- **Link Verification**: Clear screen boundary indicating an invalid or non-existent sharing link.

---

## 3. Technical Layout Constraints
- **Target Dimensions**: Designed for mobile width (375px) with responsive grids.
- **Status Timeline First**: Eliminate chat capabilities, driving alignment entirely through status updates and timeline log indicators.
