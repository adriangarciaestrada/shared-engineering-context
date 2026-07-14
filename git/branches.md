---
type: Engineering Convention
title: Git & branches
description: Branching model — never commit to main; feature branch to PR to review to main.
tags: [git, branches, workflow]
timestamp: 2026-07-07T00:00:00Z
---

# Git & branches

- **Never commit directly to `main`.** All changes go through a branch + Pull Request.
- **Use descriptive branch names**, prefixed with the ticket where applicable
  (`feature/<TICKET-ID>-<slug>`, `feat/<slug>`, `<wave>-<slug>`, etc.).
- **Respect the team's push preference** — some workflows expect the developer to
  run `git push` manually rather than having it automated.
- A change flows: **feature branch → PR → review → `main`** (and from `main` to prod).

Related: [commit messages](commit-messages.md), [merge gating](merge-gating.md),
[tickets & traceability](../tickets/traceability.md).
