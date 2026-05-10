# Behavior Audit

Updated: YYYY-MM-DD HH:MM:SS
Status: active
Scope: <project or subsystem scope>
Doc root: docs/<project-scope>/governance/
Project scope slug: <stable-slug>
Document role: working
Layer: execution

## Maintenance Threshold

Document role: `append-only-audit`
Advisory threshold: `260 lines`
Split threshold: `400 lines`

If this document exceeds the advisory threshold, explicitly tell the user that maintenance review is recommended.
If this document exceeds the split threshold, explicitly tell the user that this append-only document should be checkpointed, archived by phase, or split into routed shards before future rounds continue appending to it.
Even below the split threshold, surface the same recommendation if recent-history lookup or active-use routing has clearly become noisy.
Do not silently restructure this document during unrelated work.

## Purpose

This file is the append-only audit summary for meaningful rounds. It records:

- what kind of round occurred
- why it was run
- what surfaces were changed
- what result was achieved
- what risk, blocker, or follow-up remains

This file is not a second spec and not a full task diary. Detailed implementation or evidence belongs in task records and artifacts.

## Entry Format

Use one concise entry per meaningful completed round.

### YYYY-MM-DD HH:MM:SS - <short title>

- Lane: `docs-only | metadata-sync | review-only | probe-only | implementation | substantial-change | authority-change | lesson-promotion | index-split | archive-or-supersede`
- Purpose:
- Scope:
- Changed surfaces:
- Result:
- Evidence / task record:
- Frontier impact: `none | active plan updated | blocker changed | risk order changed`
- Authority impact: `none | proposed | accepted`
- Notes:

## Checkpoint Summary

Use this section only when the audit log becomes long enough that route-first reading is noisy.

- Latest stable checkpoint:
- Read from this timestamp when:
- Earlier entries may be skipped when:

## Entries

### YYYY-MM-DD HH:MM:SS - <round summary>

- Lane:
- Purpose:
- Scope:
- Changed surfaces:
- Result:
- Evidence / task record:
- Frontier impact:
- Authority impact:
- Notes:
