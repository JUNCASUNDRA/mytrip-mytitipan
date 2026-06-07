# AI SDLC Multi-Agent Framework

## Overview
This document defines the governance and operational framework for the AI-driven Software Development Life Cycle (SDLC) within the MyTrip - MyTitipan repository. The framework utilizes a sequential multi-agent orchestration model where each agent has a single, well-defined responsibility.

## Core Principles
1. **Single Responsibility**: Each agent performs one specific role in the SDLC.
2. **Traceability**: Every output is documented and stored in version control.
3. **Human-in-the-Loop**: Major transitions between phases require explicit human approval.
4. **Isolation**: Agents have restricted read/write access to maintain artifact integrity.
5. **Auditability**: All agent interactions and decisions must be reviewable.

## Agent Catalog

| Order | Agent | Primary Responsibility | Target Location |
|-------|-------|------------------------|-----------------|
| 1 | [Business Analyst Agent](./01-business-analyst.md) | Business Requirements & Market Alignment | `docs/01-business/` |
| 2 | [Product Manager Agent](./02-product-manager.md) | Feature Definition & Prioritization | `docs/02-product/` |
| 3 | [Solution Architect Agent](./03-solution-architect.md) | System-wide Architecture & Infra | `docs/04-technical/` |
| 4 | [Domain Architect Agent](./04-domain-architect.md) | Data Modeling & API Specs | `docs/04-technical/` |
| 5 | [Task Planner Agent](./05-task-planner.md) | Implementation Breakdown | `docs/02-product/planning/` |
| 6 | [Developer Agent](./06-developer.md) | Feature Implementation | `apps/`, `packages/` |
| 7 | [Reviewer Agent](./07-reviewer.md) | Quality & Compliance Validation | `docs/05-testing/` |

## Workflow & Governance
- [Agent Workflows](./workflows.md): Diagrams and communication protocols.
- [Framework Standards](./standards.md): Naming, versioning, and ownership matrix.

## SDLC Sequence
1. **Discovery**: Business Analyst -> Product Manager
2. **Design**: Solution Architect -> Domain Architect
3. **Planning**: Task Planner
4. **Execution**: Developer
5. **Validation**: Reviewer
