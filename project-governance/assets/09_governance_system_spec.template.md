# Governance System Spec

Updated: YYYY-MM-DD HH:MM:SS
Status: draft
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: working
Layer: mixed

## Maintenance Threshold

Document role: `support-protocol`
Advisory threshold: `220 lines`
Split threshold: `320 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this protocol document should be split into routed companion docs rather than continue growing as one file.
Even below the split threshold, surface the same recommendation if readers usually need only one semantic subset at a time.
Do not silently restructure this document during unrelated work.

## Purpose

This document defines the governance-system model for the project so the repository, `AGENTS.md`, and the `project-governance` skill can stay aligned.

This template defaults to a draft working specification. It does not become authoritative just because it exists. Promote it only when the project explicitly accepts the model and updates both routing and header status in the same round.

## Design Goals

- preserve repo-doc authority over skill memory
- separate authority, execution, learning, recovery, and probe responsibilities
- keep progressive disclosure explicit
- keep everyday execution light while keeping truth and evidence strict
- make initialization and maintenance reusable across new projects

## Non-Goals

- This spec does not make the skill authoritative over repository-local docs.
- This spec does not require every project to enable every governance surface.
- This spec does not force heavy documentation for trivial rounds.

## Governance Layers

### Authority Layer

Purpose:

- define current project truth, accepted defaults, and conflict resolution order

Typical surfaces:

- `00_index_and_priority.md`
- `01_constraints_and_spec.md`
- `02_design.md`
- `05_decision_log.md`

### Execution Layer

Purpose:

- record the current frontier, completed rounds, and searchable task history

Typical surfaces:

- `03_behavior_audit.md`
- `06_active_plan.md`
- `tasks/00_task_knowledge_base.md`
- `tasks/records/TASK-*.md`

### Learning Layer

Purpose:

- preserve reusable cross-round lessons that should alter future behavior

Typical surfaces:

- `04_lessons_learned.md`
- `governance/lessons/LES-*.md`

### Recovery Layer

Purpose:

- preserve resumable working state across compression, pause, or handoff

Typical surfaces:

- `context/00_context_index.md`
- `context/01_context_usage_and_policy.md`
- `context/shards/*.md`

### Probe Layer

Purpose:

- formalize bounded evidence-gathering work

Typical surfaces:

- `08_probe_harness_contract.md`
- task-record probe sections
- `tasks/artifacts/`

## Progressive Disclosure And Index System

### Reading Contract

1. Route first.
2. Verify authority second.
3. Expand only into the minimum relevant documents.
4. Stop relying on summary-only reading once the relevant authority or active frontier is identified.

### Graded Index Model

- Grade 0: scope entrypoint
- Grade 1: layer indexes or active authority surfaces
- Grade 2: detailed records and evidence

Rules:

- indexes route; they do not replace underlying authority
- keep the tree shallow
- add summary-entry support when lightweight triage stops being sufficient

### Summary-Entry Support

Recommended header fields:

- purpose
- status
- document role
- layer
- scope
- authority source
- read this when
- skip this when
- key sections
- last materially updated

### Index Split Rules

Split an index only when routing itself becomes noisy, topics diverge, or freshness becomes hard to maintain.

Preferred split boundaries:

- by layer
- by scope
- by active versus historical
- by semantic topic

## Modes

### `core`

Minimum surfaces:

- authority set
- execution set
- recovery skeleton

### `extended`

Adds:

- persistent active-plan support when the project uses a live frontier document
- lessons layer
- stronger summary-entry support
- richer routing

### `probe-heavy`

Adds:

- probe harness contract
- evidence-oriented task templates
- artifact and review conventions

## Responsibility Boundaries

### Repository Docs

- define current project truth and active operating surfaces

### `AGENTS.md`

- define durable repository-local guardrails and reading-order rules

### `project-governance` Skill

- initialize the chosen governance skeleton
- provide workflow guidance for routing, maintenance, and template selection
- never override repository-local truth

## Sync Triggers

Update authority docs only when accepted truth changes.

Update execution surfaces when:

- a round completes
- the frontier changes
- risk order changes
- new searchable task history is added

Update learning surfaces when:

- a stable repeated or severe pattern is promoted

Update recovery surfaces when:

- resumable working state changes
- shard status changes

Update routing and summary surfaces when:

- a target document changes materially
- document role changes
- split, archive, supersede, or promotion changes the future reading path

## Acceptance Scenarios

- initialize a new project in `core`
- initialize a new project in `extended`
- initialize a new project in `probe-heavy`
- resume after compression or handoff
- complete a docs-only round without over-syncing
- complete a probe-only round without drifting into implementation
- detect and mark a stale summary or stale route
- decide to split an index only when routing noise justifies it
