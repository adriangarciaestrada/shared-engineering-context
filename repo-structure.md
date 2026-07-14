---
type: Engineering Convention
title: Repo structure & documentation
description: CLAUDE.md and SECURITY.md baseline, terse top-level docs, memory pointers, glossary, hygiene.
tags: [documentation, claude-md, repo-hygiene]
timestamp: 2026-07-07T00:00:00Z
---

# Repo structure & documentation

- Give each repo a `CLAUDE.md` with a consistent skeleton: **What is this → Commands →
  Architecture**.
- **Ship the standard governance files** — a `SECURITY.md` (vulnerability-reporting
  policy) alongside `CLAUDE.md` — so every repo meets the same baseline.
- **Keep the top-level doc terse**; push detail into linked files rather than inlining
  everything.
- **Document related systems and cross-repo references** so the reader can navigate the
  wider system.
- Maintain **memory pointers** to persistent, hard-won decisions.
- Add a **glossary** for non-obvious project terms.
- Include a **"Don'ts" / "What not to do"** section (see [don'ts](donts.md)).
- While debugging, **document the investigation, save working configurations as soon
  as you find them, and create reproduction scripts** for both working and failing cases.
- **Keep the repo tidy:** close superseded or long-conflicting PRs, and delete stale
  local/remote branches once their work has merged.
