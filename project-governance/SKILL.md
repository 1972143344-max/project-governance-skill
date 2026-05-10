---
name: project-governance
description: Initialize and maintain project-scoped governance documents for large or long-running work. Use when the user wants a documentation-driven workflow, needs to prevent context drift or stale-file interference, wants spec/design/audit/lessons/decision docs, or wants plan-first handling before non-trivial changes.
---

# Project Governance

Use this skill to operate a project-scoped governance system without letting the skill itself become repository truth.

Default to `docs/<project-scope>/governance/` with sibling `context/` and `tasks/` directories under the same `docs/<project-scope>/` scope. Use repository-wide `docs/governance/` only when the user explicitly wants one governance layer shared across multiple projects or experiments.

## G0. Front Door

### Use This Skill When

- the user asks to initialize, adopt, re-enter, or maintain governance docs
- the repo has stale notes, conflicting design records, or unclear authority order
- the task needs spec/design/decision/task-record governance before non-trivial changes
- structural document maintenance could change what future agents read first
- recovery or context state may matter after compression, handoff, or pause

### Do Not Use This Skill When

- the task is a small code or docs change with no governance-sensitive surface
- the work only needs ordinary repo reading and does not involve governance maintenance
- the user wants implementation only and no governance workflow is active

### Skill Boundary And Precedence

This skill is a workflow surface, not a repository-truth source.

Treat these layers as distinct:

- repository docs answer what is true here now
- applicable `AGENTS.md` files answer what durable collaboration rules remain active here
- this skill answers how to operate the governance workflow

Precedence remains:

1. direct user instruction
2. written repository authority docs
3. applicable `AGENTS.md`
4. this skill

Do not let the skill silently absorb repository authority.

### Re-entry Trigger

Re-open this main `SKILL.md` when:

- governance initialization or adoption is about to happen
- structural maintenance may change future reading behavior
- context was compressed, summarized, or handed off
- written repo docs, `AGENTS.md`, and remembered workflow may have drifted apart
- conclusions may need promotion from recovery or execution into authority or learning

### First Step After Trigger

Once this skill is adopted as the governing workflow for the current action:

1. read this main `SKILL.md`
2. identify the current governance-sensitive action
3. route into only the protocol or sidecar file needed for that action, if any

Do not jump straight into low-frequency initialization or method-reference material unless the current action actually needs it.

## G1. Runtime Routing

This main file is a runtime router and boundary surface.

Use it to determine which deeper protocol or sidecar must be read next.

Do not treat this main file as a substitute for `10_runtime_reading_protocol.md` or `11_governance_execution_contract.md` when their trigger conditions are met.

### Read `10_runtime_reading_protocol.md`

Read `10_runtime_reading_protocol.md` when the current round involves:

- non-trivial repo work
- authority, task, or context routing
- deciding between route-first, probing, section expansion, or full-read
- review, planning, implementation, or governance maintenance that depends on document-reading quality

Skip `10_runtime_reading_protocol.md` when the round is:

- pure chat
- light brainstorming with no repo-document lookup
- casual explanation that does not depend on repository routing or authority adjudication

### Read `11_governance_execution_contract.md`

Read `11_governance_execution_contract.md` when the current round involves:

- task-record creation or update
- behavior-audit, active-plan, or context-index sync
- governance sync, routing changes, archive/supersede, or authority-affecting maintenance
- delivery completion, quality-gate judgment, review adjudication, or closure docs

Skip `11_governance_execution_contract.md` when the round is:

- pure chat
- exploratory reading with no governance sync or closure judgment
- implementation work that has not yet entered sync, review, or completion handling

### Read Low-Frequency Sidecars

Route to these sidecars only when the current action needs them:

- `initialization-and-adoption.md` for governance initialization or adoption
- `governance-surface-catalog.md` for full governance document-set or template routing
- `lane-reference.md` for full lane taxonomy or repo-local aliasing
- `recovery-method-reference.md` for recovery-method design or restructuring
- `index-summary-reference.md` for index, summary-header, or split-design work

### Main-File-Only Cases

This main file alone is usually enough only when the current action is:

- high-level governance workflow orientation
- deciding which deeper protocol or sidecar must be read next
- confirming precedence, truth boundary, or runtime action family before deeper routing

### Stable Entrypoints And Default Split Rule

- Treat `00_index_and_priority.md`, `00_context_index.md`, `00_task_knowledge_base.md`, `10_runtime_reading_protocol.md`, and `11_governance_execution_contract.md` as stable entrypoint surfaces by default.
- If one of those entrypoints grows too large, keep the entrypoint as the shallow read-first surface and split below it with second-level routing by semantic topic, layer, subsystem, or active-versus-historical boundary rather than renaming the entrypoint itself.

## G2. Runtime Governance Model

Use a small runtime model rather than carrying the full governance taxonomy in the main file.

### Runtime Layers

- `authority`: active truth, authority order, current constraints, accepted design rules, accepted decisions
- `execution`: current frontier, completed rounds, audits, task records, active plan
- `learning`: reusable guardrails promoted from repeated evidence
- `recovery`: effective working state needed after compression, pause, or handoff
- `probe`: bounded runtime evidence that must not silently redefine authority

### High-Frequency Runtime Actions

Keep only the high-frequency action families in this main file:

- `execution-sync`
- `structural-maintenance`
- `promotion`
- `docs-only`
- `review-only`
- `probe-only`

Use those labels as quick runtime classifiers only. Read the lane reference sidecar when you need the full lane system, template routing, aliases, or edge-case handling.

## G3. Structural Change Control

This block governs changes that alter future reading behavior.

### Ask-First

Ask before:

- initializing governance docs
- adopting an existing project into a new governance layout
- creating or replacing project-root `AGENTS.md`
- changing authority order
- merging, splitting, superseding, or archiving governance surfaces in ways that change what future agents read first

### Notify-First

Tell the user explicitly before or while performing:

- archive or supersede actions
- routing or index reorganization
- promotion of stable conclusions into more authoritative documents
- changes that materially reorganize recovery or context routing

### Hard Boundary

Repeat this rule wherever structural maintenance and context maintenance meet:

- do not silently change what future agents will read first

This includes archive, supersede, routing promotion, index reorganization, and recovery-layer restructuring.

For detailed same-round sync handling, update/notify execution rules, and closure-state sync, read `11_governance_execution_contract.md`.

## G4. Sync And Promotion

This block defines when runtime governance surfaces should move.

### Authority Sync Trigger

Update authority docs when:

- scope changes
- a hard constraint changes
- an accepted design rule changes
- a decision is made, replaced, or superseded
- a proposal becomes accepted policy

### Execution Sync Trigger

Update execution docs when:

- a meaningful implementation, review, docs, or probe round completes
- the current frontier changes
- the blocker boundary changes
- the next package changes
- the risk ordering changes

### Recovery Sync Trigger

Update recovery docs when:

- a future agent would need the state after compression, pause, or handoff
- a shard becomes superseded, stale, resolved, archived, or promoted
- a new shard changes routing relevance

Treat shard update plus `00_context_index.md` update as one atomic documentation action.

### Active Plan Rule

Treat `06_active_plan.md` as a frontier document, not a second spec.

Update it only when one of these changed materially:

- current frontier
- next package
- blocker boundary
- risk ordering
- priority order

### Promotion Rule

Promote content upward when it becomes durable:

- from probe artifacts to execution records when a round conclusion must be preserved
- from execution or recovery to learning when the lesson is stable and reusable
- from recovery, execution, or proposal docs to authority only after explicit acceptance

Do not leave accepted project truth trapped only in:

- recovery shards
- task records
- proposal docs

### Closure Binding Rule

Repeat this rule here and in closure:

- final completed-state documentation must not be written as a substitute for real closure readiness

For detailed task-record handling, file-level sync heuristics, and completion-state execution rules, read `11_governance_execution_contract.md`.

## G5. Recovery / Context Runtime

Treat `docs/<project-scope>/context/` as the concrete recovery surface unless the repository explicitly defines a different one.

### Runtime Routing

When recovery state matters:

1. read `00_context_index.md` first
2. filter out archived and superseded shards by default
3. read only the minimum relevant shards, usually `1-3`

### Runtime Truth Boundary

Repeat this rule here and in the reading protocol:

- governance docs are authoritative
- context is working or reference
- if governance and context disagree, governance wins

### Atomic Context Sync

Keep shard state and context-index state synchronized in the same update round.

Do not:

- archive a shard without updating the index
- supersede a shard without updating the index
- promote shard content without updating the index
- restructure recovery routing without updating the index

### Recovery Exclusion Rule

Do not leave durable authority trapped in context-only form forever.

Promote stable constraints, accepted decisions, design rules, and reusable lessons upward when they become durable.

### Structural Maintenance Binding Rule

Repeat this rule here and in structural change control:

- do not silently change what future agents will read first

## G6. Closure

Do not treat governance sync alone as proof that the round is complete.

### Review Requirement

After major changes, require a review pass before considering the work complete.

If reviewer agents are available, prefer an independent review pass.

### Closure Readiness

Closure is ready only when:

- the execution or docs round is actually complete
- required review has happened
- required quality gates have passed, if any
- remaining uncertainty or residual risk has been surfaced honestly

### Final Sync Rule

Repeat this rule here and in sync/promotion:

- final completed-state documentation must not be written as a substitute for real closure readiness

For detailed quality-gate, review, closure, and completed-state sync rules, read `11_governance_execution_contract.md`.

## G7. Sidecar Routing

Read these protocol and sidecar files only when the current action needs them.

### `10_runtime_reading_protocol.md`

- Position: `high-frequency support protocol`
- Description: full route-first, probing, governing-expansion, and stop-rule contract for non-trivial repository reading
- Read when:
  - non-trivial repo work depends on document-reading quality
  - authority, task, or context routing matters
  - you must decide between route-first, probing, section expansion, or full-read
- Skip when:
  - the round is pure chat
  - no repository routing or authority adjudication is involved

### `11_governance_execution_contract.md`

- Position: `high-frequency support contract`
- Description: detailed task-record, sync, update/notify, quality, review, closure, and completed-state execution rules
- Read when:
  - the round enters task-record creation or update
  - governance sync, archive/supersede, review, quality-gate, or closure adjudication matters
- Skip when:
  - the round has not entered sync, review, or closure handling
  - no governance execution decision is being made

### `initialization-and-adoption.md`

- Position: `low-frequency workflow sidecar`
- Description: initialization modes, adoption sequence, and first-round governance setup outcomes
- Read when:
  - governance docs do not exist yet
  - you are adopting an existing project into the governance system
  - you need initialization modes, initialization outcome, or adoption sequence
- Skip when:
  - governance is already established and you are not changing its foundation

### `governance-surface-catalog.md`

- Position: `low-frequency routing sidecar`
- Description: full governance document-set map, optional surfaces, and template or asset routing
- Read when:
  - you need the full governance document set
  - you need optional governance surfaces
  - you need template or asset routing
- Skip when:
  - the current action already has a known protocol or sidecar target

### `lane-reference.md`

- Position: `low-frequency taxonomy sidecar`
- Description: full lane system, lane-selection order, lane rules, and template-routing upgrades
- Read when:
  - the runtime action family in `G2` is not enough
  - you need the full lane taxonomy
  - you need repo-local aliasing or template routing
  - you need edge-case lane handling
- Skip when:
  - the action family already determines the next step without lane detail

### `recovery-method-reference.md`

- Position: `low-frequency method sidecar`
- Description: detailed recovery-write triggers, recovery exclusions, shard sizing, and recovery hygiene rules
- Read when:
  - you are designing or restructuring recovery behavior
  - you need detailed recovery write triggers, exclusions, capacity, or pollution control
- Skip when:
  - you only need ordinary recovery routing through `00_context_index.md`

### `index-summary-reference.md`

- Position: `low-frequency design sidecar`
- Description: graded index model, summary-header guidance, split rules, and routing-drift control
- Read when:
  - you are designing or restructuring indexes
  - you need summary-header rules, split rules, drift control, or bloat control
- Skip when:
  - no routing-surface or summary-entry design work is being done
