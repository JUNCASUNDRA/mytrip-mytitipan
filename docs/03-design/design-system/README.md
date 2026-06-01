# Design System

> Komponen, design tokens, dan guidelines untuk konsistensi visual.

## 1. Design Tokens

### Colors

| Token | Value | Usage |
|-------|-------|-------|
| `--color-primary` | `#` | Brand, CTA buttons |
| `--color-primary-light` | `#` | Hover states, backgrounds |
| `--color-primary-dark` | `#` | Active states |
| `--color-secondary` | `#` | Secondary actions |
| `--color-success` | `#22C55E` | Success states |
| `--color-warning` | `#F59E0B` | Warning states |
| `--color-error` | `#EF4444` | Error states |
| `--color-neutral-50` | `#F9FAFB` | Background |
| `--color-neutral-900` | `#111827` | Text |

### Typography

| Token | Value | Usage |
|-------|-------|-------|
| `--font-family` | `'Inter', sans-serif` | Body text |
| `--font-heading` | `'Inter', sans-serif` | Headings |
| `--font-size-xs` | `0.75rem` | Caption |
| `--font-size-sm` | `0.875rem` | Small text |
| `--font-size-base` | `1rem` | Body |
| `--font-size-lg` | `1.125rem` | Large body |
| `--font-size-xl` | `1.25rem` | H4 |
| `--font-size-2xl` | `1.5rem` | H3 |
| `--font-size-3xl` | `1.875rem` | H2 |
| `--font-size-4xl` | `2.25rem` | H1 |

### Spacing

| Token | Value |
|-------|-------|
| `--space-1` | `0.25rem` |
| `--space-2` | `0.5rem` |
| `--space-3` | `0.75rem` |
| `--space-4` | `1rem` |
| `--space-6` | `1.5rem` |
| `--space-8` | `2rem` |
| `--space-12` | `3rem` |
| `--space-16` | `4rem` |

### Border Radius

| Token | Value |
|-------|-------|
| `--radius-sm` | `0.25rem` |
| `--radius-md` | `0.5rem` |
| `--radius-lg` | `0.75rem` |
| `--radius-xl` | `1rem` |
| `--radius-full` | `9999px` |

### Shadows

| Token | Value |
|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.05)` |
| `--shadow-md` | `0 4px 6px rgba(0,0,0,0.1)` |
| `--shadow-lg` | `0 10px 15px rgba(0,0,0,0.1)` |
| `--shadow-xl` | `0 20px 25px rgba(0,0,0,0.15)` |

## 2. Components

| Component | Variants | Status |
|-----------|----------|--------|
| Button | Primary, Secondary, Ghost, Danger | ⬜ |
| Input | Text, Password, Search, Textarea | ⬜ |
| Card | Default, Compact, Featured | ⬜ |
| Modal | Default, Confirmation, Full-screen | ⬜ |
| Navigation | Top Bar, Bottom Tab, Sidebar | ⬜ |
| Badge | Status, Count, Label | ⬜ |
| Avatar | Image, Initials, Sizes | ⬜ |
| Toast | Success, Error, Warning, Info | ⬜ |
| Skeleton | Text, Card, Image | ⬜ |

## 3. Accessibility

| Guideline | Standard |
|-----------|----------|
| Color Contrast | WCAG 2.1 AA (4.5:1) |
| Focus States | Visible focus indicators |
| Screen Reader | Semantic HTML + ARIA |
| Touch Targets | Min 44x44px |
| Motion | `prefers-reduced-motion` support |

---

> **Output ke**: Frontend components di [apps/frontend/](../../../../apps/frontend/)
