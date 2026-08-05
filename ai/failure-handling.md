---
type: Engineering Convention
title: AI failure handling
description: Diagnose before retrying; never let malformed output through; keep raw audit trails.
tags: [ai, agents, debugging, errors]
timestamp: 2026-08-04T00:00:00Z
---

# AI failure handling

- **Diagnose before regenerating.** Blind retries hide the cause; determine
  whether the prompt, the schema, or the data was at fault, then regenerate
  deliberately.
- **Handle the parse failure, don't just prevent it.** The format-validation rule
  itself is owned by [output contracts](output-contracts.md); this file governs
  what happens when it fires: wrap all parsing in error handling, stop the
  pipeline on failure — one bad import can corrupt a project — and treat the
  failure as a diagnostic signal, not a retry trigger.
- **Log and alert, preserving the raw output.** The audit trail enables debugging
  and reveals recurring hallucination patterns.
- **Assume the deterministic stages fail silently.** The scripted parts of an AI
  pipeline (parsers, translators, watchers) give no warning outside their
  programmed states — monitor the gaps they do not cover, which is often exactly
  what the LLM stage was added to handle.
- **Record failures, not just successes.** Failed attempts, errors, and dead ends
  are part of the agent's state, kept so they are not repeated.
- **Close the loop with error feedback.** The refine payload is the original
  output plus the specific error and the criterion it failed — so the agent
  fixes that exact issue instead of regenerating from scratch.
- **Scope the fix to the documented failure.** A refine pass touches only the
  reported issue; guessed, unrelated changes from a refining agent are silent
  regressions waiting to be found.
- **Declare a pass limit before the loop runs.** Refinement gets a fixed number
  of attempts; when they are exhausted, the agent stops and escalates with a
  clear problem statement — what failed, what was tried, why it did not
  resolve. The limit is the failure bound; the success criterion remains the
  quality threshold in [validation](validation.md), and the attempts are paid
  for by the declared [token budget](cost-budgeting.md).
- **When a human debugs with an LLM's help**, follow the protocol: (1) describe
  the problem specifically, not "it doesn't work"; (2) paste the literal error;
  (3) have it read the official docs; (4) verify its answer ("where in the
  docs?"); (5) escalate to other humans with full context — what was tried, the
  error, what the LLM suggested, and why it failed.

Related: [validation](validation.md), [human oversight](human-oversight.md).
