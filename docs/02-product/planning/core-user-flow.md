# Core User Flow (MVP)

> **Status**: 📝 Draft
> **Last Updated**: 2026-06-06

This document maps the exact click-path for the 5 core features defined in the MVP. It serves as the foundation for wireframes and engineering architecture.

## The End-to-End Transaction Flow

### Step 1: Supply Creation (Traveler)
1. **Login/Register:** Traveler logs in via OTP/Google.
2. **Publish Trip:** Traveler clicks "Create Trip" → Enters Route (e.g., CGK to HND), Dates, Capacity.
3. **Link Generation:** System provides a shareable URL.
4. **Distribution:** Traveler pastes URL in their Instagram Bio/Story.

### Step 2: Demand Capture (Shopper)
1. **Link Click:** Shopper clicks the URL from Instagram and lands on the Web App (Mobile-first view).
2. **Trip View:** Shopper views Budi's trip page and sees:
   - Traveler profile & completed trips count
   - Ratings & reviews history
   - Trip destination & timeline
   - Available baggage slots / Trip status (Open / Limited / Full)
3. **Submit Request:** Shopper clicks "Request Item" → Uploads photo, adds URL, sets maximum price.   
4. **Wait State:** Shopper is notified: "Request sent to Budi. Waiting for quotation."

### Step 3: Matching & Quotation (Traveler)
1. **Notification:** Traveler receives an in-app notification and email notification: "New Request for Tokyo Trip".
2. **Review:** Traveler logs in, views the item details.
3. **Quotation:** Traveler inputs: "Item Price: IDR 500,000 | Jastip Fee: IDR 100,000 | Total: IDR 600,000".
4. **Capacity Reservation:** Platform temporarily reserves traveler baggage capacity for 24 hours.
5. **Send:** Quote is sent to Shopper. If unpaid within 24 hours, the quote and reservation expire, and capacity is automatically released.

### Step 4: Transaction & Trust (Shopper)
1. **Review Quote:** Shopper logs in, views the IDR 600,000 total.
2. **Payment:** Shopper clicks "Pay Now" → Redirected to Payment Gateway (Xendit/Midtrans) to complete payment within 24 hours. Status changes to **"Payment Pending"** while processing.
3. **Escrow Lock:** Payment successful. Funds held in Escrow. Capacity lock is confirmed. Status changes to **"Paid"**.

### Step 5: Fulfillment & Payout (Traveler)
1. **Purchase:** Traveler buys the item in Tokyo. Clicks "Mark as Purchased" in dashboard. Status changes to **"Purchased"**.
2. **Return & Ship:** Traveler returns to Jakarta, manually ships the item via JNE/GoSend, and inputs the tracking number into the dashboard. Status changes to **"In Transit"**.
3. **Delivery:** Shopper receives item, clicks "Confirm Receipt", and leaves a text review and star rating. Status changes to **"Delivered"**.
4. **Payout:** Platform automatically releases Escrow funds to the Traveler's bank account (immediately upon Shopper's "Confirm Receipt" or automatically after 7 days if no action is taken). Status changes to **"Completed"**.

---

## MVP Order Status Lifecycle

This lifecycle defines all possible states during the transaction flow. It is split into two logical stages (Request and Fulfillment) to guide database design and backend state machine transitions:

### 1. Request Lifecycle (Before Payment)
* **Requested** → **Quoted** → **Payment Pending** → **Paid** (leads to fulfillment) or **Expired** / **Cancelled**.

### 2. Fulfillment Lifecycle (After Payment)
* **Paid** → **Purchased** → **In Transit** → **Delivered** → **Completed**

*(Note: Cancellation and refund scenarios after the "Paid" stage are treated as special operational exception flows. Once an item is marked "Purchased", a standard refund is no longer available unless under exceptional circumstances).*

| Status | Description | System Trigger |
| :--- | :--- | :--- |
| **Requested** | Shopper submitted request | Shopper clicks "Request Item" |
| **Quoted** | Traveler sent quotation | Traveler sends Quote (temporary capacity reservation starts) |
| **Payment Pending** | Waiting for escrow payment | Shopper starts checkout flow (24-hour window starts) |
| **Expired** | Quote expired (payment incomplete in 24 hours) | System timeout (capacity automatically released) |
| **Cancelled** | Transaction cancelled | Traveler cancels, shopper cancels before payment, or item out of stock (allowed pre-payment; post-payment cancellations are treated as exceptional cases) |
| **Paid** | Escrow funded | Shopper completes payment (capacity lock confirmed) |
| **Purchased** | Item purchased by traveler | Traveler marks as Purchased |
| **In Transit** | Shipped to shopper | Traveler ships and inputs tracking number |
| **Delivered** | Shopper received item | Shopper clicks "Confirm Receipt" |
| **Completed** | Escrow released | Funds payout to traveler (manual confirm or 7-day auto-release) |
