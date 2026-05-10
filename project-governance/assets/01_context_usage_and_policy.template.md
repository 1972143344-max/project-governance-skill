# Context Usage And Policy

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/context/
Project scope slug: <stable-slug>

## Maintenance Threshold

Document role: `recovery-policy`
Advisory threshold: `180 lines`
Split threshold: `260 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this recovery-policy document should be split and rerouted rather than continue growing as one file.
Even below the split threshold, surface the same recommendation if recovery-writing rules and recovery-reading rules have become hard to navigate together.
Do not silently restructure this document during unrelated work.

## Purpose

This document defines how the project-scoped context layer should be used:

- what belongs in `context/`
- what does not belong in `context/`
- when to create or update context shards
- how agents should read context after compression, pause, or handoff
- how `context/` relates to authoritative governance docs

## Authority Boundary

- `docs/<project-scope>/governance/` is authoritative.
- `docs/<project-scope>/context/` is working/reference only.
- Routing indexes and summary headers are for triage, not project truth.
- If governance and context disagree, governance wins.
- If context and a routing summary disagree, the context shard wins.
- Stable constraints, decisions, design rules, and reusable lessons should not remain context-only forever; promote them into governance when they become durable.

## Context Layer Structure

- `00_context_index.md`: routing index for context shards
- `01_context_usage_and_policy.md`: local context rules for this project
- `shards/`: active context shards grouped by topic or subtask
- `archive/`: optional archive for older shards kept for traceability

## Context Unit Standard

Each context shard should preserve effective full context through one or more `Context Unit` entries instead of verbatim chat dumps.

Each context unit should capture, when relevant:

- time range
- topic or subtask
- status
- related files
- related governance docs
- keywords
- read this when
- skip this when
- session summary
- effective full context
- core constraints
- decisions and non-decisions
- open questions
- lessons or reusable patterns
- supersedes / superseded by

## Write Triggers

Create or update a context shard when:

- a new hard constraint was introduced or corrected
- a direction-changing decision was made
- a debugging chain reached a meaningful stage conclusion
- the task is about to pause, hand off, or compress context
- a long-running task enters a new phase
- a stable failure mode, eliminated path, or reusable lesson was discovered

## Index Synchronization Rule

- Treat shard update plus `00_context_index.md` update as one atomic action.
- If a shard is added, split, merged, archived, superseded, downgraded, or promoted to governance, update the index in the same round.
- Do not leave the index pointing at outdated shard state after a semantic change.

## Conflict And Pollution Control

- Keep explicit status on shards and context units.
- Use `supersedes` / `superseded by` links when one context record replaces another.
- Do not keep conflicting current-state shards active without clarifying the conflict.
- Mark outdated material as `resolved`, `superseded`, `stale`, or `archived` rather than silently deleting it.
- If a stable conclusion is promoted to governance, downgrade the old context record accordingly.

## Exclusions

Do not write context shards for:

- repeated conclusions with no new recovery value
- low-signal chat turns
- speculative notes that do not affect execution
- information that belongs only in authoritative governance docs without additional recovery value

## Shard Policy

- Split by semantic topic first, not by arbitrary size alone.
- Prefer names like `ctx-<topic>-001.md`.
- Recommended size: `8-12` context units or roughly `6k-10k` Chinese characters per shard.
- Add a summary header near the top of each shard.
- Mark old shards as `resolved`, `superseded`, `stale`, or `archived` instead of leaving status implicit.

## User Notification Rule

- Tell the user explicitly before or while performing key context-maintenance changes that alter future reading behavior.
- Key changes include archive, merge, superseding, downgrading active shards, and promoting stable conclusions into governance docs.
- Small clearly mechanical updates such as fixing timestamps, counts, or short routing summaries may be done without a separate explicit notice if the semantic change was already explained.

## Reading Order

For recovery-sensitive tasks:

1. Read `docs/<project-scope>/governance/00_index_and_priority.md`
2. Read the current authoritative spec
3. Read relevant active plans or decisions
4. Read `docs/<project-scope>/context/00_context_index.md`
5. Read the minimum relevant context shards
6. Expand into design, audit, or lessons docs only as needed

## Compression Recovery Rule

After context compression, handoff, or summarization:

- do not continue blindly from compressed chat memory alone
- re-check the current task, plan, and authoritative constraints
- read the context index if recent execution state matters
- surface uncertainty if the compressed state may have dropped important details

## Hygiene Review Triggers

Review and clean the context layer when:

- the index itself has become noisy
- a topic has accumulated several active shards
- current-state conclusions appear inconsistent
- a shard has outgrown the preferred limit
- repeated handoffs keep reopening stale context

## Notes

- The context layer exists to restore execution continuity, not to duplicate governance docs.
- Do not store secrets, credentials, or sensitive raw payloads here.
