# Governance Workflow

Use this reference when the `project-governance` skill must initialize or maintain a non-trivial project without becoming the project's authority source.

This file is a workflow and maintenance reference for the skill. It defines how the skill should operate around repository-local governance docs, `AGENTS.md`, and long-running execution history.

## Runtime Position

Treat this file as a lifecycle reference, not as the default runtime first-read surface.

For active runtime work:

- use `SKILL.md` as the router
- read `10_runtime_reading_protocol.md` for reading/routing decisions
- read `11_governance_execution_contract.md` for sync, review, quality, and closure decisions

Open this file when you need the broader lifecycle model, adoption logic, lane meaning, or maintenance rationale behind the runtime protocol.

## Goals

- keep repository-local docs authoritative for project truth
- give the skill a stable lifecycle and maintenance workflow
- support progressive disclosure instead of full-document loading by default
- keep sync obligations narrow and explicit
- promote durable patterns without forcing every round into a heavy governance lane

## Core Model

### Responsibility Split

- repository docs answer: what is true in this project now
- `AGENTS.md` answers: which short durable collaboration rules must stay active
- the skill answers: how to initialize, route, maintain, and recover the governance workflow

The skill must not treat itself as the authority source when repository-local written docs disagree.

Precedence remains: repository docs > applicable `AGENTS.md` > this skill.

### Governance Layers

Use five layers when the project is large enough to justify governance:

1. `authority`
   - scope, constraints, accepted design rules, accepted decisions, authority order
2. `execution`
   - current frontier, completed rounds, task history, behavior audit
3. `learning`
   - durable lessons that should change future agent behavior
4. `recovery`
   - resumable state for compression, pause, handoff, or long debugging chains
5. `probe`
   - bounded evidence-gathering work, probe artifacts, redaction, and verified boundaries

Each surface should have one primary role. Do not let recovery become a shadow spec or let execution history silently redefine authority.

## Lifecycle Overview

### 1. Initialize

Create governance docs only after the user confirms.

Default to a project-scoped governance root at `docs/<project-scope>/governance/`, with sibling `context/` and `tasks/` directories under the same `docs/<project-scope>/` scope.
Use repository-wide governance only when the user explicitly asks for a repository-wide operating model.

Initialization checklist:

- confirm the active project scope and stable slug
- inspect any existing `AGENTS.md` before proposing changes
- choose the initialization mode: `core`, `extended`, or `probe-heavy`
- create the minimum governance skeleton for that mode
- when mode-specific or optional surfaces are enabled, make sure `AGENTS.md` routes to them explicitly rather than only naming them
- record the authority order before relying on new or adopted docs

### 2. Adopt Existing Project Docs

When governance-like docs already exist:

- classify each important document by layer and authority status
- map each document as `authoritative`, `routing-only`, `working`, or `historical/reference`
- identify conflicts before using the docs as operational truth
- avoid mass rewrites during adoption
- preserve old material unless the user approves structural cleanup

### 3. Run The Round In The Correct Lane

Before a non-trivial round:

- classify the lane before editing anything
- use the narrowest lane that truthfully matches the intended output
- if more than one lane applies, upgrade to the strictest lane that covers the planned actions

Representative lanes:

- `metadata-sync`
- `docs-only`
- `review-only`
- `probe-only`
- `implementation`
- `substantial-change`
- `authority-change`
- `lesson-promotion`
- `index-split`
- `archive-or-supersede`

The skill may route to a project-local behavior matrix when one exists. If not, it should still apply the same lane logic.

Treat the hyphenated tokens above as canonical cross-repo identifiers.

If a repository defines repo-local lane spellings in a behavior matrix, task-template index, or similar governance surface, preserve the canonical meaning but switch to the repo-local spelling in user-facing output and persisted repository records.

Default canonical-to-local alias map:

- `metadata-sync` -> `metadata sync`
- `docs-only` -> `docs-only`
- `review-only` -> `review-only`
- `probe-only` -> `probe-only`
- `implementation` -> `implementation`
- `substantial-change` -> `substantial change`
- `authority-change` -> `authority change`
- `lesson-promotion` -> `lesson promotion`
- `index-split` -> `index split`
- `archive-or-supersede` -> `archive/supersede`

If lane-based repo-local task templates are active under `docs/<project-scope>/tasks/templates/*.md` but only `T0` through `T3` exist, route missing dedicated lanes explicitly:

- `metadata-sync` -> `T0-minor`
- `docs-only`, `review-only`, `probe-only`, `lesson-promotion`, `index-split`, `archive-or-supersede` -> `T1-probe-review-docs` by default
- `implementation` -> `T2-implementation`
- `substantial-change`, `authority-change` -> `T3-substantial-change`

If `lesson-promotion`, `index-split`, or `archive-or-supersede` also change accepted truth or the active authoritative source, upgrade the round to the stricter template lane instead of hiding the escalation.

The bundled source assets for those repo-local templates live under `assets/tasks/templates/*.template.md`.

If a repository only exposes a generic template such as `docs/<project-scope>/tasks/templates/task_record.template.md`, use that repo-local contract and state that lane-tiered repo-local templates are not yet enabled.

### 4. Sync Only What Changed

After a meaningful round, do not update every governance surface by habit.

Instead, ask:

1. did accepted project truth change
2. did the current frontier or blocker boundary change
3. did a durable reusable lesson emerge
4. did recovery state or routing relevance change
5. did probe evidence change the verified boundary or risk ordering

Repo-local governance may require same-round execution closure after an implementation, docs, review, or probe round. When the round is only syncing already-earned execution state and does not change authority, `AGENTS.md`, initialization/adoption state, or structural reading behavior, the skill may complete that required execution sync without a separate approval ask.

This direct execution-sync exception is limited to repo-required updates to the task record, task knowledge base, behavior audit, active plan, and atomic context-index/shard state sync.

Authority edits, `AGENTS.md` changes, initialization/adoption work, archive/supersede, index splits, and authority/routing promotion remain ask-first or explicit-notice surfaces.

Before claiming delivery complete, locate and run the repo-local quality gate for the touched surface.

- prefer an explicit source already present in the repository such as governance docs, `AGENTS.md`, an existing workflow/task contract, CI configuration, or other executable build/test entrypoints
- if the quality gate is inferred from existing repo surfaces rather than explicitly documented, say so clearly instead of presenting it as a formal repository rule

Update only the layers triggered by those answers.

### 5. Preserve Re-entry Quality

When the round ends:

- ensure routing surfaces still point to the right active material
- mark stale or superseded surfaces clearly
- preserve enough recovery state for the next agent to resume without rediscovering the same boundary
- keep the final handoff explicit about remaining uncertainty

## Initialization Modes

### Mode: `core`

Use when:

- the project is non-trivial but still early
- contributors are few
- probe work is not central

Expect at least:

- authority skeleton
- behavior audit
- task knowledge base
- task records
- context skeleton

### Mode: `extended`

Use when:

- the project is long-running
- repeated execution rounds, handoffs, or reviews are expected
- recovery and lesson promotion are likely to matter

Additional expectations:

- persistent active plan
- stronger summary-entry maintenance
- explicit lesson promotion cadence
- optional task-template tiering
- optional lightweight ID system

### Mode: `probe-heavy`

Use when:

- real-environment probes are a first-class workstream
- evidence capture, redaction, and verified failure-stage reporting are central
- read-only investigations must stay bounded and reproducible

Additional expectations:

- explicit probe contract or checklist
- runner isolation rules
- artifact and redaction handling
- stronger sync between probe rounds, active frontier, and risk boundaries

## Progressive Disclosure

### Reading Contract

Default reading behavior:

1. route first
2. verify authority second
3. expand only into the minimum relevant documents
4. stop relying on summary-only reading once the active authoritative rule or current frontier is identified

Do not begin by loading every governance file in full unless the project is tiny or the user explicitly asks for a full audit.

### Graded Index Model

Use a shallow graded index instead of a flat pile of large files:

- Grade 0: scope entrypoint and authority order
- Grade 1: layer indexes or active authority documents
- Grade 2: detailed records, shards, artifacts, or lessons

Rules:

- indexes route; they do not replace underlying authority
- Grade 0 chooses the scope and authority path
- Grade 1 routes within a layer or exposes the active contract
- Grade 2 preserves detail and evidence
- Grade 0 and Grade 1 routing templates should label their grade and routing family explicitly when practical so readers can tell which level they are using

### Summary-Entry Support

Add file-level summary-entry support when lightweight triage stops being enough.

Good candidates:

- long authority docs
- high-frequency recovery docs
- high-risk working docs
- routing-heavy documents repeatedly used during re-entry

Recommended summary-entry fields:

- purpose
- status
- authority
- scope
- read this when
- skip this when
- key sections
- last materially updated

Summary-entry support is routing-only. It must not replace the authoritative body of the document.

### AGENTS-Facing Routing Expectations

When a project enables optional governance surfaces, `AGENTS.md` should do more than list filenames.

It should explicitly route readers to:

- `07_governance_behavior_matrix.md` when lane-control, allowed write surfaces, required sync, or prohibited actions matter
- `08_probe_harness_contract.md` when the project is in `probe-heavy` mode, the round uses `probe-only`, or `tasks/artifacts/` is in play
- `09_governance_system_spec.md` when the repo has enabled a governance-system draft and the round is about governance-layer contracts, progressive-disclosure maintenance, summary-entry support, or skill-to-repo alignment
- `tasks/templates/00_task_template_index.md` when task-template tiering is active
- `04_lessons_learned.md` as the learning-layer entrypoint even when `governance/lessons/` contains leaf lesson files
- `tasks/artifacts/` only as an evidence surface after the governing contract is already known

## Index Split And Routing Maintenance

### Split Triggers

Split a routing surface when one of these becomes true:

- routing itself becomes noisy
- unrelated topics force repeated scanning by readers who need only one subset
- one file mixes authority routing, execution routing, and recovery routing in a confusing way
- status and freshness are hard to maintain in one place

Preferred split boundaries:

- by layer responsibility
- by project scope
- by active versus historical material
- by semantic topic rather than arbitrary file chunks

### Index Depth Rule

- default to one routing level
- add a second level only when the first becomes noisy or the project truly contains multiple governance islands
- avoid deeper trees unless repeated full-file scans are clearly more expensive

### Maintenance Classes

Mechanical maintenance:

- timestamps
- counts
- short routing summary refreshes after the semantic change is already explained
- link or label repair

Structural maintenance:

- archive
- supersede
- merge or split index families
- merge or split recovery shards
- promote stable conclusions into more authoritative surfaces

Mechanical maintenance may proceed without separate escalation.
Structural maintenance requires explicit user notice before or while the change is performed.

## Sync Triggers

### Authority Trigger

Update authority surfaces when:

- scope changes
- a hard constraint changes
- an accepted design rule changes
- a decision is made, replaced, or superseded
- a proposal becomes accepted policy
- a spec or design surface changed and the matching authority doc must be kept in sync in the same workstream

### Execution Trigger

Update execution surfaces when:

- a meaningful implementation, docs, review, or probe round completes
- the current frontier changes
- the blocker boundary changes
- the next package changes
- the risk ordering changes

### Recovery Trigger

Update recovery surfaces when:

- a future agent will need the state after compression, pause, or handoff
- a shard becomes superseded, stale, resolved, archived, or promoted
- a new shard changes routing relevance
- a shard became superseded or archived and the context index must reflect that state in the same round

Recovery sync must be atomic:

- shard status and context-index status change together

### Learning Trigger

Update learning surfaces when:

- the same pitfall appears multiple times
- one severe event merits a standing guardrail
- the lesson changes how future agents should read, probe, validate, or document work

### Probe Trigger

Update probe surfaces when:

- a probe round establishes a new verified boundary
- artifact or redaction status changes
- probe evidence changes the next execution frontier or risk order
- a probe-only round is upgraded because accepted truth must change

## Promotion Rules

Promote content upward when it becomes durable:

1. probe or recovery surfaces discover evidence or stable state
2. execution surfaces record the round outcome
3. learning surfaces preserve reusable patterns when warranted
4. authority surfaces change only after explicit acceptance

Do not leave accepted project truth trapped only inside:

- context shards
- task records
- probe artifacts
- proposal docs

## Staleness Rules

A routing surface is stale when:

- the linked authoritative document changed materially but the routing text did not
- a recovery shard changed state but the recovery index still presents the old state
- a detailed record was superseded but the routing path still points to the older boundary

Required handling:

- refresh the routing surface in the same round
- or mark it as potentially stale
- do not present stale routing as authority
- for high-stakes work, read the authoritative section directly rather than trusting a stale summary

## Compression And Re-entry

When context is compressed, summarized, or resumed after a pause:

- re-check the active task
- re-check the scope entrypoint and authority order
- re-check active authority and active frontier when relevant
- use recovery routing only when recent execution state matters
- surface uncertainty instead of silently assuming continuity

Do not trust remembered skill behavior over current written project instructions.

## Review And Closure Rules

Require review when:

- accepted truth changed
- architecture or governance contract changed
- structural routing maintenance was performed
- probe results are being used to justify blocker, risk, or next-step claims
- a lesson is promoted into a mandatory rule

Before closing a round:

- verify that routing surfaces are not left stale
- confirm whether authority changed or did not change
- confirm whether the active frontier changed or did not change
- review for correctness, regressions, security boundaries, missing tests, and doc drift
- surface residual risk explicitly in the closing handoff
- record residual uncertainty explicitly

## Do Not

- do not silently create a governance set
- do not silently widen a lane
- do not let summaries replace authority
- do not rewrite history without trace
- do not leave accepted truth discoverable only inside recovery or execution artifacts
- do not default every project to the heaviest mode
- do not treat timestamps alone as authority
