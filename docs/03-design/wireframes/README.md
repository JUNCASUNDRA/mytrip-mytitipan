# Screen Wireframes Specification Index

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This directory contains the low-fidelity layout structures and user interface specifications for the **My Trip My Titipan** MVP. The specs have been split into modular, screen-specific files to ensure clear design rules and implementation clarity.

---

## Screen Inventory Index Table

| Screen ID | Screen Name | Actor Access | Detailed Wireframe Specification |
| :--- | :--- | :--- | :--- |
| **SCR-001** | Login / Register | All Users | 📄 **[login.md](common/login.md)** |
| **SCR-002** | Trip Landing Page | Shopper (Public) | 📄 **[trip-page.md](shopper/trip-page.md)** |
| **SCR-003** | Product Request Form | Shopper | 📄 **[request-form.md](shopper/request-form.md)** |
| **SCR-004** | Shopper Dashboard | Shopper | 📄 **[shopper-dashboard.md](shopper/shopper-dashboard.md)** |
| **SCR-005** | Quote & Checkout Page | Shopper | 📄 **[checkout.md](shopper/checkout.md)** |
| **SCR-006** | Traveler Dashboard | Traveler | 📄 **[trip-dashboard.md](traveler/trip-dashboard.md)** |
| **SCR-007** | Create Trip Form | Traveler | 📄 **[create-trip.md](traveler/create-trip.md)** |
| **SCR-008** | Trip Share Modal | Traveler | 📄 **[trip-share.md](traveler/trip-share.md)** |
| **SCR-009** | Request Review Screen | Traveler | 📄 **[request-detail.md](traveler/request-detail.md)** |
| **SCR-010** | Traveler Order Details | Traveler | 📄 **[order-details.md](traveler/order-details.md)** |
| **SCR-011** | Review Submission | Shopper | 📄 **[review-submission.md](shopper/review-submission.md)** |
| **SCR-012** | Admin Dashboard | Admin (Desktop) | 📄 **[dashboard.md](admin/dashboard.md)** |
| **SCR-013** | Admin Dispute Manager | Admin (Desktop) | 📄 **[dispute.md](admin/dispute.md)** |

---

## Wireframe Guidelines & Safeguards

1. **Grayscale Layouts Only**: Layout specifications focus strictly on element hierarchy, card groupings, input fields, and action buttons without colors to avoid premature visual coupling.
2. **Component Mapping**: Low-fidelity wireframe definitions match the component layout structure directly, making it easier for backend and frontend developers to align routes, forms, and validation handlers.
3. **Traceability**: Every individual layout spec is mapped to the relevant product requirements, user stories, and state-machine transitions to ensure 100% feature trace coverage.
