---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/04-wireframes/README.md
outputs:
  - scr-001-spec
depends_on:
  - docs/02-product/user-stories/shopper/submit-request.md
---

# SCR-001: Login / Register

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This screen provides the authentication gateway for all users (Shoppers, Travelers, and Admins). It supports both Google OAuth and Email-OTP validation.

---

## 1. ASCII Wireframe Layout

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

## 2. UI Elements Specification

1. **Back Button (`BTN-001-001`):**
   * *Type:* Text button with arrow icon (`<-`).
   * *Action:* Redirects to the previously visited public page (e.g., `SCR-002: Trip Landing Page`).
2. **Continue with Google Button (`BTN-001-002`):**
   * *Type:* Secondary icon button.
   * *Action:* Redirects to Google consent page via OAuth 2.0.
3. **Email Input Field (`FLD-001-001`):**
   * *Type:* Text input.
   * *Validation:* Must follow standard email format (regex: `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$`).
4. **Send OTP Code Button (`BTN-001-003`):**
   * *Type:* Primary action button.
   * *Validation:* Disabled until a valid email format is entered in `FLD-001-001`.
   * *Action:* Sends OTP via backend API, reveals OTP input and validation button, starts a 60-second resend countdown.
5. **OTP Input Field (`FLD-001-002`):**
   * *Type:* Numeric input (6 digits).
   * *Validation:* Accepts exactly 6 numbers.
6. **Verify and Login Button (`BTN-001-004`):**
   * *Type:* Primary action button.
   * *Action:* Submits OTP for validation. Redirects to previous redirect route or user dashboard on success.

---

## 3. UI State Variations

### A. Loading / OTP Sending State
* Email field and Send OTP button are disabled.
* Spinners are displayed inside `BTN-001-003`.

### B. Error State
* If OTP is invalid: Show red text `Invalid OTP code. Please try again.` below `FLD-001-002` and highlight the field border in red.
* If Email is blocked: Show error `This account has been suspended.` at the top banner.

---

## 4. Traceability

* **User Story:** [US-001-001](../../../../02-product/user-stories/shopper/submit-request.md#us-001-001-shopper-registration--authentication), [US-001-002](../../../../02-product/user-stories/shopper/submit-request.md#us-001-002-shopper-login)
* **Requirement:** [User Onboarding](../../../02-product/requirements/product-requirements.md#2-user-role-rules--constraints)
