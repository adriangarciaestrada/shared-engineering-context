---
type: Engineering Convention
title: Designing an agent crew
description: The derivation procedure from goal to agent roster — tasks from the spec, roles from output types, pruned by the scoping tests.
tags: [ai, agents, crew, design, planning]
timestamp: 2026-08-04T00:00:00Z
---

# Designing an agent crew

The scoping and contract rules judge a decomposition once it exists; this is
the procedure that produces one. Derive the roster from the goal, in order:

1. **State the goal and its spec** — acceptance criteria and dependencies per
   the [spec / design workflow](../spec-workflow.md). Every later step is a
   derivation from this document; without it there is nothing to derive from.
2. **Run the gap analysis.** Diff the spec against the real state to obtain the
   task list ([goal-oriented work](goal-oriented-work.md)).
3. **Decompose to atomic units and subtract the deterministic.** Split into the
   smallest independently solvable tasks ([scoping](scoping.md)), then remove
   everything a script can do — code is the cheapest agent
   ([validation](validation.md): deterministic checks first).
4. **Group the remaining tasks by output type.** Tasks that produce the same
   kind of artifact under the same criteria form one candidate role — which is
   why agents are defined by their output format
   ([output contracts](output-contracts.md)).
5. **Prune with the scoping tests**: elimination test, no overlapping roles,
   head-count gate.
6. **Write each role's contract and assign its model tier.** Typed I/O and hard
   constraints per [output contracts](output-contracts.md); tier by task type
   per [cost budgeting](cost-budgeting.md) — the top tier stays with the
   orchestrator.
7. **Pick the orchestration and declare the budget.** Sequential, hierarchical,
   or pipeline follows the dependency graph from step 2; the token budget is
   declared before the run, and a pilot batch doubles as quality gate and cache
   warmer.

A crew that cannot be derived this way — roles that answer to no task, or tasks
that trace to no acceptance criterion — is architecture invented ahead of its
need.

Related: [scoping](scoping.md), [goal-oriented work](goal-oriented-work.md),
[output contracts](output-contracts.md), [cost budgeting](cost-budgeting.md).
