# Task Knowledge Base

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Storage root: `docs/<project-scope>/tasks/`
Document role: routing-only
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

- Provide a searchable index for completed engineering tasks.
- Help future contributors avoid repeated mistakes by routing them to relevant historical records first.

## Role-Change Sync Rule

If this document changes role, update its header, purpose, routing notes, and the governing index in the same round.

## Usage Rule

- Before starting a new task, search this file for matching keywords, files, modules, or requirement IDs.
- Then open only the most relevant task records.
- After completing a task, add or update its record immediately and refresh this index.

## Template Routing

- If task-template tiering is active, read `docs/<project-scope>/tasks/templates/00_task_template_index.md` before choosing a task-record template.
- Then create or update the narrowest truthful task record under `docs/<project-scope>/tasks/records/`.

## Records

### `TASK-0001`

- Title:
- Path:
- Keywords:
- Related files:
- Linked requirements:
- Read this when:
