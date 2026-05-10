# Active Plan

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: working
Layer: execution

## Maintenance Threshold

Document role: `active-plan`
Advisory threshold: `80 lines`
Split threshold: `120 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this active plan is becoming a second spec and should be shortened or split so the active frontier remains easy to read.
Even below the split threshold, surface the same recommendation if historical explanation is crowding out the current frontier.
Do not silently restructure this document during unrelated work.

## Purpose

This file records the current execution frontier. It is not a long-term project ledger and it does not replace the spec or decision log.

Use it to preserve:

- the current frontier
- the next approved package of work
- the live blocker or risk boundary
- what is explicitly out of scope for the current round

## Current Frontier

- Objective:
- Current lane:
- Working boundary:
- Why this is the current frontier:

## Next Package

1. <next step>
2. <next step>
3. <next step>

## Current Blocking Risks

| Risk ID | Status | Boundary | Evidence | Next check |
| --- | --- | --- | --- | --- |
| `RSK-0001` | `open | mitigated | blocked` | <where the blocker currently sits> | <task record / artifact / decision> | <what resolves or re-checks it> |

## Out Of Scope For This Frontier

- <what this round should not widen into>

## Read / Update Rules

Read this file when:

- the current frontier may change
- blocker ownership or failure stage may change
- next-step ordering matters

Update this file only when one of these becomes true:

- the frontier moves forward or backward
- a blocker boundary changes
- risk order changes
- the next package changes
- the user reprioritizes work

Do not update this file for:

- mechanical metadata fixes
- round completion with no frontier impact
- purely historical notes that belong in task records
