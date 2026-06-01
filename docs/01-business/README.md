# 📊 Business Documentation

> Semua dokumen terkait analisis bisnis, strategi, dan perencanaan keuangan.

## Folder Structure

```
01-business/
│
├── 01-discovery/           # Riset & analisis awal
│   ├── executive-summary
│   ├── problem-statement
│   ├── stakeholder-analysis
│   ├── market-research
│   ├── competitor-analysis
│   └── swot-analysis
│
├── 02-strategy/            # Strategi & model bisnis
│   ├── business-goals
│   ├── business-model-canvas
│   ├── revenue-model
│   ├── go-to-market-strategy
│   └── risk-analysis
│
├── 03-finance/             # Proyeksi keuangan
│   └── financial-projection
│
└── 04-business-flow/       # Alur bisnis
    ├── as-is
    ├── to-be
    └── customer-journey
```

---

## 📂 01-Discovery — Riset & Analisis Awal

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 1 | [Executive Summary](01-discovery/executive-summary.md) | 📝 Draft | Ringkasan eksekutif project |
| 2 | [Problem Statement](01-discovery/problem-statement.md) | 📝 Draft | Definisi masalah yang diselesaikan |
| 3 | [Stakeholder Analysis](01-discovery/stakeholder-analysis.md) | 📝 Draft | Pemetaan stakeholder & RACI |
| 4 | [Market Research](01-discovery/market-research.md) | 📝 Draft | Riset pasar, TAM/SAM/SOM |
| 5 | [Competitor Analysis](01-discovery/competitor-analysis.md) | 📝 Draft | Analisis kompetitor |
| 6 | [SWOT Analysis](01-discovery/swot-analysis.md) | 📝 Draft | Strengths, Weaknesses, Opportunities, Threats |

## 📂 02-Strategy — Strategi & Model Bisnis

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 7 | [Business Goals](02-strategy/business-goals.md) | 📝 Draft | Tujuan bisnis, OKR, KPI |
| 8 | [Business Model Canvas](02-strategy/business-model-canvas.md) | 📝 Draft | 9 blok model bisnis |
| 9 | [Revenue Model](02-strategy/revenue-model.md) | 📝 Draft | Model pendapatan & pricing |
| 10 | [Go-To-Market Strategy](02-strategy/go-to-market-strategy.md) | 📝 Draft | Strategi peluncuran |
| 11 | [Risk Analysis](02-strategy/risk-analysis.md) | 📝 Draft | Analisis & mitigasi risiko |

## 📂 03-Finance — Proyeksi Keuangan

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 12 | [Financial Projection](03-finance/financial-projection.md) | 📝 Draft | P&L, cash flow, break-even |

## 📂 04-Business-Flow — Alur Bisnis

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 13 | [AS-IS Flow](04-business-flow/as-is.md) | 📝 Draft | Alur bisnis saat ini |
| 14 | [TO-BE Flow](04-business-flow/to-be.md) | 📝 Draft | Alur bisnis yang diinginkan |
| 15 | [Customer Journey](04-business-flow/customer-journey.md) | 📝 Draft | Perjalanan pelanggan end-to-end |

---

## Reading Order

```
Discovery:  Executive Summary → Problem Statement → Stakeholder → Market Research
            → Competitor Analysis → SWOT
Strategy:   Business Goals → BMC → Revenue Model → GTM Strategy → Risk Analysis
Finance:    Financial Projection
Flow:       AS-IS → TO-BE → Customer Journey
```

## Relationship to Other Docs

- **→ Product**: Business Goals & Problem Statement → Product Vision & PRD
- **→ Technical**: Revenue Model mempengaruhi System Architecture (scalability needs)
- **→ Design**: User segments dari Market Research → User Persona
- **→ Product**: Customer Journey → User Journey Map
