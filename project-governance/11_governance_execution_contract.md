# Governance Execution Contract

Use this contract when the round enters governance execution, sync, review, quality, or closure handling.

## Read This When

Read this document before acting when the round involves:

- task-record creation or update
- behavior-audit, active-plan, or context-index sync
- governance sync, routing changes, archive/supersede, or authority-affecting maintenance
- delivery completion, quality-gate judgment, review adjudication, or closure docs

## Skip This When

You may skip this document for:

- pure chat
- exploratory reading with no governance sync or closure judgment
- implementation work that has not yet entered sync, review, or completion handling

## Task Record Policy

Every meaningful completed round should produce or update a task record.

- use the narrowest repo-local task-record template that truthfully fits the round
- if task-template tiering is active and a new task record is needed, read `docs/<project-scope>/tasks/templates/00_task_template_index.md`
- when a round uses an independent reviewer, `completed` should normally mean `review-adjudicated and closure-ready`, not merely `code written` or `local verification passed`
- do not fill fields that do not apply just to satisfy a large generic template

## Same-Round Execution Sync Exception

You may complete required same-round execution sync without a separate approval ask when all of the following are true:

- the repo already expects that sync in the same round
- the sync only records already-earned execution state
- the sync does not alter authority order or future reading behavior materially

This exception is limited to:

- task records
- task knowledge-base sync
- behavior audit
- active plan updates when the frontier really changed
- atomic context-index and shard-status sync

## Sync And Promotion Triggers

Update authority docs when:

- scope changes
- a hard constraint changes
- an accepted design rule changes
- a decision is made, replaced, or superseded
- a proposal becomes accepted policy

Update execution docs when:

- a meaningful implementation, review, docs, or probe round completes
- the current frontier changes
- the blocker boundary changes
- the next package changes
- the risk ordering changes

Update recovery docs when:

- a future agent would need the state after compression, pause, or handoff
- a shard becomes superseded, stale, resolved, archived, or promoted
- a new shard changes routing relevance

Treat shard update plus `00_context_index.md` update as one atomic documentation action.

## Minimal File Heuristics

Use these defaults when the layer-level trigger above already fired:

- update `00_index_and_priority.md` when authority or status routing changed
- update `01_constraints_and_spec.md` when requirements, constraints, or current rules changed
- update `02_design.md` when architecture or implementation design changed
- update `03_behavior_audit.md` after meaningful implementation, config, docs, or environment actions
- update `05_decision_log.md` when one direction was explicitly chosen over alternatives
- update `06_active_plan.md` only when the frontier actually changed

## Update And Notify Rules

Do not silently change future reading behavior in meaningful ways.

Tell the user explicitly before or while performing:

- archive or supersede actions
- routing or index reorganization
- promotion of stable conclusions into more authoritative documents
- changes that materially reorganize recovery or context routing

Only clearly mechanical small updates may be done without separate notice when the semantic change was already explained.

## Quality Gate

Before claiming delivery complete, locate and run the repo-local quality gate required for the touched surface.

Prefer an explicit repo-local source such as:

- authoritative governance docs
- applicable `AGENTS.md`
- an existing workflow contract
- CI configuration
- existing executable repo entrypoints

If the quality gate is inferred rather than explicitly documented, say so truthfully.

## Review Requirement

After major changes, require a review pass before considering the work complete.

If reviewer agents are available, prefer an independent review pass.

## Review Standard

- review for correctness, regressions, security boundaries, missing tests, and doc drift
- surface residual risk explicitly in the closing handoff

## Closure Readiness

Do not treat governance sync alone as proof that the round is complete.

Closure is ready only when:

- the execution or docs round is actually complete
- required review has happened
- required quality gates have passed, if any
- remaining uncertainty or residual risk has been surfaced honestly

## Final Sync Rule

Repeat this rule wherever sync and closure meet:

- final completed-state documentation must not be written as a substitute for real closure readiness
