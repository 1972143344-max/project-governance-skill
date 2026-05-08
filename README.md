# Project Governance Skill

[中文说明](./README.zh-CN.md)

This repository packages a reusable Codex skill for project-scoped governance in long-running repositories.

The skill is intended for work that needs stable authority routing, repeatable documentation updates, and reliable recovery after context compression, pause, or handoff.

## Repository layout

```text
project-governance-skill/
  README.md
  README.zh-CN.md
  docs/
    USAGE.md
  project-governance/
    SKILL.md
    agents/openai.yaml
    assets/
    references/
```

## What the skill covers

The packaged skill helps an agent:

- initialize or adopt project-scoped governance
- keep authority, task, audit, and decision surfaces in sync
- use route-first reading and progressive disclosure
- maintain project-scoped recovery and context state
- classify rounds by lane for docs, review, probe, implementation, and structural maintenance
- preserve authority boundaries instead of letting summaries or chat history redefine project truth

## Included skill contents

Inside `project-governance/`:

- `SKILL.md`: the governance workflow contract
- `agents/openai.yaml`: skill entry metadata
- `assets/`: templates for governance docs, context surfaces, summary headers, indexes, and lane-based task records
- `references/governance-workflow.md`: workflow reference
- `references/acceptance-scenarios.md`: validation scenarios

## Installation

### Install as a global Codex skill

Copy the `project-governance/` directory into:

```text
<CODEX_HOME>/skills/project-governance/
```

### Install as a project-local skill

Copy the same `project-governance/` directory into:

```text
<repo>/.agents/skills/project-governance/
```

If both a repo-local and a user-level skill with the same name exist, Codex can discover both. Keep them synchronized if you intentionally maintain both.

## Notes

- The skill is repository-agnostic. It does not assume one fixed project layout beyond the documented governance surfaces.
- In current repo layouts, the concrete recovery surface usually lives under `docs/<project-scope>/context/`.
- Repository-local governance still wins if a repository defines a stricter or newer contract than the packaged skill.

## Usage

See [docs/USAGE.md](./docs/USAGE.md) for a usage guide and example prompts.
