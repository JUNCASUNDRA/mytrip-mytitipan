---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/01-business/04-business-flow/customer-journey.md
---

# Core User Flow (MVP)

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document maps the exact click-path for the core features defined in the MVP. It serves as the foundation for wireframes and engineering architecture.

## The End-to-End Transaction Flow

### Step 1: Supply Creation (Traveler)

1. **Authentication:** Traveler authenticates on the platform.
2. **Publish Trip:** Traveler clicks "Create Trip".
3. **Trip Details:** Traveler defines:
   - Destination (e.g., CGK to HND)
   - Travel Dates
   - Available baggage capacity
4. **Link Generation:** System generates a public, shareable trip link.
5. **Distribution:** Traveler shares the public link externally (e.g., Instagram Bio/Story, WhatsApp).

### Step 2: Demand Capture (Shopper)

1. **Link Click:** Shopper clicks the shared URL and lands on the Traveler's Trip Landing Page (Mobile-first view).
2. **Trip Landing Page View:** Shopper views the page which acts as a trust layer, displaying:
   - Traveler identity
   - Reputation summary (completed trips, reviews, ratings)
   - Destination & timeline
   - Travel deadline
   - Remaining baggage capacity status (Open / Limited / Full)
   - Request CTA
3. **Submit Request:** Shopper clicks "Request Item" → Uploads photo, adds URL, sets maximum price/budget.
4. **Wait State:** Shopper is notified that the request has been submitted and is waiting for the traveler's review/quotation.

### Step 3: Matching & Quotation (Traveler)

1. **Notification:** System notifies the traveler of a new request.
2. **Review:** Traveler reviews the requested item details.
3. **Acceptance:** Traveler accepts the request.
4. **Quotation:** System creates a quotation, and traveler inputs: "Item Price: IDR 500,000 | Jastip Fee: IDR 100,000 | Total: IDR 600,000".
5. **Capacity Reservation:** System temporarily reserves estimated baggage capacity when traveler sends a quote. Reservation expires after 24 hours if payment is not completed.
6. **Notification to Shopper:** System notifies the shopper that a quote has been generated.

### Step 4: Transaction & Trust (Shopper)

1. **Review Quote:** Shopper views the quote total.
2. **Payment Checkout:** Shopper clicks "Pay Now" → Redirected to Payment Gateway (Xendit/Midtrans) where payment gateway transaction status is `Created`/`Pending`. Order status in the platform changes to **"Payment Pending"** while processing.
3. **Payment Completion:**
   - **Success Pathway:** Shopper completes payment successfully. Payment Gateway status becomes `Success`. Order status changes to **"Paid"** and escrow funds are locked.
   - **Failed/Expired Pathway:** Payment fails or the 24-hour window expires. Payment Gateway status becomes `Failed` or `Expired`. Order status transitions to **"Expired"** and the reserved capacity is automatically released.

### Step 5: Fulfillment & Payout (Traveler)

1. **Procurement/Travel:** Traveler begins procurement or travel. Order status changes to **"Purchasing"**.
2. **Purchase:** Traveler buys the item. Clicks "Mark as Purchased" in the dashboard and optionally uploads a photo of the receipt or item to establish trust. Status changes to **"Purchased"**.
3. **Return & Ship:** Traveler returns, manually ships the item domestically via courier, and inputs the tracking number. Status changes to **"In Transit"**.
4. **Delivery:** Shopper receives the item and clicks "Confirm Receipt". Status changes to **"Delivered"**.
5. **Payout:** System releases escrow funds to the traveler's bank account (immediately on shopper confirmation or auto-completion after 7 days). Status changes to **"Completed"**.

---

## MVP Order Status Lifecycle

This lifecycle defines all possible states during the transaction flow, split into two logical stages to guide database design and backend state machine transitions:

### 1. Request Lifecycle (Before Payment)

- **Requested** → **Quoted** → **Payment Pending** → **Paid** (leads to fulfillment) or **Expired** / **Cancelled**.

### 2. Fulfillment Lifecycle (After Payment)

- **Paid** → **Purchasing** → **Purchased** → **In Transit** → **Delivered** → **Completed**

*(Note: Pre-payment cancellations transition to "Cancelled". Post-payment exception flows or refunds transition to "Refunded" or "Cancelled" via administrative override).*

| Status | Stage | Description | System Trigger |
| --- | --- | --- | --- |
| **Requested** | Request | Shopper submitted request | Shopper clicks "Request Item" |
| **Quoted** | Request | Traveler sent quotation | Traveler accepts request and sends Quote |
| **Payment Pending** | Request | Waiting for escrow payment | Shopper starts checkout flow (payment gateway transaction Created/Pending) |
| **Expired** | Request | Quote expired or payment failed/expired | 24-hour timer expires OR gateway sends Failed/Expired status callback (capacity released) |
| **Cancelled** | Both | Request declined or manual cancel | Traveler declines request (pre-quote) OR Admin overrides cancellation |
| **Paid** | Fulfillment | Escrow funded successfully | Shopper completes payment (capacity lock confirmed, payment gateway Success callback) |
| **Purchasing** | Fulfillment | Traveler is procurement processing | Traveler begins travel/shopping |
| **Purchased** | Fulfillment | Item purchased by traveler | Traveler marks as Purchased (optional receipt upload) |
| **In Transit** | Fulfillment | Shipped to shopper | Traveler ships and inputs tracking number |
| **Delivered** | Fulfillment | Shopper received item | Shopper clicks "Confirm Receipt" |
| **Completed** | Fulfillment | Escrow released | Funds payout to traveler (manual confirm or 7-day auto-release) |
| **Refunded** | Exception | Payment returned to shopper | Admin triggers escrow refund after cancellation/dispute resolution |
