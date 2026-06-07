# MVP Definition

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-06

This document defines the strict Minimum Viable Product (MVP) for My Trip My Titipan. We are constrained by a 3-month launch window and a 3–5 person engineering team.

## 1. Core Value Proposition

The MVP exists to validate one core hypothesis:

**Shoppers are willing to pay upfront into an Escrow system for a product requested through a Traveler's trip page, while Travelers are willing to fulfill requests in exchange for a service fee.**

---

## 2. Core MVP Capabilities

The MVP is intentionally focused on enabling one complete and trusted transaction flow from trip creation to escrow payout.

### 1. Trip Publisher

Travelers can create a trip by providing:

* Destination
* Travel Dates
* Available Baggage Capacity

The platform generates a unique shareable trip link.

Example:

`mytrip.com/t/budi-tokyo-24`

**Purpose:** Creates supply and enables external traffic acquisition.

---

### 2. Traveler Profile & Trip Page

Each trip page displays:

* Traveler name and profile photo
* Completed trips count
* Completed orders count
* Reviews and ratings
* Trip destination and travel dates
* Available baggage capacity

**Purpose:** Provides basic trust signals before payment.

---

### 3. Structured Product Request

Shoppers can submit:

* Item Name
* Product URL
* Product Photo
* Quantity
* Maximum Budget

**Purpose:** Standardizes demand capture and eliminates unstructured chat-based requests.

---

### 4. Quotation & Capacity Management

Travelers review incoming requests and respond with:

* Item Price
* Jastip Fee
* Total Price

The platform temporarily reserves baggage capacity for a limited period (e.g. 24 hours).

If payment is not completed before expiry:

* Quote expires
* Reserved capacity is automatically released

**Purpose:** Prevents overbooking while allowing multiple concurrent requests.

---

### 5. Escrow Payment

Shoppers pay the quoted amount through an integrated payment gateway.

After successful payment:

* Funds are held in Escrow
* Capacity reservation becomes locked
* Traveler receives confirmation to proceed with purchase

**Purpose:** Protects both parties and reduces fraud risk.

---

### 6. Order Tracking

The platform tracks order progress through the following statuses:

* Requested
* Quoted
* Payment Pending
* Paid
* Purchased
* In Transit
* Delivered
* Completed

**Purpose:** Provides transparency throughout the transaction lifecycle.

---

### 7. Reviews & Ratings

After successful delivery:

* Shopper leaves a rating
* Shopper leaves a written review

Reviews are displayed on the Traveler profile.

**Purpose:** Creates a trust loop without requiring identity verification during MVP.

---

## 3. What is Explicitly Out of Scope (Deferred to V2)

### Discovery & Social Features

* Destination Discovery Feed
* Traveler Search Directory
* Recommendation Algorithms
* Community Forums
* Social Following System

### Creator Commerce Features

* Creator Storefronts
* Jastip by Spot Collections
* Live Shopping
* Affiliate & Referral Programs

### Trust & Compliance

* Government ID Verification (KYC)
* Automated Fraud Detection
* Advanced Reputation Badges

### Logistics & Operations

* Auto-generated AWB
* Logistics Provider Integration
* Real-time Shipment Tracking
* Automated Customs Calculation

### Communication

* In-App Chat
* Voice Calls
* Video Calls

---

## 4. MVP Success Criteria

The MVP will be considered successful if it can consistently facilitate a complete transaction flow:

Trip Published → Product Requested → Quote Sent → Escrow Paid → Item Purchased → Item Delivered → Escrow Released → Review Submitted

without requiring manual intervention for the majority of transactions.
