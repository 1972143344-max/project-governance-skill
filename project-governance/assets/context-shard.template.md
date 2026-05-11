## Maintenance Threshold

Document role: `context-shard`
Advisory threshold: `120 lines`
Split threshold: `180 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this shard should be split or replaced with narrower routed shards before future growth continues.
Even below the split threshold, surface the same recommendation if one shard now mixes multiple unresolved fronts that future agents usually need separately.
Do not silently restructure this document during unrelated work.

## Summary Header

- Purpose:
- Status: active | blocked | resolved | superseded | stale | archived
- Document role: `working`
- Layer: `recovery`
- Scope:
- Authority source:
- Read this when:
- Skip this when:
- Key sections:
- Last materially updated:
- Freshness notes:
- Related docs:

## Role-Change Sync Rule

If this document changes role, update its header, purpose, routing notes, and the governing index in the same round.

## Context Unit: `<id>`

- Time range:
- Topic / subtask:
- Status: active | blocked | resolved | superseded | stale
- Related files:
- Related governance docs:
- Keywords:
- Read this when:
- Skip this when:

### Session Summary

-

### Effective Full Context

-

### Core Constraints

-

### Decisions / Non-Decisions

-

### Open Questions

-

### Lessons / Reusable Patterns

-

### Supersedes / Superseded By

-

## Notes

- Preserve effective execution state, not verbatim transcript dumps.
- If this shard conflicts with governance docs, governance wins.
