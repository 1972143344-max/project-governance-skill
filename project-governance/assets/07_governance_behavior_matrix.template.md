# Governance Behavior Matrix

Updated: YYYY-MM-DD HH:MM:SS
Status: proposed
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: working
Layer: mixed

## Purpose

This document operationalizes governance execution lanes for the project. Use it to decide:

- which lane applies before work starts
- which documents must be read before acting
- which write surfaces are allowed for that lane
- which sync updates are required versus out of scope
- when review and authority updates are mandatory

This matrix defaults to a proposed working surface. It does not replace the authority order in `00_index_and_priority.md`, and it does not become authoritative lane-control by existing as a draft. Promote it only when the project explicitly enables it and updates the header to active authoritative status.

## Core Rules

1. Classify the round before editing anything.
2. Use the narrowest lane that truthfully matches the intended output.
3. If more than one lane applies, upgrade to the strictest lane that covers all planned actions.
4. Do not update authority docs unless project truth actually changed.
5. Do not silently change future reading behavior through archive, supersede, merge, split, or promotion actions.
6. Read `08_probe_harness_contract.md` before acting whenever the lane is `probe-only`, the round creates or relies on `tasks/artifacts/`, or the project is operating in `probe-heavy` mode.
7. Optional governance drafts do not outrank the authoritative core set until they are explicitly enabled.

## Lane Selection Checklist

1. If the round changes accepted project truth, use `authority-change` or `substantial-change`.
2. If the round changes code, config, runtime behavior, or tests without changing accepted truth, use `implementation`.
3. If the round is a broad architectural, protocol, or governance-contract shift, use `substantial-change`.
4. If the round only gathers evidence from runtime or environment without intended product change, use `probe-only`.
5. If the round only inspects and reports, use `review-only`.
6. If the round only repairs meaningful documentation content, use `docs-only`.
7. If the round only fixes headers, links, counts, or routing labels, use `metadata-sync`.
8. If the round promotes a stable repeated pattern into future guidance, use `lesson-promotion`.
9. If the round changes routing structure, use `index-split` or `archive-or-supersede`.

Artifact-backed `review-only` or `docs-only` rounds stay in their original lane, but they still inherit the `08_probe_harness_contract.md` read and redaction rules when `tasks/artifacts/` or `probe-heavy` applies.

## Required Read Baseline

For every non-trivial lane, read:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/governance/01_constraints_and_spec.md`
- `docs/<project-scope>/tasks/00_task_knowledge_base.md`

Also read:

- `05_decision_log.md` when accepted direction or authority status may matter
- `06_active_plan.md` when the current frontier may change
- `04_lessons_learned.md` when promoting or checking a lesson
- `08_probe_harness_contract.md` whenever the lane is `probe-only`, the round uses `tasks/artifacts/`, or the project is operating in `probe-heavy` mode
- `context/00_context_index.md` only when recovery state is needed

## Matrix

| Lane | Trigger conditions | Required reads | Allowed write surfaces | Required sync surfaces | Prohibited actions | Review required | Authority update required |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `docs-only` | Meaningful doc repair or drafting with no code, config, runtime, or test change | Baseline reads and full read of target docs | target docs, task record, behavior audit, task knowledge base | task record; audit when the round materially affects future work | code/config edits; new runtime claims; silent scope widening | conditional | conditional |
| `metadata-sync` | Mechanical headers, links, counts, routing labels, or summary refresh with no semantic change | touched routing doc plus source doc needed to verify metadata | metadata headers, routing indexes, short summary entries, optional `T0` task record when the round is still worth preserving | touched metadata/index surfaces, plus optional `T0` task record when the round is meaningful enough to preserve | semantic rewrites; blocker reinterpretation; hidden authority edits | no | no |
| `review-only` | Read-only review or inspection that produces findings without intended repo behavior change | baseline reads and reviewed surfaces | normally none; persisted review artifact only if requested | task record and audit only when the review must be preserved | silent fixes; opportunistic cleanup | no | no |
| `probe-only` | Runtime or environment evidence-gathering with no intended product change | baseline reads, active plan, relevant prior task records | probe artifacts, task record, behavior audit, active plan if the boundary changed | task record; audit; active plan only if frontier or blocker changed | product changes unless upgraded; unredacted artifacts; overclaiming | conditional | no unless upgraded |
| `implementation` | Feature, bug fix, hardening, or refactor within accepted truth | baseline reads, target docs/code, active plan, decisions when needed | code, tests, config, task record, audit, active plan | task record; audit; active plan when frontier changed | silent authority drift; undocumented scope expansion | yes | conditional |
| `substantial-change` | Architecture, protocol, governance contract, or multi-surface direction change | baseline reads, decisions, active plan, full authority docs | code/tests/config plus authority docs, task record, audit, active plan | task record; audit; active plan; decisions; affected authority docs | treating major direction shift as routine work | yes | yes |
| `authority-change` | Accepted truth changes without necessarily requiring broad code movement yet | baseline reads, decisions, all affected authority docs | authority docs plus task record, audit, plan as needed | decisions; changed authority docs; active plan if frontier changed | changing truth without decision trace | yes | yes |
| `lesson-promotion` | Stable repeated or severe pattern is promoted into reusable guidance | baseline reads, lessons index, source task records or audit evidence | lessons index, lesson files, source cross-links, concise audit note | updated lesson surface and source cross-links | promoting one-off noise; hiding source evidence | conditional | conditional |
| `index-split` | A routing surface became too large or ambiguous and must be reorganized | baseline reads and full read of every touched routing file | routing indexes, summary headers, split index files, concise audit note if material | every touched routing surface in the same round | silent reorganization; authority-change disguised as routing | yes | no unless authority status changed |
| `archive-or-supersede` | A doc or shard is no longer active and must be retired or replaced | baseline reads, old doc, replacement doc, affected indexes | superseded doc metadata, replacement doc, routing docs, concise audit note | every affected index and replacement marker in the same round | silent retirement; deleting history without trace | yes | conditional |

## Execution Checklists By Lane

### `docs-only`

- Keep one detailed task record and keep other sync surfaces concise.
- Upgrade if wording changes accepted truth.
- If the round creates or relies on `tasks/artifacts/`, follow the probe contract for artifact handling and redaction.

### `metadata-sync`

- Verify the source of truth for every timestamp, count, link, or label.
- Keep the edit mechanical.

### `review-only`

- Do not patch while reviewing.
- Separate observed facts from inference.
- If the round cites artifact bundles or runs under `probe-heavy`, follow the probe contract before recording evidence.

### `probe-only`

- State the probe boundary before running it.
- Read and follow `08_probe_harness_contract.md` before running the probe.
- Capture failure stage, redaction approach, and artifact set.

### `implementation`

- Stay inside accepted scope.
- Before claiming delivery complete, locate and run the repo-local quality gate required for the touched surface.
- If the quality gate is inferred from existing repository execution surfaces rather than explicitly documented, say so in the round record or closing handoff.

### `substantial-change`

- Link the round to an explicit decision or create one in the same round.
- Remove ambiguity across all changed authority surfaces.

### `authority-change`

- Record what old truth is being replaced.
- Record why the new truth is now accepted.

### `lesson-promotion`

- Cite repeated or severe evidence.
- Write the lesson as a durable guardrail, not a task diary.

### `index-split`

- Keep the split routing-only unless explicitly approved otherwise.
- Tell the user future reading behavior is being reorganized.

### `archive-or-supersede`

- Name the replacement active source.
- Mark the old source clearly as historical or superseded.

## Review Standard

- Review for correctness, regressions, security boundaries, missing tests, and doc drift.
- Surface residual risk explicitly in the closing handoff.
