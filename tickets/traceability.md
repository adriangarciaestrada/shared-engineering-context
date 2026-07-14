---
type: Engineering Convention
title: Tickets & traceability
description: Every commit, branch, and PR references exactly one Jira User Story key.
tags: [jira, traceability, pull-request]
timestamp: 2026-07-07T00:00:00Z
---

# Tickets & traceability

- **Every commit, branch, and PR must reference a Jira User Story ID.** An org
  watchdog check blocks anything without it.
- **PR title format:** `<JIRA-KEY> <type>: <description>` — bare Jira key + a
  conventional-commit type. **No parentheses or brackets** around the key, or the
  watchdog blocks the PR.
- **Exactly one Jira key per PR title.** The Jira watchdog fails when a title
  contains more than one key — reference a single User Story per PR.
- Branch names carry the same key: `feature/<TICKET-ID>-<slug>`.
- Before implementing, read the relevant spec/design section for the change.

Related: [PR body format](pr-body-format.md), [commit messages](../git/commit-messages.md),
[spec / design workflow](../spec-workflow.md).
