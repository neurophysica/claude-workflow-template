# Decision log

Locked project decisions, so neither surface (Claude Chat, Claude Code) re-litigates them.
Newest entries at the top, each dated `YYYY-MM-DD`. Entry format: **Decision** / **Rationale**.
When a decision is revisited, add a new dated entry that supersedes the old one rather than
editing history.

Add project-specific decisions as dated sections **above** the "Workflow baseline" below.

---

## Workflow baseline (from claude-workflow-template)

These decisions ship with the template and define the CC↔CCh workflow. Keep them unless you
deliberately change how the two surfaces work.

### Two-surface workflow via the repo as shared memory
**Decision:** Work is split across Claude Chat (design / specs / review) and Claude Code
(execution). The repository is the durable shared memory between them; nothing persists in
either session. See [WORKFLOW.md](WORKFLOW.md).
**Rationale:** Sessions forget; files don't. Writing decisions, specs, and results to the repo
is what makes cross-session and cross-surface work coherent.

### Commit and push on explicit approval
**Decision:** Commits and pushes happen only on explicit human approval. Claude Code stages
and surfaces the diff, then waits.
**Rationale:** The human reviews every change before it enters history — a deliberate
human-in-the-loop cadence.

### Spec persistence
**Decision:** Specs authored in Chat and saved under `docs/dev/specs/` **persist by default**
as build provenance. A spec is deleted after implementation only if it explicitly marks itself
**disposable**, and only when its content is fully absorbed into other durable files. The
determination is made in the spec itself at authoring time, never as silent cleanup.
**Rationale:** Specs record the intent behind each change — high-value durable memory. Keeping
costs a few KB; deleting risks losing context.
