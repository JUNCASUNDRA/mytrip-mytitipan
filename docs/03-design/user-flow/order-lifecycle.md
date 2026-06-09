---
agent: UX Designer Agent (UXA)
version: 1.0.0
date: 2026-06-09
status: Draft
predecessor: docs/03-design/user-flow/README.md
---

# Order Lifecycle

This document defines the status transitions, system triggers, and baggage capacity operations during the order lifecycle. It is split into two logical stages to guide database design and backend state machine transitions: the **Request Lifecycle** (pre-payment) and the **Fulfillment Lifecycle** (post-payment).

---

## 1. Status Transition Table

The following table maps the state transitions for the MVP order engine:

| Status | Stage | Description | System Trigger | Allowed Next States | Baggage Capacity Action |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Requested** | Request | Shopper submitted a product request. | Shopper clicks "Submit Request" | `Quoted`, `Cancelled` | None |
| **Quoted** | Request | Traveler has sent a quote. | Traveler sends quote details | `Payment Pending`, `Cancelled`, `Expired` | **Reserve capacity** (Starts 24h timer) |
| **Payment Pending** | Request | Shopper is in the checkout portal. | Shopper clicks "Pay Now" | `Paid`, `Expired` | Keep reserved |
| **Paid** | Fulfillment | Payment is confirmed. Escrow is funded. | Gateway webhook (success) | `Purchased`, `Cancelled` | **Confirm Lock** (Lock baggage slot) |
| **Purchased** | Fulfillment | Traveler bought the item abroad. | Traveler clicks "Mark Purchased"| `In Transit` | Locked |
| **In Transit** | Fulfillment | Traveler shipped the package domestically. | Traveler inputs tracking AWB | `Delivered`, `Completed` | Locked |
| **Delivered** | Fulfillment | Shopper confirmed package receipt. | Shopper clicks "Confirm Receipt"| `Completed` | Released (Trip completed) |
| **Completed** | Fulfillment | Escrow released to traveler wallet. | Auto-release or manual release | None (Final State) | Released (Trip completed) |
| **Expired** | Request | Quote or payment window closed. | 24-hour expiry timer triggers | None (Final State) | **Release capacity** (Restore baggage slots) |
| **Cancelled** | Both | Request rejected or custom refund. | Traveler decline / Admin refund | None (Final State) | **Release capacity** / Unlock baggage slots |

---

## 2. State Transition Diagram

The state transitions are managed strictly by the platform's transaction backend:

```mermaid
stateDiagram-v2
    [*] --> Requested : Shopper Submits Request
    
    Requested --> Quoted : Traveler Sends Quote (Capacity Reserved)
    Requested --> Cancelled : Traveler Rejects / Shopper Withdraws
    
    Quoted --> PaymentPending : Shopper Clicks "Pay Now"
    Quoted --> Expired : 24h Expiry Timeout (Capacity Released)
    Quoted --> Cancelled : Shopper Rejects / Traveler Cancels
    
    PaymentPending --> Paid : Payment Success (Capacity Locked)
    PaymentPending --> Expired : 24h Expiry Timeout (Capacity Released)
    
    Paid --> Purchased : Traveler Marks "Purchased"
    Paid --> Cancelled : Traveler Out of Stock (Refund via Admin)
    
    Purchased --> InTransit : Traveler Inputs Tracking Number
    
    InTransit --> Delivered : Shopper Confirms Receipt
    InTransit --> Completed : 7-Day Auto-Release System Trigger
    
    Delivered --> Completed : Funds Released to Traveler Wallet
    
    Cancelled --> [*]
    Expired --> [*]
    Completed --> [*]
```

---

## 3. Capacity & Expiry Business Rules

1.  **24-Hour Expiry Window**: The transition from `Quoted` or `Payment Pending` to `Expired` is managed by an automated cron job/timer. Once the timestamp exceeds `created_at + 24 hours`, the order state is updated to `Expired`, and the reserved weight is restored to the traveler's active trip.
2.  **Double Booking Protection**: The system check validates that `trip.available_capacity >= request.estimated_weight` before allowing the traveler to issue a quote.
3.  **Cancellation Post-Payment**: Once an order reaches `Paid`, standard cancellations are disabled. In case of extreme events (e.g., traveler cannot find the item, customs confiscation), the case must be escalated to the Admin to trigger a manual `Cancelled` state, returning the escrow money to the shopper.
