---
type: Engineering Convention
title: Spec / design workflow
description: OpenSpec lifecycle for non-trivial changes; validated frontmatter; acceptance criteria.
tags: [openspec, design, process]
timestamp: 2026-08-04T00:00:00Z
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

## Anatomy of a spec

A spec is an engineering contract: it defines what must exist when the work is
done, in a form anyone — human or agent — can verify. Five parts:

- **The goal in one sentence, stated as observable effect.** What the user can
  do once this exists, not what the system computes internally. The readiness
  test: every component described by what the user sees when it fires.
- **Acceptance criteria ("done when …").** Checkable conditions that define
  finished, each verifiable on its own. If a criterion does not immediately
  suggest how to test it, it is a wish, not a criterion.
- **Work items with explicit dependencies and priorities.** Each piece carries
  its own "done when", and blocking relations are written down — this is the
  graph that derived prioritization consumes.
- **Constraints with derived consequences.** Not just the limit but what it
  implies ("60 req/min → max throughput 1/s"). For AI systems this also means
  the AI contract and the token budget (see [scoping](ai/scoping.md) and
  [cost budgeting](ai/cost-budgeting.md)).
- **Non-goals.** One line of what is deliberately out. Documented exclusions are
  cheaper than scope creep — "excluded" is different from "forgotten".

## Spec quality tests

- **Vagueness test.** Ask an agent to produce a structured artifact (e.g. the
  work-item list as JSON) from the spec; failure means the spec is too vague to
  build from (see [output contracts](ai/output-contracts.md)).
- **Clarity test.** A reader outside the work answers "what does the user do?"
  from the document alone (see [writing conventions](writing-conventions.md)).
- **Logical stress-test** for high-stakes specs: synthetic reviewers hunt
  contradictory rules and unreachable conditions — three individually reasonable
  rules can be jointly impossible (see [validating AI output](ai/validation.md)).

A well-made spec turns downstream decisions into derivations: the task list,
the crew design, and the prioritization follow from it instead of being
invented.

Related: [tickets & traceability](tickets/traceability.md), [code quality](code-quality.md).
