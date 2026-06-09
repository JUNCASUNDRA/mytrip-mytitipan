---
agent: UX Designer Agent (UXA)
version: 1.0.0
date: 2026-06-09
status: Draft
predecessor: docs/03-design/user-flow/README.md
---

# Traveler Flow

This document details the step-by-step user flow, navigation paths, and user experience considerations for the **Traveler** actor in the My Trip My Titipan MVP.

---

## 1. Step-by-Step Flow

The Traveler flow focuses on creating capacity (trip setup) and fulfilling incoming product requests:

*   **Login**: The traveler logs in via OTP or Google on a mobile-first interface.
*   **Create Trip**: The traveler enters travel parameters: Route (Departure/Arrival airport), Travel Dates (Departure/Arrival), and Baggage Capacity limit (in kg).
*   **Share Link**: The traveler copies the generated unique URL (e.g., `mytrip.com/t/budi-tokyo-24`) and shares it on social media/WhatsApp.
*   **Review Request**: The traveler is notified when a shopper submits a request, reviewing item photos, external URLs, details, quantity, and budget.
*   **Send Quote**: The traveler enters the local purchase price of the item and their desired service fee (Jastip Fee).
*   **Capacity Reservation**: Sending the quote triggers a temporary 24-hour baggage capacity reservation based on the item's estimated weight.
*   **Track Orders**: The traveler views current requests and active orders in the dashboard sorted by state.
*   **Mark Purchased**: The traveler physically purchases the item abroad and updates the status to "Purchased" in the dashboard.
*   **Ship Item**: Once back in Indonesia, the traveler ships the item manually via a domestic courier and inputs the tracking AWB number in the dashboard.
*   **Receive Payout**: The escrow funds are automatically released to the traveler's balance after shopper delivery confirmation (or via the 7-day auto-release timer).
*   **Complete Trip**: Once all orders are completed, the traveler archives the trip.

---

## 2. Traveler Flow Diagram

```mermaid
flowchart TD
    T1([Start]) --> T2[Login via OTP/Google]
    T2 --> T3[Create Trip: Route, Dates, Baggage Capacity]
    T3 --> T4[Generate & Copy Unique Trip Link]
    T4 --> T5[Share Link on Instagram/TikTok/WhatsApp]
    T5 --> T6{Wait for Request}
    
    T6 -->|New Request Notification| T7[Review Request Details & Product Photos]
    T7 --> T8{Accept & Quote?}
    
    T8 -->|No| T9[Decline Request]
    T9 --> T6
    
    T8 -->|Yes| T10[Input Item Price & Jastip Fee]
    T10 --> T11[Send Quote & Start 24h Capacity Reservation]
    
    T11 --> T12{Shopper Pays in 24h?}
    T12 -->|No / Timeout| T13[Quote Expires & Capacity Automatically Released]
    T13 --> T6
    
    T12 -->|Yes| T14[Receive Escrow Secured Confirmation]
    T14 --> T15[Purchase Item Abroad]
    T15 --> T16[Mark as Purchased in Dashboard]
    T16 --> T17[Return to ID & Ship via Local Courier]
    T17 --> T18[Input Tracking Number in Dashboard]
    
    T18 --> T19{Shopper Confirms Delivery?}
    T19 -->|Yes / 7-Day Auto-Release| T20[Escrow Funds Released to Wallet]
    T19 -->|Disputed| T21[Wait for Admin Dispute Resolution]
    
    T21 --> T20
    T20 --> T22{All Orders Fulfilled?}
    T22 -->|No| T6
    T22 -->|Yes| T23[Mark Trip as Completed]
    T23 --> T24([End])
```

---

## 3. Traveler-Specific UX Notes

### Mitigation of Traveler Capital Risk Anxiety
> [!IMPORTANT]
> **Out-of-Pocket Purchasing**: Travelers must purchase the items using their own funds first, which can cause anxiety.
> *   **UX Solution**: When displaying "Paid" orders in the Traveler Dashboard, include a prominent green lock badge next to the status stating: *"Escrow Secured: Shopper funds are locked by the platform. You are guaranteed payout upon domestic shipment and receipt."*

### Error States
*   **Invalid Tracking Number**: When a traveler enters shipping details, validate the tracking number format against courier APIs. If invalid, highlight the input field in red with: *"Please enter a valid tracking number."*

### Empty States
*   **Empty Trips Dashboard**: When a traveler has no trips, show a suitcase illustration and a prompt: *"Planning a journey? Publish your trip and share the link to start receiving product requests."* with a primary CTA button: *"Create Trip"*.
*   **Empty Requests Dashboard**: When a traveler has a trip but no requests yet, show a status card: *"No requests yet. Copy your trip link and share it on Instagram or WhatsApp to attract shoppers!"* with a CTA button: *"Copy Trip Link"*.
