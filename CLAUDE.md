# CLAUDE.md

Guidance for Claude Code (and humans) working in this repo. Read this first each session.

<!-- Created from claude-workflow-template. Fill in every <!-- FILL IN --> below, then delete this line. -->

## What this project is

<!-- FILL IN: one or two paragraphs — what the project is, its goal, and its main deliverables. -->

## Layout

<!-- FILL IN: the directory layout and what lives where. -->

Durable dev-process state lives under `docs/dev/` — see [WORKFLOW.md](docs/dev/WORKFLOW.md)
(how the two Claude surfaces coordinate) and [DECISIONS.md](docs/dev/DECISIONS.md) (locked
decisions).

## Conventions

<!-- FILL IN: project-specific conventions (style, testing, structure, naming). -->

## Environment

<!-- FILL IN: how to set up and run the project (language, package manager, how to run tests). -->

## Living documents (keep in sync as we work)

These files are **not** write-once — update them as the project evolves, in the *same* piece
of work that makes one stale.

| Document | Purpose | Update when… |
|---|---|---|
| `CLAUDE.md` (this file) | Stable overview, layout, conventions, env | Architecture, conventions, deps, or layout change |
| `docs/dev/DECISIONS.md` | Dated log of locked decisions | A decision is made, changed, or superseded |
| `docs/dev/WORKFLOW.md` | How Claude Chat + Claude Code coordinate via the repo | The two-surface process or division of labor changes |
| `README.md` | Public-facing summary + setup | User-facing setup or scope changes |

## Git conventions

- **Wait for the human before committing.** Do not run `git commit` or push until explicitly
  asked — the human reviews the diff first. Prepare/stage and surface the change, then wait.
  This overrides any "commit when the task is done" default.
- **Commit sign-off is solo — do NOT add `Co-Authored-By` or any co-author trailer.**
  Use exactly: `Signed-off-by: <!-- FILL IN: Your Name <you@example.com> -->`
- Default branch is `main`.
