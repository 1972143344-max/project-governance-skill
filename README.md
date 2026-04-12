# Project Governance Skill

A reusable Codex skill for setting up and maintaining project-scoped governance documents for large or long-running work.

This skill helps prevent:

- context drift
- stale-file interference
- conflicting specs and design notes
- silent rule changes
- missing audit trails
- unclear decisions after implementation

It is designed for projects where the agent and the user need a stable documentation-driven workflow instead of relying on fragile conversational context alone.

## What This Skill Does

The skill standardizes a governance layer under:

- `docs/<project-scope>/governance/`

It guides the agent to create and maintain:

- `00_index_and_priority.md`
- `01_constraints_and_spec.md`
- `02_design.md`
- `03_behavior_audit.md`
- `04_lessons_learned.md`
- `05_decision_log.md`
- optional `06_active_plan.md`

It also includes a reusable project-root `AGENTS.md` template so a new repository can adopt the same collaboration rules without copying rules by hand from an older project.

## Why This Exists

Large projects often accumulate:

- multiple design versions
- stale notes
- old experimental artifacts
- inconsistent assumptions across turns
- undocumented constraint changes

When that happens, the agent can start reading the wrong files, inheriting obsolete rules, or making changes under unresolved uncertainty.

This skill introduces a repeatable structure for:

- deciding what is authoritative
- recording what changed
- preserving decision rationale
- forcing plan-first handling when conflicts appear
- surfacing uncertainty instead of hiding it
- requiring review after major changes

## Repository Layout

```text
project-governance/
  SKILL.md
  agents/openai.yaml
  assets/
    00_index_and_priority.template.md
    01_constraints_and_spec.template.md
    02_design.template.md
    03_behavior_audit.template.md
    04_lessons_learned.template.md
    05_decision_log.template.md
    06_active_plan.template.md
    project-root-AGENTS.template.md
  references/
    governance-workflow.md
```

## Core Design Principles

- Project-scoped by default: governance docs should normally live under `docs/<project-scope>/governance/`.
- Repository-wide only by exception: use `docs/governance/` only when one governance layer is intentionally shared across multiple projects or experiments.
- Stable slugs: use a stable `<project-scope>` slug, preferably lowercase letters, digits, and hyphens.
- Ask first: the skill is intentionally conservative. It should not silently create or silently update governance docs.
- No silent `AGENTS.md` replacement: if a project-root `AGENTS.md` already exists, the skill should review it and propose merge options instead of overwriting it.
- Ask instead of inferring: if governance initialization, adoption, classification, or document authority is unclear, the skill should ask the user explicitly.
- Plan before implementation: if a meaningful conflict or design change appears, discuss and confirm direction first.
- Review after major changes: substantial changes should receive a review pass before the task is considered complete.
- Disclose uncertainty: if implementation proceeds under non-trivial uncertainty, that uncertainty must be surfaced to the user explicitly.

## What Problems It Solves

### 1. Version confusion

Different documents often disagree about the current implementation. The index-and-priority document gives the project one explicit conflict-resolution order.

### 2. Silent drift in requirements

Constraints and requirements often change during interactive work. The constraints/spec document keeps the current active rules visible and separate from the design details.

### 3. No trace of what changed

The behavior audit provides an append-only record of meaningful actions so later runs can reconstruct what happened.

### 4. Design decisions get lost

The decision log stores alternatives, rationale, risks, and superseded choices instead of leaving them buried in chat history.

### 5. Repeated mistakes

The lessons-learned document turns resolved issues into reusable operating knowledge for future work.

## Installation

### Option 1. Install as a local project skill

Copy the `project-governance/` directory into:

- `.agents/skills/project-governance/`

within the target repository.

### Option 2. Install as a global Codex skill

Copy the `project-governance/` directory into:

- `~/.codex/skills/project-governance/`

Then restart Codex so the new skill is loaded.

## How To Use

See [docs/USAGE.md](docs/USAGE.md) for a step-by-step usage guide.

Typical prompts:

- `Use $project-governance to initialize governance docs for this project.`
- `Use $project-governance to adopt this existing project into the governance system.`
- `Use $project-governance to update the spec, design, and audit docs after these changes.`
- `Use $project-governance to set up project-root AGENTS.md and governance docs for a new experiment.`

## Recommended Workflow

1. Confirm the active project scope and choose a stable slug.
2. Decide whether the governance should be project-scoped or repository-wide.
3. Ask whether to initialize project-root `AGENTS.md`.
4. Create `00_index_and_priority.md` first.
5. Create the remaining governance docs from templates.
6. During project work:
   - discuss before major or conflicting changes
   - update governance docs only with user approval
   - keep the audit log append-only
   - review major changes
   - disclose uncertainty in the closing reply

## Included Templates

- `00_index_and_priority.template.md`
  - defines authoritative, working, and historical docs
  - defines read order and conflict resolution order
- `01_constraints_and_spec.template.md`
  - captures current requirements, constraints, and active rules
- `02_design.template.md`
  - records framework, rationale, and design changes
- `03_behavior_audit.template.md`
  - append-only audit of meaningful actions
- `04_lessons_learned.template.md`
  - reusable lessons from solved problems
- `05_decision_log.template.md`
  - alternatives, choices, rationale, risks, superseded decisions
- `06_active_plan.template.md`
  - optional persisted plan when the user wants one
- `project-root-AGENTS.template.md`
  - reusable project-local collaboration rules for repositories that want this governance model

## Safety And Privacy

This repository is intended to be safe to publish publicly.

The included skill and templates should not contain:

- local machine paths
- personal usernames
- emails
- API keys
- tokens
- project-private secrets

Before publishing, still review the repo contents in case local modifications introduced sensitive content.

## License

This repository currently ships with the `MIT` license.
