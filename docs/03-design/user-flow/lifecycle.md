---
agent: UX Designer Agent (UXA)
version: 1.2.0
date: 2026-06-17
phase: phase-1
status: Approved
---

# Status Lifecycle Management - Phase 1

This document maps user interface behaviors, status updates, and ownership definitions across the request lifecycle in Phase 1.

## 1. Core Lifecycle Transitions

The Phase 1 coordination tool uses five primary statuses:

| Status | Owner | Action/CTA | Next Step |
| --- | --- | --- | --- |
| **REQUESTED** | Traveler | "Accept Request" | Moves to `ACCEPTED` |
| **ACCEPTED** | Traveler | "Update Progress" | Moves to `IN_PROGRESS` |
| **IN_PROGRESS** | Traveler | "Mark Ready" | Moves to `READY_FOR_DELIVERY` |
| **READY_FOR_DELIVERY** | Shopper / Traveler | "Confirm Receipt" / "Hand Over Item" | Moves to `COMPLETED` |
| **COMPLETED** | System | *Finalized* (Triggers Review Form) | Moves to Completed History |

---

## 2. UX Design Requirements per Status

### A. REQUESTED
- **Context**: Shopper has submitted form details.
- **Traveler UI**: Highlight in "Pending Requests" inbox. Highlight item photo and notes. CTA: "Accept Request", "Decline".
- **Shopper UI**: Status message: "Waiting for traveler response". Disable cancel option if accepted.

### B. ACCEPTED
- **Context**: Traveler commits to the request.
- **Traveler UI**: Display in "Active List". CTA: "Update Progress".
- **Shopper UI**: Status message: "Traveler accepted request".

### C. IN_PROGRESS
- **Context**: Traveler is sourcing, checking availability, or traveling.
- **Traveler UI**: Active sourcing indicator. CTA: "Mark Ready".
- **Shopper UI**: Status message: "Traveler is sourcing your item".

### D. READY_FOR_DELIVERY
- **Context**: Item is ready for handover or shipping.
- **Traveler UI**: CTA: "Hand Over Item".
- **Shopper UI**: Highlight state. Prominent CTA: "Confirm Receipt".

### E. COMPLETED
- **Context**: Delivery/handover confirmed.
- **Traveler UI**: Display in "Trip History".
- **Shopper UI**: Prompt for "Submit Review". Show review form.

---

## 3. Termination States

- **DECLINED**: Traveler rejects incoming `REQUESTED` item.
- **CANCELLED**: Either shopper or traveler cancels prior to the `IN_PROGRESS` stage. Requires reason.
