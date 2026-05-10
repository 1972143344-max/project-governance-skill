# Initialization And Adoption

Use this sidecar only when the current action is governance initialization or adoption.

## Initialization

Use initialization when governance docs do not yet exist for the active project scope.

### Initialization Modes

#### `core`

Use when:

- the project is non-trivial but still early
- one or two contributors are active
- probe work is not yet central

Minimum expectations:

- authority layer
- behavior audit
- task knowledge base
- task records
- recovery skeleton with minimal shard use
- active plan only when a real multi-step frontier exists

#### `extended`

Use when:

- the project is long-running
- multiple execution rounds are expected
- design drift, handoff, or repeated reviews are likely

Additional expectations:

- persistent active plan
- regular recovery shards
- stronger summary-entry maintenance
- explicit lesson-promotion cadence
- optional template tiering or lightweight IDs when the repo wants them

#### `probe-heavy`

Use when:

- real-environment probes are a first-class workstream
- evidence capture, redaction, and failure-stage reporting are central
- the project often runs read-only investigations or live-environment characterization

Additional expectations:

- explicit probe contract or checklist
- runner-isolation rules
- artifact storage and redaction rules
- stronger sync between probe records, active plan, and decision boundaries

### Initialization Steps

1. Ask whether to initialize the governance system.
2. Confirm the active project scope and stable slug.
3. Choose the lightest truthful mode.
4. Default the doc root to `docs/<project-scope>/governance/`.
5. Use `docs/governance/` only when the user explicitly wants repository-wide governance.
6. If a project-root `AGENTS.md` already exists, do not overwrite it silently; read it first and ask whether to merge or replace it.
7. Create `00_index_and_priority.md` first.
8. Create the minimum governance, recovery, and task skeleton for the selected mode.
9. If the routing surface points future task rounds into support protocol docs, create those docs in the same round.

### Initialization Outcome

Initialization should make these explicit:

- stable project scope slug
- governance doc root
- authority order
- whether active plan is in use
- whether recovery is active and how to route it
- task-record requirement
- local quality-gate source, if known

## Adoption

Use adoption when the repo already has scattered docs, stale notes, old handoff files, or conflicting design records.

### Adoption Steps

1. Ask whether to adopt the current project into the governance system.
2. Confirm the project scope and governance doc root.
3. Read only the minimum current project docs needed to classify them.
4. Update `00_index_and_priority.md` to label documents as authoritative, working, or historical/reference.
5. Decide which existing files belong in authority, execution, learning, recovery, or probe surfaces.
6. Classify existing handoff or context-like files before rewriting or moving them.
7. Do not silently rewrite old docs unless the user asked for cleanup.

### Adoption Rule

Adoption should classify first and migrate second.

Do not silently treat old notes, task records, or proposal docs as current authority merely because they are detailed.
