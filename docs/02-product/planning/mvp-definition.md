# MVP Definition

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-06

This document defines the strict Minimum Viable Product (MVP) for My Trip My Titipan. We are constrained by a 3-month launch window and a 3-5 person engineering team. 

## 1. Core Value Proposition
The MVP exists to prove one single hypothesis: **Shoppers are willing to pay upfront into an Escrow system for a product requested via a Traveler's custom link.**

## 2. The "Ruthless" 5 Core Features

To prevent scope creep, the MVP is restricted to these 5 interconnected features:

1. **Trip Publisher (URL-Based)**
   * Travelers input: Destination (e.g., Tokyo), Travel Dates, and Baggage Capacity (kg).
   * System generates: A unique, shareable link (e.g., `mytrip.com/t/budi-tokyo-24`).
   * *Cut from MVP:* Internal Discovery Feed, AI recommendations.

2. **Structured Request Form**
   * Shoppers click the Traveler's link and submit: Item Name, Reference URL, Photo, Quantity, and Willingness to Pay (Maximum budget).
   * *Cut from MVP:* Pre-filled product catalogs, in-app Chat negotiation.

3. **Quotation Engine**
   * Travelers view incoming requests in a dashboard.
   * Travelers accept a request by returning a Quote: Exact Item Price + Jastip Fee.

4. **Escrow Integration**
   * Shoppers accept the Quote and pay the total amount via a Payment Gateway (Virtual Account/E-Wallet).
   * Funds are locked in a platform Escrow account.

5. **3-State Order Tracker**
   * A unified dashboard tracking three explicit states:
     1. **Paid** (Shopper has funded Escrow, Traveler is safe to buy).
     2. **Purchased** (Traveler has secured the item abroad).
     3. **Delivered** (Item shipped domestically, Escrow funds released to Traveler).
   * *Cut from MVP:* Auto-generated AWB (shipping labels), live GPS tracking.

## 3. What is EXPLICITLY Out of Scope (Deferred to V2)

*   **Destination Discovery Feed:** Travelers must bring their own demand via social media sharing.
*   **In-App Community / Forums:** Use existing WhatsApp/Discord groups for community building.
*   **Creator Storefronts & Live Shopping:** Creators can use the basic Traveler workflow for now.
*   **Identity Verification System:** Traveler identity verification (Government ID / KYC) is deferred to Phase 2 (V2.0) to keep MVP onboarding frictionless.
*   **Complex Reputation / Rating System:** MVP will just show "Completed Transactions" count.
