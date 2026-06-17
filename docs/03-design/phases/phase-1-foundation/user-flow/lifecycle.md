---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
phase: phase-1-foundation
status: draft
---

# Status Lifecycle Management - Phase 1

## Core Lifecycle Transitions

The Phase 1 MVP uses five primary manual statuses to coordinate the jastip request.

| Status | Owner | Action/CTA | Next Step |
| :--- | :--- | :--- | :--- |
| **REQUESTED** | Traveler | "Accept Request" | Moves to ACCEPTED |
| **ACCEPTED** | Traveler | "Mark as Purchased" | Moves to PURCHASED |
| **PURCHASED** | Traveler | "Mark as Delivered" | Moves to DELIVERED |
| **DELIVERED** | Shopper | "Confirm Receipt" | Moves to COMPLETED |
| **COMPLETED** | Shopper | "Submit Review" | Moves to REVIEWED |

## UX Design Requirements per Status

### 1. REQUESTED (Incoming)
- **Explanation**: Shopper has submitted the request.
- **Traveler UI**: Highlight as "New" or "Action Required". Show item photos and notes clearly.
- **Shopper UI**: "Waiting for Traveler Response".

### 2. ACCEPTED (Commitment)
- **Explanation**: Traveler has committed to sourcing the item.
- **Traveler UI**: Move to "Active Requests" list. Provide "Update to Purchased" CTA.
- **Shopper UI**: "Traveler is looking for your item".

### 3. PURCHASED (Procured)
- **Explanation**: Item has been bought by the traveler.
- **Traveler UI**: Provide option to upload purchase photo/receipt. Provide "Mark as Delivered" CTA.
- **Shopper UI**: "Item Purchased! Waiting for delivery/handover".

### 4. DELIVERED (Arrival)
- **Explanation**: Item has been handed over or shipped domestically.
- **Shopper UI**: Highlight as "Action Required". Provide large "Confirm Receipt" button.
- **Traveler UI**: "Waiting for Shopper Confirmation".

### 5. COMPLETED (Finalized)
- **Explanation**: Coordination is finished.
- **Shopper UI**: Prompt for "Submit Review".
- **Traveler UI**: Show in "History" tab.

## Termination States
- **DECLINED**: Traveler rejects an incoming "Requested" item.
- **CANCELLED**: Either party cancels (requires reason input if "Accepted").
