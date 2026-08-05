---
type: Index
title: Change log
description: Chronological history of changes to this OKF bundle.
tags: [changelog, history]
timestamp: 2026-08-04T00:00:00Z
---

# Change log

Newest first.

- **2026-08-04** — Recorded the Working with AI pre-publication review in the
  [appendix](appendix.md) (twenty candidate gaps: one merged, one reinstated,
  eighteen deliberately excluded, with method caveats), documented the
  root-vs-folder structure rule in the README, and applied the review panel's
  minor editorial findings across the family (definitions, split bullets,
  checkable phrasings).
- **2026-08-04** — Added the [Working with AI](ai/index.md) concept family:
  scoping, output contracts, grounding & context, validation
  (Generate → Evaluate → Refine), human oversight & observability, failure
  handling, cost budgeting, and goal-oriented agent work — distilled from the
  course cited in the family index's `resource` field. Four AI don'ts added to
  the consolidated list. Before publication the family was itself stress-tested
  with a multi-agent review (coverage mapping against the source material,
  adversarial gap verification, editorial panel): contradictions with
  [merge gating](git/merge-gating.md) and between family rules were resolved,
  duplicated rules were given canonical owners, vague rules were made checkable,
  and cost-budgeting rules were extended with findings from the review run's own
  token spend. Cheap review techniques moved into
  [writing conventions](writing-conventions.md).
- **2026-07-07** — Converted the single `shared-engineering-context.md` document
  into an OKF v0.1 bundle: one concept per file, YAML frontmatter (`type` +
  optional fields), markdown-link knowledge graph, `index.md` navigation.
- **2026-07-07** — Added concepts distilled from `content-www` issue #56:
  [merge gating](git/merge-gating.md) (required CI checks, branch protection,
  Dependabot auto-merge), `SECURITY.md` as a standard governance file, repo
  hygiene, edge-case testing against the real schema, acceptance criteria in
  specs, and don'ts for un-gated merges and hardcoded domain values.
- **2026-07-01** — Reworked: dropped gitmoji, added `gitleaks`, a
  Pulumi-over-Wrangler note for Cloudflare, and a containers/Miniflare concept.
