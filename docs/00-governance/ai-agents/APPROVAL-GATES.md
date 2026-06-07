# Approval Gates & Phase Transitions

## Overview
Transitions between SDLC phases are guarded by Human Approval Gates. These gates ensure that AI-generated artifacts meet the quality and strategic standards of the project.

## Approval Matrix

| Gate | Preceding Agent | Target Agent | Gatekeeper | Primary Artifacts |
|:---|:---|:---|:---|:---|
| **Gate 1: Strategy** | PMA | SAA | Business Owner | User Stories, Roadmap, MVP Definition |
| **Gate 2: Architecture** | DAA | TPA | Tech Lead | System Arch, DB Schema, API Specs |
| **Gate 3: Planning** | TPA | DA | Project Manager | Task Breakdown, Priority List |
| **Gate 4: Validation** | RA | (Production) | Lead Engineer | PR Review, Test Reports, Compliance Audit |

## The Approval Process
1. **Submission**: Gemini CLI generates a PR/Issue or provides a summary of the phase's artifacts.
2. **Review**: The Human Gatekeeper inspects the artifacts in the repository.
3. **Verdict**:
    - **Approved**: The human provides a "Signed-off" comment or approval signal.
    - **Rejected**: The human provides feedback for revision.
4. **Activation**: Only upon "Approved" status can Gemini CLI proceed to the next Agent Persona.

## Recording Approvals
- Approvals should be recorded in the `status` field of the artifact metadata (updated from `Review` to `Approved`).
- The `HANDOFF.md` of the next phase must link to the approval record (e.g., a specific Git commit or PR ID).

## Emergency Overrides
- Emergency overrides (bypassing a gate) are only permitted for critical security hotfixes.
- All overrides must be documented post-hoc in a `GATE-BYPASS.md` file under `docs/00-governance/`.
