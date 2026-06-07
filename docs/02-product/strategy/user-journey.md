# User Journeys

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-06

This document maps the core workflows for our three primary user personas. These journeys represent the core loops of the MVP and the early evolution in V2.

## 1. The Trusted Traveler Journey (Supply Side - MVP)

This journey focuses on creating inventory (publishing a trip with baggage capacity) and managing fulfillment.

### Journey Stages

| Stage | Action | Pain Point Solved / System Logic |
|-------|--------|-------------------|
| **1. Trip Setup** | Traveler logs in, creates a "Trip to Tokyo" with dates, and sets an available baggage capacity limit (e.g., 15kg). They receive a shareable `mytrip.com/budi/tokyo` link. | Eliminates the need to manually announce trips on multiple Instagram stories. |
| **2. Broadcasting** | Traveler posts the link on their social media and WhatsApp groups. | Streamlines traffic into a single funnel. |
| **3. Review Requests** | Traveler receives structured Product Requests. They review the item details (URL/Photo) and decide whether to accept. | No more chaotic WhatsApp negotiation or missing details. |
| **4. Quotation & Capacity Reservation** | Traveler sends a Quote (Item Price + Jastip Fee) through the platform. The platform temporarily *reserves* baggage capacity (estimated item weight) to prevent overbooking. The reservation expires after 24 hours if payment is not completed. | Standardizes pricing, avoids overbooking, and controls luggage capacity. Reserved capacity is automatically released when the quote/reservation expires. |
| **5. Escrow Funding & Capacity Lock** | Platform notifies Traveler that Escrow is funded. The reserved capacity becomes confirmed/locked. If capacity is depleted, the trip is closed to new requests. | Eliminates "flaky buyer" risk. **Capital Risk Alert:** Traveler uses their own funds to buy the item abroad, backed by guaranteed escrow. |
| **6. Delivery & Payout** | Traveler returns, ships the item via integrated logistics, and marks it Shipped (In Transit). Escrow funds are released to the Traveler's wallet after shopper confirmation or automatic completion after a predefined period. | Ensures safe, guaranteed payment without chasing buyers for transfers, and prevents funds from being locked indefinitely. |
| **7. Trip Completion** | Traveler marks the Trip as Completed once all active orders are fulfilled. | Closes the active trip lifecycle. |

---

## 2. The Lifestyle Shopper Journey (Demand Side - MVP)

This journey focuses on discovering a trip, requesting a product, and secure payment.

### Journey Stages

| Stage | Action | Pain Point Solved |
|-------|--------|-------------------|
| **1. Open Trip Link** | Shopper clicks Budi's shared "Trip to Tokyo" link on Instagram or WhatsApp. | Provides a clear, direct path to request items from a trusted source. |
| **2. Product Request** | Shopper fills out a structured form: Item Name, Reference URL, Photo, and Willingness to Pay. | Eliminates the back-and-forth "can you find this?" chats. |
| **3. Receive Quote** | Shopper receives Budi's Quote. They review the total cost. | Provides transparent, upfront pricing. |
| **4. Accept / Reject Quote** | Shopper accepts the quote or rejects it. (For MVP, negotiation is handled by rejecting and resubmitting a modified request, or via manual traveler quote revision). | Clarifies transaction terms. |
| **5. Escrow Payment** | Shopper funds the escrow by paying the full amount to the platform within 24 hours. | Eliminates the fear of "hit and run" fraud. |
| **6. Track Order Status** | Shopper checks their dashboard to see the status update (`Paid` → `Purchased` → `In Transit` → `Delivered`). | Relieves anxiety by showing exactly where the item is. |
| **7. Confirm & Review** | Shopper receives the item, confirms delivery (triggering release of escrow funds), and leaves a review. If shopper fails to confirm, system automatically completes the transaction and releases funds after a predefined period. | Builds community trust, ensures traveler payout safety, and prevents funds from being held indefinitely. |

> [!NOTE]
> **Exception Flows:** Exception paths such as quote revisions/rejections, traveler cancellation, shopper cancellation, refund processing, item unavailable (out of stock), customs clearance issues, and capacity exceeded constraints are handled outside the happy path in operational workflows for the MVP.

---

## 3. The Creator Traveler Journey (Amplifier - V2)

*Note: This journey is prioritized for V2, focusing on simplified storefront curation before full bulk order dashboards.*

This journey focuses on leveraging an existing audience to drive requests.

### Journey Stages

| Stage | Action | Pain Point Solved |
|-------|--------|-------------------|
| **1. Storefront Curation** | Creator builds a "Top 10 Drugstore Must-Haves" recommendations list on their platform storefront. | Moves beyond one-off requests to scalable, curated recommendations. |
| **2. Share Link** | Creator shares their curated storefront page link in their TikTok or Instagram bio. | Directs high-intent follower traffic to a frictionless request portal. |
| **3. Followers Submit Requests** | Followers click the link, select items from the recommendations, and submit standard product requests. | Standardizes and organizes fan-driven requests. |
| **4. Standard Escrow & Payout** | Transactions follow the standard MVP Escrow flow, allowing the creator to purchase and deliver items safely. | Replaces manual DM ordering with a secure transaction structure. |
| **5. Reputation & Earnings** | Creator receives verified ratings, building destination-based reputation badges for future trips. | Professionalizes their curation into a credible travel-shopping brand. |
