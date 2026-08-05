---
type: Engineering Convention
title: Tickets & traceability
description: Every commit, branch, and PR references exactly one Jira User Story key.
tags: [jira, traceability, pull-request]
timestamp: 2026-08-05T00:00:00Z
---

# Tickets & traceability

- **Every commit, branch, and PR must reference a Jira User Story ID.** An org
  watchdog check blocks anything without it.
- **Exactly one Jira key per PR title.** The watchdog fails when a title carries
  more than one key — reference a single User Story per PR. This is the invariant;
  the layout around the key is not.
- **The PR title layout varies by repository.** All three of
  `<KEY> <type>: <description>`, `<type>(<KEY>): <description>` (the key as a
  conventional-commit scope), and `<KEY>: <description>` are in active use and pass
  the watchdog. Match the repository being contributed to: read its recently merged
  PR titles and copy that shape rather than assuming a single house format. A
  repository that wants one layout enforces it in its own CI, not by convention.
- Branch names carry the same key: `feature/<TICKET-ID>-<slug>`.
- Before implementing, read the relevant spec/design section for the change.

Related: [PR body format](pr-body-format.md), [commit messages](../git/commit-messages.md),
[spec / design workflow](../spec-workflow.md).
