# vibecoding-template-app

> Template for web applications, APIs, MVPs, portals, SaaS products, or internal tools.

[![Governance](https://img.shields.io/badge/governance-lowcodai-blue)](https://github.com/lowcodai/vibecoding-copilot-governance)

## Description

GitHub template for vibecoding applications and APIs. Includes everything from
`vibecoding-template-base`, plus:
- `src/`, `tests/`, `public/` structure
- Accessibility instructions (WCAG 2.1 AA)
- Docker and CI/CD instructions
- Workflows: CI, automated release, a11y-check
- `dependency-license-checker` hook

## Agent rulebook

[`AGENTS.md`](AGENTS.md) is the first file every agent (orchestrator, Claude Code, Copilot) and every
contributor reads: commands, repository map, the DEV → REVIEW → TEST workflow (ADR-0005),
boundaries and definition of done. Fill in its `TODO` markers when you create a project from
this template. It is rendered by `vibecoding-bootstrap/scripts/apply-template.sh`, the single
source for all templates — change the generator, then re-render, rather than editing one copy.

The sequential coding team kit it refers to ships with this template (ADR-0005), copied from
`vibecoding-copilot-governance/dev-factory/project-template/`:

| Path | Purpose |
|------|---------|
| `CLAUDE.md` | Short memory for interactive Claude Code sessions (fill in the project name) |
| `.claude/settings.json`, `.claude/hooks/` | Deny rules, tool guardian and secrets scanner hooks |
| `.ai/orchestration.yaml` | Gateways, limits, validation commands — **set your lint/test commands** |
| `.ai/roles/`, `.ai/tasks/TASK-template.md` | DEV / REVIEW / TEST prompts and the task contract |
| `scripts/orchestrate.py` | The DEV → REVIEW → TEST state machine |
| `docs/{prd,adr,plans,runbooks,operations}/` | Agent-neutral documentation skeleton (READMEs and continuity files) |

Keep `.claude/` committed: the orchestrator refuses to run DEV without its hooks.

This template is agent-neutral (ADR-0007): orchestrator-specific rules (today Hermes) are installed
from `vibecoding-copilot-governance/adapters/` in the agent's own environment, not stored here.

## Usage

```bash
cd vibecoding-bootstrap
./scripts/new-project.sh --type app --name <my-app>
```

## App-specific structure

```
.
├── src/      # Main source code
├── tests/    # Unit, integration, e2e tests
└── public/   # Public static assets
```

## Conventions

- **Accessibility**: WCAG 2.1 AA minimum. Checked via `a11y-check.yml`.
- **Tests**: coverage ≥ 80%. No merge without passing tests.
- **API**: OpenAPI/Swagger spec required for every REST API.
- **Docker**: `Dockerfile` with a minimal image, multi-stage build recommended.

## App-specific Awesome Copilot elements

| Element | Type | Usage |
|---------|------|-------|
| `a11y.instructions.md` | Instruction | Accessibility standards |
| `containerization-docker-best-practices.instructions.md` | Instruction | Docker |
| `dependency-license-checker` | Hook | Licenses |
| `fix-broken-links` | Hook | Broken links in docs |
| `accessibility` | Agent | Accessibility expert |
| `accessibility-runtime-tester` | Agent | Runtime accessibility testing |

See `.github/copilot-instructions.md` for this repo's full active hooks list, and the [governance hooks registry](https://github.com/lowcodai/vibecoding-copilot-governance/blob/main/docs/awesome-copilot-map.md) for the full ecosystem-wide catalog.

## References

- [vibecoding-copilot-governance](https://github.com/lowcodai/vibecoding-copilot-governance)
- [WCAG 2.1](https://www.w3.org/TR/WCAG21/)
