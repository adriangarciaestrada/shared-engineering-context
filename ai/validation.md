---
type: Engineering Convention
title: Validating AI output
description: Generate → Evaluate → Refine; independent evaluators; deterministic checks first; the limits of synthetic judges.
tags: [ai, agents, validation, evals]
timestamp: 2026-08-04T00:00:00Z
---

# Validating AI output

- **Never use agent output without an evaluation stage.** The core loop is
  **Generate → Evaluate → Refine** — the agentic form of TDD / red-green-refactor.
- **Generator ≠ evaluator.** Evaluation is done by a second agent or a rule set; a
  model does not see the flaws in its own work.
- **Deterministic checks first, verifier agents second.** What code can verify,
  code verifies (exact, reproducible, cheap); LLM judgment is reserved for what
  rules cannot capture. At design time, ask whether a conventional test (unit,
  integration, property-based) does the job before reaching for a checker agent:
  a test encodes the criterion once and runs in CI at zero marginal token cost.
  When an agent check keeps applying the same stable criterion run after run,
  promote it to a test (see [code quality](../code-quality.md)).
- **Layer the guardrails**: (1) semantic consistency against the domain's source of
  truth, (2) format validation against a schema — owned by
  [output contracts](output-contracts.md), (3) safety/moderation filters
  before anything reaches users.
- **Evaluate against explicit, shared criteria.** The evaluator must measure
  exactly what the generator optimizes; unwritten criteria mean every evaluation
  measures something different. Define the quality threshold that ends the refine
  loop — work stops when the criterion is met, not when the agent runs out of
  attempts.
- **Overgenerate and filter — when the filter is cheap.** Producing N variants and
  keeping the top k controls quality at scale, but multiplies generation cost by
  N: use it only when the filter criterion is deterministic or cheap, with N
  bounded by the declared [token budget](cost-budgeting.md).
- **Scale the review roster to the cost of the error.** The baseline gate is one
  independent evaluator. Adversarial critics (a second agent hunting
  contradictions against the canonical docs, with a human defining what counts as
  a contradiction) and multi-persona panels (distinct lenses, findings tagged by
  severity, severity escalated when independent reviewers converge) are for
  high-stakes outputs where the cost of a miss justifies the extra spend. These
  are ephemeral review prompts, not maintained agents — they do not count against
  the head-count gate in [scoping](scoping.md).
- **Know the synthetic judge's limits.** Agents verify the formalizable (math,
  logic, edge cases, contradictions); only humans verify the experiential
  (usefulness, clarity, feel). Do not substitute agents for human validation there.
- **Demand side-by-side evidence, not claims** — query → retrieved chunk → output;
  the error and its fix shown, not asserted.
- **Schema-valid ≠ good.** Human value judgment operates on what already passed
  automated validation; it is not replaced by it.
- **Placeholder data invalidates an evaluation**, and "the code runs" is the
  minimum bar, not an achievement — value is measured as fit with the real domain.
- **Validate at the document stage ("shift left" — move checks earlier, where
  fixes are cheapest).** Stress-test specs with synthetic reviewers before
  implementation: reachability and consistency checks, structured error reports
  with actionable targets, and zero credit for generic filler.

Related: [output contracts](output-contracts.md), [human oversight](human-oversight.md),
[code quality](../code-quality.md), [spec / design workflow](../spec-workflow.md).
