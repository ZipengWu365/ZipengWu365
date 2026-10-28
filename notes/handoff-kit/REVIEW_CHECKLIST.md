# Handoff review checklist

Use this as a manual review aid. It does not automatically verify truth,
client compatibility, security, or model behavior.

## Before transfer
- Confirm the project, repository revision, branch/worktree, and pending changes.
- Check active constraints against user instructions and project rules.
- Separate proposed, rejected, superseded, and unresolved decisions.
- Keep reported changes separate from verified changes.
- Record test results only with their source, environment, and revision.
- Preserve unknowns and inaccessible evidence.
- Remove secrets and unauthorized private material; inspect external excerpts.
- Keep the original evidence in its authorized location.

## In the receiving session
- Explicitly provide or request reading of the reviewed packet.
- Verify which source files and instruction files are actually accessible.
- Ask for current constraints, withdrawn plans, unknowns, and next-action scope.
- Resolve contradictions before dependent work.
- Keep real approval controls and sandboxing enabled.
- Verify actual work after the handoff; a correct restatement is not a test pass.

## When evaluating a tool
- Use a bounded, comparable task and record its initial state.
- Separate preparation, receiving-context, retrieval, and rework costs.
- Record model settings and cache conditions where observable.
- Track missing constraints, false completion claims, and human corrections.
- Report unmeasured values as missing; do not convert missing data into zero.
