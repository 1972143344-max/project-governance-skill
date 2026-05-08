# Probe Harness Contract

Updated: YYYY-MM-DD HH:MM:SS
Status: draft
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: working
Layer: probe

## Purpose

This document defines the project contract for probe-only and evidence-gathering rounds. Use it when runtime, environment, CLI, gateway, artifact, or protocol evidence must be collected without silently widening into ordinary implementation.

This template defaults to a draft working surface. Promote it to an active authoritative probe contract only when the project explicitly enables it in `00_index_and_priority.md` or an accepted authority update, and update the header in the same round.

## Applies To

- live environment probes
- runtime reproduction rounds
- gateway or CLI observation rounds
- artifact-producing evidence collection
- protocol or failure-stage verification
- `review-only` or `docs-only` rounds that create, update, or rely on `tasks/artifacts/`

## Non-Goals

- This document does not replace the spec or design doc.
- This document does not authorize routine product changes under probe-only cover.
- This document does not require every project to run in probe-heavy mode.

## Core Rules

1. Probe-only rounds must declare a boundary before execution.
2. Rounds that use `probe-only`, create or rely on `tasks/artifacts/`, or run in `probe-heavy` mode must read and follow this contract before acting.
3. Probe-only rounds must identify the runner, target environment, and intended evidence.
4. Probe-only rounds must state the failure stage or verified boundary explicitly.
5. Probe-only artifacts must be reviewed for redaction before check-in.
6. Probe-only rounds may inform authority or execution, but do not redefine authority unless explicitly promoted.

## Allowed Surfaces

- dedicated probe runners or scripts
- task records using the `T1` probe-oriented template
- artifact bundles under `tasks/artifacts/`
- concise audit entries
- active plan only when the frontier or blocker interpretation changes

## Prohibited Actions

- silent product code changes while claiming probe-only scope
- storing secrets, tokens, or unredacted sensitive output in committed artifacts
- claiming success from partial or indirect evidence
- rewriting spec or design simply because a probe was re-run

## Required Probe Declaration

Before running a probe, record:

- Probe family / ID:
- Purpose:
- Lane: `probe-only`
- Runner / entrypoint:
- Environment:
- Expected evidence:
- Redaction plan:
- Success boundary:
- Failure boundary:

## Artifact Minimums

Capture only the minimum evidence needed:

- command or runner used
- environment or target identity
- artifact paths
- redaction status
- task record or evidence bundle link

## Review Gate

Review is required when the probe output justifies:

- a blocker claim
- a risk reordering
- an active-plan change
- a recommendation to change accepted truth

Review focus:

- redaction
- overclaim
- artifact consistency
- boundary accuracy

## Promotion Rules

Promote from probe-only to:

- `implementation` when the round intentionally changes product behavior
- `authority-change` when accepted truth must change
- `lesson-promotion` when the probe reveals a reusable future guardrail
