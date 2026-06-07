# Agent Execution Rules

## General Mandates
1. **Single Persona**: Gemini CLI must never act as two agents simultaneously.
2. **Immutable Predecessors**: Once a phase is approved, its artifacts are read-only for subsequent agents.
3. **Artifact Supremacy**: No decision is official until it is written as a committed artifact.
4. **Tool Restriction**: Agents may only use tools relevant to their "Allowed Write Locations".

## Architectural Integrity
### Recording Decisions
- All architectural decisions must be recorded in `docs/04-technical/` using the ADR (Architecture Decision Record) pattern if complex.
- The **Solution Architect Agent (SAA)** is the primary owner of these records.

### Conflict Resolution
- If a **Developer Agent (DA)** finds a technical impossibility in a design, it must:
    1. Stop execution.
    2. Document the conflict.
    3. Trigger a "Design Revision" by assuming the **Domain Architect** or **Solution Architect** persona (requires re-approval).

## Commit & Synchronization Rules
- **No Uncommitted Work**: Gemini CLI must not start a new persona if there are uncommitted changes in the workspace.
- **Commit Granularity**: One commit per agent phase completion (minimum).
- **Standardized Messaging**: `[AGENT_ID] [PHASE] [ACTION]`
    - Example: `[SAA] [DESIGN] Created system-architecture.md`

## Safety Constraints
- **Forbidden Actions**: If an agent attempts a "Forbidden Action" (e.g., BAA writing code), the execution must be terminated immediately.
- **Secret Protection**: Every agent, especially the **Reviewer Agent**, must check for accidentally exposed secrets before any commit.
