---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/use-cases/use-case-specifications.md
outputs:
  - admin-usecases
  - system-automations
depends_on:
  - state-machine.md
---

# Admin & System Use Case Specifications

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the formal Use Case specifications for the Admin actor (operations) and the System (automation/background processes) on the **My Trip My Titipan** platform.

---

## 1. Actor & System Use Case Index

| Use Case ID | Use Case Name | Priority | Status |
| :--- | :--- | :--- | :--- |
| **UC-012** | Monitor Transactions & Trips | Must Have | Done |
| **UC-006** | Manage Baggage Capacity (System) | Must Have | Done |
| **UC-013** | Auto-Expire Quote & Release Capacity (System) | Must Have | Done |
| **UC-014** | Send Notification (System) | Must Have | Done |

---

## 2. Use Case Specifications

### UC-012: Monitor Transactions & Trips
* **Use Case ID:** UC-012
* **Use Case Name:** Monitor Transactions & Trips
* **Primary Actor:** Admin
* **Goal:** Supervise platform health, view transaction metrics, and resolve exceptional cases.
* **Preconditions:** Admin is authenticated and authorized.
* **Trigger:** Admin accesses admin dashboard backend.
* **Main Flow:**
  1. Admin views overview statistics (Total active trips, active requests, escrow totals).
  2. Admin searches and views specific trip or order profiles.
* **Alternate Flow:**
  * *Dispute Resolution / Refund Override:* If an order is in dispute or cancelled post-payment, Admin triggers a manual override to update status to `REFUNDED` and release locked baggage capacity.
* **Postconditions:** Admin has monitored operations or executed required administrative actions.

### UC-006: Manage Baggage Capacity (Reserve & Lock)
* **Use Case ID:** UC-006
* **Use Case Name:** Manage Baggage Capacity (Reserve & Lock)
* **Primary Actor:** System
* **Goal:** Track and lock baggage capacity to prevent overbooking.
* **Preconditions:** A quote is sent, payment is made, or payment is cancelled/expired.
* **Trigger:** Quote is sent (Reserve) OR Payment is completed (Lock) OR Expiry/Cancellation occurs (Release).
* **Main Flow (Reservation):**
  1. System checks remaining trip capacity.
  2. If sufficient, system temporarily deducts item weight from "available capacity" and adds it to "reserved capacity".
* **Main Flow (Locking):**
  1. Upon successful checkout, system converts "reserved capacity" to "locked capacity".
  2. If trip capacity reaches zero, system automatically changes Trip status to "Full" and disables new request submissions.
* **Main Flow (Release):**
  1. Upon quotation expiry, payment failure, or cancellation, system deducts estimated weight from "reserved capacity" and adds it back to "available capacity".
* **Postconditions:** Baggage capacity calculations are updated.

### UC-013: Auto-Expire Quote & Release Capacity
* **Use Case ID:** UC-013
* **Use Case Name:** Auto-Expire Quote & Release Capacity
* **Primary Actor:** System
* **Goal:** Release capacity reserved by non-responsive shoppers or failed checkouts.
* **Preconditions:** Order status is `QUOTED` or `PAYMENT_PENDING`.
* **Trigger:** System cron worker detects quotation created > 24 hours ago without payment OR gateway webhook reports failed/expired payment.
* **Main Flow:**
  1. Cron or Webhook identifies expired/failed quotation.
  2. System cancels quote, setting order status to `EXPIRED`.
  3. System triggers capacity release: deducts estimated weight from "reserved capacity" and adds it back to "available capacity".
  4. System triggers *UC-014: Send Notification* to both parties.
* **Postconditions:** Status is `EXPIRED`; capacity is released.

### UC-014: Send Notification
* **Use Case ID:** UC-014
* **Use Case Name:** Send Notification
* **Primary Actor:** System
* **Goal:** Notify users of important order lifecycle events.
* **Preconditions:** System event is triggered.
* **Trigger:** Status changes (Requested, Quoted, Payment Pending, Paid, Purchasing, Purchased, In Transit, Delivered, Completed, Expired, Cancelled, Refunded).
* **Main Flow:**
  1. System fetches user communication channels matching target role.
  2. System compiles notification template with order metadata.
  3. System dispatches notification (email).
* **Postconditions:** Notification is sent.
