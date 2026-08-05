---
type: Engineering Convention
title: Don'ts (consolidated)
description: The consolidated "what not to do" list, cross-cutting every other concept.
tags: [donts, antipatterns]
timestamp: 2026-08-05T00:00:00Z
---

# Don'ts (consolidated)

- **Don't commit to `main`** — always branch first.
- **Don't commit secrets, local state, caches, or build output** — gitignore them.
- **Don't open a PR without a Jira key**, and don't put more than one key in the
  title. **Don't assume one repository's title layout applies to another** — check
  the target repository's merged PRs.
- **Don't leave warnings, type errors, unused imports, or broken tests** behind.
- **Don't pre-seed config with guessed values** — recover real values from a source of
  truth, not from screenshots or assumptions.
- **Don't mock the validation target** — fidelity/verification only means something
  against the real thing.
- **Don't change shared config (build, framework, infra) without testing** the
  downstream effects.
- **Don't hardcode personal or account-bound resources in production.**
- **Don't import provider-rotated keys into IaC** — it creates predictable drift.
- **Don't rely on host-installed or unpinned tooling** — run scanners and dev
  services containerized so versions are reproducible.
- **Don't push without scanning for secrets** (`gitleaks`).
- **Don't merge without required CI checks and branch protection passing.**
- **Don't hardcode domain-specific values** (topics, titles, categories, authors)
  that should come from config/profile — they break the moment the domain changes.
- **Don't use agent output without validation and review** — automated schema checks
  first, human judgment before import; schema-valid is not the same as good.
- **Don't let malformed LLM output reach a downstream system** — parse defensively
  and stop the pipeline on failure.
- **Don't blind-retry a failed generation** — diagnose whether the prompt, schema,
  or data was at fault, then regenerate deliberately.
- **Don't define an agent by "vibe"** — without a concrete output schema there is
  nothing to verify it against.
