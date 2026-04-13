---
name: project-governance
description: Initialize and maintain project-scoped governance documents for large or long-running work. Use when the user wants a documentation-driven workflow, needs to prevent context drift or stale-file interference, wants spec/design/audit/lessons/decision docs, or wants plan-first handling before non-trivial changes.
---

# Project Governance

Create and maintain a stable governance layer for large or long-running projects so implementation stays aligned with current rules instead of drifting across conflicting files.

Default to project-scoped governance under `docs/<project-scope>/governance/`. Only use `docs/governance/` when the user explicitly wants repository-wide governance shared across multiple projects or experiments.

Use a stable scope slug for `<project-scope>`, preferably lowercase letters, digits, and hyphens only.

Repository-level routing is optional and must not override project-scoped governance. If a repository contains multiple long-running projects or experiments, you may propose a routing-only registry at `docs/governance/00_project_scope_registry.md` to help identify the active project scope before reading any project-scoped governance docs.

## Use This Skill When

- the user asks to initialize governance docs
- the project has multiple versions, stale files, or conflicting design notes
- the user asks for spec, design, audit, lessons learned, or decision records
- the user wants plan-first handling before significant changes
- the current implementation and existing documents appear to conflict

## Core Rules

- Do not silently create governance docs. Ask first.
- Do not silently update governance docs after implementation. Ask first.
- Do not silently downgrade, merge, archive, or reinterpret old documents. Ask first.
- Never overwrite an existing `AGENTS.md` without explicit user approval. If one already exists, read it first and propose a merge plan instead of replacing it.
- When governance initialization, adoption, classification, document authority, or material document content is unclear, ask the user explicitly instead of inferring.
- If a conflict changes project direction, propose a plan and, when useful, a decision log entry before implementation.
- Prefer stable governance under `docs/<project-scope>/governance/` and keep `AGENTS.md` limited to durable collaboration rules.
- Do not create repository-level routing docs by default. Only propose `docs/governance/00_project_scope_registry.md` when multiple project scopes already exist, scope selection is repeatedly ambiguous, or the user explicitly wants repository-level routing.
- If `docs/governance/00_project_scope_registry.md` exists, treat it as routing-only. It must not define project spec, design, decision authority, or project-specific overrides.
- Repository-level routing docs must not override `docs/<project-scope>/governance/`. On project-specific matters, project-scoped governance always wins.
- After major changes, require a review pass before considering the work complete.
- If reviewer agents are available, prefer an independent review pass for major changes.
- If implementation proceeds despite non-trivial uncertainty, explicitly disclose the remaining assumptions or unclear points to the user in the closing reply.

## Governance Document Set

The standard project-scoped governance doc set is:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/governance/01_constraints_and_spec.md`
- `docs/<project-scope>/governance/02_design.md`
- `docs/<project-scope>/governance/03_behavior_audit.md`
- `docs/<project-scope>/governance/04_lessons_learned.md`
- `docs/<project-scope>/governance/05_decision_log.md`
- optional: `docs/<project-scope>/governance/06_active_plan.md`

Repository-wide exception:

- `docs/governance/...` only if the user explicitly wants one governance layer shared across multiple projects or experiments.
- optional repository-level routing helper: `docs/governance/00_project_scope_registry.md`

Use the templates in `assets/` when creating them.
If the user wants project-local collaboration rules initialized too, also use `assets/project-root-AGENTS.template.md` to create a project-root `AGENTS.md`.
Use `assets/00_project_scope_registry.template.md` only for a repository-level routing registry. Do not use it as a project spec or design template.
Use `assets/file-summary-header.template.md` only as a file-level summary header snippet.
Use `assets/summary-index.template.md` only as a lightweight routing index across multiple related files.

## Workflow

### 1. Initialization

If governance docs do not exist:

1. Ask whether to initialize the governance doc set.
2. Ask for the active project or experiment scope and a stable slug if it is not already clear.
3. Default the doc root to `docs/<project-scope>/governance/`.
4. Use `docs/governance/` only if the user explicitly wants repository-wide governance.
5. If the repository has multiple active project scopes and the user wants routing help, propose `docs/governance/00_project_scope_registry.md` as a routing-only helper.
6. Ask whether to initialize a project-root `AGENTS.md` from the template if one does not already exist.
7. If a project-root `AGENTS.md` already exists, do not overwrite it. Read it first and ask whether to keep it, merge governance rules into it, or replace it explicitly.
8. Create `00_index_and_priority.md` first.
9. Then create the remaining requested docs from templates.
10. Do not populate project-specific conclusions unless the user asks for adoption or migration.

### 2. Adoption

If the project already has scattered docs:

1. Ask whether to adopt the current project into the governance system.
2. Confirm the project scope and governance doc root first.
3. Read only the minimum current project docs needed to classify them.
4. Update `00_index_and_priority.md` to label documents as:
   - authoritative
   - working
   - historical/reference
5. Do not rewrite or clean old docs yet unless the user asks.
6. If multiple project scopes are already present or likely, propose a repository-level routing registry only if the user wants one; do not silently add it.

### 3. Before Non-Trivial Changes

When a spec conflict, scope change, or design contradiction appears:

1. Explain the conflict plainly.
2. Ask whether to create or update:
   - `docs/<project-scope>/governance/06_active_plan.md`
   - `docs/<project-scope>/governance/05_decision_log.md`
   - `docs/<project-scope>/governance/01_constraints_and_spec.md`
3. Only implement after the user confirms the direction.

### 4. After Meaningful Changes

After code, config, workflow, environment, or design changes:

1. Ask whether to update governance docs.
2. If the user wants updates:
   - record what changed in `docs/<project-scope>/governance/03_behavior_audit.md`
   - update current rules in `docs/<project-scope>/governance/01_constraints_and_spec.md` if the active spec changed
   - update `docs/<project-scope>/governance/02_design.md` if the implementation design changed
   - update `docs/<project-scope>/governance/04_lessons_learned.md` if a reusable lesson emerged
   - update `docs/<project-scope>/governance/05_decision_log.md` if a decision was made or an old one was overridden
3. For major changes, perform a review pass before closing the task.
4. If uncertainty remained during implementation, explicitly surface it to the user in the closing reply.

## Update Heuristics

- Update `docs/<project-scope>/governance/00_index_and_priority.md` when document authority or status changes.
- Update `docs/<project-scope>/governance/01_constraints_and_spec.md` when requirements, hard constraints, or the unified current rule set changes.
- Update `docs/<project-scope>/governance/02_design.md` when architecture, design rationale, or implementation details change.
- Update `docs/<project-scope>/governance/03_behavior_audit.md` after meaningful implementation, config, environment, or documentation actions.
- Update `docs/<project-scope>/governance/04_lessons_learned.md` when a problem yields a reusable lesson.
- Update `docs/<project-scope>/governance/05_decision_log.md` when alternatives were considered and one direction was explicitly chosen.
- Update `docs/<project-scope>/governance/06_active_plan.md` only when the user wants the plan persisted.

## Progressive Disclosure And Context Hygiene

Use progressive disclosure to reduce context load in large or long-running projects. The goal is not to summarize everything blindly. The goal is to help the agent decide what to read next while preserving authority, traceability, and current correctness.

### Core Intent

- Read the minimum context needed to make the next correct decision.
- Prefer routing, summaries, and headers before full-document reads.
- Avoid loading large historical files when a smaller authoritative source already answers the question.
- Do not let summaries replace authoritative project rules.

### Authority Boundary

- Summaries are for routing and quick orientation first, not for redefining project truth.
- Current spec, hard constraints, accepted decisions, and active plans must remain in authoritative governance docs, not only in summaries.
- If a summary and a full authoritative document disagree, the authoritative project document wins.
- If a summary may be stale and cannot be quickly verified, read the authoritative section instead of trusting the summary.

### Preferred Reading Strategy

For large projects, prefer this reading order:

1. Read the scope/index or routing doc first.
2. Read file-level summary headers before reading full documents.
3. Read only the sections needed for the current task.
4. Expand to full-document reading only when the summary/header is insufficient.
5. Prefer recent authoritative docs over long historical references.

Do not default to scanning all related files when a smaller authoritative subset is available.

### File-Level Summary Headers

When documents are long or frequently revisited, prefer adding a compact summary header near the top of the file. That header should help the agent decide whether to keep reading.

Recommended header fields:

- `Purpose`
- `Status`
- `Authority`
- `Scope`
- `Read this when`
- `Skip this when`
- `Key sections`
- `Last materially updated`

Use these headers to support triage. Do not use them to hide the actual active rules.
Use `assets/file-summary-header.template.md` when the user wants a standard summary-header format.

### Summary Indexes

When a project has many relevant files, you may propose a summary index that helps the agent choose which files to open next.

A good summary index should contain, for each linked file:

- file path
- document role
- a short summary
- when to read it
- whether it is authoritative, working, or historical

Keep the summary index lightweight. It should route reading, not restate whole documents.
Use `assets/summary-index.template.md` when the user wants a standard summary-index format.

### Splitting Large Files

If a file becomes too large, prefer splitting by responsibility or semantic boundary, not by arbitrary size alone.

Good split boundaries include:

- current spec vs historical reference
- design vs decision log
- audit log vs lessons learned
- active rules vs archived material

Avoid mechanical splitting such as `part1/part2/part3` unless there is no better semantic boundary.

### Compression And Summarization Boundaries

Not all files should be compressed the same way.

Usually safe to compress or summarize aggressively:

- historical debugging notes
- historical design drafts
- lessons learned collections
- old reference material
- long audit logs, as long as append-only detail is preserved somewhere

Usually not safe to replace with summary-only reading:

- current constraints/spec
- active decision records
- active design details that govern current implementation
- active plans

For those authoritative files, summaries may guide reading, but they should not replace reading the relevant authoritative sections.

### Bloat Control

For files that continuously grow, use explicit control mechanisms:

- For audit logs, keep append-only detail but add periodic checkpoint summaries so agents can read the newest checkpoint first.
- For lessons learned, deduplicate overlapping entries when the user wants cleanup.
- For decision logs, keep the final decision and rationale easy to scan near the top of each decision entry.
- For design docs, split when multiple independent subtopics start forcing unrelated readers into the same large file.

### Index Depth

Keep the index tree shallow by default.

- Prefer one level of index: one index file routing to child files.
- Only propose a second level when the first-level index itself becomes too large or the project truly contains multiple distinct governance islands.
- Avoid deep index trees unless the user explicitly wants them.

The cost of extra navigation can cancel out the token savings if the tree becomes too deep.

### Staleness And Drift Control

Progressive disclosure only works if the summaries stay aligned.

- When a document is materially updated, update the corresponding summary header or summary index entry too, or mark it as potentially stale.
- Do not present a stale summary as authoritative.
- If summary freshness is unclear and the task is important, read the authoritative section directly.

### After Compression Events

If context is compressed, summarized, or otherwise reduced during task execution, do not continue blindly from the compressed state.

- Re-check the active task, current plan, and the authoritative project context before continuing.
- Verify that no constraints, subtasks, decisions, pending actions, or user instructions were dropped or distorted by the compression.
- If any uncertainty remains after re-alignment, surface it explicitly to the user instead of silently assuming the compressed context is complete.

### Flexible Use Of Lossy Context Reduction

Lossy context reduction is allowed when the task does not require full fidelity and the user accepts a lighter context strategy.

Examples:

- reading historical notes through a summary instead of full detail
- reading a checkpoint summary before expanding into a long audit log
- routing from an index before opening full design/history files

Do not use lossy reduction as the default for current hard constraints or active project decisions.

### Practical Rule

When in doubt:

- reduce context by routing first
- preserve authority in the real source document
- expand only when the next decision actually needs more detail

## Reading Order

For complex tasks:

1. Read `docs/<project-scope>/governance/00_index_and_priority.md` first if it exists.
2. If `docs/governance/00_project_scope_registry.md` exists, use it only to identify the active project scope before reading project-scoped governance docs.
3. If the task is explicitly repository-wide, read `docs/governance/00_index_and_priority.md` instead.
4. Then read the current authoritative spec.
5. Then read only the design/audit/lessons docs needed for the task.

## Reference Map

- Read `references/governance-workflow.md` for the recommended operating model and update triggers.
- Copy or adapt templates from `assets/`, including the optional project-root `AGENTS.md` template, the optional repository-level `00_project_scope_registry.template.md`, the optional `file-summary-header.template.md`, and the optional `summary-index.template.md`.
