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
- **Close the loop with error feedback.** Return the detected error to the agent
  that produced it for a corrected pass; escalate to a human when it persists.
- **When a human debugs with an LLM's help**, follow the protocol: (1) describe
  the problem specifically, not "it doesn't work"; (2) paste the literal error;
  (3) have it read the official docs; (4) verify its answer ("where in the
  docs?"); (5) escalate to other humans with full context — what was tried, the
  error, what the LLM suggested, and why it failed.

Related: [validation](validation.md), [human oversight](human-oversight.md).
