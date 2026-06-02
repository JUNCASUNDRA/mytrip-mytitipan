# User Flow

> Diagram alur interaksi pengguna di dalam aplikasi.

## Naming Convention

File: `[flow-name].md` atau `[flow-name].png`

## Flows

| Flow | Description | Status |
|------|-------------|--------|
| Registration Flow | Alur pendaftaran user baru | ⬜ Todo |
| Login Flow | Alur login user | ⬜ Todo |
| Search & Browse Flow | Alur pencarian traveler dan produk | 🚧 In Progress |
| Request-to-Payment Flow | Alur dari Shopper buat request sampai bayar Escrow | ✅ Defined |
| Trip-to-Fulfillment Flow | Alur Traveler buat trip sampai kirim barang | ✅ Defined |
| Profile & Reputation Flow | Alur manajemen profil dan sistem badge | ⬜ Todo |

## Core Flow: Shopper Request-to-Payment

```mermaid
sequenceDiagram
    participant S as Shopper
    participant P as Platform
    participant T as Traveler

    S->>P: Browse Feed/Search Trip
    P-->>S: Display Verified Travelers
    S->>P: Fill Request Form (Item, Budget)
    P->>T: Notify New Request
    T->>P: Send Final Quote (Price + Fee + Shipping)
    P->>S: Notify Quote Received
    S->>P: Approve & Pay via Payment Gateway
    P->>P: Lock Funds in Escrow
    P->>T: Notify: Payment Secured, Start Purchasing
```

## Core Flow: Traveler Trip-to-Fulfillment

```mermaid
sequenceDiagram
    participant T as Traveler
    participant P as Platform
    participant S as Shopper

    T->>P: Create Trip (Destination, Dates)
    P->>S: Notify Followers / Update Feed
    T->>T: Purchase Items at Destination
    T->>P: Upload Proof of Purchase (Receipt/Photo)
    P->>S: Update Status to "Purchased"
    T->>P: Generate Shipping Label (Return to ID)
    T->>P: Input Tracking Number
    P->>S: Update Status to "Shipped"
    S->>P: Confirm Delivery
    P->>T: Release Funds to Wallet
```

---

> **Input dari**: [User Journey](../../02-product/user-journey.md), [User Persona](../../02-product/user-persona.md)
> **Output ke**: [Wireframes](../wireframes/), [Sequence Diagrams](../../04-technical/sequence-diagrams/)
