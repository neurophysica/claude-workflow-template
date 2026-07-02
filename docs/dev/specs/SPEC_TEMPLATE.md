---
status: draft
targets: []
depends_on: []
---

# Spec: <title>

<!-- Author this in Claude Chat, then save a copy as docs/dev/specs/<name>.md and point
     Claude Code at it. Delete these HTML comments in the real spec. -->

`status` is one of: draft, approved, executing, done.
`targets` lists every file path this spec touches.
`depends_on` lists other spec filenames under docs/dev/specs/ that must land first.

Specs are retained after execution, not deleted. A spec at status done stays in
docs/dev/specs/ as a permanent provenance record of what was built and why. Do not delete,
archive, or clean up done specs.

Scope: <one line — what this touches, and what it explicitly does NOT>.
<!-- e.g. "documentation only", or "reference/ module X + its tests; no other files". -->

Disposable: **no**
<!-- "no" (default) = persist this spec as build provenance.
     "yes" = Claude Code deletes this spec as the final step of implementing it — allowed
     only when its content is fully absorbed into other durable files. -->

Commit gate: do not commit — stage changes and surface the diff for review, then wait for
explicit approval.

## 1. <step title>

<Describe the change precisely enough to execute without the authoring conversation. Name
exact files, functions, and expected behavior.>

## 2. <step title>

<...>

## Acceptance Criteria

Testable, pass/fail conditions. No prose. Each line is checkable true or false against actual
repo state.

- [ ]
- [ ]

## Definition of Done

State exactly what "complete" means for this spec, referencing the acceptance criteria above.
A spec without this section is not ready for execution.

## Report

Show diffs for every changed file. Confirm any files created or deleted. Propose a commit
message and wait for approval.
