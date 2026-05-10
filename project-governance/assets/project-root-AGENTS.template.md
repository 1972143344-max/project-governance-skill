# Project AGENTS

This file defines project-local collaboration and governance rules for this repository.

## Scope

- These rules apply to this repository only.
- Stable workflow rules live here. Project truth lives in project-scoped governance docs under `docs/<project-scope>/governance/`.
- Recovery state lives under `docs/<project-scope>/context/`.
- Task records and delivery history live under `docs/<project-scope>/tasks/`.

## Reading Order

Before non-trivial work:

1. Determine the active project scope.
2. Read `docs/<project-scope>/governance/00_index_and_priority.md`.
3. Read the current authoritative spec.
4. Read the authoritative design doc when structure or behavior matters.
5. If `docs/<project-scope>/governance/07_governance_behavior_matrix.md` is active and the round is non-trivial, read it before final lane classification.
6. If the round uses `probe-only`, touches `tasks/artifacts/`, or the project is running in `probe-heavy` mode, read `docs/<project-scope>/governance/08_probe_harness_contract.md`.
7. Read relevant decisions or active plan only if the task may change direction or frontier.
8. Read task routing and recovery routing only after the relevant authority surface is known.
9. Expand into only the minimum detailed task records or context shards needed.

Stable entrypoint names should not be changed lightly.
If a referenced entrypoint grows too large, keep that entrypoint as the shallow read-first surface and split below it with second-level routing.

## Progressive Disclosure

Use the full repository reading protocol instead of relying on summary bullets in this file when the current round depends on document-reading quality.

Read `docs/<project-scope>/governance/10_runtime_reading_protocol.md` before acting when the round involves:

- non-trivial repo work
- authority, task, or context routing
- deciding between route-first, probing, section expansion, or full-read
- review, planning, implementation, or governance maintenance that depends on document-reading quality

You may skip that full protocol for:

- pure chat
- light brainstorming with no repo-document lookup
- casual explanation that does not depend on repository routing or authority adjudication

## Task Record Policy

Every meaningful completed round should produce or update a task record.

- use the narrowest repo-local task-record template that truthfully fits the round
- if task-template tiering is active and a new task record is needed, read `docs/<project-scope>/tasks/templates/00_task_template_index.md`

Read `docs/<project-scope>/governance/11_governance_execution_contract.md` before acting when the round involves:

- task-record creation or update
- behavior-audit, active-plan, or context-index sync
- governance sync, routing changes, archive/supersede, or authority-affecting maintenance
- delivery completion, quality-gate judgment, review adjudication, or closure docs

You may skip that contract for:

- pure chat
- exploratory reading with no governance sync or closure judgment
- implementation work that has not yet entered sync, review, or completion handling

## Governance Sync Rules

- Do not leave changed authority, routing, execution-state, or closure-state expectations implicit.
- Use `docs/<project-scope>/governance/11_governance_execution_contract.md` for the detailed same-round sync and closure rules when this section is active for the current round.

## Authority Boundary

- Governance docs under `docs/<project-scope>/governance/` are authoritative.
- If active, `docs/<project-scope>/governance/07_governance_behavior_matrix.md` controls lane discipline.
- If active, `docs/<project-scope>/governance/08_probe_harness_contract.md` is mandatory for `probe-only` rounds and for rounds that create or rely on `tasks/artifacts/`.
- Recovery docs under `docs/<project-scope>/context/` are working/reference only.
- `docs/<project-scope>/governance/04_lessons_learned.md` remains the learning-layer entrypoint even when `governance/lessons/` contains leaf lesson files.
- `docs/<project-scope>/tasks/artifacts/` stores evidence outputs only and does not become an authority surface by itself.
- Summary headers and summary indexes are routing-only.
- If governance and context disagree, governance wins.

## Update Policy

Do not silently change future reading behavior in meaningful ways.

- If a high-frequency, routing, or authority document has grown long enough to degrade reading quality, explicitly tell the user that maintenance, splitting, or second-level indexing is needed instead of letting it grow without control.
- Read `docs/<project-scope>/governance/11_governance_execution_contract.md` before archive/supersede, routing reorganization, authority-affecting maintenance, or closure-state sync.
- Clearly mechanical updates may be handled without separate notice only when the semantic change was already explained.

## Delivery Quality Gate

Use `docs/<project-scope>/governance/11_governance_execution_contract.md` for quality-gate, review, closure, and completed-state sync rules when the current round enters completion or closure adjudication.

## Review Standard

- Review for correctness, regressions, security boundaries, missing tests, and doc drift.
- Surface residual risk explicitly in the closing handoff.

## Compression Recovery

After any context compression, summarization, or handoff:

- re-check the active task, current plan, and authoritative context before proceeding
- verify that no constraints, subtasks, decisions, or pending actions were dropped or made stale
- if recent execution state matters, consult the project-scoped recovery layer before trusting compressed chat memory alone
- if uncertainty remains, surface it explicitly to the user

## Skill Re-entry

Use the `project-governance` skill when the task involves governance initialization, authority boundaries, task-template selection, lessons promotion, routing/index maintenance, probe-only governance, or context-layer maintenance.

Do not rely on memory of the skill alone when current written instructions may have drifted.
