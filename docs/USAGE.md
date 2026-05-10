# Usage Guide

This guide explains how to use the packaged `project-governance` skill after installation.

## Runtime Order

Treat the packaged skill as a routed workflow, not as one giant document.

1. Read `project-governance/SKILL.md`.
2. Let it decide whether the current action needs:
   - `10_runtime_reading_protocol.md`
   - `11_governance_execution_contract.md`
   - one low-frequency sidecar such as `initialization-and-adoption.md`
3. Read only the routed support file(s), not the whole bundle by default.

The packaged skill is designed so the main `SKILL.md` stays focused on runtime routing, while lower-frequency details live in sidecars.

## AGENTS As An Index Surface

Treat project-root `AGENTS.md` as a durable routing and control surface, not as a place to paste a weak summary copy of the whole governance workflow.

Use this pattern:

- keep only short durable rules in `AGENTS.md`
- route from `AGENTS.md` into the full support protocol or sidecar only when needed
- when `AGENTS.md` points to a longer document, include explicit `read when` / `skip when` conditions

This reduces always-loaded token cost and lowers the chance that a short but weaker summary displaces the stronger runtime contract.

## Typical Use Cases

Use the skill when:

- a repository is large or long-running
- multiple document versions already exist
- specs, decisions, and design notes may conflict
- the user wants a documentation-driven workflow
- structural document changes could alter what future agents read first

Skip it when the task is a small change with no governance-sensitive surface.

## Default Governance Model

Default to project-scoped governance:

- `docs/<project-scope>/governance/`
- `docs/<project-scope>/context/`
- `docs/<project-scope>/tasks/`

Use `docs/governance/` only when the user explicitly wants one repository-wide governance layer across multiple projects or experiments.

Stable read-first entrypoints are:

- `00_index_and_priority.md`
- `00_context_index.md`
- `00_task_knowledge_base.md`
- `10_runtime_reading_protocol.md`
- `11_governance_execution_contract.md`

If one of those becomes too large, keep the filename as the stable entrypoint and split below it with second-level routing.

## Initialization And Adoption

Read `initialization-and-adoption.md` only when:

- governance docs do not exist yet
- an existing project must be adopted into the governance system
- the current round is changing the governance foundation

Initialization still requires ask-first behavior. Do not silently create governance docs or overwrite an existing project-root `AGENTS.md`.

## Progressive Disclosure

Use the routed reading contract from `10_runtime_reading_protocol.md`:

- external routing first
- internal routing second
- controlled probing last

Do not default to long `Get-Content -Raw` reads on large governance or task documents when route-first narrowing is still possible.

Once the governing authority set is identified, stop relying on summary-only reading for that item.

## Reading And Non-Reading Cases

To reduce context waste, do not stop at “this file exists.” Define when each longer document should and should not be read.

Read a longer protocol or sidecar when:

- the current action enters that document's decision surface
- the main router no longer contains enough detail for a safe next step
- failing to read it would leave authority, sync, closure, or routing judgment under-specified

Skip it when:

- the round is pure chat or light brainstorming
- the current action has not yet entered that protocol's responsibility surface
- the main routing document is already sufficient for the immediate next action

This is why the packaged governance skill uses explicit `read when` / `skip when` sections across its support protocols and sidecars.

## AGENTS Template Design

The packaged `project-root-AGENTS.template.md` is intentionally short.

It should:

- carry only durable project-local collaboration rules
- point to the full reading or execution protocol when the current action actually needs it
- avoid duplicating the full governance workflow in always-loaded text

## Structural Maintenance

When routing, index, archive, supersede, or promotion work changes future reading behavior:

- notify the user explicitly
- route into `11_governance_execution_contract.md`
- keep routing surfaces and their downstream targets synchronized in the same round

## Example Prompts

- `Use $project-governance to initialize project-scoped governance for slug browser-runtime-migration.`
- `Use $project-governance to adopt this repository's existing docs into the governance system.`
- `Use $project-governance to route this governance-sensitive round and load only the required protocol files.`
- `Use $project-governance to update the task record, audit, and active plan after today's implementation round.`
