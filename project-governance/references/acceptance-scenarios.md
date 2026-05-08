# Governance Acceptance Scenarios

Use these scenarios to check whether the `project-governance` skill can initialize and maintain a project in a way that stays aligned with repository-local authority docs.

These are acceptance scenarios for the skill workflow, not repository-local truth. They should be used to evaluate whether the skill, its references, and its templates support the intended lifecycle.

## How To Use This File

- choose the scenario that matches the task
- compare the observed skill behavior against the acceptance criteria
- treat failures as skill-design or maintenance gaps, not as justification to override repo-local authority
- when a repository already defines its own governance-system spec or behavior matrix, those project docs remain the authority for that repository

## Scenario 1: New Project Initialization In `core` Mode

Given:

- a new non-trivial project with no governance docs

Accept when:

- a project-scoped governance root is created unless the user explicitly requested repository-wide governance
- the authority skeleton exists
- the context skeleton exists
- the task knowledge base exists
- the scope slug and governance root are explicit
- `AGENTS.md` stays short and durable instead of becoming the full workflow manual
- probe-heavy or extended-only surfaces were not forced without need

Reject when:

- the skill initializes the heaviest governance mode by default
- `AGENTS.md` absorbs detailed project truth
- initialization happens without user confirmation

## Scenario 2: New Project Initialization In `extended` Mode

Given:

- a long-running project with repeated rounds, likely handoffs, and expected design drift risk

Accept when:

- the `core` skeleton exists
- an active-plan surface is initialized or clearly supported
- recovery routing and shard support are available
- lesson promotion is supported as a first-class workflow
- summary-entry maintenance is supported for high-frequency or high-risk docs
- if task-template tiering is enabled, AGENTS or routing surfaces point readers to the task-template index instead of only naming `T0` to `T3`
- the skill does not claim that every document needs a summary header immediately

Reject when:

- the skill creates execution-heavy surfaces but provides no maintenance guidance
- the skill turns every round into a broad authority sync by default

## Scenario 3: New Project Initialization In `probe-heavy` Mode

Given:

- a project where runtime probes, environment evidence, and artifact handling are first-class workstreams

Accept when:

- the `extended` skeleton exists
- probe work is explicitly recognized as its own layer or contract surface
- runner isolation, artifact handling, and redaction expectations are supported
- AGENTS or routing surfaces explicitly route probe-heavy rounds to the probe contract before artifacts are relied on
- probe closure is distinguishable from implementation closure
- the skill does not imply that probe evidence automatically changes project truth

Reject when:

- probe work is collapsed into ordinary implementation without boundary rules
- the skill lacks any mechanism for probe-only routing or artifact discipline

## Scenario 4: Docs-Only Round With No Authority Change

Given:

- a meaningful docs round that repairs wording, drafts guidance, or aligns docs without changing accepted truth

Accept when:

- the skill chooses a docs-only lane
- execution surfaces are updated only when the round is meaningful enough to preserve
- authority docs remain unchanged unless accepted truth actually changed
- review is required only when the semantic meaning or future behavior changed

Reject when:

- the skill treats every docs round as authority change
- the skill requires irrelevant sync surfaces just to satisfy a template

## Scenario 4A: Metadata-Sync Round

Given:

- a mechanical update that only repairs timestamps, links, labels, counts, or short routing summaries after the semantic change is already explained elsewhere

Accept when:

- the skill chooses a `metadata-sync` lane
- the edit stays mechanical and does not quietly reinterpret project truth
- the source of truth for each refreshed field is checked before editing
- the skill escalates if a sentence-level semantic rewrite becomes necessary

Reject when:

- the skill uses `metadata-sync` to smuggle in a semantic governance change
- the skill triggers broad execution or authority sync for a purely mechanical refresh

## Scenario 4B: Review-Only Round

Given:

- a read-only audit, inspection, or review round that should not change repo behavior during the review itself

Accept when:

- the skill chooses a `review-only` lane
- review findings stay separated from fixes or speculation
- no opportunistic edits are made while the round still claims to be review-only
- any persisted review artifact remains clearly framed as review output rather than updated authority

Reject when:

- the skill patches files while still describing the round as `review-only`
- the skill promotes lessons or authority changes without a follow-up lane or explicit escalation

## Scenario 5: Probe-Only Investigation

Given:

- a read-mostly probe round intended to establish a verified boundary, failure stage, or environment fact

Accept when:

- the skill chooses a probe-only lane
- probe scope and runner boundary are made explicit
- artifacts and redaction are treated as first-class concerns
- the round records the verified boundary or failure stage without overstating closure
- authority remains unchanged unless the round is explicitly upgraded

Reject when:

- the skill silently widens probe work into implementation
- the skill treats re-observed evidence as accepted truth by default

## Scenario 5A: Implementation Round

Given:

- a feature, fix, hardening pass, or refactor that changes code, config, or tests within already accepted project truth

Accept when:

- the skill chooses an `implementation` lane
- the skill reads the active frontier and decision constraints before changing behavior
- verification expectations are made explicit for the touched surface
- before claiming delivery complete, the skill locates and runs the repo-local quality gate for the touched surface
- if the quality gate is inferred from existing repository execution surfaces rather than explicitly declared, the skill says so instead of pretending it is formal policy
- repo-required same-round execution closure can directly update the task record, task knowledge base, behavior audit, active plan, and atomic context-index/shard state sync when the round is only closing execution surfaces
- execution sync is limited to the surfaces the implementation actually changed unless the lane is upgraded

Reject when:

- the skill treats ordinary implementation as a docs-only or probe-only round
- the skill blocks required execution-layer closeout behind a fresh approval ask even though no authority or structural reading change is being made
- the skill silently changes accepted truth without escalating to `authority-change` or `substantial-change`
- the skill claims delivery complete without locating a repo-local quality gate or disclosing that the gate had to be inferred

## Scenario 6: Authority Change Round

Given:

- accepted project truth changes, whether or not code changes at the same time

Accept when:

- the skill upgrades to an authority-changing lane
- the changed truth is recorded in the proper authority surfaces
- a decision trace is preserved when needed
- execution surfaces are updated only when the frontier or round history also changed
- the skill does not hide unresolved conflicts between old and new authority text

Reject when:

- the skill buries accepted truth only inside task history
- the skill edits authority surfaces without any authority-specific reasoning or trace

## Scenario 7: Stale Summary Or Routing Surface Detected

Given:

- a summary header or routing index looks older than the linked active authority

Accept when:

- the skill treats the routing surface as stale
- the authoritative section is read directly for the current decision
- the routing surface is refreshed or marked stale in the same round when scope allows
- the stale routing surface is not presented as the current truth

Reject when:

- the skill trusts the stale summary because it is shorter
- the skill leaves stale routing unmarked after discovering the mismatch

## Scenario 8: Index Split Decision

Given:

- a routing surface has grown large enough that repeated scans are noisy and users usually need only one semantic subset

Accept when:

- the skill classifies the work as structural maintenance
- the split happens on semantic or layer boundaries
- the resulting tree stays shallow
- old and new routes clearly point to the active destinations
- the user is explicitly notified that future reading behavior is being reorganized

Reject when:

- the split is arbitrary `part1/part2/part3`
- the skill creates deep routing trees by default
- structural reorganization happens silently

## Scenario 8A: Archive-Or-Supersede Round

Given:

- an older document, shard, or routing surface is no longer the active read path and must be clearly retired or replaced

Accept when:

- the skill classifies the work as `archive-or-supersede`
- the replacement active source is named explicitly
- affected indexes and routing surfaces are synchronized in the same round
- the user is explicitly told that future reading behavior is changing

Reject when:

- the skill silently retires an older surface without naming the replacement
- the old route remains discoverable as if it were still active

## Scenario 9: Ordinary Route-First Index Use

Given:

- a non-trivial task where multiple governance, execution, or recovery surfaces are plausible

Accept when:

- the grade-0 entrypoint routes the reader to the next relevant authority or layer surface
- the selected grade-1 routing surface makes the next detailed file discoverable
- the reader stops relying on routing-only text once the relevant authority or active frontier is identified
- the templates do not force a full-doc reload of every governance file by default

Reject when:

- a routing surface names files but does not help the reader choose the next hop
- the templates treat summary-only reading as sufficient after the relevant authority is known

## Scenario 9A: Repo-Local Lane Alias And Template Contract

Given:

- a repository defines repo-local lane spellings in its behavior matrix, task-template index, or equivalent governance surface

Accept when:

- the skill preserves the canonical lane meaning internally
- the skill uses the repo-local spelling in user-facing output and persisted repository records when the repository defines one
- lane-to-template routing follows the lane meaning rather than exact punctuation or separator style
- the skill distinguishes adopted repo-local templates under `docs/<project-scope>/tasks/templates/*.md` from bundled skill assets under `assets/tasks/templates/*.template.md`
- if the repository only has a generic repo-local template such as `task_record.template.md`, the skill says lane-tiered repo-local templates are not yet enabled instead of inventing them

Reject when:

- the skill forces canonical spellings into repo-local records despite a defined repo-local matrix
- the skill confuses repo-local `.md` templates with bundled `.template.md` skill assets

## Scenario 10: Compression Re-entry

Given:

- context was compressed, summarized, or resumed after a pause

Accept when:

- the skill re-checks the active task
- the skill re-checks the scope entrypoint and current authority path
- the skill re-checks active frontier only when relevant
- the skill uses recovery routing only when recent execution state matters
- the skill surfaces uncertainty instead of pretending continuity

Reject when:

- the skill trusts remembered chat context over written project instructions
- the skill reloads every governance file in full by default

## Scenario 11: Learning Promotion

Given:

- a repeated or severe pitfall should change future agent behavior beyond a single round

Accept when:

- the skill promotes the pattern into a learning surface rather than leaving it only inside task history
- the promotion cites the source evidence
- the skill distinguishes guidance from mandatory policy
- the skill upgrades to authority change only when the lesson becomes a hard rule

Reject when:

- one-off noise becomes a permanent lesson
- a lesson is used as a backdoor authority rewrite

## Scenario 12: Existing Project Adoption

Given:

- a repository already contains a mix of old governance-like docs, notes, and historical records

Accept when:

- the skill classifies surfaces by layer and authority status before relying on them
- the skill records conflict order before broad edits
- the skill avoids mass rewriting older material during adoption
- the skill preserves historical/reference material unless structural cleanup is explicitly approved

Reject when:

- the skill silently reclassifies history as authority
- the skill overwrites an existing `AGENTS.md` instead of reviewing and proposing merge options

## Scenario 13: Skill Driven By Repo-Local Governance Spec

Given:

- a repository defines its own governance-system spec or behavior matrix and the skill is being used there

Accept when:

- the skill follows repository-local authority over its own generic defaults
- the skill can still provide lifecycle, maintenance, and acceptance workflow support
- the skill does not claim to replace repo-local governance
- the skill preserves the responsibility split between repo docs, `AGENTS.md`, and skill workflow

Reject when:

- the skill behaves as if its references are more authoritative than the repository's written docs
- generic skill defaults overwrite a project-specific accepted governance contract
