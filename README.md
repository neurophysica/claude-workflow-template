# claude-workflow-template

A minimal template for running a project across two Claude surfaces:

- **Claude Chat (CC)** — where understanding, design, specs, and review happen.
- **Claude Code (CCh)** — the executor with filesystem, git, and shell access.

The repository is the **shared memory** between them: durable state lives in files, not in
either conversation. This template ships the bare-minimum scaffolding to establish that
bridge, with no project-specific content.

## What's in here

| Path | Purpose |
|---|---|
| `CLAUDE.md` | Read by Claude Code each session: project overview, conventions, git rules, living-doc registry. |
| `docs/dev/WORKFLOW.md` | How the two surfaces coordinate through the repo. |
| `docs/dev/DECISIONS.md` | Dated log of locked decisions so neither surface re-litigates them. Seeded with the workflow baseline. |
| `docs/dev/specs/` | Specs authored in Chat, executed by Claude Code by reference. `SPEC_TEMPLATE.md` is a starting point. |

## Using this template

1. On GitHub, click **"Use this template" → Create a new repository** — or from the CLI:
   `gh repo create <owner>/<name> --private --template neurophysica/claude-workflow-template`
2. Clone the new repo and work through the customize checklist below.
3. Point Claude Code at the repo; it reads `CLAUDE.md` on its first turn.

## Customize checklist (after creating a repo from this template)

- [ ] `CLAUDE.md` — fill every `<!-- FILL IN -->`: what the project is, layout, environment, conventions.
- [ ] `CLAUDE.md` — set the sign-off name/email under "Git conventions" (or remove that rule).
- [ ] `README.md` — replace this file's contents with your project's README.
- [ ] `docs/dev/DECISIONS.md` — keep the workflow baseline; add project decisions as dated entries above it.
- [ ] `.gitignore` — add language/tooling-specific ignores for your stack.
- [ ] `docs/dev/specs/SPEC_TEMPLATE.md` — keep it as a starting point, or delete if unused.
