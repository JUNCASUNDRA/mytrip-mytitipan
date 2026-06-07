# Master Orchestrator Governance (GEMINI.md)

This file serves as the **Master Orchestrator** for the AI SDLC Multi-Agent Framework within the MyTrip - MyTitipan monorepo. It does not define agent capabilities (which are located in `docs/00-governance/ai-agents/`), but rather **governs their execution, orchestration, and workflow**. 

As Gemini CLI, you must strictly adhere to these instructions when operating within this repository.

---

## 1. Project Philosophy

* **Documentation First:** Code is merely a byproduct of well-documented decisions. If it isn't documented, it doesn't exist.
* **Business Driven Development:** Every technical task must trace back to a validated business goal or user persona.
* **Architecture Before Implementation:** No code may be written until the high-level and domain architectures are approved.
* **Human Approval Required:** Major phase transitions (Strategy, Architecture, Production) require explicit human sign-off.
* **Traceable Decision Making:** All design choices must be captured in formal records linking back to requirements.
* **Repository as Single Source of Truth:** External task trackers or chats are secondary; the Git repository holds the canonical state of product and architecture.

---

## 2. Core Principles

1. **No coding before approved architecture.**
2. **No architecture before approved requirements.**
3. **Every phase must generate artifacts.** (An agent execution without output is an invalid execution).
4. **Every artifact must be versioned.** (Metadata headers are mandatory).
5. **Every change must be reviewable.** (All agent outputs must be submitted via PR or isolated branch).
6. **Every workflow must be auditable.** (Traceability from code to task to architecture to requirement is strictly enforced via immutable handoff logs).

---

## 3. Workflow Selector

Depending on the human directive, the orchestrator must select the appropriate workflow. 

| Workflow | Entry Agent | Agent Sequence | Required Outputs | Approval Gates |
|:---|:---|:---|:---|:---|
| **Research** | BAA / SAA | BAA &rarr; PMA (or SAA &rarr; DAA) | Discovery Docs, Tech Feasibility | Strategy / Architecture |
| **Feature** | BAA | BAA &rarr; PMA &rarr; SAA &rarr; DAA &rarr; TPA &rarr; DA &rarr; RA | Full Artifact Chain + Source Code | All Gates |
| **Enhancement** | PMA | PMA &rarr; SAA &rarr; DAA &rarr; TPA &rarr; DA &rarr; RA | Updated PRDs, Tasks, Source Code | Product, Arch, Dev, Release |
| **Bugfix** | RA | RA (Diagnostic) &rarr; TPA &rarr; DA &rarr; RA | RCA Report, Task Breakdown, Patch | Dev, Release |
| **Hotfix** | RA | RA (Diagnostic) &rarr; DA &rarr; RA | RCA Report, Patch, Regressions | Release (Emergency Override) |
| **Refactoring** | SAA / DA | SAA &rarr; TPA &rarr; DA &rarr; RA | Arch Updates, Source Code | Arch, Dev, Release |
| **Arch Change** | SAA | SAA &rarr; DAA &rarr; TPA &rarr; DA &rarr; RA | ADRs, Schema, Tasks, Source Code | Arch, Dev, Release |
| **Production Incident**| RA | RA &rarr; DA &rarr; RA | Audit Logs, Patch, Compliance Check| Release |

---

## 4. Agent Orchestration Rules

1. **Only one active agent at a time:** Concurrent execution of distinct agent personas is strictly prohibited.
2. **Sequential execution only:** Agents must execute in the exact order defined by the selected workflow.
3. **Explicit handoff required:** An agent must produce a unique, timestamped `HANDOFF-[YYYYMMDD]-[TICKET]-[AGENT].md` in `docs/00-governance/handoffs/`.
4. **Agent must consume previous artifacts:** Every agent must read the outputs of its immediate predecessor before acting.
5. **Agent may not skip workflow stages:** Bypassing an agent in the sequence requires invoking an Emergency Override (P1 Incidents only).

---

## 5. Approval Gates

Transitions between major phases are blocked until a Human Gatekeeper approves.

* **Business Approval:** Required after BAA. Validates market alignment and financial constraints.
* **Product Approval:** Required after PMA. Validates scope, user stories, and MVP definition.
* **Architecture Approval:** Required after SAA/DAA. Validates system design, security, and data schemas.
* **Development Approval:** Required after TPA/DA. Validates code completeness against tasks.
* **Release Approval:** Required after RA. Validates QA, compliance, and readiness for production.

**Rejection and Revision Flow:**
If an approval is rejected, the orchestrator immediately halts progression, reverts the active persona to the agent responsible for the rejected artifact, applies the human feedback, regenerates the artifact, and re-submits for approval.

---

## 6. Artifact Contracts

Each domain requires specific artifacts, stored in designated locations:

| Domain | Target Directory | Mandatory Artifacts |
|:---|:---|:---|
| **Business** | `docs/01-business/` | Discovery Docs, Strategy, Financials, Business Flows |
| **Product** | `docs/02-product/` | Roadmaps, User Personas, User Stories, Planning |
| **Design** | `docs/03-design/` | (Human-driven) Wireframes, Design System |
| **Technical** | `docs/04-technical/` | System Arch, DB Schemas, API Specs, ADRs, Sequence Diagrams |
| **Testing** | `docs/05-testing/` | Test Plans, Test Cases, QA Reports |

---

## 7. Definition of Done (DoD) - Tiered Testing Model

To maintain startup velocity, a risk-based testing model is enforced:

* **Critical Paths (Payment, Escrow, Auth):** 90%+ unit/integration coverage. No untested edge cases.
* **Core Business Logic (Trips, Orders):** 70%+ unit/integration coverage. 
* **UI/Presentation Layer:** Snapshot tests and critical path E2E smoke tests.
* **Security/Compliance:** 0 critical vulnerabilities. RA must pass `Security Review` mode.
* **Documentation:** All public APIs documented; relevant ADRs updated and approved.

---

## 8. Repository Ownership Matrix

| Area | Write Owner | Read Access |
|:---|:---|:---|
| `docs/00-governance/`| Lead Architect (Human) | All Agents |
| `docs/01-business/` | Business Analyst Agent | All Agents |
| `docs/02-product/` | Product Manager Agent | All Agents |
| `docs/03-design/` | UI/UX Designer (Human) | All Agents |
| `docs/04-technical/` | Solution Architect, Domain Architect | All Agents |
| `docs/05-testing/` | Reviewer Agent | All Agents |
| `apps/` | Developer Agent | All Agents |
| `packages/` | Developer Agent | All Agents |
| `infra/` | Solution Architect | All Agents |

---

## 9. Reviewer Capability Matrix & Authority Boundaries

The **Reviewer Agent (RA)** operates under a **Strict Read-Only / Recommendation-Only** mandate for application code. It cannot modify source code or generate patches.

1. **Architecture Review:** Validates DA implementation against SAA/DAA blueprints.
2. **Domain Review:** Validates implementation against BAA/PMA business rules.
3. **Security Review:** Scans for secrets, PII leaks, and dependency vulnerabilities.
4. **Integration Review:** Validates API contracts and monorepo package compatibility.
5. **Release Review:** Validates QA completeness and documentation sync.
6. **Financial Compliance Review:** Audits logic for idempotency, race conditions, and transactional integrity (Payment/Escrow).
7. **Diagnostic (RCA) Mode:** Analyzes logs and code to identify root causes for Bugfix/Hotfix workflows.

---

## 10. Change & Incident Classification

### Incident Severity Matrix
* **P1 (Critical):** System outage or financial risk (Escrow/Payment failure). *Workflow: Hotfix (Emergency Gates).*
* **P2 (High):** Major feature broken for many users. *Workflow: Bugfix (Standard Gates).*
* **P3 (Medium):** Feature degraded, workaround exists. *Workflow: Bugfix (Standard Gates).*
* **P4 (Low):** Minor cosmetic/UX issues. *Workflow: Enhancement/Bugfix.*

### Change Types
* **Feature:** Net-new capability impacting business flows.
* **Enhancement:** Improvement to existing functionality.
* **Bugfix:** Correcting unintended behavior.
* **Arch Change:** Structural changes requiring SAA/DAA involvement.

---

## 11. Escalation Rules

### Architecture Escalation
The `Arch Change` workflow (SAA & DAA involvement) is **mandatory** if a change involves:
1. Database schema modifications (DDL).
2. API contract modifications (breaking changes or new endpoints).
3. Authentication or Authorization logic changes.
4. Changes to asynchronous event schemas or payloads.
5. New external third-party API integrations.

### Critical Domain Escalation
Any change (regardless of size) touching the following domains automatically escalates to the **Architecture Change** workflow and requires **Architecture Approval**:
* **Payment, Escrow, Settlement, Dispute, Shipment, Billing, KYC, Compliance.**

---

## 12. Decision Records (ADR)

* **Naming Convention:** `ADR-[000]-[slug].md` in `docs/04-technical/adrs/`.
* **Financial ADRs:** Must explicitly document **Idempotency**, **State Machine transitions**, and **Ledger immutability**.
* **Approval Process:** Must be approved by SAA/DAA and Human Lead before implementation.

---

## 13. Anti-Patterns

* **Reviewer Patching:** RA attempting to fix code instead of documenting recommendations.
* **Ephemeral Handoffs:** Overwriting `HANDOFF.md` and losing historical audit trails.
* **Shadow Architecture:** Modifying schemas or API contracts in a `Bugfix` or `Feature` workflow without SAA/DAA escalation.
* **Ungated Financial Logic:** Deploying payment or escrow changes without the `Financial Compliance Review` signal.
* **Coverage Blindness:** Chasing 100% coverage on non-critical UI code while ignoring low coverage on PII-handling logic.

---

## 14. Future Scalability Guidance

As MyTrip - MyTitipan evolves into complex financial services:
* **Prefer specialized RA modes** (e.g., `Dispute Audit Mode`, `Billing Reconciliation Mode`) over new agents.
* **Domain Architects** must maintain the integrity of the **Global State Machine** for all financial transactions.
* **Task Planners** must sequence financial tasks to ensure zero downtime for ledger-sensitive operations.
