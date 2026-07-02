# claude-workflow-template

A minimal template for running a project across two Claude surfaces:

- **Claude Chat (CC)** — where understanding, design, specs, and review happen.
- **Claude Code (CCh)** — the executor with filesystem, git, and shell access.

The repository is the **shared memory** between them: durable state lives in files, not in
either conversation. This template ships the bare-minimum scaffolding to establish that
bridge, with no project-specific content.

## See it in action

**[neurophysica/claude-workflow-example](https://github.com/neurophysica/claude-workflow-example)**
is a worked example built from this template: a tiny unit-converter CLI created one spec at a
time. Its [`WALKTHROUGH.md`](https://github.com/neurophysica/claude-workflow-example/blob/main/WALKTHROUGH.md)
narrates the full design→spec→execute→review→commit loop, and each step is a git tag
(`step_01`…`step_03`) you can diff.

## What's in here

| Path | Purpose |
|---|---|
| `CLAUDE.md` | Read by Claude Code each session: project overview, conventions, git rules, living-doc registry. |
| `docs/ROADMAP.md` | Live progress tracker so any session sees what's done and what's next. |
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
- [ ] `docs/ROADMAP.md` — replace the placeholder milestones with your project's phases.
- [ ] `.gitignore` — add language/tooling-specific ignores for your stack.
- [ ] `docs/dev/specs/SPEC_TEMPLATE.md` — keep it as a starting point, or delete if unused.

## Getting started: seed your two Claude surfaces

Once the repo is created and customized, bootstrap both surfaces. The repo is the shared
memory — each surface is told its role, and specs/results flow between them through files.

### 1. Claude Code (the executor)

Open the repo directory in Claude Code (CLI, IDE extension, or desktop). It automatically
reads `CLAUDE.md` on its first turn, so it starts with the conventions, git rules, and
living-doc registry already loaded. Nothing to upload — it has the filesystem.

Its role: filesystem, git, tests, and execution. It **commits only on your explicit
approval**, and executes specs by reference (you point it at a file under `docs/dev/specs/`).

### 2. Claude Chat (the designer)

Start a new Chat (a Project works well). Chat has **no filesystem access**, so give it the
durable context by **uploading these files**:

- `CLAUDE.md` — project overview + conventions
- `docs/dev/WORKFLOW.md` — how the two surfaces coordinate
- `docs/dev/DECISIONS.md` — locked decisions
- `docs/ROADMAP.md` — current progress and focus
- `docs/dev/specs/SPEC_TEMPLATE.md` — the spec format Chat should emit

Then tell it its role, e.g.: *"You are the Claude Chat surface for this project. You own
understanding, design, specs, and review. Claude Code executes. Emit specs as downloadable
files following SPEC_TEMPLATE.md; I'll save them under docs/dev/specs/ and run them in Claude
Code."*

Re-upload a file whenever Claude Code changes it — Chat only sees the version at upload time.

### 3. The loop

1. **Design in Chat** → it emits a spec as a downloadable file.
2. **Save** the spec under `docs/dev/specs/` and tell Claude Code: *"implement
   `docs/dev/specs/<name>.md`."*
3. **Claude Code executes**, shows diffs / test output, and waits for your approval to commit.
4. **Report back to Chat** by uploading changed files (or pasting the diff) so it can review.
5. Keep `docs/ROADMAP.md` and `docs/dev/DECISIONS.md` current as work lands.
