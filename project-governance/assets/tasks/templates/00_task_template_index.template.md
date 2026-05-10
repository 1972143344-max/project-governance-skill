# Task Template Index

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/tasks/templates/
Project scope slug: <stable-slug>
Document role: routing-only
Layer: execution
Index grade: `1`
Index family: `execution routing`

## Maintenance Threshold

Document role: `routing-doc`
Advisory threshold: `140 lines`
Split threshold: `200 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this document should be split or given a second-level routing surface before future growth continues.
Even below the split threshold, surface the same recommendation if routing quality has clearly degraded.
Do not silently restructure this document during unrelated work.

## Purpose

Use this index to choose the narrowest task-record template that truthfully matches the round.

This file is normally a `Grade 1` execution-routing surface. It helps route readers from lane classification into the correct task-record template family. It does not replace the lane-control surface itself.

## Template Selection

| Template | Use for | Avoid when |
| --- | --- | --- |
| `T0-minor.template.md` | metadata-only or minor routing/doc sync with no semantic impact | the round changes execution boundary, authority, or runtime evidence |
| `T1-probe-review-docs.template.md` | probe-only, review-only, or meaningful docs-only rounds | the round changes code, config, tests, or accepted truth |
| `T2-implementation.template.md` | standard feature, bug fix, hardening, or refactor work | the round is authority-changing or broad architectural change |
| `T3-substantial-change.template.md` | substantial change or authority-changing work | the round is routine implementation or minor maintenance |

## Lane-To-Template Defaults

| Lane | Default template | Upgrade rule |
| --- | --- | --- |
| `lesson-promotion` | `T1-probe-review-docs.template.md` | Upgrade to `T3-substantial-change.template.md` if the promotion becomes a mandatory rule or changes accepted truth. |
| `index-split` | `T1-probe-review-docs.template.md` | Upgrade to `T3-substantial-change.template.md` if the split also changes authority status or active truth. |
| `archive-or-supersede` | `T1-probe-review-docs.template.md` | Upgrade to `T3-substantial-change.template.md` if the active authoritative source changes. |

## Rules

- Do not fill fields that do not apply just to satisfy a large generic template.
- Upgrade to a stricter template if the round widens in scope.
- Keep the task record detailed enough for audit and recovery, but not heavier than the lane requires.
- If the chosen `T1` round uses `probe-only`, creates or relies on `tasks/artifacts/`, or the project is operating in `probe-heavy` mode, read `08_probe_harness_contract.md` before recording or interpreting evidence.
- If template names or lane-to-template mapping change materially, update this index in the same round or mark it as potentially stale.
- If the task-template family ever becomes too large for one quick scan, split by semantic task family or lane grouping instead of arbitrary chunks, and keep this file as the shallow selector entrypoint.
