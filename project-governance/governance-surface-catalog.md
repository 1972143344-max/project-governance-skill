# Governance Surface Catalog

Use this sidecar when you need the full document set, optional governance surfaces, or template routing.

## Standard Governance Set

Default project-scoped governance files:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- `docs/<project-scope>/governance/01_constraints_and_spec.md`
- `docs/<project-scope>/governance/02_design.md`
- `docs/<project-scope>/governance/03_behavior_audit.md`
- `docs/<project-scope>/governance/05_decision_log.md`
- optional but recommended when a real frontier exists: `docs/<project-scope>/governance/06_active_plan.md`
- optional when the learning layer is active: `docs/<project-scope>/governance/04_lessons_learned.md`

## Support Protocol Surfaces

- `10_runtime_reading_protocol.md`
- `11_governance_execution_contract.md`

Treat these as stable support-entrypoint surfaces when the runtime router or project-root `AGENTS.md` routes task rounds into them.

## Standard Recovery Skeleton

- `docs/<project-scope>/context/00_context_index.md`
- `docs/<project-scope>/context/01_context_usage_and_policy.md`
- `docs/<project-scope>/context/shards/`
- optional: `docs/<project-scope>/context/archive/`

## Standard Task Layer

- `docs/<project-scope>/tasks/00_task_knowledge_base.md`
- `docs/<project-scope>/tasks/templates/`
- `docs/<project-scope>/tasks/records/`

Optional task-template tiering:

- `docs/<project-scope>/tasks/templates/00_task_template_index.md`
- `docs/<project-scope>/tasks/templates/T0-minor.md`
- `docs/<project-scope>/tasks/templates/T1-probe-review-docs.md`
- `docs/<project-scope>/tasks/templates/T2-implementation.md`
- `docs/<project-scope>/tasks/templates/T3-substantial-change.md`

## Optional Governance Surfaces

- `04_lessons_learned.md`
  - use when the learning layer is active
- `07_governance_behavior_matrix.md`
  - use when the repo enables repo-local lane control
- `08_probe_harness_contract.md`
  - use when the round is probe-only or the project is probe-heavy
- `09_governance_system_spec.md`
  - use for governance-maintenance or governance-redesign work after the core set is already known

## Repository-Wide Exception

Use `docs/governance/...` only if the user explicitly wants one governance layer shared across multiple projects or experiments.

Optional repository routing helper:

- `docs/governance/00_project_scope_registry.md`

Treat that registry as routing-only, never as project-specific authority.

## Asset Routing

When creating repo-local governance docs, reuse bundled templates under `assets/`:

- file summary headers
- summary indexes
- governance templates
- context templates
- task templates
- project-root `AGENTS.md` template
