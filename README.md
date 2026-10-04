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

[`AGENTS.md`](AGENTS.md) is the first file every agent (Hermes, Claude Code, Copilot) and every
contributor reads: commands, repository map, the DEV → REVIEW → TEST workflow (ADR-0005),
boundaries and definition of done. Fill in its `TODO` markers when you create a project from
this template. It is rendered by `vibecoding-bootstrap/scripts/apply-template.sh`, the single
source for all templates — change the generator, then re-render, rather than editing one copy.
The orchestration files it refers to (`.ai/`, `.claude/`, `scripts/orchestrate.py`) are
installed by `vibecoding-bootstrap/scripts/sync-governance.sh`.

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
