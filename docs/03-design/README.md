# 🎨 Design Documentation

## Purpose

Stores all visual design assets and guidelines (UI/UX), ranging from screen flow diagrams, wireframes, interactive prototypes, final mockups, and the design system.

## Rules

- **Mobile-First Design:** Since the application heavily targets mobile users, all interface designs must prioritize mobile layouts before designing desktop/tablet versions.
- **Design System Consistency:** Standardized colors, typography, grids, and UI components from the `design-system/` folder must be used.
- **Standardized Visual Assets:** All images must use WebP/PNG formats, and icons must be clean SVGs with structured naming conventions.
- **Iterative Feedback:** Ensure wireframes are reviewed and approved before moving to high-fidelity mockups.

---

## Document Index

| # | Folder | Description |
|---|--------|-------------|
| 1 | [UX Research](ux-research/) | Core design principles, pain points, and usability assumptions |
| 2 | [Information Architecture](information-architecture/) | Navigation maps, site map routes, and screen inventory |
| 3 | [User Flow](user-flow/) | Screen-by-screen user interaction flows and exception flows |
| 4 | [Wireframes](wireframes/) | Low-fidelity visual layout sketches grouped by actor (`traveler`, `shopper`) |
| 5 | [Mockups](mockups/) | High-fidelity visual interface designs and screenshots grouped by actor (`traveler`, `shopper`) |
| 6 | [Design System](design-system/) | Design tokens, foundations, typography, and UI components |
| 7 | [UI Assets](ui-assets/) | Icons, brand illustrations, and image assets |

---

## Design Process

```
User Persona → User Journey → User Flow → Wireframe → Mockup → Prototype → Handoff
     ↑              ↑            ↑           ↑          ↑          ↑          ↑
  Product         Product      Design      Design     Design    Design     Design→Dev
```

---

## Tools & Standards

| Aspect | Tool/Standard |
|--------|--------------|
| Design Tool | Figma |
| Prototyping | Figma |
| Handoff | Figma Dev Mode |
| Icons | Custom / Lucide / Material Icons |
| Illustrations | Custom |
| Naming Convention | `[page]-[component]-[state]` |
| File Format | SVG (icons), PNG/WebP (images) |

---

## Relationship to Other Docs

- **← Product**: User Persona & User Journey → User Flow
- **→ Technical**: Design System → Frontend Components
- **→ Testing**: Mockups → Visual Regression Tests
