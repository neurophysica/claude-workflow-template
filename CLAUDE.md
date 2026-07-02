<!-- sync: sha=b720739e476627fb8ca53957147c4458335ea94a date=2026-07-02T09:22:10Z -->
# CLAUDE.md

Guidance for Claude Code (and humans) working in this repo. Read this first each session.

## What this project is

<!-- FILL IN: one paragraph, what the project does and who it's for -->

## Layout

Durable dev-process state lives under `docs/dev/` — see [WORKFLOW.md](docs/dev/WORKFLOW.md)
(how the two Claude surfaces coordinate) and [DECISIONS.md](docs/dev/DECISIONS.md) (locked
decisions).

<!-- FILL IN: describe any other top-level directories specific to this project -->

## Conventions

<!-- FILL IN: language/framework conventions, naming, style, testing approach -->

## Environment

<!-- FILL IN: how to install deps and run this project locally -->

## Living documents (keep in sync as we work)

These files are **not** write-once — update them as the project evolves, in the *same* piece
of work that makes one stale.

| Document | Purpose | Update when… |
|---|---|---|
| `CLAUDE.md` (this file) | Stable overview, layout, conventions, env | Architecture, conventions, deps, or layout change |
| `docs/ROADMAP.md` | Live progress tracker | A milestone starts or lands; focus or plan changes |
| `docs/dev/DECISIONS.md` | Dated log of locked decisions | A decision is made, changed, or superseded |
| `docs/dev/WORKFLOW.md` | How Claude Chat + Claude Code coordinate via the repo | The two-surface process or division of labor changes |
| `README.md` | Public-facing summary + setup | User-facing setup or scope changes |

## Spec execution

Do not report a spec complete unless every Acceptance Criteria item is checked off with evidence:
a command, a diff, or test output. If a spec under docs/dev/specs/ is missing Acceptance Criteria
or Definition of Done, stop and ask the human to send it back to Chat for completion. Do not infer
missing acceptance criteria and proceed on judgment call.

Do not delete a spec after completing it. Set its status to done and leave it in place as a
provenance record.

## Secrets and sensitive data

Never include in specs, decision entries, roadmap items, or commit messages: IP addresses,
hostnames, API tokens, SSH key paths, account IDs, or credentials of any kind. Reference
infrastructure by role, not by address. If a value must be recorded, it goes in a local,
gitignored file, never in a tracked doc.

## Git conventions

- **Wait for the human before committing.** Do not run `git commit` or push until explicitly
  asked — the human reviews the diff first. Prepare/stage and surface the change, then wait.
  This overrides any "commit when the task is done" default.
- **Commit sign-off is solo — do NOT add `Co-Authored-By` or any co-author trailer.**
  Use exactly: `Signed-off-by: <!-- FILL IN: Your Name <you@example.com> -->`
- Default branch is `main`.
