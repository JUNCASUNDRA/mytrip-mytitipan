---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/planning/core-user-flow.md
---

# Use Case Specifications

This document outlines the formal Use Case Diagram Specification, Detailed Use Case Specifications, and the Traceability Matrix for the **My Trip My Titipan** MVP.

---

# 1. Use Case Diagram Specification

## Actor: Traveler (Supply Side)

### Domain: Onboarding & Authentication
* **UC-001: Register & Login**
  * *Description:* Allows a traveler to register an account via OTP or Google OAuth, and log in to manage trips and orders.

### Domain: Trip Management
* **UC-002: Publish Trip**
  * *Description:* Allows a traveler to create a trip listing with a destination, travel dates, and baggage capacity limit, generating a shareable trip link.

### Domain: Order & Quotation Management
* **UC-005: Create & Send Quotation**
  * *Description:* Allows a traveler to review a request, accept it, and send a quotation.
  * *Relationships:* Includes *UC-006: Reserve Baggage Capacity*.
* **UC-009: Ship & Deliver Item**
  * *Description:* Allows a traveler to ship a purchased item to the shopper domestically and input the tracking details.
* **UC-016: Procure & Purchase Item**
  * *Description:* Allows a traveler to transition an order to "Purchasing" when starting procurement, and to "Purchased" (with optional receipt/photo upload) upon buying the item.

### Domain: Trip Completion & Payout
* **UC-015: Complete Trip**
  * *Description:* Allows a traveler to mark a trip as Completed once all active orders are fulfilled, closing the trip lifecycle.

---

## Actor: Shopper (Demand Side)

### Domain: Onboarding & Authentication
* **UC-001: Register & Login**
  * *Description:* Allows a shopper to register and log in to request products and make payments.

### Domain: Demand Capture
* **UC-003: View Traveler Profile & Trip Page**
  * *Description:* Allows a shopper to open a shared trip link to view traveler stats (completed orders, reviews, remaining capacity) and destination timeline.
* **UC-004: Submit Product Request**
  * *Description:* Allows a shopper to submit a request for an item including its name, photo, reference URL, and maximum budget.

### Domain: Payment & Tracking
* **UC-007: Pay via Escrow**
  * *Description:* Allows a shopper to accept a quote and pay via virtual account or e-wallet, locking the funds in the platform escrow.
  * *Relationships:* Includes *UC-006: Lock Baggage Capacity*.
* **UC-008: Track Order Status**
  * *Description:* Allows a shopper to track status changes (`Paid` → `Purchased` → `In Transit` → `Delivered` → `Completed`).

### Domain: Fulfillment & Feedback
* **UC-010: Confirm Delivery**
  * *Description:* Allows a shopper to confirm they have received the package, triggering the payout to the traveler.
  * *Relationships:* Extends *UC-011: Submit Review & Rating*.
* **UC-011: Submit Review & Rating**
  * *Description:* Allows a shopper to submit a text review and star rating for the traveler.

---

## Actor: Admin (Operations)

### Domain: Platform Monitoring
* **UC-012: Monitor Transactions & Trips**
  * *Description:* Allows an administrator to view active trips, order lifecycles, and transaction history for customer service and operational overview.

---

## Actor: System (Automation)

### Domain: Capacity & Expiry Automation
* **UC-006: Manage Baggage Capacity (Reserve & Lock)**
  * *Description:* Automates temporary baggage weight reservation when a quote is created, and confirms the capacity lock when payment is completed.
* **UC-013: Auto-Expire Quote & Release Capacity**
  * *Description:* Automatically expires unpaid quotes after 24 hours or upon payment gateway failure/expiry, releasing the reserved capacity.
* **UC-014: Send Notification**
  * *Description:* Automatically sends status updates to shoppers and travelers when milestones are met.

---

# 2. Detailed Use Case Specifications

### UC-001: Register & Login
* **Use Case ID:** UC-001
* **Use Case Name:** Register & Login
* **Primary Actor:** Traveler, Shopper
* **Goal:** Create a user account or access an existing account on the platform.
* **Preconditions:** User has a valid email address or Google account.
* **Trigger:** User opens the platform web app and clicks "Login/Register".
* **Main Flow:**
  1. User selects authentication method (OTP via Email or Google Social Login).
  2. If OTP: User enters email, receives code, and enters OTP.
  3. If Google Login: User authorizes application via Google consent page.
  4. System verifies credentials/OAuth token.
  5. System logs user in. If new user, creates database record and redirects to role onboarding.
* **Alternate Flow:**
  * *Authentication Fails:* If OTP is incorrect, system displays "Invalid OTP code" and prompts resubmission.
* **Postconditions:** User is authenticated and assigned a session token.

### UC-002: Publish Trip
* **Use Case ID:** UC-002
* **Use Case Name:** Publish Trip
* **Primary Actor:** Traveler
* **Goal:** Broadcast traveler travel plans and suitcase capacity.
* **Preconditions:** Traveler is registered and logged in.
* **Trigger:** Traveler clicks "Create Trip" on dashboard.
* **Main Flow:**
  1. Traveler inputs Destination (e.g. Tokyo), Dates (departure and return), and baggage slots capacity status.
  2. System validates input data.
  3. Traveler clicks "Publish Trip".
  4. System saves trip details, sets status to "Open", and generates a unique shareable link (e.g., `mytrip.com/t/budi-tokyo-24`).
  5. Traveler copies link to share on social media.
* **Alternate Flow:**
  * *Invalid inputs:* If dates are in the past, system shows error validation and stays on creation form.
* **Postconditions:** Trip is saved and active; shareable URL is active.

### UC-003: View Traveler Profile & Trip Page
* **Use Case ID:** UC-003
* **Use Case Name:** View Traveler Profile & Trip Page
* **Primary Actor:** Shopper
* **Goal:** Verify traveler credibility and details before requesting an item.
* **Preconditions:** A trip has been published by a traveler.
* **Trigger:** Shopper clicks a shared trip URL.
* **Main Flow:**
  1. System displays traveler trip page containing: traveler name, photo, trip route/dates, and trip status (Open/Limited/Full).
  2. Shopper clicks "View Profile".
  3. System displays traveler's completed trips count, completed orders count, and reviews/ratings history.
* **Alternate Flow:**
  * *Trip Closed:* If trip capacity is full or dates have passed, page displays "Full" or "Closed for requests" status; request button is disabled.
* **Postconditions:** Shopper has reviewed traveler trust signals.

### UC-004: Submit Product Request
* **Use Case ID:** UC-004
* **Use Case Name:** Submit Product Request
* **Primary Actor:** Shopper
* **Goal:** Request a traveler to buy an item from their destination.
* **Preconditions:** Shopper is logged in; trip is open for requests.
* **Trigger:** Shopper clicks "Request Item" on traveler's trip page.
* **Main Flow:**
  1. Shopper enters Item Name, Reference URL, Photo, Quantity, and Willingness to Pay.
  2. System validates that required fields are filled.
  3. Shopper submits request.
  4. System registers order in state "Requested".
  5. System triggers *UC-014: Send Notification* to the Traveler.
* **Alternate Flow:**
  * *User not logged in:* System redirects shopper to UC-001 (Register & Login) before saving request details.
* **Postconditions:** Request is saved; order status is "Requested".

### UC-005: Create & Send Quotation
* **Use Case ID:** UC-005
* **Use Case Name:** Create & Send Quotation
* **Primary Actor:** Traveler
* **Goal:** Present shopper with clear pricing terms for their request.
* **Preconditions:** Order status is "Requested"; traveler is logged in.
* **Trigger:** Traveler opens a request on their dashboard.
* **Main Flow:**
  1. Traveler reviews request.
  2. Traveler accepts request.
  3. System creates quotation.
  4. Traveler inputs: Item Price, Jastip Fee, and estimated weight/slots.
  5. Traveler clicks "Send Quote".
  6. Status changes to "Quoted".
  7. System triggers *UC-006: Manage Baggage Capacity (Reserve)*.
  8. System triggers *UC-014: Send Notification* to the Shopper with a 24-hour payment link.
* **Alternate Flow:**
  * *Traveler Rejects Request:* Traveler clicks "Decline Request". Status changes to "Cancelled" and shopper is notified.
* **Postconditions:** Quotation is sent; baggage capacity is reserved.

### UC-006: Manage Baggage Capacity (Reserve & Lock)
* **Use Case ID:** UC-006
* **Use Case Name:** Manage Baggage Capacity (Reserve & Lock)
* **Primary Actor:** System
* **Goal:** Track and lock baggage capacity to prevent overbooking.
* **Preconditions:** A quote is sent, payment is made, or payment is cancelled/expired.
* **Trigger:** Quote is sent (Reserve) OR Payment is completed (Lock) OR Expiry/Cancellation occurs (Release).
* **Main Flow (Reservation):**
  1. System checks remaining trip capacity.
  2. If sufficient, system temporarily deducts item weight/slots from "available capacity" and adds it to "reserved capacity".
* **Main Flow (Locking):**
  1. Upon successful checkout, system converts "reserved capacity" to "locked capacity".
  2. If trip capacity reaches zero, system automatically changes Trip status to "Full" and disables new request submissions.
* **Main Flow (Release):**
  1. Upon quotation expiry, payment failure, or cancellation, system deducts estimated weight from "reserved capacity" and adds it back to "available capacity".
* **Postconditions:** Baggage capacity calculations are updated.

### UC-007: Pay via Escrow
* **Use Case ID:** UC-007
* **Use Case Name:** Pay via Escrow
* **Primary Actor:** Shopper
* **Goal:** Securely fund the transaction into escrow to authorize purchase.
* **Preconditions:** Order status is "Quoted" or "Payment Pending".
* **Trigger:** Shopper clicks "Pay Now" on quote.
* **Main Flow:**
  1. Shopper clicks "Pay Now". Order status transitions to "Payment Pending".
  2. System redirects shopper to payment page and creates a transaction on the payment gateway (status: Created/Pending).
  3. Shopper completes checkout within payment gateway widget.
  4. Payment gateway sends payment webhook notification (Success) to platform.
  5. System locks funds in Escrow account.
  6. System triggers *UC-006: Manage Baggage Capacity (Lock)*.
  7. Status changes to "Paid".
  8. System triggers *UC-014: Send Notification* to the Traveler indicating it is safe to proceed with procurement.
* **Alternate Flow:**
  * *Payment Fails/Expires:* If the payment gateway sends a Failed/Expired callback, or the 24-hour payment window closes, status transitions directly to "Expired" and system triggers capacity release.
* **Postconditions:** Escrow is funded; status changes to "Paid" (or "Expired" on failure).

### UC-008: Track Order Status
* **Use Case ID:** UC-008
* **Use Case Name:** Track Order Status
* **Primary Actor:** Shopper, Traveler
* **Goal:** Monitor status changes and tracking updates.
* **Preconditions:** Order has been created.
* **Trigger:** User accesses the dashboard.
* **Main Flow:**
  1. User logs in and selects order.
  2. System displays tracking history showing: Status, Timestamp, and Tracking Number (if in transit).
* **Postconditions:** User is informed of exact status.

### UC-009: Ship & Deliver Item
* **Use Case ID:** UC-009
* **Use Case Name:** Ship & Deliver Item
* **Primary Actor:** Traveler
* **Goal:** Fulfill delivery to shopper post-travel.
* **Preconditions:** Order status is "Purchased"; traveler has returned.
* **Trigger:** Traveler drops package at courier and inputs tracking details.
* **Main Flow:**
  1. Traveler inputs domestic tracking number into the platform order dashboard.
  2. Traveler clicks "Mark as Shipped".
  3. Status changes to "In Transit".
  4. System triggers *UC-014: Send Notification* to Shopper with tracking details.
* **Postconditions:** Status is "In Transit".

### UC-010: Confirm Delivery
* **Use Case ID:** UC-010
* **Use Case Name:** Confirm Delivery
* **Primary Actor:** Shopper
* **Goal:** Release escrow funds to traveler upon receipt.
* **Preconditions:** Order status is "In Transit".
* **Trigger:** Shopper receives item and clicks "Confirm Receipt" in dashboard.
* **Main Flow:**
  1. Shopper clicks "Confirm Receipt".
  2. System changes status to "Delivered".
  3. System initiates escrow payout to traveler.
  4. Status changes to "Completed".
  5. System triggers *UC-011: Submit Review & Rating* (Extend).
* **Postconditions:** Escrow funds are released; order is "Completed".

### UC-011: Submit Review & Rating
* **Use Case ID:** UC-011
* **Use Case Name:** Submit Review & Rating
* **Primary Actor:** Shopper
* **Goal:** Rate traveler performance to build platform reputation.
* **Preconditions:** Order status is "Delivered" or "Completed".
* **Trigger:** Shopper completes delivery confirmation.
* **Main Flow:**
  1. Shopper selects star rating (1–5) and inputs text review.
  2. Shopper clicks "Submit".
  3. System saves review and links it to traveler's profile page.
  4. System recalculates traveler's aggregate rating.
* **Postconditions:** Review is saved and visible on traveler profile.

### UC-012: Monitor Transactions & Trips
* **Use Case ID:** UC-012
* **Use Case Name:** Monitor Transactions & Trips
* **Primary Actor:** Admin
* **Goal:** Supervise platform health and resolve issues.
* **Preconditions:** Admin is authenticated.
* **Trigger:** Admin accesses admin dashboard backend.
* **Main Flow:**
  1. Admin views overview statistics (Total active trips, active requests, escrow totals).
  2. Admin searches and views specific trip/order files.
* **Postconditions:** Admin is aware of operational statistics.

### UC-013: Auto-Expire Quote & Release Capacity
* **Use Case ID:** UC-013
* **Use Case Name:** Auto-Expire Quote & Release Capacity
* **Primary Actor:** System
* **Goal:** Release capacity reserved by non-responsive shoppers or failed checkouts.
* **Preconditions:** Order status is "Quoted" or "Payment Pending".
* **Trigger:** System cron worker detects quotation created > 24 hours ago without payment OR gateway webhook reports failed/expired payment.
* **Main Flow:**
  1. Cron or Webhook identifies expired/failed quotation.
  2. System cancels quote, setting order status to "Expired".
  3. System triggers capacity release: deducts estimated weight from "reserved capacity" and adds it back to "available capacity".
  4. System triggers *UC-014: Send Notification* to both parties.
* **Postconditions:** Status is "Expired"; capacity is released.

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
  3. System dispatches notification (email, push, or in-app).
* **Postconditions:** Notification is sent.

### UC-016: Procure & Purchase Item
* **Use Case ID:** UC-016
* **Use Case Name:** Procure & Purchase Item
* **Primary Actor:** Traveler
* **Goal:** Procure requested items and verify the purchase to build trust.
* **Preconditions:** Order status is "Paid".
* **Trigger:** Traveler travels/begins procurement OR traveler successfully buys the item.
* **Main Flow:**
  1. Traveler begins procurement process. Status changes to "Purchasing".
  2. Traveler successfully purchases the item.
  3. Traveler navigates to dashboard and clicks "Mark as Purchased", with the option to upload a receipt image or product photo.
  4. Status changes to "Purchased".
* **Postconditions:** Status is "Purchased".

### UC-015: Complete Trip
* **Use Case ID:** UC-015
* **Use Case Name:** Complete Trip
* **Primary Actor:** Traveler
* **Goal:** Close the trip lifecycle to calculate performance/revenues.
* **Preconditions:** All active orders for the trip have reached final states ("Completed", "Expired", or "Cancelled").
* **Trigger:** Traveler clicks "Mark Trip Completed" on their trip dashboard.
* **Main Flow:**
  1. Traveler requests trip completion.
  2. System verifies all active requests/orders for this trip are in final states.
  3. System updates Trip status to "Completed".
  4. System archives the trip from the active planner list.
* **Postconditions:** Trip status is "Completed".

---

# 4. Traceability Matrix

The table below maps the **Product Vision** strategic objectives to the **MVP Features**, the corresponding **Use Cases**, and the **User Stories** (epics and IDs):

| Product Vision Objective | MVP Feature | Use Case | User Story ID |
| :--- | :--- | :--- | :--- |
| **P2P Trust & Social Commerce** | 2. Traveler Profile | **UC-003**: View Traveler Profile & Trip Page | `US-002-003` |
| **Request-Driven Commerce** | 3. Product Request Form | **UC-004**: Submit Product Request | `US-003-001` |
| **Request-Driven Commerce** | 4. Quotation Engine | **UC-005**: Create & Send Quotation | `US-004-001` |
| **Travel Suitcase Capacity Management** | 5. Capacity Management | **UC-006**: Manage Baggage Capacity | `US-002-002` |
| **Overbooking Prevention** | 6. Quote Expiry & Capacity Release | **UC-013**: Auto-Expire Quote & Release Capacity | `US-004-002` |
| **Fraud Risk Elimination (Escrow)** | 7. Escrow Payment Integration | **UC-007**: Pay via Escrow | `US-006-001` |
| **Peer-to-Peer Transparency** | 8. Order Tracking | **UC-008**: Track Order Status | `US-005-001` |
| **Peer-to-Peer Transparency** | 8. Order Tracking (Purchase) | **UC-016**: Procure & Purchase Item | `US-005-005` |
| **Invisible Trust Infrastructure** | 8. Order Tracking (Payout) | **UC-010**: Confirm Delivery | `US-005-002` |
| **Verification & Trust Loop (P2P)** | 9. Reviews & Ratings | **UC-011**: Submit Review & Rating | `US-005-003` |
| **Operational & Admin Controls** | 10. Admin Dashboard | **UC-012**: Monitor Transactions & Trips | `US-005-004` |
| **Transactional Updates** | 11. Notifications | **UC-014**: Send Notification | `US-004-003` |
| **Supply Creation (Suitcase Inventory)** | 1. Trip Publisher | **UC-002**: Publish Trip | `US-002-001` |
| **Onboarding & Access** | Authentication | **UC-001**: Register & Login | `US-001-001`, `US-001-002` |
