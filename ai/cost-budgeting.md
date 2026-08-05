---
type: Engineering Convention
title: AI cost budgeting
description: Token budgets before code; projections at scale; cognitive depth matched to the task.
tags: [ai, tokens, cost]
timestamp: 2026-08-04T00:00:00Z
---

# AI cost budgeting

- **Budget tokens before writing code.** LLM cost is a design input to plan, not a
  billing surprise.
- **Project at scale**: per action → per session → per month at N uses; validate
  viability before building.
- **Derive concrete consequences from each constraint** ("60 req/min → max
  throughput 1/s"; "200K context → no pagination needed at this scope").
- **Match cognitive depth to the task.** Reactive (single-call, no planning — e.g.
  classifying a ticket in one shot) is cheap and fast for frequent simple tasks;
  deliberative (the agent plans multi-step work and verifies as it goes) is
  reserved for tasks with two or more dependent sub-steps whose order or output
  affects correctness, or where a wrong answer has a named downstream cost
  (rollback, re-review, incident) exceeding the token-cost difference. State
  which condition applies; choosing wrong wastes budget or quality.
- **Iterate on a cheap model, run production on the strong one** — and mirror
  production parameters when measuring, or the eval measures a different system.
- **Treat inter-agent communication as a cost variable.** Design what context each
  handoff carries; redundant context is paid for on every call.
- **Gate downstream work on dependencies.** An agent does not start until its
  prerequisite input is confirmed valid — wasted generation cycles are pure cost.
- **Pilot with a small batch before running at scale**, and cache whatever
  repeats.
- **Declare the run budget before launching, not after.** Any multi-agent run gets
  a token budget stated up front; if the projection exceeds it, resize the design
  (fewer agents, smaller context, cheaper tiers) before running. Afterwards,
  report actual vs. budgeted — an overrun is a finding, not a footnote.
- **Route models by task type.** Reserve the top model tier for the orchestrating
  loop only — planning, synthesis, final judgment. Verification and judgment
  gates run one tier below; volume work (mapping, drafting, extraction over many
  items) runs on the mid tier; mechanical schema-bound transforms run on the
  small tier. Escalating a stage's tier requires a stated reason.
- **Charge shared context once, not N times.** Fan-out agents that each re-read
  the same corpus pay its input cost per agent — input tokens, not output, are
  where fan-out cost concentrates. Pre-digest shared material once and hand each
  agent the minimal slice its task needs.
- **Stagger the fan-out so the cache works for you.** When many agents share the
  same material, give them an identical prompt prefix and launch a pilot first:
  the pilot writes the shared context into the prompt cache, and the agents that
  follow re-read it at the cheap cached rate instead of paying the fresh-input
  cost N times. The pilot doubles as the small-batch quality gate.
- **Audit the spend by token class after the run.** Fresh input (cache writes),
  cached re-reads, and output are billed differently; a stage that pays a large
  fresh-input cost to produce little output is the first candidate for a cheaper
  tier, a smaller context slice, or a deterministic replacement.
- **Treat media reads as premium tokens.** Images and PDFs cost far more per item
  than text; cap how many an agent may read, and keep media-heavy stages off the
  top tier.

Related: [scoping](scoping.md), [validation](validation.md).
