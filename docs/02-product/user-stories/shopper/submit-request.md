---
agent: Product Manager Agent (PMA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/02-product/user-stories/ep-003-product-request.md
outputs:
  - shopper-request-stories
depends_on:
  - state-machine.md
---

# Shopper User Stories - Product Request & Onboarding

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This document captures the user stories related to shopper account registration, login, profile onboarding, and product request submission.

---

## US-001-001: Shopper Registration & Authentication

**As a** new Shopper,
**I want to** register with email or social login,
**So that** I can create an account and submit product requests.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 5 |

### Acceptance Criteria

```gherkin
Scenario: Successful registration with email
  Given I am on the registration page
  When I enter a valid email and password
  And I click "Register"
  Then my account should be created
  And I should receive a verification email
  And I should be redirected to the onboarding flow

Scenario: Registration with existing email
  Given I am on the registration page
  When I enter an email that is already registered
  And I click "Register"
  Then I should see an error "Email already registered"
  And I should see a link to the login page

Scenario: Social login registration
  Given I am on the registration page
  When I click "Continue with Google"
  And I authorize the application
  Then my account should be created with Google profile data
  And I should be redirected to the onboarding flow
```

---

## US-001-002: Shopper Login

**As a** registered Shopper,
**I want to** login with my credentials,
**So that** I can access my active requests.

| Attribute | Value |
|-----------|-------|
| Priority | Must Have |
| Story Points | 3 |

### Acceptance Criteria

```gherkin
Scenario: Successful login
  Given I am on the login page
  When I enter valid email and password
  And I click "Login"
  Then I should be authenticated
  And I should be redirected to my shopper dashboard
```

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
  And the Traveler (Budi) should receive an email notification for a new request
  And I should see the request in my "My Requests" dashboard

Scenario: Attempt product request without logging in
  Given I am on Budi's Tokyo Trip page
  And I am not logged in to the platform
  When I fill out the request details and click "Submit Request"
  Then the system should redirect me to the Login/Registration page
  And after successful authentication, my draft request should be automatically submitted
```
