---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/03-user-flow/README.md
outputs:
  - navigation-map
depends_on:
  - 02-information-architecture/screen-inventory.md
---
# Global Navigation Map & Information Architecture

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the application information architecture, layout grids, permission boundaries, and navigation maps for the **My Trip My Titipan** MVP.

---

## 1. Global Layout Structures

### A. Mobile Web Frame (Shopper & Traveler Context)

- **Header Bar:** Brand logo (MyTrip-MyTitipan), User Avatar trigger (opens dropdown with Profile Link & Logout CTA), and active role switch selector (Switch to Traveler / Switch to Shopper).
- **Footer Navigation Tabs:** Persistent bottom tab bar displayed on all authenticated shopper/traveler dashboards.
  - *Shopper Mode Tab Bar:*
    - Tab 1: **Home** (Directs to `SCR-004: Shopper Dashboard` showing My Requests).
    - Tab 2: **Profile** (Directs to user details).
  - *Traveler Mode Tab Bar:*
    - Tab 1: **Home** (Directs to `SCR-006: Traveler Dashboard` showing My Trips & Requests).
    - Tab 2: **Profile** (Directs to traveler info).
  - *Floating CTA (Traveler Mode Only):*
    - **+ Create Trip** (Floating CTA on Traveler Dashboard, redirects to `SCR-007: Create Trip`).

---

## 2. Route & Access Boundaries

To protect user safety and simplify checkout transitions, the router enforces access controls:

```mermaid
graph TD
    G1[Guest / Public Access] --> R1[SCR-002: Trip Landing Page]
    G1 --> R2[SCR-001: Login]
    
    A1[Shopper Authenticated Route] --> R3[SCR-003: Request Form]
    A1 --> R4[SCR-004: Shopper Dashboard]
    A1 --> R5[SCR-005: Request Detail]
    A1 --> R6[SCR-011: Review Form]
    
    T1[Traveler Authenticated Route] --> R7[SCR-006: Traveler Dashboard]
    T1 --> R8[SCR-007: Create Trip]
    T1 --> R9[SCR-008: Trip Share]
    T1 --> R10[SCR-009: Request Review]
    T1 --> R11[SCR-010: Traveler Request Detail]

    style G1 fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style A1 fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px
    style T1 fill:#e8f5e9,stroke:#1b5e20,stroke-width:2px
```

- **Guest Mode:**
  - Public users can visit `SCR-002` (Trip Landing Page) and `SCR-001` (Login).
  - If a guest clicks "Request Item" on `SCR-002`, the form details are cached in session state, and the router redirects to `SCR-001` for registration.
- **Auth Guards (User Roles):**
  - Accessing screens `SCR-003` to `SCR-011` requires active user session cookies.
  - A traveler trying to request an item on their own trip link is blocked at route level (`shopper.id != traveler.id`).