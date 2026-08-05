---
type: Index
title: Working with AI
description: Conventions for building with LLMs and agent pipelines — scoping, contracts, grounding, validation, oversight, failure handling, cost, and goal-oriented work.
tags: [ai, agents, llm, index]
timestamp: 2026-08-04T00:00:00Z
resource: "ELVTR — Multi-Agent AI for Game Development (instructor-led course, Jul–Aug 2026); session slide captures, not publicly linkable"
---

# Working with AI

Conventions for using LLMs and multi-agent pipelines as engineering components.
Distilled from the course referenced in `resource` above (domain examples
generalized from game development to any product) and adapted to the org's
practices; rules that are house practice rather than course material are marked
by their cross-links into the rest of this bundle.

- [Scoping AI systems](scoping.md) — when AI earns its place, and how much of it.
- [AI output contracts](output-contracts.md) — schemas, typed I/O, forced structure.
- [Grounding & context](grounding.md) — feeding agents the right source of truth.
- [Validating AI output](validation.md) — the Generate → Evaluate → Refine loop and its gates.
- [Human oversight & observability](human-oversight.md) — where human judgment goes, and staying in control.
- [AI failure handling](failure-handling.md) — malformed output, diagnosis before retry, debugging with LLMs.
- [AI cost budgeting](cost-budgeting.md) — token budgets as a design input.
- [Goal-oriented agent work](goal-oriented-work.md) — specs, gap analysis, stop conditions.
