# Summary Index

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project-scope or repository-scope>
Document role: routing-only
Index grade: `1 | 2`
Index family: `authority routing | execution routing | recovery routing | learning routing | mixed`

## Maintenance Threshold

Document role: `routing-doc`
Advisory threshold: `140 lines`
Split threshold: `200 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this document should be split or given a second-level routing surface before future growth continues.
Even below the split threshold, surface the same recommendation if routing quality has clearly degraded.
Do not silently restructure this document during unrelated work.

## Purpose

This index is a routing surface across multiple related files. It helps the reader choose the next file to open without restating the full contents of those files.

This template is never a substitute for `00_index_and_priority.md` and must not be used as an alternate Grade 0 entrypoint.

## Role-Change Sync Rule

If this document changes role, update its header, purpose, routing notes, and the governing index in the same round.

## Grade Meaning

- `1`: layer index or active contract surface
- `2`: detailed record or evidence routing surface

Choose the lightest truthful grade for this index. Grade 0 belongs to the project entrypoint, not to summary indexes.

## Reading Rule

- Read this index first when multiple files are plausible.
- Use it to choose the next file to open.
- If a listed file is authoritative for the current question, read the relevant section in that file before relying on the summary alone.
- Do not use this file to redefine authority order or scope entrypoint behavior.

## Split Policy

- Keep the tree shallow.
- Split this index only when routing itself becomes noisy, topics diverge, or freshness becomes hard to maintain.
- Prefer semantic or layer-based splits over `part1/part2/part3`.

## Entries

### `<label>`

- Path:
- Role: `authoritative | routing-only | working | historical/reference`
- Layer:
- Status:
- Summary:
- Read this when:
- Skip this when:
- Freshness notes:

## Notes

- Keep entries short and routing-oriented.
- Do not restate full spec, design, or decision content here.
- If a linked file changes materially, update the corresponding entry or mark it as potentially stale.
