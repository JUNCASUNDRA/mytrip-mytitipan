---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/strategy/user-persona.md
outputs:
  - user-pain-points
depends_on:
  - usability-assumptions.md
---

# User Pain Points & Friction Points

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the primary user pain points identified for Shoppers and Travelers in peer-to-peer (P2P) jastip services, along with their UX-driven mitigations for the **My Trip My Titipan** platform.

---

## 1. Shopper Pain Points & Mitigations

### Pain Point A: Fraud & Direct Payment Anxiety
* **Context:** Shoppers are highly anxious about transferring money directly to a traveler's personal bank account before receiving the requested item.
* **UX Friction:** Pre-paying strangers lacks structural security.
* **UX Mitigation:**
  * Displays prominent trust badges and copywriting: `Escrow Secured 🔒: Funds are held safely by the platform until you confirm receipt.`
  * Showcases traveler rating indicators (stars, total completed jastip orders) directly in public view (`SCR-002`).
  * Standardized Virtual Account (VA) or E-wallet payment screens (`SCR-005`) that confirm the recipient is the platform escrow, not an individual traveler.

### Pain Point B: Sourcing Miscommunication
* **Context:** Shoppers describe items vaguely, leading to travelers purchasing the wrong product model, color, or price range.
* **UX Friction:** Endless messaging chats to resolve specs.
* **UX Mitigation:**
  * Mandatory field constraints on the Product Request Form (`SCR-003`) requiring specific Item Name, description text, Willing-to-Pay Budget (IDR), and a mandatory photograph/reference link upload.
  * Replaces unstructured chat dialogues with a formal quote review screen (`SCR-005`) showing item photos, proposed fees, and total price breakdown.

---

## 2. Traveler Pain Points & Mitigations

### Pain Point C: Out-of-Pocket Capital Risk
* **Context:** Travelers must purchase items abroad using their own physical funds. If the shopper cancels or refuses the item, the traveler loses capital and gets stuck with unwanted inventory.
* **UX Friction:** Travelers are hesitant to start purchasing items.
* **UX Mitigation:**
  * Visual green status lock icons (`Escrow Funded 🔒`) on the Traveler Dashboard (`SCR-006`) and Traveler Order Details tracker (`SCR-010`).
  * Microcopy explaining: *"Funds are secured in escrow. Your payout is guaranteed once Courier tracking verifies dispatch."*

### Pain Point D: Administrative & Logistics Overload
* **Context:** Travelers are on vacation/business trips and do not want to manage spreadsheets, calculations, or coordinate multiple courier pick-ups.
* **UX Friction:** Complex platform admin panel interfaces.
* **UX Mitigation:**
  * Simplified Traveler Order Details interface (`SCR-010`) featuring a step-by-step progressive checklist:
    1. **Sourcing:** Traveler clicks "Start Purchasing" when going to store.
    2. **Receipt Upload:** Take photo of paper invoice receipt.
    3. **Shipping:** Enter Courier name and AWB tracking code.
  * Weight capacity tracker is calculated automatically in the background, showing a dynamic remaining capacity HSL visual bar.

### Pain Point E: Inventory Reservation Lock (Unpaid Requests)
* **Context:** Shoppers submit request drafts, and travelers generate quotes. These quotes reserve luggage space. If shoppers delay checking out, the traveler's baggage capacity remains locked.
* **UX Friction:** Capacity blocked for genuine buyers.
* **UX Mitigation:**
  * Strict 24-hour expiration window on outstanding quotes.
  * Real-time countdown timer prominently displayed on checkout widgets (`SCR-004`, `SCR-005`) prompting immediate payment.
