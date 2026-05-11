# Context Index

Updated: <timestamp>
Status: active | standby | archived
Scope: <project-scope>
Doc root: docs/<project-scope>/context/
Document role: routing-only
Index grade: `1`
Index family: `recovery routing`

## Maintenance Threshold

Document role: `routing-doc`
Advisory threshold: `140 lines`
Split threshold: `200 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this document should be split or given a second-level routing surface before future growth continues.
Even below the split threshold, surface the same recommendation if routing quality has clearly degraded.
Do not silently restructure this document during unrelated work.

Purpose: lightweight routing across project-scoped context shards. This index helps recover effective execution state after compression, pause, or handoff. It does not replace authoritative governance documents.

This file is normally a `Grade 1` recovery index used after the scope entrypoint and active authority path are already known.

## Role-Change Sync Rule

If this document changes role, update its header, purpose, routing notes, and the governing index in the same round.

## Reading Rule

- Read this index when the task depends on recent execution history, handoff state, or compressed chat recovery.
- Use it to select the minimum relevant context shards to open next.
- If the current question is answered by authoritative governance docs alone, prefer those first.
- If a shard is marked `active`, `blocked`, or `unresolved`, prefer it over older resolved shards when the topic matches.

## Entries

### `<label>`

- Path:
- Topic:
- Time range:
- Status: active | blocked | resolved | superseded | stale | archived
- Supersedes / Superseded by:
- Keywords:
- Context units:
- Summary:
- Read this when:
- Skip this when:
- Freshness:
- Notes:

## Notes

- Keep entries short and routing-oriented.
- Do not restate the full contents of the shard here.
- If a shard changes materially, update its entry or mark it as potentially stale.
- If a shard is archived, merged, superseded, or promoted to governance, reflect that state here in the same update round.
- If a shard conflicts with governance docs, governance wins.
- If recovery routing itself becomes noisy, split by semantic topic, phase, or sub-project and keep this file as the shallow entrypoint into the recovery index family.
