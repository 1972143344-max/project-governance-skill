# Project Scope Registry

Updated: <timestamp>
Status: active
Scope: repository-level routing
Doc root: docs/governance/

Purpose: repository-level routing only. This document does not define project spec, design, decisions, or project-specific overrides.

## Routing Rules

- If the user explicitly names a project, experiment, or scope slug, use that scope.
- If multiple scopes are plausible and the active scope is unclear, ask the user before proceeding.
- After selecting a scope, read `docs/<project-scope>/governance/00_index_and_priority.md` first if it exists.
- If the task is explicitly repository-wide, use repository-level governance docs instead of any one project scope.

## Authority Boundary

- This registry is routing-only.
- It must not define project spec, design, decisions, or implementation details.
- It must not override `docs/<project-scope>/governance/`.
- On project-specific matters, project-scoped governance always wins.

## Registered Scopes

### `<scope-slug>`

- Status: active | working | historical | archived
- Doc root: `docs/<scope-slug>/governance/`
- Entry doc: `docs/<scope-slug>/governance/00_index_and_priority.md`
- Summary:
- When to use:
- Do not confuse with:

## Notes

- Add a scope here only when it is a meaningful long-running project, experiment, or governance island.
- Do not duplicate project spec, design, or decision details here; link to the project governance entry instead.
