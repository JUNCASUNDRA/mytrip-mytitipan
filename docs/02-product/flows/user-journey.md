---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-1
status: approved
priority: must-have
depends_on:
  - core-user-flow.md
outputs:
  - ux-flow
---

# User Journeys

> **Status**: Approved **Last Updated**: 2026-06-14

This document maps the user journeys for the two primary actor personas during Phase 1 Foundation MVP.

---

## 1. Traveler Journey (Supply Side)

This journey focuses on traveler registration, trip sharing, and manual coordination of requests.

| Stage | Action | Emotional State | Pain Point Solved / System Logic |
| :--- | :--- | :--- | :--- |
| **1. Trip Setup** | Traveler creates a "Trip to Tokyo" specifying destinations, dates, and optional baggage notes. | Optimistic | Replaces messy, manual social media broadcast stories. |
| **2. Share Link** | Traveler copies and shares the trip link on social networks or WhatsApp groups. | Motivated | Channels shopper interest into a single structured backlog. |
| **3. Review Requests**| Traveler reviews structured shopper requests (names, images, URLs, notes). | Curious | No more back-and-forth chat negotiation for missing details. |
| **4. Accept Request** | Traveler commits to fulfilling the request by clicking "Accept Request". | Committed | Formally structures the agreement list. |
| **5. Sourcing & Update**| Traveler updates request status to "In Progress" as sourcing or coordination begins.| Active | Keeps shoppers updated on progress without chat friction. |
| **6. Return & Handover**| Traveler marks item "Ready for Delivery", hands over the item, and coordinates offline payment. | Relieved | Complete record list replaces spreadsheets. |
| **7. Review Check** | Traveler checks shopper's review rating post-completion. | Satisfied | Verified history establishes reputation for future trips. |

---

## 2. Shopper Journey (Demand Side)

This journey focuses on discovering shared trip links, requesting items, and receipt confirmation.

| Stage | Action | Emotional State | Pain Point Solved / System Logic |
| :--- | :--- | :--- | :--- |
| **1. Open Link** | Shopper clicks traveler's link on Instagram or WhatsApp bio. | High Intent | Directly targets trusted networks. |
| **2. Submit Request** | Shopper authenticates and submits a request (item name, photo reference, URL, quantity). | Hopeful | Eliminates "Can you buy this?" chat threads. |
| **3. Request Accepted**| Shopper receives notification that traveler accepted the request. | Reassured | Confirms traveler's commitment. |
| **4. Sourcing Watch** | Shopper monitors request timeline log as traveler shifts state to `In Progress` and `Ready for Delivery`. | Reassured | Visual timeline updates resolve shopper anxiety. |
| **5. Delivery Confirm**| Shopper receives package, clicks "Confirm Receipt" (completes request to `Completed`). | Pleased | Closes the loop. |
| **6. Review Traveler**| Shopper submits star rating and feedback review via the review form. | Helpful | Contributes back to community trust. |
