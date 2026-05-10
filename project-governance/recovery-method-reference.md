# Recovery Method Reference

Use this sidecar when you are designing, restructuring, or deeply maintaining recovery behavior.

## Recovery Context Units

Treat recovery or context shards as routing-friendly working-state units, not shadow authority files.

A good shard should usually focus on one of:

- one active subsystem frontier
- one unresolved blocker cluster
- one execution checkpoint that future agents would otherwise have to reconstruct expensively

## Recovery Write Triggers

Write or update recovery state when:

- a future agent would need the state after compression, pause, or handoff
- the unresolved boundary matters for safe continuation
- recent execution state would be expensive or risky to reconstruct

## Recovery And Context Exclusions

Do not put durable authority only in recovery form.

Do not use recovery shards as the long-term home for:

- accepted constraints
- accepted decisions
- stable design rules
- reusable lessons

Promote those upward once they become durable.

## Recovery Shards And Capacity

Prefer multiple small, routeable shards over one giant undifferentiated context file.

When recovery routing becomes noisy:

- split by subsystem
- split by unresolved frontier
- split by active versus archived state

## Conflict And Pollution Control

Recovery surfaces should help continuation, not redefine project truth.

If recovery and governance disagree:

- governance wins
- recovery must be corrected, archived, or explicitly marked as stale

## Recovery Hygiene

Keep recovery routing clean:

- index first
- minimum relevant shard count
- explicit stale or superseded status
- atomic shard/index sync

