# Lane Reference

Use this sidecar only when the runtime action families in the main `SKILL.md` are not enough.

## Canonical Lanes

Default canonical lane set:

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

If more than one lane applies, upgrade to the strictest lane that covers all planned actions.

## Lane Selection Order

1. If accepted project truth changes, use `authority-change` or `substantial-change`.
2. If code, config, runtime behavior, or tests change without changing accepted truth, use `implementation`.
3. If the round is a broad architecture, protocol, or governance-contract shift, use `substantial-change`.
4. If the round only gathers evidence from runtime or environment without intended product change, use `probe-only`.
5. If the round only inspects and reports, use `review-only`.
6. If the round only repairs meaningful documentation content, use `docs-only`.
7. If the round only fixes labels, links, timestamps, counts, or other mechanical routing drift, use `metadata-sync`.
8. If the round promotes a repeated stable pattern into a reusable guardrail, use `lesson-promotion`.
9. If the round changes routing structure, use `index-split` or `archive-or-supersede`.

## Lane Rules

### `metadata-sync`

- keep the edit mechanical
- verify the source of truth for every count, label, or link
- escalate immediately if any sentence changes meaning

### `docs-only`

- keep one detailed round record and keep other sync surfaces concise
- if wording changes future agent behavior, treat it as semantic and escalate as needed

### `review-only`

- do not patch while reviewing
- separate observed facts from inference

### `probe-only`

- state the probe boundary before running it
- make runner boundary, redaction approach, and artifact set explicit
- do not let probe evidence silently redefine authority

### `implementation`

- keep changes inside accepted scope
- verify with the required repo quality gates
- record what quality-gate source was used

### `substantial-change`

- link the round to an explicit decision or create one in the same round
- update every affected authority surface needed to remove ambiguity
- do not close the round without review

### `authority-change`

- record what old truth is being replaced
- record why the new truth is now accepted
- update spec, design, decision, and authority-routing text consistently

### `lesson-promotion`

- cite repeated or severe evidence
- write the lesson as a durable guardrail, not a task diary
- escalate to `authority-change` if the lesson becomes a mandatory project rule

### `index-split`

- keep the split routing-only unless explicitly approved otherwise
- split on semantic or layer boundaries, not arbitrary `part1/part2/part3`
- tell the user that future reading behavior is being reorganized

### `archive-or-supersede`

- name the replacement active source
- mark the old source clearly as historical, superseded, or archived
- synchronize every route that could still send future agents to the old source first

## Template Routing

When repo-local task templates are enabled:

- `metadata-sync` -> `T0-minor`
- `docs-only`, `review-only`, `probe-only` -> `T1-probe-review-docs`
- `implementation` -> `T2-implementation`
- `substantial-change`, `authority-change` -> `T3-substantial-change`
- `lesson-promotion` -> `T1` by default, upgrade to `T3` if accepted truth also changes
- `index-split`, `archive-or-supersede` -> `T1` by default, upgrade to `T3` if active authority also changes

If the repo only has a generic template, use that repo-local contract and say so explicitly.

