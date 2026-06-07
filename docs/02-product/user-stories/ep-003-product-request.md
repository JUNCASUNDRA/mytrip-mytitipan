# Epic 003: Product Request Form

> **Status**: 📝 Draft
> **Sprint**: TBD

---

## US-003-001: Submit Product Request

**As a** Shopper,
**I want to** fill out a structured product request form on a traveler's trip page,
**So that** I can communicate my demand details clearly without unstructured messaging.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Successful product request submission
  Given I am on Budi's Tokyo Trip page
  And I am logged in as a Shopper
  When I click "Request Item"
  And I fill out the form:
    | Field | Value |
    | Item Name | Tokyo Banana Classic (Box of 8) |
    | Reference URL | https://tokyobanana.jp/classic |
    | Photo Upload | tokyo_banana.jpg |
    | Quantity | 2 |
    | Willingness to Pay | IDR 350,000 |
  And I click "Submit Request"
  Then the request should be saved with status "Requested"
  And the Traveler (Budi) should receive an in-app and email notification for a new request
  And I should see the request in my "My Requests" dashboard

Scenario: Attempt product request without logging in
  Given I am on Budi's Tokyo Trip page
  And I am not logged in to the platform
  When I fill out the request details and click "Submit Request"
  Then the system should redirect me to the Login/Registration page (OTP / Google Login)
  And after successful authentication, my draft request should be automatically submitted
```

---

> **Total Story Points**: 5
> **Related Use Cases**: [UC-004](use-cases/use-case-specifications.md#uc-004-submit-product-request)
