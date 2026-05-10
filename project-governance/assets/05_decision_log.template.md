# Decision Log

Updated: YYYY-MM-DD HH:MM:SS
Status: draft
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>

## Maintenance Threshold

Document role: `authority-doc`
Advisory threshold: `200 lines`
Split threshold: `300 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this authority document should be split and rerouted rather than continue growing as one file.
Even below the split threshold, surface the same recommendation if accepted, proposed, and superseded decisions have become hard to scan separately.
Do not silently restructure this document during unrelated work.

## Decision Identifier Contract

Use stable decision IDs so task records, plans, audits, and later governance docs can cite decisions without depending on title wording alone.

- Pattern: `DEC-0001`, `DEC-0002`, `DEC-0003`, ...
- Keep IDs unique and never reuse them, even if a decision is later rejected or superseded.
- Cite decision IDs in downstream docs whenever a round depends on an accepted or proposed decision.

## Entry Template

### Decision: <title>

- Decision ID: `DEC-0001`
- Timestamp:
- Status: proposed | accepted | superseded | rejected
- Background:
- Options considered:
- Final decision:
- Rationale:
- Risks:
- Affected scope:
- Supersedes:

## Decisions

### Decision: <title>

- Decision ID:
- Timestamp:
- Status:
- Background:
- Options considered:
- Final decision:
- Rationale:
- Risks:
- Affected scope:
- Supersedes:
