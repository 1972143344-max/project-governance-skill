# Governance Workflow

Use this workflow when a project is large, long-running, or at risk of context drift.

## Goals

- keep one current source of truth
- reduce stale-file interference
- separate stable collaboration rules from changing project details
- preserve traceability for decisions and meaningful actions

## Recommended Lifecycle

### 1. Initialize

Create governance docs only after the user confirms.

Default to project-scoped governance under `docs/<project-scope>/governance/`.
Use `docs/governance/` only when the user explicitly wants repository-wide governance.

Use a stable scope slug for `<project-scope>`, preferably lowercase letters, digits, and hyphens only.

Recommended first step:

- confirm the active project scope and stable slug
- ask whether to initialize a project-root `AGENTS.md`
- create `docs/<project-scope>/governance/00_index_and_priority.md`

Then create the other requested docs.

### 2. Adopt Existing Project Docs

When the repo already contains many docs:

- classify them within the active project scope unless the task is explicitly repository-wide
- classify each important document as authoritative, working, or historical/reference
- do not mass-edit older files during adoption
- record document priority and conflict order before relying on the old set

### 3. Plan Before Significant Changes

If changes affect spec, design scope, runtime behavior, evaluation behavior, data flow, or document authority:

- discuss first
- ask whether to create/update a decision record
- ask whether to persist an active plan

### 4. Sync After Changes

After meaningful changes:

- audit what happened
- update spec if current rules changed
- update design if implementation details changed
- write lessons only when a reusable pattern or pitfall emerged
- perform a review pass for major changes before closing the task
- if uncertainty remained during implementation, explicitly disclose it to the user instead of hiding it in a successful-sounding summary

## Minimal Update Matrix

- Code/config changed, but no rule change:
  - audit
- Rule/constraint changed:
  - audit + spec
- Implementation design changed:
  - audit + design
- Conflict resolved through explicit choice:
  - audit + decision log
- Reusable lesson discovered:
  - audit + lessons learned

## Do Not

- do not silently create the governance doc set
- do not silently rewrite history
- do not silently downgrade old documents
- do not treat timestamps alone as authority
