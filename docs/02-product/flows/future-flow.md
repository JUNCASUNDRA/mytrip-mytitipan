---
agent: Product Manager Agent (PMA)
version: 1.0.0
date: 2026-06-17
status: Draft
---

# Future Flows: Phase 2 (Transaction & Escrow) & Phase 3 (Platform Expansion)

This document contains out-of-scope system behaviors for the initial Phase 1 MVP. These flows serve as architecture preparation points to ensure modular growth.

---

## 1. Phase 2: Transaction & Escrow Flows

In Phase 2, secure payment gateways and quotation flows are introduced.

### Shopper Transaction Flow
1. **Receive Quote**: Shopper receives notification for a detailed quote from traveler (Item Price + Jastip Fee).
2. **Escrow Funding**: Shopper clicks "Pay Now" and completes checkout (funds locked in platform escrow).
3. **Receipt Release**: Upon physical receipt, shopper confirms delivery which triggers escrow release to traveler's wallet.

### Traveler Sourcing Flow
1. **Send Quote**: Traveler reviews shopper request and drafts/sends a formal quotation.
2. **Payment Watch**: Traveler monitors dashboard for successful shopper escrow payment (`Paid`).
3. **Start Sourcing**: Once payment is confirmed, traveler commences sourcing the item.
4. **Collect Funds**: After delivery is confirmed, traveler withdraws earnings from platform wallet.

---

## 2. Phase 3: Discovery Feed & Logistics Expansion

Phase 3 introduces platform discovery mechanisms and integrated local logistics.

### Discovery Feed (No Shared Link Required)
1. **Search Trips**: Shoppers can browse and search active travel routes by country or city on the homepage without needing a direct link.
2. **Storefront Collections**: Travelers publish collections/storefront templates of popular items they can easily procure.

### Logistics Integration
1. **Shipping Carrier API**: Traveler books shipping through integrated courier APIs (e.g., JNE, J&T).
2. **Fulfillment Map**: Shopper clicks tracking code in the dashboard to see shipment location on a map.
3. **KYC Verification**: Identity checks (KYC) for travelers to earn verified badges.
