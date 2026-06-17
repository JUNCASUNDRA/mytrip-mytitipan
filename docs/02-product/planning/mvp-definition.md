---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/strategy/product-vision.md
---
# MVP Definition

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the strict Minimum Viable Product (MVP) for My Trip My Titipan under the Phase 1 Simplification model. We are constrained by a 3-month launch window and a 3–5 person engineering team.

## 1. Core Value Proposition

The Phase 1 MVP exists to validate one core hypothesis:

**Can Travelers and Shoppers use a structured platform to record and manage jastip requests without relying on scattered chat applications and unstructured social media posts?**

## Validation Metrics

The MVP validates the hypothesis if:
- travelers publish upcoming trips on the platform.
- shoppers submit structured product requests.
- travelers accept and manually update request statuses.
- users complete the request lifecycle to completion.
- repeat usage occurs from shoppers and travelers.

---

## 2. Core MVP Capabilities

The Phase 1 MVP is intentionally focused on enabling a lightweight coordination and record-keeping flow.

### 1. Trip Publisher

Travelers can create a trip by providing:

- Destination
- Travel Dates
- Optional baggage notes

The platform generates a unique shareable trip link.

Example:

`mytrip.com/t/budi-tokyo-24`

**Purpose:** Creates supply and replaces manual social media posts with a structured link.

---

### 2. Traveler Trip Page

Displays:
* Traveler profile summary
* Trip destination and travel dates
* Active shopper requests for the trip
* Request status (Requested → Accepted → Purchased → Delivered → Completed)

**Purpose:** Allows shoppers to see available trip information and track request statuses.

---

### 3. Structured Product Request

Shoppers can submit:

- Item Name
- Product URL
- Product Photo
- Quantity
- Notes

*Escrow dependencies, payment gateway integrations, checkout loops, and willingness-to-pay budget constraints are completely removed.*

**Purpose:** Standardizes demand capture and eliminates unstructured chat-based requests.

---

### 4. Request Management

Travelers review incoming requests and manually update the request status as it progresses.

*All automated capacity reservations, baggage limit calculations (kg), quotation engines (Item Price + Jastip Fee), and 24-hour expiration clocks are removed.*

**Purpose:** Replaces manual spreadsheet and chat-based order tracking.

---

### 5. Request Tracking

The platform tracks request progress through the following simplified manual states:

- **Requested:** Shopper submitted request.
- **Accepted:** Traveler accepted the request.
- **Processing:** Traveler is in travel/procurement phase.
- **Completed:** Shopper confirmed receipt of the item.
- **Reviewed:** Shopper submitted review and rating feedback.

**Purpose:** Provides transparency throughout the request lifecycle.

---

### 6. Reviews & Ratings

After a shopper marks an order as completed:

- Shopper leaves a rating (1-5 stars)
- Shopper leaves a written review

Reviews are displayed on the Traveler's profile.

**Purpose:** Creates a trust loop based on actual completed request history.

---

### 7. Simple Record History

The system records and stores:

- Completed requests
- Past trip histories

**Purpose:** Creates a basic transaction history to serve as a baseline for future reputation features.

---

## 3. What is Explicitly Out of Scope (Deferred to V2)

### Payment & Escrow Subsystem

- Payment gateway integrations (Midtrans/Xendit)
- Escrow fund holding logic
- Quotation calculations (Item Price + Jastip Fee structures)
- Payout distribution systems
- Transactional billing and invoice generation

### Trust & Identity

- Advanced Traveler Verification (KYC)
- Automated Fraud Detection
- Advanced Reputation Badges

### Logistics & Courier Operations

- Auto-generated AWB shipping labels
- Courier API integrations
- Real-time shipment tracking

### Communications & Discovery

- In-App Chat
- Destination Discovery Feed or Traveler Directories

---

## 4. MVP Success Criteria

The MVP will be considered successful if it can consistently facilitate a complete request lifecycle:

Trip Published → Product Requested → Request Accepted → Request Processing → Request Completed → Traveler Reviewed

without requiring transaction checkout steps, administrative intervention, or payment gateway APIs.