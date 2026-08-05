---
type: Engineering Convention
title: Goal-oriented agent work
description: Gap analysis against an explicit spec; derived prioritization; rescan loop with fresh perception.
tags: [ai, agents, planning, specs]
timestamp: 2026-08-04T00:00:00Z
---

# Goal-oriented agent work

Give an agent a goal plus the source of truth to diff against — a spec with
acceptance criteria and dependencies per the
[spec / design workflow](../spec-workflow.md) — rather than micro-tasks. Without a
spec, "goal-oriented" degenerates into the agent inventing work. What this
concept adds on top of the spec workflow and
[human oversight](human-oversight.md):

- **Gap analysis first.** The agent scans the real state, compares it against the
  spec — distinguishing what is wired up from what is merely declared but
  unimplemented (stubbed) — and identifies what is missing.
- **Prioritization must be derived and explained.** Order comes from the
  dependency graph, blockers, and declared priority — and the agent shows its
  scoring, so a human can audit why this item is next.
- **Loop with fresh perception.** Re-scan after every action rather than
  following a stale plan; work ends when the spec-vs-reality diff is empty (the
  quality threshold of [validation](validation.md)), not when the agent runs out
  of ideas.

Division of labor and review-against-intent are governed by
[human oversight](human-oversight.md).
