# Project AGENTS

This file defines project-local collaboration and governance rules for this repository.

## Scope

- These rules apply to this repository only.
- This file defines stable workflow rules, not rapidly changing project details.
- Project-specific specs, design details, audit trails, decisions, and lessons should live under `docs/<project-scope>/governance/`.

## Governance Documents

Each major or long-running project in this repository should maintain governance documents under `docs/<project-scope>/governance/`.

Default project-scoped governance document set:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/governance/01_constraints_and_spec.md`
- `docs/<project-scope>/governance/02_design.md`
- `docs/<project-scope>/governance/03_behavior_audit.md`
- `docs/<project-scope>/governance/04_lessons_learned.md`
- `docs/<project-scope>/governance/05_decision_log.md`
- Optional: `docs/<project-scope>/governance/06_active_plan.md`

Use `docs/governance/` only for repository-wide governance that is intentionally shared across multiple projects or experiments.

## Project Scope Naming

When governance docs are project-scoped, use a stable project scope slug in the path.

- Preferred format: lowercase letters, digits, and hyphens only.
- Good examples:
  - `experiment3`
  - `exp3-bua87-formal`
  - `browser-runtime-migration`
- Avoid unstable natural-language titles as directory names when a stable slug is available.
- If the correct project scope slug is unclear, ask the user before creating governance docs.

Document roles:

- `00_index_and_priority.md`: authoritative, working, historical document lists and conflict resolution order.
- `01_constraints_and_spec.md`: current requirements, hard constraints, active rules, and unified spec.
- `02_design.md`: framework, implementation details, design rationale, and design-change records.
- `03_behavior_audit.md`: append-only log of meaningful actions, edits, environment operations, and outcomes.
- `04_lessons_learned.md`: problems, root causes, solutions, reusable lessons, and follow-up cautions.
- `05_decision_log.md`: decisions, alternatives, rationale, risks, and effective timestamps.
- `06_active_plan.md`: currently approved execution plan when a plan needs to be persisted.

## Discussion Before Implementation

Do not directly implement non-trivial changes when any of the following is true:

- a spec conflict is found
- old documents conflict with current implementation
- design scope, constraints, or project rules would change
- governance documents need to be created, merged, downgraded, or updated
- runtime, evaluation, environment, data-flow, or workflow behavior would change
- a historical decision would be overridden

In these cases:

- first explain the conflict or pending change clearly
- then ask the user whether to create or update a plan and/or governance documents
- only implement after the user confirms the direction

## Documentation Update Policy

Do not silently create or update governance documents.

After meaningful code, config, workflow, requirement, or design changes:

- explicitly ask whether to update `spec`, `design`, `audit`, `lessons learned`, and `decision log`
- if the user requires auditability, keep `03_behavior_audit.md` updated for each meaningful action
- if a change overrides an older conclusion, record that override explicitly in the relevant governance document

If governance documents do not exist yet and the task is large, long-running, or conflict-prone:

- explicitly ask the user whether to initialize the governance document set before proceeding
- explicitly confirm the active project scope slug before creating project-scoped governance docs
- do not silently create the governance document set

## Priority And Conflict Resolution

- If `docs/<project-scope>/governance/00_index_and_priority.md` exists for the active project, use its priority order instead of guessing from timestamps alone.
- If the task is explicitly repository-wide and `docs/governance/00_index_and_priority.md` exists, use that repository-level priority order.
- If governance docs are missing and the task is large, long-running, or conflict-prone, recommend initializing the governance doc set before relying on scattered files.
- Do not treat old files as authoritative just because they are detailed.

## Auditability

For meaningful implementation, environment, or documentation actions, record:

- background
- purpose
- change content
- scope
- result
- timestamp
- lessons if applicable

Prefer append-only audit logs for traceability.

## Review After Major Changes

After major code changes or other major project changes:

- perform a review pass before considering the work complete
- focus the review on correctness, regressions, missing updates, and unresolved conflicts
- if subagents or reviewer agents are available, use a review-focused agent for an independent review pass when appropriate
- if no reviewer agent is available, perform the review manually and report any residual risks

## Uncertainty Disclosure

If implementation proceeds despite non-trivial uncertainty:

- do not hide the uncertainty in the final reply
- explicitly tell the user which assumptions, unclear points, or partially verified areas remain
- explain how those uncertainties may affect the result or the next decision
- surface this even if the implementation was completed successfully

## Context Hygiene

Before starting a complex task:

- determine the active project scope first
- read `docs/<project-scope>/governance/00_index_and_priority.md` first if it exists
- then read the current authoritative spec
- check whether an index/priority doc exists
- identify conflicts before proposing or making changes

If no priority/index doc exists for a large project, recommend creating one before trusting scattered historical files.

## Skill Usage

If a project-governance skill exists in this environment, use it when the user asks to:

- initialize governance docs
- reconcile conflicting project docs
- create or update spec/design/audit/lessons/decision docs
- establish a plan-first workflow for a large project

If such a skill is not yet installed, follow the same workflow manually and say so briefly.
