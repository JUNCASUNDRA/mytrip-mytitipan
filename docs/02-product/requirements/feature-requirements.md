---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/requirements/product-requirements.md
outputs:
  - functional-specifications
  - input-validations
depends_on:
  - feature-prioritization.md
---

# Functional Feature Requirements Specification

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document details the functional specifications and business rules for the Must Have and Should Have features of the **My Trip My Titipan** MVP.

---

## 1. Trip Publisher

### Functional Requirements
* **Input Fields:**
  * Destination Country & City (Free text or autocomplete dropdown).
  * Departure Date (Date selector, must be > current date).
  * Return Date (Date selector, must be >= departure date).
  * Luggage Capacity Limit (Numeric input in kg, 1 decimal place).
* **System Action:**
  * Generates a unique, non-guessable slug (e.g., `/t/budi-tokyo-2026`).
  * Generates a public trip landing page accessible via the slug without authentication.
* **Validations:**
  * Departure/Return dates cannot be in the past.
  * Luggage capacity must be between 1.0 kg and 30.0 kg.

---

## 2. Product Request Form

### Functional Requirements
* **Input Fields:**
  * Item Name (Text, max 100 characters).
  * Product Reference URL (Optional, URL format).
  * Product Image (Optional, image file upload, max 5MB).
  * Quantity (Integer, minimum 1).
  * Willingness to Pay (Numeric, budget in IDR).
* **System Action:**
  * Links the request to the specific trip ID.
  * Sets initial state to `REQUESTED`.
  * Triggers notifications to the traveler.
* **Validations:**
  * Item Name and Willingness to Pay are required.
  * Budget must be a positive integer > 0.
  * Image uploads must be limited to standard web formats (JPEG, PNG, WebP).

---

## 3. Quotation Engine

### Functional Requirements
* **Input Fields:**
  * Item Price (Numeric, in IDR).
  * Jastip Fee (Numeric, in IDR).
  * Estimated Weight (Numeric, in kg).
* **System Action:**
  * Computes: $\text{Total Quote Price} = \text{Item Price} + \text{Jastip Fee}$.
  * Sets status to `QUOTED`.
  * reserves weight from trip available capacity.
  * Generates invoice link and sends notification to shopper.
* **Validations:**
  * Item Price and Jastip Fee must be positive integers.
  * Estimated Weight must not exceed the remaining available baggage capacity of the trip.

---

## 4. Baggage Capacity Management

### Functional Requirements
* **System Actions:**
  * **On Quote Sent:** Move estimated weight from `Available Capacity` to `Reserved Capacity`.
  * **On Payment Success:** Move estimated weight from `Reserved Capacity` to `Locked Capacity`.
  * **On Quote Expiry / Decline:** Move estimated weight from `Reserved Capacity` back to `Available Capacity`.
  * **On Admin Refund:** Move estimated weight from `Locked Capacity` back to `Available Capacity`.
  * **On Trip Completion:** Clear active capacities; archive trip suitcase allocation.

---

## 5. Quote Expiry & Capacity Release

### Functional Requirements
* **System Actions:**
  * A cron job or database event run every 5 minutes must check for orders in `QUOTED` or `PAYMENT_PENDING` status with `quote_created_at` timestamp older than 24 hours.
  * Automatically transitions matching records to `EXPIRED`.
  * Releases reserved weight.
  * Sends email notification to both shopper and traveler indicating that the quote has expired.

---

## 6. Escrow Payment Integration

### Functional Requirements
* **System Actions:**
  * Integrates with payment gateway API (e.g., Midtrans/Xendit) to generate Virtual Account numbers or E-Wallet QR codes.
  * Listens to payment status webhooks.
  * On payment success callback, sets order status to `PAID` and logs escrow ledger entry.
  * On payment failure/cancel callback, sets order status to `EXPIRED`.

---

## 7. Traveler Profiles

### Functional Requirements
* **Display Fields:**
  * Traveler Avatar, Name, and Biography.
  * Count of Completed Trips (derived from Completed trip records).
  * Count of Completed Orders (derived from Completed order records).
  * Aggregate Star Rating (1.0 to 5.0 scale, rounded to 1 decimal place).
  * List of text reviews with dates and shopper avatars.

---

## 8. Order Lifecycle Tracking Dashboard

### Functional Requirements
* **System Actions:**
  * Displays a progress tracking dashboard timeline showing the current state: `Requested` → `Quoted` → `Payment Pending` → `Paid` → `Purchasing` → `Purchased` → `In Transit` → `Delivered` → `Completed`.
  * If the status is `In Transit`, display Courier Name and domestic tracking code link.

---

## 9. Reviews & Ratings System

### Functional Requirements
* **Input Fields:**
  * Rating (1 to 5 stars selection).
  * Feedback Review Text (Optional, max 500 characters).
* **System Actions:**
  * Restricts submission to Shoppers whose order is in `DELIVERED` or `COMPLETED` status.
  * Upon submission, triggers recalculation of traveler aggregate ratings.

---

## 10. Admin Dashboard & Exception Handling

### Functional Requirements
* **Admin Controls:**
  * View active ledger (escrow holdings).
  * List active trips and order status logs.
  * Manual status override triggers:
    * `Refund Override`: Initiates gateway refund API call, updates status to `REFUNDED`, and releases capacity.
    * `Force Cancellation`: Updates status to `CANCELLED` and releases capacity.
