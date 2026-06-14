---
agent: UX Designer Agent (UXA)
version: 1.1.0
date: 2026-06-14
status: Draft
predecessor: docs/03-design/wireframes/README.md
outputs:
  - scr-008-spec
depends_on:
  - user-stories/traveler/create-trip.md
---

# SCR-008: Trip Share Modal

> **Status**: 📝 Draft **Last Updated**: 2026-06-14

This modal overlay displays the generated unique trip URL and handles copying and external social media distribution.

---

## 1. ASCII Wireframe Layout

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

## 2. UI Elements Specification

1. **Trip URL Display Box (`TXT-008-001`):**
   * Displays the read-only generated link string (e.g., `mytrip.com/t/budi-tokyo-2026`).
2. **Copy Trip Link Button (`BTN-008-001`):**
   * *Type:* Action button.
   * *Action:* Copies the URL text to clipboard. Replaces button text with a brief success confirmation (`Copied! ✔`) for 2 seconds.
3. **WhatsApp Share Handle (`BTN-008-002`):**
   * *Type:* Secondary button.
   * *Action:* Opens external WhatsApp web/app intent pre-filled with the shared link message: `Hi! I'm traveling to Tokyo soon. Request items you want me to bring back here: [URL]`.
4. **Instagram Share Action (`BTN-008-003`):**
   * *Type:* Secondary button.
   * *Action:* Copies URL and prompts instructions to paste in Instagram Bio/Story.
5. **Dashboard Transition Link (`BTN-008-004`):**
   * *Action:* Closes modal and redirects back to `SCR-006: Traveler Dashboard`.

---

## 3. UI State Variations

### A. Clipboard Disallowed state
* If the browser restricts automatic clipboard writing, displays message: `Please select and copy the link manually.`

---

## 4. Traceability

* **User Story:** [US-002-001](../user-stories/traveler/create-trip.md#us-002-001-publish-trip)
* **Requirement:** [Unique Link Generation specs](../../02-product/requirements/feature-requirements.md#1-trip-publisher)
