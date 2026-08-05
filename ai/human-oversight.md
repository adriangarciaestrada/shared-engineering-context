---
type: Engineering Convention
title: Human oversight & observability
description: Generate → Validate → Review → Import; review against intent; reasoning logged before changes land.
tags: [ai, agents, review, observability]
timestamp: 2026-08-04T00:00:00Z
---

# Human oversight & observability

- **Pipeline shape: Generate → Validate → Review → Import.** Human review sits
  between automated validation and the import into the real system; only approved
  content lands.
- **Review is not a rubber stamp.** Skipped review turns agent mistakes into
  product bugs. A review counts as done only if it records at least one point
  where the reviewer compared the output against the original spec/ticket goal
  (not just code style) and states pass or fail against it; a review with no such
  note is treated as not done.
- **Humans decide WHAT and WHERE; the LLM writes the HOW** — and the HOW is
  reviewed.
- **Review against intent, not just style.** "Follows the codebase patterns" is
  not the same as "matches the design intent".
- **Document the intervention**: what the agent produced, why it chose that, and
  what a human changed before accepting it.
- **Route agent-generated content through staging.** Watchers and batch jobs that
  carry LLM-generated content feed a staging area for review — never the target
  system directly. This does not restrict deterministic automation gated by
  required CI checks (e.g. dependency auto-merge per
  [merge gating](../git/merge-gating.md)): the rule is about ungated generative
  output, not automation as such.
- **Log reasoning before changes land**: what the agent read, what it scored and
  why, the exact prompts sent, and the output — recorded before anything is
  applied. Sanitize these logs of secrets and credentials before persisting
  (prompts can embed whatever the agent read — see [secrets](../secrets.md)). If
  the agent's decisions cannot be explained, nobody was in control of them.
- **Keep agent memory in plain, editable text** (markdown): durable, auditable
  state a human can read, correct, and feed back. Avoid opaque infrastructure —
  any state store a human cannot open, read, and edit as plain text (embedded
  databases, external memory services).
- **Version prompts and pipeline definitions as code** — they change behavior
  exactly like code does, so they get the same history, review, and rollback.
- **Keep architecture diagrams as code** (e.g. Mermaid): diffable next to the
  source, and they expose bottlenecks and circular dependencies early.
- **Run agent components in reproducible environments.** The house rule against
  host-installed, unpinned tooling applies to agent pipelines too — see
  [local development & containers](../local-containers.md).
- **Escalate to humans what agents cannot verify.** Route to a human any question
  whose answer depends on subjective usefulness, clarity, or taste rather than on
  facts verifiable from the repo or docs — and name the specific question that
  could not be resolved from grounding material. The deliverable of any review
  round is the revised artifact, not the feedback itself. (Cheap human-review
  techniques live in [writing conventions](../writing-conventions.md).)

Related: [validation](validation.md), [failure handling](failure-handling.md),
[writing conventions](../writing-conventions.md).
