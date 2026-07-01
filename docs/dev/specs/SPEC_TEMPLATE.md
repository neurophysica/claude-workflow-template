# Spec: <title>

<!-- Author this in Claude Chat, then save a copy as docs/dev/specs/<name>.md and point
     Claude Code at it. Delete these HTML comments in the real spec. -->

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

## Report

Show diffs for every changed file. Confirm any files created or deleted. Propose a commit
message and wait for approval.
