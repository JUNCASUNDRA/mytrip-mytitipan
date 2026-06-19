`# Design System

> Komponen, design tokens, dan guidelines untuk konsistensi visual.

## 1. Design Tokens

### Colors (Proposed)

| Token | Value | Usage |
| --- | --- | --- |
| `--color-primary` | `#0066FF` | Trust Blue (Brand, Primary CTA) |
| `--color-primary-light` | `#E6F0FF` | Light Blue (Hover, Backgrounds) |
| `--color-primary-dark` | `#0044AA` | Deep Blue (Active states) |
| `--color-secondary` | `#FF8800` | Warning Orange (Secondary actions, Alerts) |
| `--color-success` | `#22C55E` | Safe Green (Payment Secured, Delivered) |
| `--color-warning` | `#F59E0B` | Warning Yellow |
| `--color-error` | `#EF4444` | Danger Red |
| `--color-neutral-50` | `#F9FAFB` | Main Background |
| `--color-neutral-900` | `#111827` | Primary Text |

### Typography

| Token | Value | Usage |
| --- | --- | --- |
| `--font-family` | `'Inter', sans-serif` | Body text |
| `--font-heading` | `'Inter', sans-serif` | Headings |
| `--font-size-xs` | `0.75rem` | Caption |
| `--font-size-sm` | `0.875rem` | Small text |
| `--font-size-base` | `1rem` | Body |
| `--font-size-lg` | `1.125rem` | Large body |

## 2. Components Status

| Component | Variants | Status |
| --- | --- | --- |
| Button | Primary, Secondary, Ghost, Danger | 🏗️ Defined |
| Input | Text, Password, Search, Textarea | 🏗️ Defined |
| Card | Traveler Card, Product Feed, Order Card | 📝 Drafted |
| Status Tracker | Vertical Stepper (Fulfillment) | 📝 Drafted |
| Navigation | Bottom Tab (Home, Request, Profile) | 🏗️ Defined |
| Badge | Verified, Expertise, Status | 📝 Drafted |

## 3. UI Principles for MyTrip-MyTitipan

1. **Trust-Centric:** Gunakan badge verifikasi yang kontras dan informatif.
2. **Clarity over Flash:** Informasi harga dan status escrow harus selalu terlihat jelas.
3. **Mobile First:** Prioritaskan penggunaan satu tangan karena jastiper sering menggunakannya saat bepergian.

---

> **Output ke**: Frontend components di [apps/frontend/](../../../../apps/frontend/)`