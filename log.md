---
type: Index
title: Change log
description: Chronological history of changes to this OKF bundle.
tags: [changelog, history]
timestamp: 2026-07-07T00:00:00Z
---

# Change log

Newest first.

- **2026-07-07** — Converted the single `shared-engineering-context.md` document
  into an OKF v0.1 bundle: one concept per file, YAML frontmatter (`type` +
  optional fields), markdown-link knowledge graph, `index.md` navigation.
- **2026-07-07** — Added concepts distilled from `content-www` issue #56:
  [merge gating](git/merge-gating.md) (required CI checks, branch protection,
  Dependabot auto-merge), `SECURITY.md` as a standard governance file, repo
  hygiene, edge-case testing against the real schema, acceptance criteria in
  specs, and don'ts for un-gated merges and hardcoded domain values.
- **2026-07-01** — Reworked from Diego's review: dropped gitmoji, added `gitleaks`,
  a Pulumi-over-Wrangler note for Cloudflare, and a containers/Miniflare concept.
