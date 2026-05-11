# Index And Priority

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: routing-only
Index grade: `0`
Index family: `authority routing`

## Maintenance Threshold

Document role: `routing-doc`
Advisory threshold: `240 lines`
Split threshold: `320 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this document should be split or given a second-level routing surface before future growth continues.
Even below the split threshold, surface the same recommendation if routing quality has clearly degraded.
Do not silently restructure this document during unrelated work.

## Purpose

This document is the governance entrypoint for the project. It defines:

- the authority order for project truth
- the routing order for related governance, task, and recovery surfaces
- which documents are authoritative, routing-only, working, or historical
- which optional governance surfaces are active for this project mode

This file applies only to the scope named above unless explicitly marked as repository-wide.

## Grade Meaning

- `0`: scope entrypoint and authority order
- `1`: layer index or active contract surface
- `2`: detailed record or evidence routing surface

This file is normally the project's `Grade 0` entrypoint.

## Index Maintenance Contract

This file is a stable read-first entrypoint.

### Stable Entrypoints

Treat these as stable entrypoint surfaces by default:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/context/00_context_index.md`
- `docs/<project-scope>/tasks/00_task_knowledge_base.md`
- `docs/<project-scope>/tasks/templates/00_task_template_index.md` when task-template tiering is active

Do not rename or replace these entrypoints lightly.

### Split Rule

If a stable entrypoint or layer-routing document grows large enough that routing quality degrades, keep the existing file as the shallow read-first surface and split below it with second-level routing.

Prefer splitting by:

- semantic topic
- layer boundary
- subsystem
- active-versus-historical boundary

Do not silently replace an established entrypoint with a different filename when downward splitting is enough.

### When To Add A Layer Index

Add a second-level routing surface only when one of these becomes true:

- one file can no longer route most reads to one clear next hop
- multiple distinct topics or surfaces are mixed in one routing document
- routing noise, stale-read risk, or maintenance overhead has become material
- the file is still serving as an entrypoint, but detailed content now needs to live below it

### Naming Stability

When a previously stable document is split:

- keep the existing filename as the stable entrypoint whenever possible
- move detailed content into child documents or second-level routing files below it
- update the existing file so its current routing role is explicit near the top
- keep upper-layer references pointing to the stable entrypoint unless a true scope change requires otherwise

A stable entrypoint may become more index-like over time even if its filename does not contain `index`. This is acceptable as long as its current role is stated clearly in the document header and body.

### Routing-Only Boundary

Indexes and routing entrypoints help the reader choose what to open next.

They do not replace underlying authority documents.

Do not treat routing text as authoritative project truth once the relevant authority or active execution surface has been identified.

### Role-Change Sync Rule

If a governance document changes role, update its header role/status, purpose text, index classification, and routing notes in the same round.

## Governance Mode

Active mode: `core | extended | probe-heavy`

Mode notes:

- `core`: minimal governance skeleton for ordinary project work
- `extended`: adds lessons, stronger summary-entry support, and richer routing
- `probe-heavy`: adds explicit probe contract and evidence-oriented operating rules

## Reading Contract

Default reading order:

1. Read this file first.
2. Read the current authoritative spec.
3. Read the current authoritative design doc when structure or behavior matters.
4. Read accepted decisions when direction, exception handling, or authority status may matter.
5. If an enabled `07_governance_behavior_matrix.md` exists and the round is non-trivial, read it before final lane classification.
6. If the round uses `probe-only`, creates or relies on `tasks/artifacts/`, or the project is in `probe-heavy` mode, read `08_probe_harness_contract.md` before running probes or interpreting artifacts.
7. Read the current active plan only when the frontier, blocker boundary, or next package may matter.
8. If an enabled `04_lessons_learned.md` exists and reusable guardrails or prior repeated failures may matter, read it before promoting a new lesson.
9. If the round needs the full repository reading protocol, read `10_runtime_reading_protocol.md`.
10. If task-template tiering is enabled and a new task record is needed, read `tasks/templates/00_task_template_index.md`.
11. If the round enters governance sync, closure, or update/notify adjudication, read `11_governance_execution_contract.md`.
12. Read task routing and recovery routing only after the active authoritative rule or plan is known.
13. Expand into only the minimum detailed records needed for the active question.

Progressive disclosure rules:

- route first and expand second
- use summary headers and summary indexes for routing only
- do not rely on summary-only reading once the relevant authority or active frontier is identified

## Document Roles

Use these role labels consistently:

- `authoritative`: current project truth
- `routing-only`: helps choose what to read next but does not define truth
- `working`: active execution or recovery surface
- `historical/reference`: closed, superseded, archived, or evidence-only material

## Governance Surface Catalog

Use this catalog to list the surfaces available to the project.
Keep only the entries that are active for the current project mode or explicitly approved by the user.

### Authority Layer

- `docs/<project-scope>/governance/00_index_and_priority.md`: authority order and routing entrypoint
- `docs/<project-scope>/governance/01_constraints_and_spec.md`: current requirements, constraints, and accepted rules
- `docs/<project-scope>/governance/02_design.md`: accepted design boundaries and system structure
- `docs/<project-scope>/governance/05_decision_log.md`: accepted decisions, overrides, and rationale

Read next inside the authority layer when:

- scope, constraints, or accepted rules matter: `01_constraints_and_spec.md`
- structure, ownership, or implementation responsibility matters: `02_design.md`
- accepted direction, exception handling, or override history matters: `05_decision_log.md`

### Execution Layer

- `docs/<project-scope>/governance/03_behavior_audit.md`: append-only audit summary for meaningful rounds
- `docs/<project-scope>/governance/06_active_plan.md`: current execution frontier and next package when the project currently persists an active frontier
- `docs/<project-scope>/tasks/00_task_knowledge_base.md`: routing index into completed task records
- `docs/<project-scope>/tasks/records/TASK-*.md`: detailed round records

Read next inside the execution layer when:

- the current frontier, blocker boundary, or next package may matter: `06_active_plan.md`
- recent completed rounds or durable implementation history may matter: `03_behavior_audit.md`
- you need a prior task record or searchable round history: `tasks/00_task_knowledge_base.md`

### Learning Layer

- `docs/<project-scope>/governance/04_lessons_learned.md`: lesson index and promotion surface when the mode or user direction enables an active learning layer
- `docs/<project-scope>/governance/lessons/LES-*.md`: optional detailed lesson records when the project splits lessons into dedicated files

Read next inside the learning layer when:

- you need to know whether a reusable lesson already exists: `04_lessons_learned.md`
- the index points you to a detailed active lesson: `governance/lessons/LES-*.md`

### Recovery Layer

- `docs/<project-scope>/context/00_context_index.md`: routing index into recovery context
- `docs/<project-scope>/context/01_context_usage_and_policy.md`: recovery-writing contract
- `docs/<project-scope>/context/shards/*.md`: working recovery checkpoints

Read next inside the recovery layer when:

- recent execution state, handoff state, or compressed-context recovery matters: `context/00_context_index.md`
- you need the local write/read contract for recovery maintenance: `context/01_context_usage_and_policy.md`

### Probe Layer

- `docs/<project-scope>/governance/08_probe_harness_contract.md`: active probe-only operating contract when probe-heavy or explicitly enabled
- `docs/<project-scope>/tasks/artifacts/`: optional evidence bundles and probe outputs

Read next inside the probe layer when:

- the round uses `probe-only`, uses `tasks/artifacts/`, or needs artifact/redaction rules: `08_probe_harness_contract.md`
- you need the evidence payload after the probe contract is already known: `tasks/artifacts/`

## Optional Governance Surfaces

Enable these only when the project mode or user direction justifies them:

- `docs/<project-scope>/governance/04_lessons_learned.md`
- `docs/<project-scope>/governance/07_governance_behavior_matrix.md`
- `docs/<project-scope>/governance/08_probe_harness_contract.md`
- `docs/<project-scope>/governance/09_governance_system_spec.md`
- `docs/<project-scope>/governance/12_*` or later proposal docs
- `docs/<project-scope>/governance/lessons/`
- `docs/<project-scope>/tasks/templates/00_task_template_index.md`

### Enabled Optional Surface Routing

- `04_lessons_learned.md`
  - enable when the project keeps an active learning layer
  - read when checking for reusable guardrails or deciding whether to promote a lesson
- `07_governance_behavior_matrix.md`
  - enable when the project wants explicit lane discipline beyond the core reading order
  - read before final lane classification once it is active
- `08_probe_harness_contract.md`
  - enable when the project is `probe-heavy` or artifact-backed probes are a recurring workstream
  - read before `probe-only` work and before any round that creates or relies on `tasks/artifacts/`
- `09_governance_system_spec.md`
  - enable when the project is actively designing or revising its governance model
  - read for governance-maintenance work only after the authoritative core set is already known
- `tasks/templates/00_task_template_index.md`
  - enable when the project uses lane-tiered task templates
  - read before creating a new task record when multiple templates are plausible

## Support Protocol Surfaces

Treat these as stable support-entrypoint surfaces when the runtime router or project-root `AGENTS.md` routes task rounds into them:

- `docs/<project-scope>/governance/10_runtime_reading_protocol.md`
- `docs/<project-scope>/governance/11_governance_execution_contract.md`

Read them according to the routing contract instead of treating them as optional governance proposals.

## Conflict Resolution Order

1. direct user instruction in the active session
2. active authoritative governance docs under `governance/`
3. accepted decisions and authority notes that explicitly override defaults
4. this file for routing order, document-role interpretation, and discoverability only
5. active execution docs under `governance/` and `tasks/`
6. active recovery docs under `context/`
7. summary headers and summary indexes as routing only
8. historical/reference material only when explicitly needed

## Update Triggers

Update this file when one of these becomes true:

- the authority order changes
- a new governance lane or mode becomes active
- a new authoritative or routing surface becomes part of the standard reading path
- an active document becomes superseded, archived, or replaced

Do not update this file for:

- ordinary round completion with no routing impact
- task-local evidence that did not change the reading path
- purely mechanical wording that does not affect authority or discoverability

## Split And Staleness Rules

- This `Grade 0` entrypoint should stay singular unless the repository truly contains multiple governance islands or repeated scope selection ambiguity.
- If one routing surface is no longer enough, split below this file by layer or scope rather than replacing the Grade 0 entrypoint.
- If a linked authoritative or routing surface changes materially and this file still points to the older path, refresh the affected route in the same round or mark it as potentially stale.
- Do not present a stale route in this file as current authority.

## Notes

- Keep this file concise and routing-oriented.
- If this file points to long or high-frequency documents, add summary-entry support to those documents rather than bloating this entrypoint.
