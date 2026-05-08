# Project AGENTS

This file defines project-local collaboration and governance rules for this repository.

## Scope

- These rules apply to this repository only.
- Stable workflow rules live here. Project truth lives in project-scoped governance docs under `docs/<project-scope>/governance/`.
- Recovery state lives under `docs/<project-scope>/context/`.
- Task records and delivery history live under `docs/<project-scope>/tasks/`.

## Governance Layers

- `authority`: current project truth and accepted decisions
- `execution`: current frontier, completed rounds, and searchable task history
- `learning`: durable lessons that should influence future agent behavior
- `recovery`: resumable working state after compression, pause, or handoff
- `probe`: evidence-only work that must stay bounded and reviewable

## Default Governance Skeleton

Required for ordinary project-scoped governance:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/governance/01_constraints_and_spec.md`
- `docs/<project-scope>/governance/02_design.md`
- `docs/<project-scope>/governance/03_behavior_audit.md`
- `docs/<project-scope>/governance/05_decision_log.md`
- `docs/<project-scope>/tasks/00_task_knowledge_base.md`

Optional by mode or user direction:

- `docs/<project-scope>/governance/04_lessons_learned.md`
- `docs/<project-scope>/governance/06_active_plan.md`
- `docs/<project-scope>/governance/07_governance_behavior_matrix.md`
- `docs/<project-scope>/governance/08_probe_harness_contract.md`
- `docs/<project-scope>/governance/09_governance_system_spec.md`
- `docs/<project-scope>/governance/lessons/`
- `docs/<project-scope>/tasks/templates/00_task_template_index.md`
- `docs/<project-scope>/tasks/artifacts/`

Required recovery skeleton:

- `docs/<project-scope>/context/00_context_index.md`
- `docs/<project-scope>/context/01_context_usage_and_policy.md`
- `docs/<project-scope>/context/shards/`

## Reading Order

Before non-trivial work:

1. Determine the active project scope.
2. Read `docs/<project-scope>/governance/00_index_and_priority.md`.
3. Read the current authoritative spec.
4. If `docs/<project-scope>/governance/07_governance_behavior_matrix.md` is active and the round is non-trivial, read it before final lane classification.
5. If the round uses `probe-only`, touches `tasks/artifacts/`, or the project is running in `probe-heavy` mode, read `docs/<project-scope>/governance/08_probe_harness_contract.md`.
6. If task-template tiering is active and a new task record is needed, read `docs/<project-scope>/tasks/templates/00_task_template_index.md`.
7. Read relevant decisions or active plan only if the task may change direction or frontier.
8. Read task routing and recovery routing only after the relevant authority surface is known.
9. Expand into only the minimum detailed task records or context shards needed.

## Enabled Optional Surface Routing

- Read `docs/<project-scope>/governance/04_lessons_learned.md` when the learning layer is enabled and you need to check or promote a reusable lesson.
- Read `docs/<project-scope>/governance/07_governance_behavior_matrix.md` when it is active and the round needs explicit lane-control rules.
- Read `docs/<project-scope>/governance/08_probe_harness_contract.md` whenever the round uses `probe-only`, creates or relies on `tasks/artifacts/`, or the project is running in `probe-heavy` mode.
- Read `docs/<project-scope>/governance/09_governance_system_spec.md` only for governance-maintenance or governance-redesign work, and only after the authoritative core set is already known.
- Read `docs/<project-scope>/tasks/templates/00_task_template_index.md` when task-template tiering is active and more than one task-record template could fit the round.

## Progressive Disclosure

Use progressive disclosure by default when document relevance is uncertain.

- route first and expand only as needed
- prefer indexes, routing docs, file paths, filenames, and authority markers before full-document reading
- if summary headers or summary indexes exist, read them first
- if summaries do not exist, fall back to lightweight triage through title or heading skim, targeted search, and partial section reads before reading the whole file
- once an authoritative current rule, active plan, or active decision is identified as relevant, do not rely on summary-only reading for that item

## Lane Classification

Classify the round before editing anything.

Supported governance lanes:

- `docs-only`
- `metadata-sync`
- `review-only`
- `probe-only`
- `implementation`
- `substantial-change`
- `authority-change`
- `lesson-promotion`
- `index-split`
- `archive-or-supersede`

Use the narrowest lane that truthfully matches the intended output. Upgrade to a stricter lane if the round changes accepted truth, architecture, routing structure, or execution boundary.

If `docs/<project-scope>/governance/07_governance_behavior_matrix.md` is active, treat it as the authoritative lane-control surface for:

- required read baseline
- allowed write surfaces
- required sync obligations
- prohibited actions
- review and authority-update requirements

## Task Record Policy

Every meaningful completed round should produce or update a task record. Use the narrowest template that fits the round:

- `T0`: minor or metadata-only
- `T1`: probe-only, review-only, or docs-only
- `T2`: standard implementation
- `T3`: substantial or authority-changing work

Do not fill fields that do not apply just to satisfy a large generic template.

When task-template tiering is active, use `docs/<project-scope>/tasks/templates/00_task_template_index.md` as the selector surface for `T0` to `T3` rather than relying on this summary alone.

Default edge-case routing:

- `lesson-promotion`: use `T1` when the lesson is guidance-only; upgrade to `T3` if the promotion changes mandatory policy or accepted truth.
- `index-split`: use `T1` for routing-only reorganization; upgrade to `T3` if the split also changes authority status or active truth.
- `archive-or-supersede`: use `T1` when retiring or replacing routing, recovery, working, or historical surfaces without truth change; upgrade to `T3` if the active authoritative source changes.

## Governance Sync Rules

- If specs or design decisions change, update the matching governance docs in the same workstream.
- If context shards are superseded or archived, update the context index in the same round.
- Prefer append-only audit updates for meaningful implementation and environment actions.

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

Tell the user explicitly before or while performing:

- archive or supersede actions
- index splits or routing reorganizations
- lesson promotions that change future workflow
- authority changes

Only clearly mechanical small updates may be done without separate notice.

## Delivery Quality Gate

Before claiming delivery complete:

- locate and run the repo-local quality gate required for the touched surface
- prefer an explicit quality-gate source already present in the repository, such as governance docs, `AGENTS.md`, an existing workflow/task contract, CI configuration, or other executable build/test entrypoints
- if the quality gate is inferred from repository execution surfaces rather than explicitly documented, say so clearly instead of presenting it as a formal repository rule

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
