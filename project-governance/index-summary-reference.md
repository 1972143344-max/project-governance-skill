# Index And Summary Reference

Use this sidecar when you are designing or restructuring routing surfaces.

## Graded Index Model

Prefer a shallow graded index:

- Grade 0: scope entrypoint
- Grade 1: layer indexes or active authority docs
- Grade 2: detailed records and evidence

Indexes should route. They should not duplicate full underlying content.

## File-Level Summary Headers

When a document is long or frequently revisited, prefer a compact summary header near the top.

Useful fields:

- purpose
- status
- authority
- scope
- read this when
- skip this when
- key sections
- last materially updated

Use summary headers for routing, not to replace the authoritative body.

## Summary Indexes

When a project has many relevant files, propose a summary index that helps the agent choose which files to open next.

A good summary index should include:

- file path
- document role
- short summary
- when to read it
- whether it is authoritative, working, or historical

## Large Index Rule

If an index becomes too noisy to route efficiently, maintain a second-level routing structure instead of forcing the agent to rescan a giant first-level index forever.

Good split boundaries include:

- active versus historical
- topical clusters
- per-scope sub-indexes
- milestone-based task slices

## Split Rules

Split on semantic or layer boundaries, not arbitrary `part1/part2/part3`.

Good split examples:

- current spec versus historical reference
- design versus decision log
- audit log versus lessons learned
- active rules versus archived material

## Drift And Bloat Control

A routing surface is stale when:

- the linked authoritative document changed materially but the routing surface did not
- a recovery shard changed status but the recovery index still presents the old state
- a superseded record still appears as the preferred route

Use these controls:

- periodic checkpoint summaries for ever-growing audit logs
- deduplication for overlapping lessons when cleanup is wanted
- shallow trees by default
- route-friendly indexes rather than aggressive arbitrary truncation

