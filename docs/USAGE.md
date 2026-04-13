# Usage Guide

This guide explains how to use the `project-governance` skill in real projects.

## When To Use It

Use the skill when:

- a repository is large or long-running
- multiple document versions already exist
- specs and design notes conflict
- the user wants plan-first handling
- the user wants auditability
- the user wants reusable project-local governance

## Default Model

The skill defaults to project-scoped governance:

- `docs/<project-scope>/governance/`

Do not default to `docs/governance/` unless the task is explicitly repository-wide.

If a repository contains multiple long-running projects or experiments, the skill may also propose:

- `docs/governance/00_project_scope_registry.md`

That registry is routing-only. It should help identify the active project scope before reading project-specific governance docs. It must not override project spec, design, or decisions.

## Step 1. Pick A Project Scope Slug

Choose a stable slug before initializing governance docs.

Recommended format:

- lowercase letters
- digits
- hyphens

Examples:

- `experiment3`
- `exp3-bua87-formal`
- `browser-runtime-migration`

## Step 2. Decide Whether To Initialize Project-Root AGENTS

The skill can initialize both:

- project-root `AGENTS.md`
- governance docs under `docs/<project-scope>/governance/`

This is the recommended choice for new projects that want the full workflow.
If a project-root `AGENTS.md` already exists, the skill should not overwrite it silently. It should read the current file first and propose keep, merge, or explicit replace options.

## Step 3. Initialize Governance Docs

The normal order is:

1. `00_index_and_priority.md`
2. `01_constraints_and_spec.md`
3. `02_design.md`
4. `03_behavior_audit.md`
5. `04_lessons_learned.md`
6. `05_decision_log.md`
7. `06_active_plan.md` if needed

## Step 4. Use The Governance Docs During Work

### Before major or conflicting changes

- explain the conflict
- ask whether to create/update a plan
- ask whether to create/update a decision record
- only then implement

### After meaningful changes

- ask whether to update governance docs
- update audit first if approval is given
- then update spec/design/lessons/decision docs as needed

### After major changes

- do a review pass
- use a reviewer agent if available
- otherwise review manually

### If uncertainty remains

- explicitly tell the user
- name the assumptions or unclear points
- explain the impact on the result or next decision

## Step 5. Use Progressive Disclosure For Large Document Sets

If the project has many documents or very large files, do not default to reading everything in full.

Prefer this sequence:

1. read the scope/index or routing doc first
2. read file-level summary headers next
3. read only the sections needed for the current task
4. expand to full documents only when the summary is insufficient

Useful companion templates:

- `assets/file-summary-header.template.md`
- `assets/summary-index.template.md`

Recommended uses:

- add a short summary header near the top of large files
- create a summary index when many files are plausible reading candidates
- split files by semantic boundary when they grow too large
- keep current spec and active decisions authoritative in the real document, not only in the summary

Avoid using summary-only reading for:

- current constraints/spec
- active decisions
- active design rules
- active plans

## Adoption For Existing Projects

If a project already contains many docs:

1. ask whether to adopt it into the governance system
2. classify existing docs as:
   - authoritative
   - working
   - historical/reference
3. record the conflict resolution order in `00_index_and_priority.md`
4. do not mass-clean old docs unless the user asks

## Example Prompts

- `Use $project-governance to initialize project-scoped governance for slug exp3-bua87-formal.`
- `Use $project-governance to create project-root AGENTS.md and governance docs for slug browser-runtime-migration.`
- `Use $project-governance to adopt this repository's existing docs into the governance system.`
- `Use $project-governance to update the audit and decision log after today's runtime changes.`

## Common Mistakes To Avoid

- creating governance docs silently
- using unstable natural-language titles as scope directories
- treating detailed old docs as authoritative without an index
- updating governance docs without user approval
- skipping review after major changes
- hiding uncertainty in a confident-sounding final reply
- turning a repository-level routing registry into a project spec
- letting summary headers drift away from the actual document contents
- splitting files by size alone when a cleaner semantic split is available
- treating summary-only reading as a safe replacement for current authoritative rules
