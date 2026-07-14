---
type: Engineering Convention
title: Spec / design workflow
description: OpenSpec lifecycle for non-trivial changes; validated frontmatter; acceptance criteria.
tags: [openspec, design, process]
timestamp: 2026-07-07T00:00:00Z
---

# Spec / design workflow

- For non-trivial changes, use the **OpenSpec lifecycle**:
  **proposal → design → specs → tasks → implementation → archive.**
- **Skip the spec for small, single-unit changes**; reach for it when a change is large
  enough to warrant a shared design.
- Define authoring formats with **validated frontmatter** (e.g. SKILL.md: required YAML
  fields, a max line count, validated in CI).
- **Verify API behavior against the docs before guessing** (use a docs/MCP source when
  available) rather than assuming.
- **State acceptance criteria** ("done when …") for each work item, and make cross-item
  dependencies and priorities explicit so the plan is executable, not just descriptive.

Related: [tickets & traceability](tickets/traceability.md), [code quality](code-quality.md).
