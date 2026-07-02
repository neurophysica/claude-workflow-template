<!-- sync: sha=279212b59fa10b767538651bf6a1c5bc4e2eef03 date=2026-07-02T09:22:10Z -->
# Workflow — how the two surfaces coordinate

This project spans two surfaces:

- **Claude Chat (CC)** — where understanding, design, specifications, and review happen.
- **Claude Code (CCh)** — the executor with access to the filesystem, git, and a shell.

## The repo is shared memory

Neither session persists on its own — a Chat thread and a Claude Code session both forget.
**The repository is the shared memory between them.** If a decision, spec, or result isn't
written to a file in the repo, it does not survive the session. Durable state lives in the
repo, not in either conversation.

## Division of labor

| Surface | Owns |
|---|---|
| **Claude Chat** | Understanding, design, specs, and review — the *thinking* |
| **Claude Code** | Filesystem, git, tests, and execution — the *doing* |
| **The repo** | All durable state — decisions, specs, code, results, progress |

Chat designs; Claude Code executes; the repo remembers.

## Scope discipline

Claude Code implements what a spec defines. When scope is ambiguous, or a change would exceed
what was asked, it **stubs and asks** rather than guessing. A project may define explicit
carve-outs — work reserved for the human, or off-limits areas — in [DECISIONS.md](DECISIONS.md).

## Specs: author in Chat, execute by reference

Build specifications are produced in Claude Chat as **downloadable files**, which the human
saves under `docs/dev/specs/`. Execute them by **pointing Claude Code at the file** (e.g.
"implement `docs/dev/specs/<name>.md`") rather than pasting the text into the session. The
spec file — not pasted text — is the unit of execution.

Why: the spec becomes durable, reviewable, and versioned; the executing session reads exactly
what was agreed, and later sessions can see what was asked for and why.

Persistence: specs persist under `docs/dev/specs/` by default as build provenance; a spec is
deleted after implementation only if it explicitly marks itself **disposable**. See
[DECISIONS.md](DECISIONS.md) for the full policy.

## Reviewing repo files in Chat: upload, don't paste

- When Chat needs to review a repo file, the human **uploads the actual file** to Chat —
  rather than pasting its contents or relying on Claude Code dumping the file into its reply.
- Rationale: uploads are the real repo bytes — no transcription drift, no ambiguity from
  tool-result rendering, less token waste.
- Freshness caveat: Chat only sees the version at upload time. After Claude Code changes a
  file, re-upload it for Chat to review the current state. When in doubt, state "current as
  of <point>".

## Reporting: durable and paste-able

Claude Code reports results in **durable, paste-able form** — diffs, test output, and written
summaries — not just ephemeral chat. Results then travel back to Chat (or into a file) intact,
so the other surface reviews what actually happened rather than a paraphrase.

## Living documents

Keep the repo's durable-state files current as work lands (see the "Living documents" section
of [../../CLAUDE.md](../../CLAUDE.md)).
