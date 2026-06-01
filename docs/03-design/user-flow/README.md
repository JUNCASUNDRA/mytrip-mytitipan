# User Flow

> Diagram alur interaksi pengguna di dalam aplikasi.

## Naming Convention

File: `[flow-name].md` atau `[flow-name].png`

## Flows

| Flow | Description | Status |
|------|-------------|--------|
| Registration Flow | Alur pendaftaran user baru | ⬜ Todo |
| Login Flow | Alur login user | ⬜ Todo |
| Search & Browse Flow | Alur pencarian dan browsing | ⬜ Todo |
| Order Flow | Alur pemesanan | ⬜ Todo |
| Payment Flow | Alur pembayaran | ⬜ Todo |
| Profile Flow | Alur manajemen profil | ⬜ Todo |

## Example Flow: Registration

```mermaid
flowchart TD
    A[Open App] --> B{Has Account?}
    B -->|Yes| C[Login Page]
    B -->|No| D[Registration Page]
    D --> E{Registration Method}
    E -->|Email| F[Enter Email & Password]
    E -->|Google| G[Google OAuth]
    E -->|Apple| H[Apple Sign-in]
    F --> I[Email Verification]
    I --> J[Onboarding]
    G --> J
    H --> J
    J --> K[Complete Profile]
    K --> L[Home Page]
    C --> M{Valid Credentials?}
    M -->|Yes| L
    M -->|No| N[Error Message]
    N --> C
```

---

> **Input dari**: [User Journey](../../02-product/user-journey.md), [User Persona](../../02-product/user-persona.md)
> **Output ke**: [Wireframes](../wireframes/), [Sequence Diagrams](../../04-technical/sequence-diagrams/)
