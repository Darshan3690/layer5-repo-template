# AGENTS.md

This file is for agentic coding tools working in this repo.

This repository is created from the `layer5io/layer5-repo-template`
boilerplate. It provides a consistent foundation for all Layer5 projects.
This AGENTS.md is the single source of truth for AI coding agent instructions
in this repository. CLAUDE.md is a symbolic link to AGENTS.md.

---

## Repository Overview

> **REPO-SPECIFIC — fill in for your project**

- **Purpose:** `<one-line description of what this repo does>`
- **Primary language:** `<e.g. Go, JavaScript, Python, Docker>`
- **Entry point:** `<e.g. cmd/<app>, main.go, index.js, Dockerfile>`
- **Implementation layout:** `<brief description of key directories>`
- **License:** Apache 2.0 (see LICENSE)

This repo follows Layer5 project conventions. See README.md and
CONTRIBUTING.md for project- and community-level details.

---

## Source of Truth

- `AGENTS.md` is the canonical source of instructions for AI coding agents.
- `CLAUDE.md` is a symbolic link pointing to `AGENTS.md`.
- Edit only `AGENTS.md` to update agent instructions.
- Do not maintain a separate copy in `CLAUDE.md`.

---

## Build, Test, and Lint

Build, test, and release commands are owned by the `Makefile`; read it
for the full target list instead of relying on a copy here.

### Common targets (verify in the repo's Makefile)

| Target | Purpose |
|--------|---------|
| `make setup` | Install dependencies |
| `make build` | Build the project |
| `make test` | Run unit tests |
| `make lint` | Run linters |
| `make docker` | Build Docker image |

### Suggested local verification sequence after non-trivial changes

1. Run any language-specific formatter (e.g. `gofmt -w .` for Go, `prettier --write` for JS/TS).
2. `make lint` — run all configured linters.
3. `make test` — run the test suite.
4. `make build` — confirm a clean build.
5. `make docker` (if applicable) — confirm the Docker image builds.

> **REPO-SPECIFIC — replace with the actual commands and tags for this repo**

---

## Where Detail Lives

### Per-area implementation maps

Area-specific agent skills live at:

```
.agents/skills/<area>/SKILL.md
```

`.claude/skills` is a symbolic link to `.agents/skills` where supported by the agent
toolchain. Read the matching skill before changing that area.

Example areas (customize per repo):

- `.agents/skills/cli/SKILL.md` — CLI command structure, flag parsing, command registration
- `.agents/skills/api/SKILL.md` — API routes, handlers, request/response shapes
- `.agents/skills/ui/SKILL.md` — frontend components, styling, state management
- `.agents/skills/infra/SKILL.md` — infrastructure, Docker, Kubernetes, deployment

### Docs and config that own behavior

Do not guess where user-facing semantics live — these files are authoritative:

| What | Where |
|------|-------|
| CI / GitHub Actions workflows | `.github/workflows/*.yml` |
| Release notes configuration | `.github/release-drafter.yml` |
| PR/issue labeling rules | `.github/labeler.yml`, `.github/workflows/labeler.yml` |
| Label commenter responses | `.github/label-commenter-config.yml` |
| Stale issue handling | `.github/stale.yml` |
| Behaviorbot welcome messages | `.github/config.yml` |
| Contribution guidelines | `CONTRIBUTING.md`, `CONTRIBUTING-gitflow.md` |
| Code of conduct | `CODE_OF_CONDUCT.md` |
| Docker build args / release channel | `.github/build/latest_release.sh`, `.github/build/Makefile.core.mk` |
| Makefile targets | `Makefile`, `.github/build/Makefile.core.mk`, `.github/build/Makefile.show-help.mk` |

> **REPO-SPECIFIC — adjust paths as needed for your project layout**

### Generated files — do not hand-edit

The following are generated from source. Never edit them directly;
modify the source and run the documented generation process instead.

> **REPO-SPECIFIC — list generated files and their generation commands**

Examples (adopt or remove as applicable):

| Generated file | Source | Generation command |
|----------------|--------|-------------------|
| `skills/<name>/SKILL.md` | `internal/skill/skill.go` (or equivalent) | `make generate-skills` |
| `CHANGELOG.md` | Release drafter / git history | `make changelog` or GitHub release |
| `docs/api/*` | Source code annotations | `make gen-docs` |

If a file is not listed above and appears generated, check for a header comment
or generation script before editing.

---

## Invariants Every Change Must Keep

> **REPO-SPECIFIC — add project-specific invariants, security boundaries, or rules**

Layer5-wide conventions:

- All commits must be signed off (`Signed-off-by:` line) per the DCO.
- Use `git commit -s` or `--signoff` to sign off automatically.
- Follow the fork-and-PR workflow described in `CONTRIBUTING-gitflow.md`.
- Reference an open issue in every pull request.
- Keep changes focused and well documented.

---

## Maintaining This File

Keep this file for knowledge useful to almost every future agent session in
this project. Do not repeat what the codebase already shows; point to the
authoritative file or command instead. Prefer rewriting or pruning existing
entries over appending new ones. When updating this file, preserve this bar
for all agents and keep entries concise.

---

## Repository-Specific Sections to Complete

When adapting this template for a specific Layer5 repo, replace every
`> **REPO-SPECIFIC — ...**` placeholder with concrete values:

- [ ] Repository Overview — purpose, language, entry point, layout
- [ ] Build, Test, and Lint — actual Makefile targets and commands
- [ ] Where Detail Lives — actual skill areas, doc paths, generated files
- [ ] Invariants — project-specific rules and security boundaries
- [ ] Any additional area-specific skill files under `.agents/skills/`

---

## Contributions

Follow `CONTRIBUTING.md` when submitting changes.

Review the relevant tests and documentation before opening a pull request.

All Layer5 projects are community-built and welcome collaboration. Join the
[Layer5 Community](https://layer5.io/community) and our
[Slack](http://slack.layer5.io).