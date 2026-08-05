---
type: Engineering Convention
title: Scoping AI systems
description: The deliverable outranks the pipeline; minimal sufficient mechanism; narrow single-purpose agents.
tags: [ai, agents, scope]
timestamp: 2026-08-04T00:00:00Z
---

# Scoping AI systems

- **The deliverable outranks the pipeline.** Judge AI work by what it ships, not by
  how elaborate the agent architecture is — a sophisticated pipeline that delivers
  nothing is a failure.
- **Use the minimal sufficient mechanism.** Escalate script → rules/heuristics → LLM;
  each step buys generalization at the price of cost and non-determinism. The test:
  before adding an LLM, write down the finite list of input cases a script/rules
  approach would need to enumerate; the LLM is justified only when that list is
  unbounded or not enumerable in advance — record the reasoning in the design doc.
- **Every AI feature needs a validation baseline.** Either a non-AI version it can
  be compared against, or a set of representative cases with expected outputs to
  measure it by. If neither exists, define one before building — a system with no
  baseline cannot be validated, iterated, or shipped reliably.
- **Draw the AI contract explicitly.** State in the design where the system is free
  to generate and where it must reliably adhere to defined rules and constraints.
  Without that boundary, the model's creativity erodes the system's guarantees —
  and the [validation gates](validation.md) have nothing defined to enforce.
- **Scope to the actual gap, not to tool capability.** Ask "what is the biggest
  missing piece?" before deciding what to generate.
- **One agent, one job.** Overloading an agent with responsibilities produces broken
  logic and unpredictable output; roles must be narrow and non-overlapping.
- **Apply the elimination test.** Every agent needs a role, input, and output such
  that removing it breaks the pipeline; if it can be removed without breakage, it
  was redundant.
- **Justify head-count at design time.** A design that puts five or more
  *maintained* agent types on a single developer must justify each one against the
  elimination test in its spec before being built. (Ephemeral review prompts spun
  up for one validation run are not part of this count — see
  [validation](validation.md).)
- **Decompose into atomic tasks** — the smallest independently solvable units —
  before any agent acts, and pick the orchestration model deliberately: sequential
  is predictable but cascades bottlenecks; hierarchical delegation adds parallelism
  and complexity.
- **Prefer minimal transparent orchestration over frameworks.** Adopt a framework
  only once the hand-rolled orchestrator needs at least two of: retries with
  backoff, parallel fan-out/fan-in, persistent state across runs, rate-limit
  handling — and name which ones before adding the dependency. Then learn what
  the framework abstracts (context tracking, rate limiting, tool-output parsing)
  in order to debug it.
- **Design for provider portability.** Keep provider-specific API calls behind the
  system's own typed contracts so models and vendors can be swapped; adopt
  patterns, not a vendor. Model churn (pricing, deprecation, capability shifts)
  is a given, not a risk.
- **Anchor every agent system to a concrete deliverable**, with goals measurable
  enough that the agent can self-check completion.
- **Separate pipeline AI from product AI.** AI in the development pipeline (offline,
  latency-tolerant) and AI inside the product (bound by latency and
  cost-per-interaction) are different engineering problems with different budgets.

Related: [validation](validation.md), [cost budgeting](cost-budgeting.md),
[spec / design workflow](../spec-workflow.md).
