# Low-Fidelity Wireframes Spec (SCR-001 - SCR-013)

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document defines the low-fidelity text wireframes and layout structures for all 13 screens in the **My Trip My Titipan** MVP screen inventory. Every layout is optimized for mobile-first views, with the exception of the Admin screens (`SCR-012` and `SCR-013`), which are designed for desktop-first layouts.

---

## Screen Directory

1. [SCR-001: Login / Register](#scr-001-login--register)
2. [SCR-002: Trip Landing Page](#scr-002-trip-landing-page)
3. [SCR-003: Product Request Form](#scr-003-product-request-form)
4. [SCR-004: Shopper Dashboard](#scr-004-shopper-dashboard)
5. [SCR-005: Quote & Checkout Page](#scr-005-quote--checkout-page)
6. [SCR-006: Traveler Dashboard](#scr-006-traveler-dashboard)
7. [SCR-007: Create Trip Form](#scr-007-create-trip-form)
8. [SCR-008: Trip Share Modal](#scr-008-trip-share-modal)
9. [SCR-009: Request Review Screen](#scr-009-request-review-screen)
10. [SCR-010: Traveler Order Details](#scr-010-traveler-order-details)
11. [SCR-011: Review Submission](#scr-011-review-submission)
12. [SCR-012: Admin Dashboard](#scr-012-admin-dashboard)
13. [SCR-013: Admin Dispute Manager](#scr-013-admin-dispute-manager)

---

### SCR-001: Login / Register
* **Actor Access:** All Users
* **Objective:** Authenticate user session using email OTP or Google OAuth.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]                    My Trip My Titipan   |
|                                                |
|                   [Logo]                       |
|           Welcome to MyTrip-MyTitipan          |
|                                                |
|  [ Button: Continue with Google              ] |
|                                                |
|  ----------- Or Login with Email -----------   |
|                                                |
|  Email Address                                 |
|  [ input: enter your email                   ] |
|                                                |
|  [ Button: Send OTP Code                     ] |
|                                                |
|  [ input: enter 6-digit OTP                  ] (Hidden initially)
|  [ Button: Verify and Login                  ] (Hidden initially)
|                                                |
|  By logging in, you agree to our Terms of Svc. |
--------------------------------------------------
```

---

### SCR-002: Trip Landing Page
* **Actor Access:** Shopper (Publicly accessible)
* **Objective:** Display traveler route, dates, suitcase availability, and reputation count.
* **Layout Structure:**
```text
--------------------------------------------------
| [Profile Avatar]  Budi Santoso                 |
|                   Completed Trips: 8           |
|                   Completed Orders: 24         |
|                   Rating: ⭐ 4.8 (12 Reviews)   |
|                                                |
|  ----------- Active Trip Details -----------   |
|  Route: Tokyo (HND) -> Jakarta (CGK)           |
|  Departure: 20 Jun 2026                        |
|  Return: 28 Jun 2026                           |
|                                                |
|  Baggage Availability:                         |
|  [||||||||||||||||-------] 12.5 kg / 20.0 kg    |
|  Status: Open for Requests                     |
|                                                |
|  ---------------- Reviews -----------------   |
|  - "Fast response and safe!" - Andi (⭐ 5)    |
|  - "Item arrived intact." - Maria (⭐ 4)      |
|                                                |
|  [ Button: Request Item from Tokyo           ] |
--------------------------------------------------
```

---

### SCR-003: Product Request Form
* **Actor Access:** Authenticated Shopper
* **Objective:** Submit a structured product request form linked to a specific traveler's trip.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]            Request New Item             |
|                                                |
|  Item Details                                  |
|  Item Name *                                   |
|  [ input: Tokyo Banana Classic 8-pack        ] |
|                                                |
|  Reference URL (Optional)                      |
|  [ input: https://tokyobanana.jp/classic     ] |
|                                                |
|  Quantity *                                    |
|  [ - ]  2  [ + ]                               |
|                                                |
|  Willingness to Pay (Budget in IDR) *          |
|  IDR [ input: 350,000                        ] |
|                                                |
|  Product Photo *                               |
|  +------------------------------------------+  |
|  | [Icon: Camera] Upload Photo (Max 5MB)    |  |
|  +------------------------------------------+  |
|                                                |
|  [ Button: Submit Request                    ] |
--------------------------------------------------
```

---

### SCR-004: Shopper Dashboard
* **Actor Access:** Authenticated Shopper
* **Objective:** Manage product requests, fund quotes, and track order fulfillment.
* **Layout Structure:**
```text
--------------------------------------------------
| [User Avatar]  Shopper Area    [Logout]         |
|                                                |
|  [ Tab: Active Orders (3) | History (8) ]       |
|                                                |
|  --------------------------------------------  |
|  Tokyo Banana Classic (Qty: 2)                 |
|  Traveler: Budi Santoso                        |
|  Status: QUOTED                                |
|  [ Button: Review Quote & Pay ]  (Expires 14h) |
|  --------------------------------------------  |
|  Seoul Skincare Essence                        |
|  Traveler: Maria                               |
|  Status: IN TRANSIT                            |
|  Courier: JNE | AWB: CGK8810293                |
|  [ Button: Confirm Receipt ] [Raise Dispute]   |
|  --------------------------------------------  |
|  Matcha Green Tea                              |
|  Traveler: Andi                                |
|  Status: DELIVERED                             |
|  [ Button: Leave Review ]                      |
--------------------------------------------------
```

---

### SCR-005: Quote & Checkout Page
* **Actor Access:** Authenticated Shopper
* **Objective:** Review pricing breakdown from traveler and fund the escrow.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]            Quotation & Payment          |
|                                                |
|  Quote for: Tokyo Banana Classic (Qty: 2)       |
|  Traveler: Budi Santoso                        |
|  Weight Estimate: 1.0 kg                       |
|                                                |
|  ----------- Quote Breakdown -----------       |
|  Item Price:         IDR  250,000              |
|  Jastip Service Fee: IDR  100,000              |
|  ---------------------------------------       |
|  Total Quote Cost:   IDR  350,000              |
|                                                |
|  [!] Funds will be held securely in escrow.    |
|  Quote expires in: 14h 23m                     |
|                                                |
|  Select Payment Method:                        |
|  ( ) Mandiri Virtual Account                   |
|  ( ) GoPay / QRIS                              |
|                                                |
|  [ Button: Pay IDR 350,000                   ] |
|  [ Link: Decline & Cancel Request ]            |
--------------------------------------------------
```

---

### SCR-006: Traveler Dashboard
* **Actor Access:** Authenticated Traveler
* **Objective:** View active trips, baggage limits, wallet status, and pending request actions.
* **Layout Structure:**
```text
--------------------------------------------------
| [User Avatar]  Traveler Dashboard   [Logout]   |
|  Wallet Payout Balance: IDR 1,200,000          |
|                                                |
|  ----------- Active Trips -----------          |
|  Tokyo -> Jakarta (20 - 28 Jun 2026)           |
|  Capacity: [|||||||||------] 12.5kg/20kg       |
|  [ Button: Create / Publish New Trip ]         |
|                                                |
|  ----------- Incoming Requests -----------     |
|  - Tokyo Banana (Maria)   - Willing: IDR 350k  |
|    [ Button: Review Request & Quote ]          |
|                                                |
|  ----------- Active Orders (Fulfillment) ----- |
|  - Seoul Cosmetics (Andi) - Status: PAID       |
|    [ Button: Open Order Details ]              |
--------------------------------------------------
```

---

### SCR-007: Create Trip Form
* **Actor Access:** Authenticated Traveler
* **Objective:** Input itinerary dates, destination routes, and baggage weight thresholds.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]            Publish New Trip             |
|                                                |
|  Destination Route                             |
|  Departure Airport                             |
|  [ input: Jakarta (CGK)                      ] |
|  Arrival Airport                               |
|  [ input: Tokyo (HND)                        ] |
|                                                |
|  Travel Schedule                               |
|  Departure Date                                |
|  [ date picker: 2026-06-20                   ] |
|  Return Date                                   |
|  [ date picker: 2026-06-28                   ] |
|                                                |
|  Baggage Capacity Limit                        |
|  [ input: 20.0                               ] kg
|  (Max platform weight: 30.0 kg)                |
|                                                |
|  [ Button: Publish Trip & Generate Link      ] |
--------------------------------------------------
```

---

### SCR-008: Trip Share Modal
* **Actor Access:** Authenticated Traveler
* **Objective:** Display the generated trip URL and quick share handles.
* **Layout Structure:**
```text
--------------------------------------------------
|               Trip Published!                  |
|                                                |
|  Your trip link is active. Share it to receive  |
|  product requests:                             |
|                                                |
|  +------------------------------------------+  |
|  | mytrip.com/t/budi-tokyo-2026             |  |
|  +------------------------------------------+  |
|                                                |
|  [ Button: Copy Trip Link ]                    |
|                                                |
|  [ Button: Share to WhatsApp Story ]           |
|  [ Button: Share to Instagram Bio ]            |
|                                                |
|  [ Link: Go to Traveler Dashboard ]            |
--------------------------------------------------
```

---

### SCR-009: Request Review Screen
* **Actor Access:** Authenticated Traveler
* **Objective:** Propose quote terms or decline shopper item requests.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]            Review Product Request       |
|                                                |
|  From Shopper: Maria                           |
|  Item: Tokyo Banana Classic 8-pack             |
|  Quantity: 2                                   |
|  Shopper Willing-to-Pay: IDR 350,000           |
|                                                |
|  Reference Image:                              |
|  +------------------------------------------+  |
|  |               [ Image ]                  |  |
|  +------------------------------------------+  |
|                                                |
|  ----------- Propose Quotation -----------     |
|  Item Purchase Price (in IDR)                  |
|  IDR [ input: 250,000                        ] |
|  Jastip Service Fee (in IDR)                   |
|  IDR [ input: 100,000                        ] |
|                                                |
|  Estimated Suitcase Weight                     |
|  [ input: 1.0 ] kg                             |
|                                                |
|  [ Button: Send Quote (Expires in 24h)       ] |
|  [ Button: Decline & Cancel Request ]          |
--------------------------------------------------
```

---

### SCR-010: Traveler Order Details
* **Actor Access:** Authenticated Traveler
* **Objective:** Sourcing updates and courier tracking number submissions.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]            Order Fulfillment Details    |
|                                                |
|  Order ID: #ORD-9902                           |
|  Shopper: Maria   | Contact: email@mail.com    |
|  Item: Tokyo Banana Classic (Qty: 2)           |
|                                                |
|  Status: PAID (Escrow Secured 🔒)               |
|                                                |
|  ----------- Procurement Status -----------    |
|  [ Button: Start Purchasing ] (Moves to PURCHASING)
|                                                |
|  [ Button: Mark as Purchased ] (Moves to PURCHASED)
|  Optional: Upload photo of receipt/item        |
|                                                |
|  ----------- Shipping & Dispatch -----------   |
|  Courier Service                               |
|  [ dropdown: JNE / J&T / Sicepat             ] |
|  Courier Tracking AWB                          |
|  [ input: Enter AWB tracking number          ] |
|  [ Button: Submit Tracking & Ship ]            |
|                                                |
|  [ Link: Mark as Out of Stock ] (Dispute/Refund)
--------------------------------------------------
```

---

### SCR-011: Review Submission
* **Actor Access:** Authenticated Shopper
* **Objective:** Rate traveler performance after receiving items.
* **Layout Structure:**
```text
--------------------------------------------------
| [Back]            Submit Traveler Review       |
|                                                |
|  Order ID: #ORD-9902                           |
|  Traveler: Budi Santoso                        |
|                                                |
|  How was your experience?                      |
|  Rating: ⭐ ⭐ ⭐ ⭐ ⭐                         |
|  (Click stars to rate traveler)                |
|                                                |
|  Write a Review:                               |
|  +------------------------------------------+  |
|  | textarea: Fast response, item arrived     |  |
|  | safely in perfect condition.              |  |
|  +------------------------------------------+  |
|                                                |
|  [ Button: Submit Review & Rating            ] |
--------------------------------------------------
```

---

### SCR-012: Admin Dashboard
* **Actor Access:** Authenticated Administrator (Desktop layout)
* **Objective:** Monitor system overview, active trips, and transaction volume list.
* **Layout Structure:**
```text
-------------------------------------------------------------------------------------
| ADMIN PANEL |  Active Trips: 342  | Active Escrow Ledger: IDR 45,200,000  [Logout] |
-------------------------------------------------------------------------------------
| Search Orders / Users                                                             |
| [ input: search by Order ID, Shopper Name, or AWB...                 ] [Search]   |
|                                                                                   |
| ----------- System Transactions Log -----------                                   |
| Order ID | Shopper    | Traveler | Price       | Status      | Actions            |
| ORD-1002 | Maria      | Budi     | IDR 350,000 | PAID        | [View Details]     |
| ORD-1003 | Andi       | Maria    | IDR 620,000 | DISPUTED    | [Audit Dispute]    |
| ORD-1004 | Jenny      | Budi     | IDR 120,000 | EXPIRED     | [View Log]         |
| ORD-1005 | Clara      | Andi     | IDR 450,000 | COMPLETED   | [View Log]         |
-------------------------------------------------------------------------------------
```

---

### SCR-013: Admin Dispute Manager
* **Actor Access:** Authenticated Administrator (Desktop layout)
* **Objective:** Auditing disputed courier tracking codes and executing overrides.
* **Layout Structure:**
```text
-------------------------------------------------------------------------------------
| [Back]                    Dispute Resolution Audit Manager                        |
-------------------------------------------------------------------------------------
|  Order Details                                                                    |
|  Order ID: ORD-1003  | Shopper: Andi  | Traveler: Maria                           |
|  Status: DISPUTED (Escrow Locked: IDR 620,000)                                    |
|  Dispute Reason: Andi claims item arrived damaged.                                |
|                                                                                   |
|  ----------- Photo Evidence & Receipt -----------                                  |
|  Shopper Evidence Photo: [ damaged_perfume.jpg ]                                  |
|  Traveler Sourcing Receipt: [ korea_dutyfree_receipt.png ]                        |
|                                                                                   |
|  ----------- Logistics & Courier Validation -----------                           |
|  Courier: JNE | AWB Code: JNE-99082302                                            |
|  Courier Webhook status: DELIVERED (Recipient: Security Guard)                    |
|                                                                                   |
|  ----------- Manual Escrow Overrides -----------                                  |
|  Reason / Justification for Override (Mandatory Log Entry):                       |
|  [ text input: Enter detailed rationale here for audit trail...               ]  |
|                                                                                   |
|  [ Button: Release Payout to Traveler ]      [ Button: Refund Escrow to Shopper ] |
-------------------------------------------------------------------------------------
```
