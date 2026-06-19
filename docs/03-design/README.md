# Design Documentation (03-design)

This directory contains the visual architecture, user interface (UI/UX) designs, and assets for the My Trip My Titipan platform.

## Directory Structure

| Folder | Description |
| :--- | :--- |
| **[user-flow/](user-flow/)** | **Core UX Flows (Shopper, Traveler, and Status Lifecycle maps).** |
| **[phases/](phases/)** | **Phase-specific visual requirements and wireframe scopes (Phase 1, 2, 3).** |
| [design-system/](design-system/) | Design tokens, Foundations, Typography, and UI Components. |
| [information-architecture/](information-architecture/) | Navigation maps and application routing. |
| [ux-research/](ux-research/) | Core design principles, assumptions, and usability logs. |
| [mockups/](mockups/) | High-fidelity visual interface designs and screenshots. |
| [ui-assets/](ui-assets/) | Icons, brand illustrations, and image assets. |

## UX Design Lifecycle

The design process is segmented by development phases to ensure focused delivery:

1.  **[Phase 1: Foundation (Current)](phases/phase-1/)**: Lightweight request tracking and trip coordination.
2.  **[Phase 2: Transaction](phases/phase-2/)**: Payment, escrow, and quotation engines.
3.  **[Phase 3: Platform](phases/phase-3/)**: Discovery, logistics APIs, and global scaling.

## Key Artifacts

- **[Phase 1 User Flows](user-flow/)**: Interactive maps for [Shopper Flow](user-flow/shopper-flow.md) and [Traveler Flow](user-flow/traveler-flow.md).
- **[Status Lifecycle](user-flow/lifecycle.md)**: The five-stage status machine (`REQUESTED` → `ACCEPTED` → `IN_PROGRESS` → `READY_FOR_DELIVERY` → `COMPLETED`).
- **[Wireframe Scope](phases/phase-1/wireframe-scope.md)**: Screen-by-screen inventory for the Phase 1 launch.
- **[Handoff Specification](HANDOFF.md)**: Master design contract and out-of-scope boundaries.

---

## Design Principles

1.  **Documentation First**: Every UI change must be preceded by a wireframe update.
2.  **Mobile-First**: Primary user interaction happens via shared links on mobile devices.
3.  **Trust-Centric**: Visual design must emphasize traveler history and request transparency.
