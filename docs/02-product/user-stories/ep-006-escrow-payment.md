---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/planning/core-user-flow.md
---

# Epic 006: Escrow Integration

> **Status**: 📝 Draft
> **Sprint**: TBD

---

## US-006-001: Fund Escrow Payment

**As a** Shopper,
**I want to** fund a traveler's quote by paying via Virtual Account or E-Wallet,
**So that** my money is securely held by the platform until the traveler delivers the item.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Successful payment funds escrow
  Given I am logged in as a Shopper
  And I have a quote from Budi for "Tokyo Banana Classic" (IDR 350,000) in status "Payment Pending"
  When I click "Pay Now"
  And I select "GoPay" or "Mandiri Virtual Account" as the payment method
  And I complete the transaction on the payment gateway screen
  Then the platform should receive a successful payment webhook from Xendit/Midtrans
  And the system should lock IDR 350,000 in the platform's Escrow account
  And the order status should change to "Paid"
  And Budi (Traveler) should receive a confirmation notification to purchase the item

Scenario: Failed or expired payment transitions to Expired
  Given I am logged in as a Shopper
  And I have a quote from Budi for "Tokyo Banana Classic" (IDR 350,000) in status "Payment Pending"
  When the payment gateway session fails or expires
  Then the platform should receive a failed/expired webhook from Xendit/Midtrans
  And the order status should change to "Expired"
  And the system should release the reserved baggage capacity of Budi's trip
```

---

> **Total Story Points**: 5
> **Related Use Cases**: [UC-007](use-cases/use-case-specifications.md#uc-007-pay-via-escrow)
