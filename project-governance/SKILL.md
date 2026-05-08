---
name: project-governance
description: Initialize and maintain project-scoped governance documents for large or long-running work. Use when the user wants a documentation-driven workflow, needs to prevent context drift or stale-file interference, wants spec/design/audit/lessons/decision docs, or wants plan-first handling before non-trivial changes.
---

# Project Governance

Use this skill to initialize, adopt, maintain, and re-enter a project-scoped governance system without letting the skill itself become project authority.

Default to a project-scoped governance root at `docs/<project-scope>/governance/`, with sibling `context/` and `tasks/` directories under the same `docs/<project-scope>/` scope. Only use `docs/governance/` when the user explicitly wants repository-wide governance shared across multiple projects or experiments.

Use a stable scope slug for `<project-scope>`, preferably lowercase letters, digits, and hyphens only.

Repository-level routing is optional and must not override project-scoped governance. If a repository contains multiple long-running projects or experiments, you may propose a routing-only registry at `docs/governance/00_project_scope_registry.md` to help identify the active project scope before reading any project-scoped governance docs.

## Use This Skill When

- the user asks to initialize governance docs
- the project has multiple versions, stale files, or conflicting design notes
- the user asks for spec, design, audit, lessons learned, task records, or decision records
- the user wants plan-first handling before significant changes
- the current implementation and existing documents appear to conflict
- the repo needs a stable reading and maintenance protocol for long-running agent work

## Skill Boundary

This skill is a reusable workflow surface, not a repository-truth source.

Treat the three layers below as distinct:

- repository docs answer: what is true here now
- `AGENTS.md` answers: what durable collaboration and re-entry rules must remain active here
- this skill answers: how to initialize and operate the governance workflow

Do not let the skill silently absorb repository authority.

If written repository docs, applicable `AGENTS.md`, and remembered skill behavior disagree:

1. follow the written repository authority docs first
2. follow applicable `AGENTS.md` rules next
3. use this skill only as the workflow method

Precedence remains: repository docs > applicable `AGENTS.md` > this skill.

The skill may propose or help maintain governance surfaces. It must not claim that using the skill alone changes project truth.

## Operating Model

Use a layered governance model.

- authority layer
  - defines project truth, authority order, active constraints, accepted design rules, and accepted decisions
- execution layer
  - records completed rounds, current frontier, task history, and behavior audit
- learning layer
  - preserves reusable lessons that should affect future agent behavior
- recovery layer
  - preserves working state needed after compression, pause, or handoff without becoming a shadow spec
- probe layer
  - preserves bounded evidence-gathering and runtime investigation rules without pretending probe work is production truth by default

Default responsibility split:

- authority docs change only when project truth changes
- execution docs change when work moves
- learning docs change when a reusable pattern becomes durable
- recovery docs change when future re-entry would otherwise be costly or unsafe
- probe surfaces change when evidence must be preserved with explicit scope and truth boundary

Terminology bridge:

- use `recovery layer` for the functional role: preserving effective execution state across compression, pause, handoff, and long-running work
- use `docs/<project-scope>/context/` for the concrete project-scoped document surface that usually implements that role in current repos
- if a repository uses a different concrete layout, follow the repository-local docs, but keep the same functional distinction between the role and the storage surface

## Quick Re-entry Rules

Use this section when re-entering after context growth, compression, summarization, handoff, or suspected drift.

This section is a re-entry aid, not a replacement for the full skill.
It is also not the default first stop for every task: use `AGENTS.md` and current project docs first, then use this section when deeper governance guidance is actually needed.

### Re-entry Trigger

Re-open the relevant parts of this skill when:

- governance initialization or adoption is about to happen
- maintenance may change future reading behavior
- context was compressed, summarized, or handed off
- repository docs, `AGENTS.md`, and remembered workflow may have drifted apart
- a stable conclusion may need promotion from recovery or execution into authority or learning

Do not rely on earlier memory of this skill alone in those cases.

### Re-entry Scope

Do not re-read the entire skill by default.

Read only the sections relevant to the current action, for example:

- initialization and adoption workflow
- authority boundary and reading order
- recovery or `context/` write triggers and exclusions
- context hygiene and index synchronization
- user-notification rules for key maintenance actions

Expand into the rest of the skill only when the current task is broad enough that a partial read would be unsafe.

### Persistent Governance Contract

This skill works together with `AGENTS.md`:

- `AGENTS.md` holds persistent short rules that should remain active even after compression
- this `SKILL.md` holds the complete workflow, detailed method, and template guidance
- when a governance-sensitive task is triggered, follow both
- if `AGENTS.md` and remembered skill behavior feel inconsistent, re-read the relevant skill sections and use the written documents, not memory

### Minimum Re-alignment Checklist

Before acting on a governance-sensitive task after re-entry, verify:

1. the active project scope
2. the authoritative governance entry point
3. the current authoritative spec
4. whether accepted decisions or active plan matter
5. whether recent execution state requires consulting the project-scoped recovery or context layer
6. whether any shard state, index state, or remembered workflow may be stale
7. whether any routing surface may be stale

If uncertainty remains after this check, surface it explicitly to the user.

### Context-Layer Re-entry Rules

When the current task touches `docs/<project-scope>/context/`, treat it as the concrete recovery surface unless the repository explicitly defines a different recovery layout:

- treat `governance/` as authoritative and `context/` as working or reference only
- use `00_context_index.md` for routing before opening shards
- default to the minimum relevant `1-3` shards
- skip `archived` and `superseded` shards unless history is explicitly needed
- keep shard state and index state synchronized in the same update round
- do not leave durable rules in context-only form forever
- promote stable constraints, decisions, design rules, and reusable lessons into governance docs when they become durable

### Practical Re-entry Rule

When in doubt:

- route first
- verify authority second
- expand only into the minimum relevant documents and sections
- prefer written project docs over remembered workflow
- surface uncertainty rather than silently assuming continuity

## Core Rules

- Do not silently create governance docs. Ask first.
- Do not treat every post-round governance update as ask-first. When repo-local governance requires same-round execution-layer closure and the round is only syncing already-earned execution state, you may complete that required execution sync without a separate approval ask.
- This direct execution-sync exception is limited to repo-required updates to the task record, task knowledge base, behavior audit, active plan, and atomic context-index/shard state sync.
- Do not use that exception for authority docs, `AGENTS.md`, governance initialization or adoption, or structural reading-behavior changes such as archive/supersede, index splits, or authority/routing promotion. Those remain ask-first or explicit-notice work.
- Do not silently create or materially expand a project-scoped recovery layer outside the governance workflow the user approved.
- Do not silently downgrade, merge, archive, supersede, or reinterpret old documents. Ask first or notify explicitly when the user already approved structural maintenance in the round.
- Do not silently archive, downgrade, supersede, merge, or promote project-scoped recovery or context in ways that change what future agents will read first. Explicitly tell the user unless the change is a clearly mechanical small sync with no semantic effect.
- Never overwrite an existing `AGENTS.md` without explicit user approval. If one already exists, read it first and propose a merge plan instead of replacing it.
- When governance initialization, adoption, classification, document authority, or material document content is unclear, ask the user explicitly instead of inferring.
- If a conflict changes project direction, propose a plan and, when useful, a decision-log entry before implementation.
- Prefer stable governance under `docs/<project-scope>/governance/` and keep `AGENTS.md` limited to durable collaboration rules.
- Initialize the project-scoped recovery skeleton together with governance initialization so agents can rely on a stable recovery layer from the start.
- Treat `docs/<project-scope>/governance/` as authoritative and `docs/<project-scope>/context/` as working or reference only.
- Do not create repository-level routing docs by default. Only propose `docs/governance/00_project_scope_registry.md` when multiple project scopes already exist, scope selection is repeatedly ambiguous, or the user explicitly wants repository-level routing.
- If `docs/governance/00_project_scope_registry.md` exists, treat it as routing-only. It must not define project spec, design, decision authority, or project-specific overrides.
- Repository-level routing docs must not override `docs/<project-scope>/governance/`.
- Before claiming delivery complete, locate and run the repo-local quality gate required for the touched surface.
- Prefer an explicit repo-local quality-gate source such as authoritative governance docs, applicable `AGENTS.md`, an existing task or workflow contract, CI configuration, or other executable build/test entrypoints already present in the repository.
- If no explicit repo-local quality-gate source exists, say that the quality gate is inferred from the repository's existing execution surfaces instead of presenting it as a formally declared rule.
- After major changes, require a review pass before considering the work complete.
- If reviewer agents are available, prefer an independent review pass for major changes.
- If implementation proceeds despite non-trivial uncertainty, explicitly disclose the remaining assumptions or unclear points to the user in the closing reply.

## Initialization Modes

Support three initialization modes. Choose the lightest mode that truthfully fits the project.

### Mode: `core`

Use when:

- the project is non-trivial but still early
- one or two contributors are active
- probe work is not yet central

Minimum expectations:

- authority layer
- behavior audit
- task knowledge base
- task records
- recovery skeleton with minimal shard use
- active plan only when a real multi-step frontier exists

### Mode: `extended`

Use when:

- the project is long-running
- multiple execution rounds are expected
- design drift, handoff, or repeated reviews are likely

Additional expectations:

- persistent active plan
- regular recovery shards
- stronger summary-entry maintenance
- explicit lesson-promotion cadence
- optional template tiering and lightweight ID system when the repo wants them

### Mode: `probe-heavy`

Use when:

- real-environment probes are a first-class workstream
- evidence capture, redaction, and failure-stage reporting are central
- the project often runs read-only investigations or live-environment characterization

Additional expectations:

- explicit probe contract or probe checklist
- runner-isolation rules
- artifact storage and redaction rules
- stronger sync between probe records, active plan, and decision boundaries
- acceptance checks that distinguish probe closure from implementation closure

## Governance Document Set

The standard project-scoped governance set is:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/governance/01_constraints_and_spec.md`
- `docs/<project-scope>/governance/02_design.md`
- `docs/<project-scope>/governance/03_behavior_audit.md`
- `docs/<project-scope>/governance/05_decision_log.md`
- optional but recommended when there is a real frontier: `docs/<project-scope>/governance/06_active_plan.md`
- optional when the mode or user direction enables an active learning layer: `docs/<project-scope>/governance/04_lessons_learned.md`

The standard recovery skeleton is:

- `docs/<project-scope>/context/00_context_index.md`
- `docs/<project-scope>/context/01_context_usage_and_policy.md`
- `docs/<project-scope>/context/shards/`
- optional: `docs/<project-scope>/context/archive/`

The standard task layer is:

- `docs/<project-scope>/tasks/00_task_knowledge_base.md`
- `docs/<project-scope>/tasks/templates/`
- `docs/<project-scope>/tasks/records/`
- recommended when lane-based task records are enabled:
  - `docs/<project-scope>/tasks/templates/00_task_template_index.md`
  - `docs/<project-scope>/tasks/templates/T0-minor.md`
  - `docs/<project-scope>/tasks/templates/T1-probe-review-docs.md`
  - `docs/<project-scope>/tasks/templates/T2-implementation.md`
  - `docs/<project-scope>/tasks/templates/T3-substantial-change.md`

Repository-wide exception:

- `docs/governance/...` only if the user explicitly wants one governance layer shared across multiple projects or experiments
- optional repository-level routing helper: `docs/governance/00_project_scope_registry.md`

Use templates in `assets/` when creating them.

Prefer the lane-specific task templates when they exist.

If the current asset set in a given installation does not yet provide a needed mode-specific or lane-specific template, adapt the closest existing template and say so explicitly instead of pretending a dedicated template already exists.

## Workflow Overview

Keep the main workflow in four flows:

1. initialization
2. adoption
3. maintenance
4. re-entry

Always classify the current round before editing anything.

## 1. Initialization Flow

Use this flow when governance docs do not yet exist for the active project scope.

### Initialization Steps

1. Ask whether to initialize the governance system.
2. Ask for the active project or experiment scope and a stable slug if it is not already clear.
3. Choose `core`, `extended`, or `probe-heavy` mode with the user, defaulting to the lightest truthful mode.
4. Default the doc root to `docs/<project-scope>/governance/`.
5. Use `docs/governance/` only if the user explicitly wants repository-wide governance.
6. If the repository has multiple active project scopes and the user wants routing help, propose `docs/governance/00_project_scope_registry.md` as a routing-only helper.
7. Ask whether to initialize a project-root `AGENTS.md` from the template if one does not already exist.
8. If a project-root `AGENTS.md` already exists, do not overwrite it. Read it first and ask whether to keep it, merge governance rules into it, or replace it explicitly.
9. Create `00_index_and_priority.md` first.
10. Create the minimum governance, recovery, and task skeleton for the chosen mode.
11. Do not populate project-specific conclusions unless the user asks for adoption or migration.

### Initialization Outcome

At minimum, initialization should make the following explicit:

- stable project scope slug
- governance doc root
- authority order
- whether active plan is in use
- whether recovery is active and how to route it
- task-record requirement
- local quality-gate source if known

## 2. Adoption Flow

Use this flow when the repo already has scattered docs, stale notes, old handoff files, or conflicting design records.

### Adoption Steps

1. Ask whether to adopt the current project into the governance system.
2. Confirm the project scope and governance doc root first.
3. Read only the minimum current project docs needed to classify them.
4. Update `00_index_and_priority.md` to label documents as:
   - authoritative
   - working
   - historical or reference
5. Decide which existing files belong in authority, execution, learning, recovery, or probe surfaces.
6. If the project already contains handoff, notes, or historical chat-derived context files, classify whether they should remain external references or be re-homed into the project-scoped recovery layer.
7. Do not rewrite or clean old docs yet unless the user asks.
8. If multiple project scopes are already present or likely, propose a repository-level routing registry only if the user wants one.

### Adoption Rule

Adoption should classify first and migrate second.

Do not silently treat old notes, task records, or proposal docs as current authority merely because they are detailed.

## 3. Maintenance Flow

Use this flow once the governance system exists and the repo needs routine updates, structural maintenance, lesson promotion, or probe-aware sync.

### Lane-Based Behavior

Classify the round into the narrowest truthful lane.

Use these default lanes:

- `metadata-sync`
  - mechanical timestamps, links, labels, counts, or summary refreshes with no semantic change
- `docs-only`
  - meaningful documentation updates with no code or runtime behavior change
- `review-only`
  - read-only inspection and reporting
- `probe-only`
  - evidence gathering without intended production change
- `implementation`
  - code, config, or test changes within accepted truth
- `substantial-change`
  - architecture, protocol, governance-contract, or execution-model change
- `authority-change`
  - accepted truth changes
- `lesson-promotion`
  - repeated or severe patterns promoted into durable guidance
- `index-split`
  - routing or summary structure reorganization
- `archive-or-supersede`
  - retirement or replacement of a previously readable surface

If more than one lane applies, upgrade to the strictest lane that covers all planned actions.

Treat the hyphenated lane tokens in this skill as canonical cross-repo identifiers.

If a repository defines repo-local lane spellings in a behavior matrix, task-template index, or equivalent governance surface, map the canonical token to the repo-local label before writing user-facing output or persisted repository records.

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

Repo-local spellings win in user-facing output and persisted records when the repository defines them. Keep the canonical token only for skill-internal routing or as an optional parenthetical note when clarity is needed.

When lane-specific task templates are available as repo-local documents under `docs/<project-scope>/tasks/templates/*.md`, route to them as follows:

- `metadata-sync` -> `T0-minor`
- `docs-only`, `review-only`, `probe-only` -> `T1-probe-review-docs`
- `implementation` -> `T2-implementation`
- `substantial-change`, `authority-change` -> `T3-substantial-change`
- `lesson-promotion` -> `T1-probe-review-docs` by default; upgrade to `T3-substantial-change` if the promotion also changes accepted truth or hard execution policy
- `index-split`, `archive-or-supersede` -> `T1-probe-review-docs` by default as structural maintenance; upgrade to `T3-substantial-change` if the round also changes the active authoritative source or accepted truth

The bundled skill assets that generate those repo-local templates live under `assets/tasks/templates/*.template.md`.

If a repository has not enabled lane-specific repo-local templates and only exposes a generic template such as `docs/<project-scope>/tasks/templates/task_record.template.md`, use that repo-local contract and say explicitly that lane-tiered repo-local templates are not yet enabled.

If only `T0` through `T3` exist, say explicitly when one of these structural or promotion lanes is borrowing the closest existing template instead of pretending a dedicated template already exists.

### Lane Selection Checklist

Use this decision order:

1. If the round changes accepted project truth, use `authority-change` or `substantial-change`.
2. If the round changes code, config, runtime behavior, or tests without changing accepted truth, use `implementation`.
3. If the round is a broad architectural, protocol, or governance-contract shift, use `substantial-change`.
4. If the round only gathers evidence from runtime or environment without intended product change, use `probe-only`.
5. If the round only inspects and reports, use `review-only`.
6. If the round only repairs meaningful documentation content without changing product or runtime behavior, use `docs-only`.
7. If the round only fixes routing labels, timestamps, counts, links, or similar mechanical drift, use `metadata-sync`.
8. If the round promotes a repeated stable pattern into a reusable guardrail, use `lesson-promotion`.
9. If the round changes document routing structure, use `index-split` or `archive-or-supersede`.

### Lane Rules

#### `metadata-sync`

- keep the edit mechanical
- verify the source of truth for every count, label, or link
- escalate immediately if any sentence changes meaning

#### `docs-only`

- keep one detailed round record and keep other sync surfaces concise
- if wording changes future agent behavior, treat it as semantic and escalate as needed
- do not claim runtime evidence from docs work alone

#### `review-only`

- do not patch while reviewing
- separate observed facts from inference
- if the user later approves fixes, start a new implementation or docs lane

#### `probe-only`

- state the probe boundary before running it
- make runner boundary, redaction approach, and artifact set explicit
- record the verified boundary or failure stage
- do not let probe evidence silently redefine authority

#### `implementation`

- keep changes inside accepted scope
- verify with the repo quality gates required for the touched surface
- record which quality-gate source was used and which commands were actually run
- if the quality gate is inferred rather than explicitly documented, say so in the closing handoff or task record
- sync only the execution surfaces that actually changed unless the lane is upgraded

#### `substantial-change`

- link the round to an explicit decision or create one in the same round
- update every affected authority surface needed to remove ambiguity
- do not close the round without review

#### `authority-change`

- record what old truth is being replaced
- record why the new truth is now accepted
- update spec, design, decision, and authority-routing text consistently in one round

#### `lesson-promotion`

- cite the repeated or severe evidence source
- write the lesson as a durable guardrail, not a task diary
- escalate to `authority-change` if the lesson becomes a mandatory project rule

#### `index-split`

- keep the split routing-only unless explicitly approved otherwise
- split on semantic or layer boundaries, not arbitrary `part1/part2/part3`
- tell the user that future reading behavior is being reorganized

#### `archive-or-supersede`

- name the replacement active source
- mark the old source clearly as historical, superseded, or archived
- synchronize every route that could still send future agents to the old source first

### Sync Triggers

#### Authority Sync Trigger

Update authority docs when:

- scope changes
- a hard constraint changes
- an accepted design rule changes
- a decision is made, replaced, or superseded
- a proposal becomes accepted policy
- if spec or design surfaces changed, update the matching authority docs in the same workstream

#### Execution Sync Trigger

Update execution docs when:

- a meaningful implementation, review, docs, or probe round completes
- the current frontier changes
- the blocker boundary changes
- the next package changes
- the risk ordering changes

#### Learning Sync Trigger

Update learning docs when:

- the same pitfall appears multiple times
- one severe event merits a standing guardrail
- the lesson changes how future agents should read, probe, document, or validate

#### Recovery Sync Trigger

Update recovery docs when:

- a future agent would need the state after compression, pause, or handoff
- a shard becomes superseded, stale, resolved, archived, or promoted
- a new shard changes routing relevance
- if a shard becomes superseded or archived, update the context index in the same round

Recovery sync is atomic:

- shard status and context-index status must change together

#### Review Standard

Review for:

- correctness
- regressions
- security boundaries
- missing tests
- doc drift

Surface residual risk explicitly in the closing handoff.

#### Routing Sync Trigger

Update summary headers, indexes, or routing surfaces when:

- the linked authoritative document changed materially
- a context shard changed status
- a task record was superseded by a later current boundary
- a split, archive, supersede, or promotion action changed future reading order

### File Update Heuristics

Use these heuristics to implement the layer-level sync triggers above.

The sync triggers answer which governance layer changed.
These file heuristics answer which concrete documents should usually move with that layer change.

Use these file-level defaults when deciding what to sync:

- Update `docs/<project-scope>/governance/00_index_and_priority.md` when document authority or status changes.
- Update `docs/<project-scope>/governance/01_constraints_and_spec.md` when requirements, hard constraints, or the unified current rule set changes.
- Update `docs/<project-scope>/governance/02_design.md` when architecture, design rationale, or implementation details change.
- Update `docs/<project-scope>/governance/03_behavior_audit.md` after meaningful implementation, config, environment, or documentation actions.
- Update `docs/<project-scope>/governance/04_lessons_learned.md` when a problem yields a reusable lesson.
- Update `docs/<project-scope>/governance/05_decision_log.md` when alternatives were considered and one direction was explicitly chosen.
- Update `docs/<project-scope>/governance/06_active_plan.md` only when the current frontier, next package, blocker boundary, risk ordering, or priority order changed materially.
- Update `docs/<project-scope>/context/00_context_index.md` whenever active recovery or context shards, statuses, freshness, or routing relevance change materially.
- Update or append project-scoped recovery or context shards when the task produces new effective state that would be needed after compression, pause, or handoff.
- Treat shard update plus `00_context_index.md` update as one atomic documentation action. Do not change shard state, archive location, merge structure, or promotion status without synchronizing the index in the same round.

### Active Plan Rule

Treat `06_active_plan.md` as a frontier document, not a second spec.

Update it only when one of these changes:

- current frontier
- next package
- blocker boundary
- risk ordering
- current priority order

Do not update it for routine metadata edits or because a completed task record exists.

### Promotion Rule

Promote content upward when it becomes durable:

- from probe artifacts to execution records when a round conclusion is preserved
- from execution or recovery to learning when the lesson is stable and reusable
- from recovery, execution, or proposal docs to authority only after explicit acceptance

Do not leave accepted project truth trapped only in:

- recovery shards
- task records
- proposal docs

## 4. Re-entry Flow

Use this flow after compression, summarization, handoff, or any pause where the recent working state may matter.

This section operationalizes the quick re-entry rules above.

### Re-entry Reading Order

For governance-sensitive tasks:

1. Read `docs/<project-scope>/governance/00_index_and_priority.md` first if it exists.
2. If `docs/governance/00_project_scope_registry.md` exists, use it only to identify the active project scope before reading project-scoped governance docs.
3. If the task is explicitly repository-wide, read `docs/governance/00_index_and_priority.md` instead.
4. Then read the current authoritative spec.
5. Then read the active plan and relevant decision records if the task depends on them.
6. If history or recovery state matters, read `docs/<project-scope>/context/00_context_index.md`.
7. Filter out archived and superseded shards by default unless history is explicitly needed.
8. Expand into only the `1-3` most relevant recovery shards based on scope, topic, unresolved status, and freshness.
9. Then read only the design, audit, lesson, task, or probe surfaces needed for the current lane.

### Compression Rule

If context is compressed, summarized, or otherwise reduced during task execution, do not continue blindly from the compressed state.

- re-check the active task, current plan, and authoritative project context before continuing
- verify that no constraints, subtasks, decisions, pending actions, or user instructions were dropped or distorted
- if the task depends on recent execution state, consult the recovery layer before trusting compressed chat memory alone
- if uncertainty remains after re-alignment, surface it explicitly to the user

## Progressive Disclosure And Index System

Use progressive disclosure to reduce context load in large or long-running projects.

The goal is not to summarize everything blindly. The goal is to decide what to read next while preserving authority, traceability, and current correctness.

This section elaborates the route-first reading rules referenced earlier in the re-entry guidance.

### Reading Contract

Default reading behavior:

1. route first
2. verify authority second
3. expand only into the minimum relevant documents
4. stop using summary-only reading once the active authoritative rule or plan is identified

Do not let summaries replace authoritative project rules.

### Authority Boundary

- summaries are for routing and quick orientation first, not for redefining project truth
- current spec, hard constraints, accepted decisions, and active plans must remain in authoritative governance docs, not only in summaries
- the project-scoped `context/` layer is for working or reference state recovery, not for defining authoritative project truth
- if a summary and a full authoritative document disagree, the authoritative project document wins
- if a governance doc and a context doc disagree, the governance doc wins
- if a context doc and a routing summary disagree, the context doc wins
- if a summary may be stale and cannot be quickly verified, read the authoritative section instead of trusting the summary

### Preferred Reading Strategy

For large projects, prefer this reading order:

1. read the scope, index, or routing doc first
2. read file-level summary headers before reading full documents
3. read only the sections needed for the current task
4. expand to full-document reading only when the summary or header is insufficient
5. prefer recent authoritative docs over long historical references

Do not default to scanning all related files when a smaller authoritative subset is available.

### Graded Index Model

Use a shallow graded index rather than a flat pile of large files.

- Grade 0: scope entrypoint
  - examples: `00_index_and_priority.md`, optional repository routing registry
- Grade 1: layer indexes or authority docs
  - examples: spec, decision log, active plan, task knowledge base, context index
- Grade 2: detailed records
  - examples: task records, recovery shards, artifact bundles, lesson files

Rules:

- Grade 0 routes scope and authority order
- Grade 1 routes within one layer or provides the active authoritative contract
- Grade 2 stores detail and evidence
- indexes should route; they should not duplicate full underlying content

### Summary-Entry Support

Progressive disclosure is not complete with route-first indexes alone.

Frequently revisited or high-risk documents should gain summary-entry support once lightweight triage stops being sufficient.

Minimum summary-entry expectations:

- file-level summary headers for long or high-frequency documents
- routing indexes for layers that accumulate multiple candidate files
- freshness or status signals when a stale read would materially mislead the next action

Recommended file-level summary-header fields:

- purpose
- status
- authority
- scope
- read this when
- skip this when
- key sections
- last materially updated

Use summary-entry support for routing only, not to replace the authoritative body.

### File-Level Summary Headers

When documents are long or frequently revisited, prefer adding a compact summary header near the top of the file. That header should help the agent decide whether to keep reading.

Use the recommended header fields already listed above. Use these headers to support triage, not to hide the actual active rules.

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

The same rule applies to `docs/<project-scope>/context/00_context_index.md`:

- keep it routing-oriented
- do not restate the full contents of every shard
- update it when shard status, freshness, or relevance changes materially
- record enough state so future agents can avoid stale or superseded shards without opening everything first

### Index Split Rules

Split an index when one of these becomes true:

- the index is large enough that routing itself becomes noisy
- unrelated topics force repeated scanning by readers who need only one subset
- the file mixes authority routing, execution routing, and recovery routing in one place
- freshness and status tracking become hard to maintain

Preferred split boundaries:

- layer responsibility
- project scope
- active versus historical material
- semantic topic, not `part1/part2/part3`

Keep the tree shallow:

- default to one routing level
- introduce a second level only when the first-level index becomes noisy or the project truly contains multiple distinct governance islands
- avoid deeper trees unless the navigation cost is clearly lower than repeated full-file scans

### Splitting Large Files

If a file becomes too large, prefer splitting by responsibility or semantic boundary, not by arbitrary size alone.

Good split boundaries include:

- current spec versus historical reference
- design versus decision log
- audit log versus lessons learned
- active rules versus archived material

Avoid mechanical splitting such as `part1/part2/part3` unless there is no better semantic boundary.

### Compression And Summarization Boundaries

Not all files should be compressed the same way.

Usually safe to compress or summarize aggressively:

- historical debugging notes
- historical design drafts
- lessons learned collections
- old reference material
- long audit logs, as long as append-only detail is preserved somewhere
- resolved or superseded context shards, as long as the recovery path remains discoverable

Usually not safe to replace with summary-only reading:

- current constraints or spec
- active decision records
- active design details that govern current implementation
- active plans
- active context shards that contain the current recovery state for an unfinished task

For those authoritative files, summaries may guide reading, but they should not replace reading the relevant authoritative sections.

### Bloat Control

For files that continuously grow, use explicit control mechanisms:

- for audit logs, keep append-only detail but add periodic checkpoint summaries so agents can read the newest checkpoint first
- for lessons learned, deduplicate overlapping entries when the user wants cleanup
- for decision logs, keep the final decision and rationale easy to scan near the top of each decision entry
- for design docs, split when multiple independent subtopics start forcing unrelated readers into the same large file

### Index Depth

Keep the index tree shallow by default.

- prefer one level of index: one index file routing to child files
- only introduce a second level when the first-level index itself becomes too large or the project truly contains multiple distinct governance islands
- avoid deep index trees unless the user explicitly wants them

The cost of extra navigation can cancel out the token savings if the tree becomes too deep.

### Staleness And Drift Control

A routing surface is stale when:

- the linked authoritative document changed materially but the summary or index did not
- a recovery shard changed status but the recovery index still presents the old state
- a task record was superseded by a later authoritative round but the routing text still points to the older boundary

Required handling:

- update the routing surface in the same round
- or mark it as potentially stale
- do not present stale summaries as authority
- if freshness cannot be re-established quickly for a high-stakes task, read the authoritative section directly instead of trusting the routing surface

### Flexible Use Of Lossy Context Reduction

Lossy context reduction is allowed when the task does not require full fidelity and the user accepts a lighter context strategy.

Examples:

- reading historical notes through a summary instead of full detail
- reading a checkpoint summary before expanding into a long audit log
- routing from an index before opening full design or history files
- routing from `00_context_index.md` before opening specific context shards

Do not use lossy reduction as the default for current hard constraints or active project decisions.

### Practical Rule

When in doubt:

- reduce context by routing first
- preserve authority in the real source document
- expand only when the next decision actually needs more detail

## Recovery Layer Method

The recovery layer exists to preserve effective execution state across:

- chat compression
- pauses and resumptions
- multi-stage debugging
- long-running experiments
- handoffs between sessions or agents

The recovery layer is project-scoped, not conversation-scoped and not repository-scoped.
In current repo layouts, this recovery surface usually lives under `docs/<project-scope>/context/`.

Do not create a single detailed repository-wide recovery ledger for unrelated projects.

The recovery layer should be lightweight at initialization time:

- create the recovery skeleton together with governance initialization
- do not pre-fill large content unless the user asks for adoption or migration
- create actual shards only when useful state needs to be preserved

Use recovery shards for the minimum complete state that would let a future agent continue correctly, not for transcript dumping.

### Recovery Context Units

The smallest useful recovery or context-layer record is a focused context unit, not an entire verbatim conversation transcript.

A good unit should capture:

- time range
- topic or subtask
- status such as `active`, `blocked`, `resolved`, `superseded`, or `stale`
- related files
- related governance docs
- routing keywords
- when to read it
- when to skip it
- session summary
- effective full context
- core constraints
- decisions and non-decisions
- open questions
- reusable lessons or patterns
- `supersedes` or `superseded by` links when applicable

Use `effective full context` for the minimum complete state needed to recover execution, not for chat-by-chat replay.

### Recovery Write Triggers

Write or append recovery state when the task produces state that a future agent would likely need after compression, pause, or handoff.

Common triggers:

- a new hard constraint was introduced or corrected
- a direction-changing decision was made
- a debugging chain reached a stage conclusion
- the task is about to pause, hand off, or compress context
- a long-running task moved into a new stage
- a reusable lesson, eliminated path, or stable failure mode was discovered
- a historical experiment result was confirmed, downgraded, or overturned

Do not write recovery shards for repeated conclusions with no new execution value, speculative noise, or facts already stably available in authority docs unless the recovery state itself matters.

### Recovery And Context Exclusions

Do not write recovery or context shards for:

- repeated conclusions with no new execution value
- speculative notes that do not affect current or near-term execution
- facts already stably available in authoritative governance docs unless the recovery state itself matters
- low-signal back-and-forth that would not help a future agent continue the task

Do not let the recovery or context layer become a shadow spec:

- if a constraint, design rule, decision, or reusable lesson has become stable, promote it to the appropriate governance doc
- after promotion, mark the old recovery or context unit as `resolved`, `superseded`, or `promoted to governance` instead of leaving it active indefinitely

### Recovery Shards And Capacity

Organize the recovery layer by semantic topic or subtask first, then split into shards inside that bucket.

Good patterns:

- `docs/<project-scope>/context/shards/ctx-<topic>-001.md`
- `docs/<project-scope>/context/shards/ctx-<topic>-002.md`

Avoid mechanical `part1/part2/part3` splits unless there is no better semantic boundary.

Recommended shard limits:

- roughly `8-12` context units per shard
- or roughly `6k-10k` Chinese characters before splitting

Each shard should include a summary header so the agent can decide whether it is relevant before reading the whole file.
If old shards remain useful for traceability but not active routing, mark or move them as archived instead of silently deleting them.

### Conflict And Pollution Control

Prevent recovery-layer drift by treating every shard as a stateful working or reference artifact instead of a passive note dump.

Use these rules:

- every shard and context unit should carry an explicit status instead of remaining implicitly current
- use `supersedes` or `superseded by` links when one conclusion replaces another
- prefer marking outdated material as `superseded`, `stale`, `resolved`, or `archived` over deleting it
- do not keep multiple active shards that express conflicting current-state conclusions for the same topic without clarifying the conflict
- if a stable conclusion has already been promoted into governance, downgrade the old recovery or context record accordingly
- do not keep speculative or obsolete execution state in `active` status

### Recovery Hygiene

Perform a hygiene review when:

- `00_context_index.md` has become noisy
- the same topic has accumulated several active shards
- old and new shards appear to disagree about current state
- shard size has crossed the preferred capacity limit
- repeated handoffs keep reopening the same stale material

Useful actions include:

- merge duplicate or overlapping shards
- mark older shards superseded, stale, resolved, or archived
- split oversized shards by semantic topic
- promote stable conclusions into governance docs
- remove low-signal routing noise from the recovery index

Key hygiene actions are structural maintenance:

- tell the user when you archive shards
- tell the user when you downgrade or supersede previously active recovery state
- tell the user when you promote stable conclusions from recovery into governance
- tell the user when you merge or materially reorganize shards
- only skip explicit notification for clearly mechanical small updates such as fixing timestamps, counts, or a short routing summary after the semantic decision was already explained

## User Communication Rule

Key governance and recovery maintenance actions must not become silent drift.

Explicitly tell the user before or while performing actions that materially change future reading behavior, including:

- archive
- supersede
- merge
- split index families
- downgrade active shards
- promote stable conclusions into learning or authority
- materially reorganize routing or index structure

Only clearly mechanical small updates may be silent when they do not change semantic meaning.

## Reference Map

- Read `references/governance-workflow.md` for the recommended operating model and update triggers if it exists and is still aligned.
- Read `references/acceptance-scenarios.md` when checking whether the skill, its templates, and its maintenance workflow still satisfy the intended lifecycle.
- When a repository enables `docs/<project-scope>/governance/09_governance_system_spec.md`, use it as the route-first repo-local explainer for governance-layer responsibilities, graded-index rules, summary-entry expectations, and optional governance-system surfaces before falling back to this skill's generic defaults. Treat it as workflow guidance only unless the repository explicitly promotes it into authority.
- Copy or adapt templates from `assets/`, including:
  - the optional project-root `AGENTS.md` template
  - the optional repository-level `00_project_scope_registry.template.md`
  - the routing templates `file-summary-header.template.md` and `summary-index.template.md`
  - the project-scoped recovery templates `00_context_index.template.md`, `01_context_usage_and_policy.template.md`, and `context-shard.template.md`
  - the optional governance-system templates `07_governance_behavior_matrix.template.md`, `08_probe_harness_contract.template.md`, and `09_governance_system_spec.template.md`
  - the lane-specific task-template assets under `assets/tasks/templates/`, including `T0-minor.template.md`, `T1-probe-review-docs.template.md`, `T2-implementation.template.md`, and `T3-substantial-change.template.md`; when a repo adopts them, the repo-local copies live under `docs/<project-scope>/tasks/templates/*.md`
- If repository-local docs define a stricter or newer governance contract than this skill, follow the repository-local docs and treat this skill as needing future update rather than forcing the repo back to the older skill behavior.
