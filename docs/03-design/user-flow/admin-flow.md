---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/03-user-flow/README.md
outputs:
  - admin-ux-flow
  - dispute-resolution-states
depends_on:
  - 02-information-architecture/screen-inventory.md
  - 03-user-flow/exception-flows.md
---

# Admin UX User Flow Specifications

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the step-by-step user interaction flow, navigation entry/exit points, screen inventory mappings, and interface states for the **Admin** actor (platform operators) in the My Trip My Titipan MVP.

---

## 1. Journey Entry & Exit Points

* **Entry Point (Input):** Admin accesses the platform backend administrative login page url (protected route) and authenticates using their designated administrator credentials.
* **Exit Point (Output):** Admin clicks the "Logout" button in the navigation header, clearing their active session token, or the session automatically times out, redirecting them to `SCR-001`.

---

## 2. Screen Mapping & Step-by-Step Flow

Every admin interaction maps to a unique Screen ID from the design inventory:

```mermaid
flowchart TD
    E[Entry: Admin Login Page] --> S1[SCR-001: Authenticate with Admin Credentials]
    S1 --> S2[SCR-012: Admin Dashboard Overview]
    
    S2 -->|Views metrics, audits transactions| S2
    S2 -->|Clicks "View Disputes" / Selects Dispute Card| S3[SCR-013: Admin Dispute Manager]
    
    S3 -->|Inspects dispute timeline, uploaded evidence, courier status| S3
    
    S3 -->|Option A: Selects Refund Shopper| M1[Mandatory Justification Modal]
    M1 -->|Enters rationale >= 20 chars & submits| S4[Refund Processed & Email Alert Sent]
    S4 --> S2
    
    S3 -->|Option B: Selects Payout Traveler| M2[Mandatory Justification Modal]
    M2 -->|Enters rationale >= 20 chars & submits| S5[Payout Processed & Email Alert Sent]
    S5 --> S2
    
    S3 -->|Option C: Click Contact User| S6[Draft system-mediated email]
    S6 --> S3
    
    S3 -->|Option D: Click Suspend / Flag Account| S7[Modal: Select violation reason & Suspend]
    S7 --> S3
    
    S2 -->|Clicks Logout| EX[Exit: Session Cleared & Redirected to SCR-001]
```

### Flow Breakdown & Screen Actions:
1. **Login & Session Validation (`SCR-001`):** Admin enters email and password credentials. Successful login initiates a session token and redirects to the dashboard.
2. **Dashboard Review (`SCR-012`):** Admin views high-level cards showing platform health metrics. Clicks tab menus in the sidebar to review transactions, active trips, or open disputes.
3. **Dispute Investigation (`SCR-013`):** Admin opens a disputed order ticket. Reviews Shopper and Traveler transaction history, purchase receipts, chat logs (where applicable), and courier tracking data.
4. **Resolution Decision (`SCR-013` Modal overlays):**
   * **Refund Shopper:** Admin inputs reason text, confirms refund, and system triggers gateway settlement reversal.
   * **Release Payout:** Admin inputs reason text, confirms payout release, and system completes traveler escrow disbursement.

---

## 3. User-Centered Admin Dashboards & Action Panels

### A. Admin Dashboard Overview Layout (`SCR-012`)
The admin interface is optimized for desktop viewports, using a split panel design layout:
* **Persistent Left Sidebar Menu:** Quick access links for:
  1. *Dashboard Overview* (`SCR-012`)
  2. *Open Disputes* (`SCR-013`)
  3. *Escrow Ledger Logs*
* **Top KPI Card Row:** Displays five core operational metrics:
  * **Active Trips:** Total published trips with open available suitcase capacity.
  * **Pending Payments:** Total outstanding traveler quotes awaiting shopper checkout (within the 24h timer).
  * **Active Orders:** Total orders funded in escrow and currently in procurement or shipping stages.
  * **Open Disputes:** Number of orders currently in `Disputed` state (flagged in orange).
  * **Total Revenue / Transaction Volume:** Cumulative value of escrow funds processed in IDR.
* **Audit Transaction Log Table:** Paginated row list featuring order hashes, traveler profiles, shopper names, prices, status badges (e.g., `Paid`, `Purchasing`, `In Transit`, `Disputed`), and timestamp markers. Clicking a row redirects the Admin to `SCR-013`.

### B. Admin Dispute & Detail Resolver (`SCR-013`)
When an administrator clicks a disputed order card, they enter the resolution panel, which presents the interface in three logical content zones:

1. ** Fulfillments Timeline & Receipts:**
   * Shows chronological order milestones (Quote Sent -> Payment Received -> Sourcing Initiated -> Package Dispatched).
   * Displays Traveler's uploaded purchase receipt image thumbnail (clickable to expand in lightbox).
   * Includes external courier API status checker showing AWB logs.
2. ** Dispute Evidence Preview:**
   * Shopper's text description of the grievance.
   * Uploaded photos of the damaged or wrong items.
3. ** Action Resolution CTA Panel:**
   * **Refund Shopper CTA (Primary Red Button):** Clicks to trigger a confirmation modal. The modal requests text explanation, verifies characters, and invokes gateway refund webhook.
   * **Payout Traveler CTA (Primary Green Button):** Clicks to trigger a confirmation modal. Recommends releasing funds when traveler proof of shipment is verified and correct.
   * **Contact Support (Secondary Border Button):** Launches mail client populated with traveler/shopper details and order ID references.
   * **Flag/Suspend User Account (Danger Secondary Button):** Allows temporary freeze of fraudulent traveler profiles or bad-faith shopper accounts.

---

## 4. Separation of Business Rules vs. UX Behaviors

Logical platform rules are isolated from interface components:

### A. Escrow Modifications Audit Logging
* **Business Rule:**
  * All escrow-modifying actions (Refunds and Payouts) must write an immutable record to the database audit log, containing: `audit_id`, `admin_user_id`, `action_type`, `order_id`, `amount`, `justification_text`, and `timestamp`.
* **UX Behavior:**
  * When Admin clicks "Refund Shopper" or "Payout Traveler", a modal overlays. The "Confirm Action" button is disabled by default.
  * Admin must enter a minimum of 20 characters in the text input justification area. A dynamic character counter displays `X / 20` characters. Once the count reaches 20, the confirm button transitions to active state.

### B. Dispute Escalation Auto-Freeze
* **Business Rule:**
  * Escalating an order to `Disputed` suspends the automated 7-day delivery settlement confirmation timer.
* **UX Behavior:**
  * The order detail header displays a prominent orange badge: `Escrow Frozen (Disputed)`.
  * The countdown timer ticker is hidden, and any auto-completion routines are disabled.

---

## 5. Journey State & Exception UX Variations

### A. Empty Dispute Center State
* **Visual:** Shield verification graphic icon displayed on `SCR-012`.
* **UX Copy:** *"All quiet! No active disputes or escrow investigations at this time."*

### B. Empty Transaction Search Logs State
* **Visual:** Folder search graphic icon.
* **UX Copy:** *"No transactions found matching the selected dates or filter criteria. Reset filters to try again."*

### C. Processing Transaction Overlay
* **UX Behavior:** Disable all sidebar navigations and display a processing dialog modal: `Processing Escrow transaction... Please do not close this browser tab.` to prevent double-submit actions.