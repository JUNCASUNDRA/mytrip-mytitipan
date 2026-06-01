# Use Cases

> Spesifikasi use case formal untuk setiap fitur utama.

## Template

Setiap use case mengikuti format standard:

- **Use Case ID**: UC-[Number]
- **Actor(s)**: Siapa yang melakukan
- **Preconditions**: Kondisi awal
- **Main Flow**: Langkah-langkah utama
- **Alternative Flows**: Skenario alternatif
- **Exception Flows**: Penanganan error
- **Postconditions**: Kondisi akhir

## Use Case Diagram

```mermaid
graph LR
    subgraph System
        UC1[Register]
        UC2[Login]
        UC3[Browse]
        UC4[Order]
        UC5[Pay]
        UC6[Track]
        UC7[Review]
        UC8[Manage Users]
        UC9[Dashboard]
    end

    User((User)) --> UC1
    User --> UC2
    User --> UC3
    User --> UC4
    User --> UC5
    User --> UC6
    User --> UC7
    Admin((Admin)) --> UC8
    Admin --> UC9
```

## Use Case Index

| ID | Use Case | Actor | Priority | Status |
|----|----------|-------|----------|--------|
| UC-001 | [Authentication](uc-001-authentication.md) | User | Must | 📝 Draft |
| UC-002 | Browse & Search | User | Must | ⬜ Todo |
| UC-003 | Place Order | User | Must | ⬜ Todo |
| UC-004 | Payment | User | Must | ⬜ Todo |
| UC-005 | Track Order | User | Should | ⬜ Todo |
| UC-006 | Review & Rating | User | Should | ⬜ Todo |
| UC-007 | Admin Dashboard | Admin | Must | ⬜ Todo |

---

> **Input dari**: [User Stories](../user-stories/), [PRD](../prd.md)
> **Output ke**: [Sequence Diagrams](../../04-technical/sequence-diagrams/), [API Specification](../../04-technical/api-specification/)
