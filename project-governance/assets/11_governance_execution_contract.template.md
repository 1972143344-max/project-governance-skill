# Governance Execution Contract

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/

## Maintenance Threshold

Document role: `support-protocol`
Advisory threshold: `220 lines`
Split threshold: `320 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this protocol document should be split into routed companion docs rather than continue growing as one file.
Even below the split threshold, surface the same recommendation if readers usually need only one semantic subset at a time.
Do not silently restructure this document during unrelated work.

## Purpose

This document defines the detailed rules for:

- task-record handling
- same-round governance sync
- update and notify boundaries
- quality, review, closure, and completed-state sync

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
- when a round uses an independent reviewer, `completed` normally means `review-adjudicated and closure-ready`
- do not fill fields that do not apply just to satisfy a large generic template

## Same-Round Sync Rules

- if specs or design decisions change, update the matching governance docs in the same workstream
- if context shards are superseded or archived, update the context index in the same round
- prefer append-only audit updates for meaningful implementation and environment actions
- if a round materially changes future reading behavior, authority routing, or execution-layer retrieval expectations, sync the affected governance and execution-layer docs in the same workstream instead of leaving the new read path implicit

## Update And Notify Rules

Do not silently change future reading behavior in meaningful ways.

Tell the user explicitly before or while performing:

- archive or supersede actions
- index splits or routing reorganizations
- lesson promotions that change future workflow
- authority changes

Only clearly mechanical small updates may be done without separate notice, and only when the semantic change was already explained.

## Quality Gate

Before claiming delivery complete:

- locate and run the repo-local quality gate required for the touched surface
- prefer an explicit quality-gate source already present in the repository
- if the quality gate is inferred rather than explicitly documented, say so clearly instead of presenting it as a formal repository rule

## Review Standard

- review for correctness, regressions, security boundaries, missing tests, and doc drift
- surface residual risk explicitly in the closing handoff

## Closure Rule

Do not treat completed-state governance or task sync as a substitute for real closure readiness.

If the repository expects broad closure-stage gates such as `build`, `ci`, or equivalent, those gates should pass before final completed-state sync is treated as ready.
