# Gemini CLI: Agent Runbook

## Overview
This runbook defines the operational procedures for Gemini CLI when executing as a specific logical persona within the Multi-Agent SDLC. Gemini CLI acts as the single orchestrator, assuming one persona at a time to complete a phase-specific task.

## Execution Procedure

### 1. Initialization
- **Persona Selection**: Identify the required agent persona for the current task (e.g., `BAA`, `PMA`, `SAA`).
- **Context Loading**: Gemini CLI must read all artifacts from the preceding phase (as defined in `workflows.md`).
- **State Verification**: Confirm that the predecessor's `HANDOFF.md` exists and the phase has been approved by the relevant human gatekeeper.
- **GitHub Sync (Fetch)**: Retrieve tasks from the pool using `gh issue list --label "task","persona:<agent_type>" --state "open"`. Use `gh issue view <ID>` to load detailed requirements.

### 2. Execution Phase
- **GitHub Sync (Status)**: Mark the task as active using `gh issue edit <ID> --add-label "in-progress"`.
- **Persona Assumption**: Gemini CLI operates under the constraints (Read/Write/Forbidden) defined in the agent's profile (e.g., `01-business-analyst.md`).
- **Iterative Drafting**: Generate the required artifacts. If the task is complex, use sub-tasks but ensure all output is written to the agent's designated directory.
- **Self-Correction**: Gemini CLI must validate its own output against the agent's "Success Criteria".

### 3. Finalization & Commit
- **Artifact Generation**: Ensure all required markdown files, diagrams, or code are present.
- **Metadata Tagging**: Apply the standard metadata header to every generated file.
- **Handoff Creation**: Write a `HANDOFF.md` summarizing the work, key decisions, and remaining risks.
- **GitHub Sync (Close)**: Close the issue using `gh issue close <ID> --comment "Completed. Handoff: <PATH_TO_HANDOFF>"`.
- **Atomic Commit**: All artifacts must be committed to a feature branch using the standardized commit message format: `[AGENT_ID] Action: Brief Description`.

### 4. Transition
- **Approval Request**: Notify the human gatekeeper that the phase is ready for review.
- **Halt**: Gemini CLI must stop execution and wait for human approval before assuming the next persona.

## Troubleshooting
- **Missing Inputs**: If a preceding artifact is missing, Gemini CLI must backtrack to the previous agent persona to generate it (requires re-approval).
- **Tool Failures**: If a shell command or tool fails, document the error in the current draft and retry with a corrected strategy.
