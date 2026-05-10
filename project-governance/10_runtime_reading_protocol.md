# Runtime Reading Protocol

Use this protocol when non-trivial repository work depends on document-reading quality.

## Read This When

Read this document before acting when the round involves:

- non-trivial repo work
- authority, task, or context routing
- deciding between route-first, probing, section expansion, or full-read
- review, planning, implementation, or governance maintenance that depends on document-reading quality

## Skip This When

You may skip this document for:

- pure chat
- light brainstorming with no repo-document lookup
- casual explanation that does not depend on repository routing or authority adjudication

## Core Order

Progressive disclosure is a routing protocol, not a fixed front-window habit.

Use this focused rule:

- prefer external routing first
- then internal routing
- only then allow controlled probing

## External Routing First

For governance-sensitive work, prefer:

- `docs/<project-scope>/governance/00_index_and_priority.md`
- optional repository routing registry, if one exists
- `docs/<project-scope>/context/00_context_index.md`
- `docs/<project-scope>/tasks/00_task_knowledge_base.md`

Use those routing surfaces before opening longer downstream governance or context files.

## Internal Routing Second

If no adequate external routing surface exists, use the target document's own structure:

- summary header
- TOC
- section-routing block
- clear headings
- keywords such as `purpose`, `authority`, `status`, `read this when`, `skip this when`

Section titles and keyword anchors are more robust than line-number routing. Use line numbers only as a convenience, not as the primary routing contract.

## Runtime Document Classes

After routing begins, classify the target surface by function and use the matching default first-read action.

- `routing docs`
  - read the routing document itself first
  - use it to narrow downstream files before opening them
- `single authoritative docs with internal structure`
  - first inspect summary header, TOC, section-routing block, headings, or authority markers
  - then expand only the relevant section set
- `large registries or knowledge bases`
  - first search by task id, keyword, filename, subsystem, or other narrowing anchor
  - do not treat the registry itself as a normal whole-file first read
- `recovery or context shards`
  - first read `00_context_index.md`
  - then open only the minimum relevant shard set
- `low-frequency sidecars or references`
  - read them only when the main file or current action explicitly routes into them

## Avoided Reading Patterns

When relevance is still uncertain:

- do not default to `Get-Content -Raw` on long documents
- do not use fixed large front-window reads as a substitute for routing
- do not bulk-open multiple long downstream documents before narrowing

## Controlled Probing Last

Use probing only when:

1. no adequate external routing surface exists, or
2. no adequate internal routing surface exists, or
3. the available routing surface still does not identify the governing section safely

Every probe must answer a bounded question.

Before probing, be able to state:

- what question the probe is answering
- why routing alone was not enough
- what structure, rule, or boundary the probe expects to confirm

If you cannot state those three things, stop probing and reassess.

Keep probing narrow:

- use it to confirm structure, governing relevance, or section boundaries
- if probing succeeds, return to targeted section expansion
- if probing fails, say why routing was insufficient before expanding further

## Governing Expansion

Once governing material is identified, continue reading until the action-ready authority set is loaded.

For governance-sensitive work, this usually means loading enough material to know:

- the active authority boundary
- the active structural boundary
- the next safe maintenance action

Do not stop at summary-only reading once the governing document set is known.

## Stop Rule

Stop expanding when all three are true:

1. the governing material is identified
2. the minimum authority set needed for the next action is loaded
3. further reading would not materially change the next action, ownership boundary, or safety judgment

If you cannot explain why the next document or section is needed, stop and reassess.

## Short Routing Patterns

- governance maintenance: start with `00_index_and_priority.md`
- recovery or handoff state: start with `00_context_index.md`
- task-history lookup: start with `00_task_knowledge_base.md`, then open the relevant record only
- no external routing surface: fall back to the target document's internal routing before broader probing

## Governance-Sensitive Actions

Treat these as governance-sensitive actions that require deliberate reading before editing:

- initializing or adopting governance
- changing authority order, reading order, or document status
- performing structural maintenance that changes what future agents read first
- promoting conclusions from recovery or execution into authority or learning
- writing closure docs meant to represent completed-state truth

## Truth Boundary

Repeat this rule wherever routing and context maintenance meet:

- governance docs are authoritative
- `context/` is working or reference unless explicitly promoted
- if governance and context disagree, governance wins
