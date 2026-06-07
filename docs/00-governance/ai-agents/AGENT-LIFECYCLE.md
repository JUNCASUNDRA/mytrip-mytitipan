# Agent Lifecycle Management

## Phase Lifecycle
Every agent persona follows a strict lifecycle: `Start -> Execute -> Review -> Commit -> Handoff`.

### 1. Start Phase
- Triggered by: Human request or completion of the preceding phase.
- Action: Load the `HANDOFF.md` from the predecessor.
- Status: `ACTIVE`

### 2. Execution Phase
- Action: Gemini CLI performs the agent's primary responsibilities.
- Constraint: Only one agent is active. No parallel agent execution is permitted.
- Status: `IN_PROGRESS`

### 3. Review Phase (Internal)
- Action: Gemini CLI performs a self-audit against `standards.md` and the agent's success criteria.
- Status: `INTERNAL_REVIEW`

### 4. Commit Phase
- Action: Stage all changed/new files. Verify no forbidden locations were modified.
- Action: Commit to the repository.
- Status: `COMMITTED`

### 5. Handoff Phase
- Action: Generate `HANDOFF.md`.
- Action: Wait for Human Approval Gate.
- Status: `WAITING_FOR_APPROVAL`

## Rollback & Revision
### Rollback Procedure
1. Identify the failing phase.
2. Revert the repository to the state of the last approved `HANDOFF.md`.
3. Clear all uncommitted artifacts from the failed phase.
4. Restart the lifecycle for the affected agent.

### Handling Rejected Work
1. If a Human Gatekeeper rejects the output, Gemini CLI enters the `REVISION` state.
2. Read the rejection feedback.
3. Modify the artifacts in the current phase.
4. Re-submit for approval.

### Revision Tracking
- Every artifact includes a `version` in its metadata.
- Revisions are tracked via Git history.
- Significant revisions must be noted in the `HANDOFF.md` of the current phase.
