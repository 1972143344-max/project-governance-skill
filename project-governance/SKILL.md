---
name: project-governance
description: Initialize and maintain project-scoped governance documents for large or long-running work. Use when the user wants a documentation-driven workflow, needs to prevent context drift or stale-file interference, wants spec/design/audit/lessons/decision docs, or wants plan-first handling before non-trivial changes.
---

# Project Governance

Create and maintain a stable governance layer for large or long-running projects so implementation stays aligned with current rules instead of drifting across conflicting files.

Default to project-scoped governance under `docs/<project-scope>/governance/`. Only use `docs/governance/` when the user explicitly wants repository-wide governance shared across multiple projects or experiments.

Use a stable scope slug for `<project-scope>`, preferably lowercase letters, digits, and hyphens only.

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
- When governance initialization, adoption, classification, or document authority is unclear, ask the user explicitly instead of inferring.
- If a conflict changes project direction, propose a plan and, when useful, a decision log entry before implementation.
- Prefer stable governance under `docs/<project-scope>/governance/` and keep `AGENTS.md` limited to durable collaboration rules.
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

Use the templates in `assets/` when creating them.
If the user wants project-local collaboration rules initialized too, also use `assets/project-root-AGENTS.template.md` to create a project-root `AGENTS.md`.

## Workflow

### 1. Initialization

If governance docs do not exist:

1. Ask whether to initialize the governance doc set.
2. Ask for the active project or experiment scope and a stable slug if it is not already clear.
3. Default the doc root to `docs/<project-scope>/governance/`.
4. Use `docs/governance/` only if the user explicitly wants repository-wide governance.
5. Ask whether to initialize a project-root `AGENTS.md` from the template if one does not already exist.
6. If a project-root `AGENTS.md` already exists, do not overwrite it. Read it first and ask whether to keep it, merge governance rules into it, or replace it explicitly.
7. Create `00_index_and_priority.md` first.
8. Then create the remaining requested docs from templates.
9. Do not populate project-specific conclusions unless the user asks for adoption or migration.

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

## Reading Order

For complex tasks:

1. Read `docs/<project-scope>/governance/00_index_and_priority.md` first if it exists.
2. If the task is explicitly repository-wide, read `docs/governance/00_index_and_priority.md` instead.
3. Then read the current authoritative spec.
4. Then read only the design/audit/lessons docs needed for the task.

## Reference Map

- Read `references/governance-workflow.md` for the recommended operating model and update triggers.
- Copy or adapt templates from `assets/`, including the optional project-root `AGENTS.md` template.
