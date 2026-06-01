# Business Flow — AS-IS

> **Status**: 📝 Draft
> **Last Updated**: YYYY-MM-DD

---

## Overview

Dokumentasi alur bisnis saat ini (sebelum ada solusi digital).

## Current Process Flow

```mermaid
flowchart TD
    A[Start: User has need] --> B[Search manually]
    B --> C{Found solution?}
    C -->|No| D[Give up / Ask friends]
    C -->|Yes| E[Contact provider]
    E --> F[Negotiate manually]
    F --> G[Manual payment]
    G --> H[Wait for delivery]
    H --> I{Satisfied?}
    I -->|No| J[Complaint via chat/call]
    I -->|Yes| K[End]
    J --> L[Manual resolution]
    L --> K
    D --> K
```

## Current Pain Points

| Step | Pain Point | Severity | Frequency |
|------|-----------|----------|-----------|
| Search | Tidak ada platform terpusat | High | Every time |
| Contact | Harus hubungi satu per satu | High | Every time |
| Payment | Tidak ada escrow/jaminan | Critical | Every time |
| Tracking | Tidak bisa track status | Medium | Every time |
| Resolution | Proses komplain manual | High | Frequent |

## Process Metrics (Current)

| Metric | Current Value | Pain Level |
|--------|-------------|-----------|
| Time to complete | | 🔴 |
| Success rate | | 🔴 |
| Customer satisfaction | | 🟡 |
| Cost per transaction | | 🟡 |

## Stakeholders in Current Process

| Role | Responsibility | Pain Points |
|------|---------------|------------|
| | | |

---

> **Compare with**: [TO-BE Flow](to-be.md)
