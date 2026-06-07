# 📊 Business Documentation

## Purpose

Explains the business vision, market research, competitor analysis, Go-To-Market (GTM) strategy, revenue model, and financial feasibility of the My Trip My Titipan platform.

## Rules

- **MVP Focus:** All business analysis must prioritize a rapid launch within 3 months with a small team (3-5 people).
- **Asset-Light:** The business model must focus on the platform's role as a trusted intermediary (escrow & trust infrastructure) without physical inventory ownership.
- **Realistic Research:** Competitor analysis and financial projections must be grounded in the initial target market (mobile-first, local).

## Folder Structure

```
01-business/
│
├── 01-discovery/           # Early research & analysis
│   ├── executive-summary
│   ├── problem-statement
│   ├── stakeholder-analysis
│   ├── market-research
│   ├── competitor-analysis
│   └── swot-analysis
│
├── 02-strategy/            # Strategy & business model
│   ├── business-goals
│   ├── business-model-canvas
│   ├── revenue-model
│   ├── go-to-market-strategy
│   └── risk-analysis
│
├── 03-finance/             # Financial projections
│   └── financial-projection
│
└── 04-business-flow/       # Business flows
    ├── as-is
    ├── to-be
    └── customer-journey
```

---

## 📂 01-Discovery — Early Research & Analysis

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 1 | [Executive Summary](01-discovery/executive-summary.md) | 📝 Draft | Executive summary of the project |
| 2 | [Problem Statement](01-discovery/problem-statement.md) | 📝 Draft | Definition of the problem being solved |
| 3 | [Stakeholder Analysis](01-discovery/stakeholder-analysis.md) | 📝 Draft | Stakeholder mapping & RACI matrix |
| 4 | [Market Research](01-discovery/market-research.md) | 📝 Draft | Market research, TAM/SAM/SOM |
| 5 | [Competitor Analysis](01-discovery/competitor-analysis.md) | 📝 Draft | Competitor analysis |
| 6 | [SWOT Analysis](01-discovery/swot-analysis.md) | 📝 Draft | Strengths, Weaknesses, Opportunities, Threats |

## 📂 02-Strategy — Strategy & Business Model

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 7 | [Business Goals](02-strategy/business-goals.md) | 📝 Draft | Business goals, OKRs, and KPIs |
| 8 | [Business Model Canvas](02-strategy/business-model-canvas.md) | 📝 Draft | 9 blocks of the business model |
| 9 | [Revenue Model](02-strategy/revenue-model.md) | 📝 Draft | Revenue streams and pricing model |
| 10 | [Go-To-Market Strategy](02-strategy/go-to-market-strategy.md) | 📝 Draft | Product launch strategy |
| 11 | [Risk Analysis](02-strategy/risk-analysis.md) | 📝 Draft | Risk analysis & mitigation |

## 📂 03-Finance — Financial Projections

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 12 | [Financial Projection](03-finance/financial-projection.md) | 📝 Draft | P&L, cash flow, and break-even analysis |

## 📂 04-Business-Flow — Business Flows

| # | Document | Status | Description |
|---|----------|--------|-------------|
| 13 | [AS-IS Flow](04-business-flow/as-is.md) | 📝 Draft | Current business flows (pre-platform) |
| 14 | [TO-BE Flow](04-business-flow/to-be.md) | 📝 Draft | Proposed business flows (post-platform) |
| 15 | [Customer Journey](04-business-flow/customer-journey.md) | 📝 Draft | End-to-end customer journey map |

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
- **→ Technical**: Revenue Model affects System Architecture (scalability needs)
- **→ Design**: User segments from Market Research → User Persona
- **→ Product**: Customer Journey → User Journey Map
