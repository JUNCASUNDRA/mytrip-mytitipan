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
2. **Trip View:** Shopper sees "Budi is going to Tokyo (Closes in 3 days)".
3. **Submit Request:** Shopper clicks "Request Item" → Uploads photo, adds URL, sets maximum price.   
4. **Wait State:** Shopper is notified: "Request sent to Budi. Waiting for quotation."

### Step 3: Match & Negotiation (Traveler)
1. **Notification:** Traveler receives an email/SMS: "New Request for Tokyo Trip".
2. **Review:** Traveler logs in, views the item details.
3. **Quotation:** Traveler inputs: "Item Price: IDR 500,000 | Jastip Fee: IDR 100,000 | Total: IDR 600,000".
4. **Send:** Quote sent back to Shopper.

### Step 4: Transaction & Trust (Shopper)
1. **Review Quote:** Shopper logs in, views the IDR 600,000 total.
2. **Payment:** Shopper clicks "Pay Now" → Redirected to Payment Gateway (Xendit/Midtrans).
3. **Escrow Lock:** Payment successful. Funds held in Escrow. Status changes to **"Paid"**.

### Step 5: Fulfillment & Payout (Traveler)
1. **Purchase:** Traveler buys the item in Tokyo. Clicks "Mark as Purchased" in dashboard. Status changes to **"Purchased"**.
2. **Return & Ship:** Traveler returns to Jakarta, manually ships the item via JNE/GoSend, and inputs the tracking number into the dashboard. Status changes to **"In Transit"**.
3. **Delivery:** Shopper receives item, clicks "Confirm Receipt", and leaves a text review and star rating.
4. **Payout:** Platform automatically triggers Escrow release to Traveler's bank account. Status changes to **"Delivered"**.
