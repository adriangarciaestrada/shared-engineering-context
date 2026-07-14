---
type: Engineering Convention
title: Continuous integration & merge gating
description: Required CI checks, branch protection on main, and automated dependency updates.
tags: [ci, branch-protection, dependabot, merge]
timestamp: 2026-07-07T00:00:00Z
---

# Continuous integration & merge gating

- **Every PR must pass required CI checks before merging** — at minimum `lint`,
  `typecheck`, `build`, and a secret scan (`gitleaks`). Where a test suite exists it
  runs too; until one does, typecheck + build is the verification step
  (see [code quality](../code-quality.md)).
- **Protect `main` with branch protection** that *requires* those checks — the gate is
  enforced by config, not by convention or good intentions.
- **Run dependency/SAST scanners in CI** (`trivy`, `semgrep`), pinned and containerized,
  reporting CRITICAL/HIGH (see [security](../security.md) and
  [local development & containers](../local-containers.md)).
- **Automate dependency updates** (e.g. Dependabot) and **auto-merge patch/minor bumps
  once required checks pass**, reserving manual review for majors. A stuck auto-merge
  usually means required checks or branch protection are misconfigured — fix the config
  rather than merging by hand.
