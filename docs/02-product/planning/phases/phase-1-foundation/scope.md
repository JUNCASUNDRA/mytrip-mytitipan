---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
phase: phase-1
status: approved
priority: must-have
depends_on:
  - core-user-flow.md
outputs:
  - ux-flow
  - technical-requirement
---

# Phase 1 Scope: Foundation (MVP)

> **Status**: Approved  
> **Last Updated**: 2026-06-14  

## 1. Rationale for Foundation Phase
The objective of Phase 1 is to validate the core user behavior: will travelers and shoppers use a single structured platform to coordinate jastip lists instead of relying on scattered social media posts and chat messaging apps? We focus strictly on request management and trip coordination without payment operations.

## 2. Core Capabilities
1.  **Trip Publisher:** Traveler registers upcoming journeys (Destination, Dates, and optional notes) and copies a shareable URL.
2.  **Traveler Trip Page:** Displays traveler profile info, destination details, active requests, and request status.
3.  **Product Request Form:** Shoppers submit a structured product name, reference URL, photo upload, quantity, and notes. No budget inputs or payments are required.
4.  **Request Lifecycle Management:** Travelers view requests and manually transition their status via the simplified pipeline.
5.  **Request Timeline:** Chronological status history log shown on the request details screen to build traveler-shopper trust.
6.  **Simple Record History:** Persists past trip history and completed request records to serve as the reputation baseline.

## 3. Scope Boundaries
The status transitions are coordination-focused:

$$\text{Requested} \longrightarrow \text{Accepted} \longrightarrow \text{In Progress} \longrightarrow \text{Ready for Delivery} \longrightarrow \text{Completed}$$

To avoid premature transactional expectations, we utilize **In Progress** and **Ready for Delivery** instead of *Purchased* / *Delivered*.

## 4. Excluded Subsystems (Deferred to Phase 2/3)
*   No payment gateway checkouts, escrow accounts, or quotation calculations.
*   No automated baggage weight slot tracking (in kg).
*   No traveler KYC government ID verification.
*   No Courier API logistics integrations or AWB print labels.
