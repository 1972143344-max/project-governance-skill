# Lessons Learned

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: working
Layer: learning

## Maintenance Threshold

Document role: `learning-index`
Advisory threshold: `180 lines`
Split threshold: `260 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this lesson index should be split or rerouted before future growth continues.
Even below the split threshold, surface the same recommendation if active lessons and historical lessons are becoming hard to distinguish quickly.
Do not silently restructure this document during unrelated work.

## Purpose

This file is the lesson index for reusable governance or execution guardrails that should influence future agent behavior beyond one task.

Use this file to:

- route readers to active lessons
- summarize why a lesson was promoted
- link each lesson back to evidence or source rounds

Do not use this file as a full task diary. One-off observations stay in task records unless they are promoted.

## Promotion Rules

Promote a lesson when one of these becomes true:

- the same pattern recurs
- the pattern is severe or high-risk even if seen once
- the pattern would materially change future workflow
- the pattern concerns authority drift, overclaim, redaction, recovery misuse, or routing failure

Upgrade from lesson to `authority-change` when the lesson becomes a mandatory repository rule rather than guidance.

## Index

| Lesson ID | Title | Status | Category | Promoted from | Read this when | Escalates to authority? |
| --- | --- | --- | --- | --- | --- | --- |
| `LES-0001` | <short title> | `active | superseded` | `governance | execution | recovery | probe | review` | `TASK-xxxx / audit entry / decision` | <when it matters> | `yes | no` |

## Entry Template

### `LES-0001` - <short title>

- Status: `active | superseded`
- Category: `governance | execution | recovery | probe | review`
- Problem pattern:
- When to apply:
- Do:
- Do not:
- Promotion source:
- Related authority / decisions:
- Supersedes / superseded by:

## Notes

- Keep index entries short enough for routing.
- Put large or evolving lessons in `governance/lessons/LES-*.md` and keep this file as the layer entrypoint.
- If a lesson changes future reading behavior materially, call that out explicitly while promoting it.
